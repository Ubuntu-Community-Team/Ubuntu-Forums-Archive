---
title: "Does Ubuntu UFW limits incoming connections?"
date: 2018-01-23
forum: Server Platforms
---

### Post by agriz2 on 2018-01-23
My Ubuntu 16.04 server has Nginx.
Nginx settings are seems to be good.

I have already tweaked the network settings for sysctl.conf to increase incoming connections.
But i am not getting more than 500 connections per second.

Sometimes suddenly the traffic cross the level to 1500 visitors/sec and makes the system to stop responding.
Please tell me how to troubleshoot this problem

The sysctl.conf settings are 

```

net.ipv6.conf.all.accept_ra=2
net.core.rmem_max = 16777216
net.core.rmem_default = 31457280
net.ipv4.tcp_rmem = 4096 87380 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_wmem = 4096 16384 16777216
net.ipv4.tcp_mem = 65536 131072 262144
net.ipv4.udp_mem = 65536 131072 262144
net.ipv4.udp_rmem_min = 16384
net.ipv4.udp_wmem_min = 16384
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_fin_timeout = 20
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_tw_reuse = 1
net.core.netdev_max_backlog = 10000
net.core.somaxconn = 4096
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.ip_local_port_range = 15000 61000
kernel.pid_max = 65535
fs.inotify.max_queued_events = 2000000
net.ipv4.tcp_keepalive_time = 300
net.ipv4.tcp_keepalive_probes = 5
net.ipv4.tcp_keepalive_intvl = 15
net.core.optmem_max = 25165824
vm.swappiness = 10
vm.dirty_ratio = 60
vm.dirty_background_ratio = 2
fs.inotify.max_user_watches=100000

```

---

### Post by LHammonds on 2018-01-24
> Does Ubuntu UFW limits incoming connections?
UFW is a front-end interface for iptables...it isn't the firewall itself.

Check to see if your rules include RATE-LIMIT or RECENT or CONNLIMIT-ABOVE or UPDATE.

Reference articles:
 * [RATE-LIMIT]("https://making.pusher.com/per-ip-rate-limiting-with-iptables/")
 * [RECENT]("http://www.microhowto.info/howto/limit_the_rate_of_inbound_tcp_connections_using_iptables.html")
 * [CONNLIMIT-ABOVE]("https://www.cyberciti.biz/faq/iptables-connection-limits-howto/")
 * [UPDATE]("https://debian-administration.org/article/187/Using_iptables_to_rate-limit_incoming_connections")

Articles related to limiting connections to Nginx:
 * [Nginx manual - limit_conn]("http://nginx.org/en/docs/http/ngx_http_limit_conn_module.html?&_ga=2.147121584.666134236.1516794253-1198074100.1516794253#limit_conn")
 * [Nginx manual - limit_rate]("http://nginx.org/en/docs/http/ngx_http_core_module.html?&_ga=2.151774782.666134236.1516794253-1198074100.1516794253#limit_rate")
 * [Nginx manual - limit_req, limit_req_zone]("http://nginx.org/en/docs/http/ngx_http_limit_req_module.html?&_ga=2.151774782.666134236.1516794253-1198074100.1516794253#limit_req")
 * [Nginx manual - max_conns]("http://nginx.org/en/docs/http/ngx_http_upstream_module.html?&_ga=2.151774782.666134236.1516794253-1198074100.1516794253#max_conns")
 * [Nginx manual - queue]("http://nginx.org/en/docs/http/ngx_http_upstream_module.html?&_ga=2.252972814.666134236.1516794253-1198074100.1516794253#queue")
 * [limit_conn_zone]("https://www.nginx.com/resources/admin-guide/restricting-access/")
 * [limit_req_zone, limit_req]("https://www.nginx.com/blog/rate-limiting-nginx/")
 * [Tuning NGINX for Performance]("https://www.nginx.com/blog/tuning-nginx/")

LHammonds

---

