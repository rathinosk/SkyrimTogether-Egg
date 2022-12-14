FROM         ubuntu:jammy

LABEL        LABEL author="Torsten Widmann" maintainer="info@goover.de" repository="https://github.com/PteroForge/pterodactyl-images"
LABEL        LABEL comment="This Dockerfile was copied to https://github.com/Technoguyfication/SkyrimTogether-Egg for archival purposes"

ENV           DEBIAN_FRONTEND noninteractive

RUN           useradd -m -d /home/container -s /bin/bash container
RUN           ln -s /home/container/ /nonexistent
ENV           USER=container HOME=/home/container

## Update base packages
RUN           apt update \
              && apt upgrade -y

## Install dependencies
RUN           apt install -y gcc g++ libgcc1 lib32gcc-s1 libc++-dev gdb libc6 git wget curl tar zip unzip binutils xz-utils liblzo2-2 cabextract iproute2 net-tools netcat telnet libatomic1 libsdl1.2debian libsdl2-2.0-0
RUN           apt install -y libfontconfig libicu67 icu-devtools libunwind8 libssl-dev sqlite3 libsqlite3-dev libmariadbclient-dev-compat libduktape205 locales ffmpeg gnupg2 apt-transport-https software-properties-common ca-certificates
RUN           apt install -y liblua5.4-0 libz-dev rapidjson-dev tzdata libstdc++6

## Configure locale
RUN          update-locale lang=en_US.UTF-8 \
             && dpkg-reconfigure --frontend noninteractive locales

WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
