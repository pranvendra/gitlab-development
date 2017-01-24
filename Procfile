# GDK Procfile rules to help foreman shut down services:
# - all commands must start with 'exec'
# - no inline shell scripts ('&&' or ';')
#
redis: exec redis-server /home/kmadmin/final/gitlab-development-kit/redis/redis.conf
postgresql: exec support/postgresql-signal-wrapper /usr/bin/postgres -D /home/kmadmin/final/gitlab-development-kit/postgresql/data -k /home/kmadmin/final/gitlab-development-kit/postgresql -h ''
#postgresql-replica: exec support/postgresql-signal-wrapper /usr/bin/postgres -D /home/kmadmin/final/gitlab-development-kit/postgresql-replica/data -k /home/kmadmin/final/gitlab-development-kit/postgresql-replica -h ''
#openldap: exec support/exec-cd gitlab-openldap libexec/slapd -F slapd.d -d2 -h "ldap://$host:3890"
gitlab-workhorse: exec /usr/bin/env PATH="/home/kmadmin/final/gitlab-development-kit/gitlab-workhorse/bin:$PATH" gitlab-workhorse -authSocket /home/kmadmin/final/gitlab-development-kit/gitlab.socket -listenAddr $host:$port -documentRoot /home/kmadmin/final/gitlab-development-kit/gitlab/public -developmentMode -secretPath /home/kmadmin/final/gitlab-development-kit/gitlab/.gitlab_workhorse_secret
rails-web: exec /usr/bin/env RAILS_ENV=development support/exec-cd gitlab bin/web start_foreground
rails-background-jobs: exec /usr/bin/env SIDEKIQ_LOG_ARGUMENTS=1 RAILS_ENV=development support/exec-cd gitlab bin/background_jobs start_foreground
#influxdb: exec influxdb/bin/influxd -config influxdb/influxdb.conf
#grafana: exec support/wait-postgresql-ready support/exec-cd grafana bin/grafana-server -config grafana.ini
#sshd: exec /usr/sbin/sshd -e -D -f /home/kmadmin/final/gitlab-development-kit/openssh/sshd_config
#nginx: exec nginx -p /home/kmadmin/final/gitlab-development-kit/nginx -c conf/nginx.conf
#gitaly: exec /usr/bin/env GITALY_SOCKET_PATH=/home/kmadmin/final/gitlab-development-kit/gitaly.socket GITALY_PROMETHEUS_LISTEN_ADDR=:9101 gitaly/bin/gitaly
