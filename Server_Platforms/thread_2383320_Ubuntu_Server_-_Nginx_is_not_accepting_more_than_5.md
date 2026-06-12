---
title: "Ubuntu Server - Nginx is not accepting more than 500 connections per second"
date: 2018-01-23
forum: Server Platforms
---

### Post by agriz2 on 2018-01-23
```
worker_processes auto;
pid /run/nginx.pid;
worker_rlimit_nofile 100000;
error_log /var/log/nginx/error.log crit;
events {
        worker_connections 4000;
        multi_accept on;
        use epoll;
}

http {
        include  /etc/nginx/mime.types;
        sendfile on;
        tcp_nopush on;
        tcp_nodelay on;
        directio 4m;
        types_hash_max_size 2048;

        client_body_buffer_size 15K;
        client_max_body_size 8m;

        keepalive_timeout 20;
        client_body_timeout 15;
        client_header_timeout 15;
        send_timeout 10;

        open_file_cache max=5000 inactive=20s;
        open_file_cache_valid 60s;
        open_file_cache_min_uses 5;
        open_file_cache_errors off;

        gzip on;
        gzip_comp_level 2;
        gzip_min_length 1000;
        gzip_proxied any;
        gzip_types text/plain text/css application/json application/xjavascript text/xml application/xml application/xml+rss text/javascript;

        access_log off;
        log_not_found off;
        include /etc/nginx/conf.d/*.conf;
}

sysctl.conf
net.ipv6.conf.all.accept_ra = 2
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
```


It suddenly reached to 1500 request per second and halted immediately. I restarted nginx.
What is causing such a problem?

---

### Post by coffeecat on 2018-01-23
*Thread moved to **Server Platforms**.*

@agriz2, I've added code tags where appropriate to your post. In order to preserve columnar formatting, please use code tags for code, contents of config files, and terminal output. There's a link in my sig if you don't know how to add BBCode code tags.

---

### Post by agriz2 on 2018-01-23
> **coffeecat said:**
> *Thread moved to **Server Platforms**.*

@agriz2, I've added code tags where appropriate to your post. In order to preserve columnar formatting, please use code tags for code, contents of config files, and terminal output. There's a link in my sig if you don't know how to add BBCode code tags.

Okay sir. I got it

---

