# Dockerized MySQL service, running under Supervisord
# (docker.io: morriz/mysql)
#
# expects:
#   -e COLLECTD_HOST={HOST}
#
# VERSION 0.0.1

FROM morriz/service

MAINTAINER Maurice Faber "morriz@idiotz.nl"

# Install MySQL
RUN apt-get -y install mysql-server

# add some stuff to play nicely with docker
ADD /etc/mysql/conf.d/docker.cnf /etc/mysql/conf.d/
ADD /etc/mysql/conf.d/mysqld_safe_syslog.cnf /etc/mysql/conf.d/

# Add startup stuff
ADD /etc/supervisor/conf.d/mysql.conf /etc/supervisor/conf.d/

# and an init script we want to run once on a new data container
ADD /root/init-mysql-data.sh /root/

EXPOSE 22 3306

VOLUME ["/var/lib/mysql"]

CMD ["/usr/bin/supervisord", "-n"]