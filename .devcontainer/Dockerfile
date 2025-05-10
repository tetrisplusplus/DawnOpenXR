# ベースとなるOSはubuntu 25.04を選択
FROM ubuntu:25.04
RUN userdel -r ubuntu

RUN apt-get update \
    && apt-get -y install \
    git g++ cmake \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update \
    && apt-get -y install \
    python-is-python3 \
    libxrandr-dev \
    libxinerama-dev \ 
    libxcursor-dev \
    mesa-common-dev \
    libx11-xcb-dev \
    libxi-dev \
    pkg-config \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ARG USERNAME=shin_yamamoto
ARG USER_ID=1000
ARG GROUP_ID=$USER_ID

RUN groupadd --gid $GROUP_ID $USERNAME \
    && useradd -s /bin/bash --uid $USER_ID --gid $GROUP_ID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
    && chmod 0440 /etc/sudoers.d/$USERNAME 

USER $USER_ID