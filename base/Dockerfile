############################################
# version : centos/base:v1
# desc : 当前版本安装的ssh，wget，curl，supervisor 
############################################
# 设置继承自centos官方镜像
FROM centos

# 下面是一些创建者的基本信息
MAINTAINER io@centos.net

# 注意这里要更改系统的时区设置，因为在 web 应用中经常会用到时区这个系统变量，默认的 ubuntu 会让你的应用程序发生不可思议的效果哦
ENV DEBIAN_FRONTEND noninteractive

RUN yum -y update &&\
    yum install -y vim wget curl


# 安装supervisor工具
RUN yum -y install python-setuptools &&\
    easy_install supervisor &&\
    mkdir -p /var/log/supervisor

# 添加 supervisord 的配置文件，并复制配置文件到对应目录下面。（supervisord.conf文件和Dockerfile文件在同一路径）
ADD supervisord.conf /etc

# 执行supervisord来同时执行多个命令，使用 supervisord 的可执行路径启动服务。
CMD ["/usr/bin/supervisord","-c","/etc/supervisord.conf"]
