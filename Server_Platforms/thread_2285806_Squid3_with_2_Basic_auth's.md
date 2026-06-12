---
title: "Squid3 with 2 Basic auth's"
date: 2015-07-08
forum: Server Platforms
---

### Post by dennis48 on 2015-07-08
Hi,

I am running Squid3 with Basic Auth as a reverse proxy, now i want to add another IP/port which needs basic auth.
This is my config (with the second site) :

```

https_port 10.0.0.168:443 accel cert=/etc/ssl/cert.crt key=/etc/ssl/cert.key


auth_param basic program /usr/lib/squid3/basic_db_auth --user squid --password *PW* --md5 --persist


http_port 12900 accel


cache_peer 10.0.0.202 parent 12900 0 no-query originserver name=graylog1api
cache_peer 10.0.0.195 parent 12900 0 no-query originserver name=graylog2api


acl graylogapi myport 12900
cache_peer_access graylog1api allow graylogapi
cache_peer_access graylog2api allow graylogapi
http_access allow graylogapi


http_port 80 accel defaultsite=graylog2.company.x


cache_peer 10.0.0.202 parent 80 0 no-query originserver name=graylog1
cache_peer 10.0.0.195 parent 80 0 no-query originserver name=graylog2
cache_peer 10.0.0.202 parent 12201 0 no-query originserver name=gelf1 round-robin
cache_peer 10.0.0.203 parent 12201 0 no-query originserver name=gelf2 round-robin


acl HTTPS proto HTTPS
acl requireHTTPS dstdomain graylog2.company.x
http_access deny !HTTPS requireHTTPS
deny_info 307:https://%H%R requireHTTPS


acl graylogip myip 10.0.0.168
acl graylog myport 80
acl graylog myport 443
cache_peer_access graylog1 allow graylogip
cache_peer_access graylog2 allow graylogip
#cache_peer_access graylog1 allow graylog
#cache_peer_access graylog2 allow graylog




http_access allow graylog


https_port 12201 accel cert=/etc/ssl/cert.crt key=/etc/ssl/cert.key


auth_param basic children 5
auth_param basic realm Graylog2
auth_param basic credentialsttl 1 minute
auth_param basic casesensitive on
acl gelf myport 12201
cache_peer_access gelf1 allow gelf
cache_peer_access gelf2 allow gelf
acl db-auth proxy_auth REQUIRED
http_access allow db-auth
http_access deny all




https_port 10.0.0.224:443 accel cert=/etc/ssl/cert.crt key=/etc/ssl/cert.key
auth_param basic children 5
auth_param basic realm Graylog2
auth_param basic credentialsttl 1 minute
auth_param basic casesensitive on
acl graylogip2 myip 10.0.0.225
cache_peer_access graylog1 allow graylogip2
cache_peer_access graylog2 allow graylogip2
acl db-auth proxy_auth REQUIRED
http_access allow db-auth
http_access deny all

```

The only thing that isn't working now is the host with 10.0.0.224:443. It is serving data fine, but i get no basic auth.
Does anybody know how to fix this issue?

---

