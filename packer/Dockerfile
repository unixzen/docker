FROM debian:latest as builder

ARG PACKER_VERSION=1.6.0

RUN set -ex \
  && apt-get update && apt-get install -y \
    curl \
    unzip

RUN curl https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip -o /tmp/packer_${PACKER_VERSION}_linux_amd64.zip \
  && cd /tmp \
  && unzip /tmp/packer_${PACKER_VERSION}_linux_amd64.zip

FROM alpine:latest

ARG TERRAFORM_PROVIDER_VERSION=0.41.1
COPY --from=builder /tmp/packer /usr/local/bin
CMD ["packer"]
