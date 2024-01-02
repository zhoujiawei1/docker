# 使用基础镜像
FROM opencloudos/opencloudos:8.8

#MAINTAINER 维护者信息
LABEL MAINTAINER="zhoujiawei"

# 设置工作目录
WORKDIR /app

# 安装依赖和运行环境
RUN yum update -y && yum install -y \
        tar gzip zip unzip wget curl openssl openssl-devel \
        gcc gcc-c++ make autoconf automake libtool \
        python3 python3-pip \
        protobuf perf
RUN yum clean all

# 安装 gperftools
RUN wget -O gperftools-2.13.tar.gz https://github.com/gperftools/gperftools/releases/download/gperftools-2.13/gperftools-2.13.tar.gz
RUN tar zxvf gperftools-2.13.tar.gz
RUN cd gperftools-2.13 && ./configure && make && make install

#安装 boost
RUN wget -O boost_1_84_0.tar.gz https://archives.boost.io/release/1.84.0/source/boost_1_84_0.tar.gz
RUN tar zxvf boost_1_84_0.tar.gz
RUN cd boost_1_84_0 && ./bootstrap.sh && ./b2 install

# CMD
CMD ["/bin/bash", "-c", "while true; do echo 'Docker container is running...'; sleep 10; done"]
