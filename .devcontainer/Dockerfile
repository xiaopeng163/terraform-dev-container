FROM python:3.9-bullseye

ARG TARGETARCH

ENV OS_ARCH="${TARGETARCH:-amd64}" \
    TERRAFORM_VERSION="1.2.9"
ENV TZ Europe/Amsterdam
ENV SHELL /bin/bash

RUN pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir pre-commit

# install tflint
RUN curl -s https://raw.githubusercontent.com/terraform-linters/tflint/master/install_linux.sh | bash

# install terraform
RUN curl \
    --location \
    --output /tmp/terraform.zip \
    https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_${OS_ARCH}.zip \
    && unzip /tmp/terraform.zip -d /usr/local/bin \
    && rm -rf /tmp/terraform.zip

COPY config/bashrc /root/.bashrc
