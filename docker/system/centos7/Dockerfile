# Docker for Centos
#Base image
FROM centos
#whio
MAINTAINER tanghao@topshifts.com

#EPEL
ADD epel.repo /etc/yum.repos.d/
ADD sysctl.conf /etc/
#ADD ssh_config /etc/ssh/
#ADD sshd_config /etc/ssh/
ADD limits.conf /etc/security/

#Base pkg
RUN yum install -y openssh-clients openssl-devel openssh-server wget gcc gcc-c++ vim tree supervsor net-tools bash-completion bzip2 bzip2* curl curl-devel net-tools sudo psmisc python-devel python-pip && yum clean all

#For SSHD
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key
RUN useradd dlr
RUN echo "dlr:ablejava" | chpasswd
RUN echo "dlr     ALL=(ALL)       NOPASSWD: ALL" >> /etc/sudoers

#ssh file
#ADD sshd_config /etc/ssh/
#ADD ssh_config /etc/ssh/

#qi dong
RUN mkdir /var/run/sshd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
