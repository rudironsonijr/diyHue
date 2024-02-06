FROM debian:stable-slim as prod
WORKDIR /opt/hue-emulator

COPY requirements.txt /tmp/pip-tmp/

## Install requirements
RUN apt update
RUN apt install --no-install-recommends -y \
        curl unzip python3-minimal python3-pip python3-dev python3-setuptools gcc \
        openssl nmap psmisc iproute2 bluez bluetooth libcoap3-bin faketime \
        git
RUN pip3 --disable-pip-version-check install --no-cache-dir --break-system-packages -r /tmp/pip-tmp/requirements.txt
RUN apt purge -y python3-pip python3-setuptools
RUN apt autoremove -y
RUN rm -rf /var/lib/apt/lists/*
RUN rm -rf /tmp/pip-tmp

## Expose ports
EXPOSE 80 443 1900/udp 1982/udp 2100/udp
