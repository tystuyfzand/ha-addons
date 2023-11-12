# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Execute during the build of the image
ARG INFINITIVE_VERSION BUILD_ARCH
RUN \
	DOWNLOAD_ARCH=`echo ${BUILD_ARCH} |  sed -e 's/aarch64/arm64/g' -e 's/armhf/arm/g' -e 's/armv7/arm/g' -e 's/i386/386/g'` && \
    echo "Downloading from https://github.com/tystuyfzand/infinitive/releases/download/${INFINITIVE_VERSION}/infinitive_linux_${DOWNLOAD_ARCH}" && \
    curl -sSLf -o /usr/bin/infinitive \
    "https://github.com/tystuyfzand/infinitive/releases/download/${INFINITIVE_VERSION}/infinitive_linux_${DOWNLOAD_ARCH}" && \
    chmod +x /usr/bin/infinitive

# Copy root filesystem
COPY rootfs /
