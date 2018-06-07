ARG BASE_IMAGE_TAG=ginkgo2
FROM tmrocha89/xenial-common:${BASE_IMAGE_TAG}
LABEL maintainer="Tiago Rocha<tmrocha89@gmail.com>"

ADD . /edx/app/edx_ansible/edx_ansible
COPY docker/build/mysql/ansible_overrides.yml /
WORKDIR /edx/app/edx_ansible/edx_ansible/docker/plays
RUN /edx/app/edx_ansible/venvs/edx_ansible/bin/ansible-playbook -vvvv mysql.yml \
    -i '127.0.0.1,' -c local \
    -e@/ansible_overrides.yml
WORKDIR /edx/app
