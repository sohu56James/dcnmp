ARG NGINX_VERSION
FROM nginx:${NGINX_VERSION}

ARG TZ
ARG ALPINE_REPOSITORIES

RUN sed -i "s/dl-cdn.alpinelinux.org/${ALPINE_REPOSITORIES}/g" /etc/apk/repositories

# apk update && install bash
RUN apk update \
        && apk add --no-cache bash bash-doc bash-completion tzdata \
        && cp "/usr/share/zoneinfo/$TZ" /etc/localtime \
        && echo "$TZ" > /etc/timezone \
        && rm -rf /var/cache/apk/*

RUN set -x ; \
    addgroup -g 82 -S www-data ; \
    adduser -u 82 -D -S -G www-data www-data && exit 0 ; exit 1
