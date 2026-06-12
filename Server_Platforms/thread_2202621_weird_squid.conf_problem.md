---
title: "weird squid.conf problem"
date: 2014-01-30
forum: Server Platforms
---

### Post by sububtu on 2014-01-30
Hi. . . 
i had configured squid3 as transparent proxy.The proxy is working perfectly, But have some weird problems
Iam not able to connect FTP clients from host machines,
iam not able to use any chats/messengers from clients (ie from mobile: apps like whatsapp, or any other messengers)
ill post the uncommented squid.conf file pls help

acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8


acl SSL_ports port 443
acl purge method PURGE
acl CONNECT method CONNECT
acl ftp proto FTP
acl ftp_port port 21


http_access allow manager localhost
http_access deny manager


http_access deny CONNECT !SSL_ports

http_access allow purge localhost
http_access deny purge


http_access allow localnet
http_access allow localhost
http_access allow ftp_port CONNECT
http_access allow ftp
always_direct allow ftp


http_access allow


icp_access allow all

htcp_access allow all


http_port 4239 transparent


cache_dir ufs /var/spool/squid3 3000 16 256


coredump_dir /var/spool/squid3


refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320



visible_hostname proxyserver1

---

### Post by SeijiSensei on 2014-01-30
Do you have an iptables rules to push port 21 traffic through the proxy like you have for port 80?

---

### Post by sububtu on 2014-01-30
> **SeijiSensei said:**
> Do you have an iptables rules to push port 21 traffic through the proxy like you have for port 80?

I havnt touched the iptables yet, And i dont know how to do it!!!!

---

### Post by SeijiSensei on 2014-01-31
How are you running a transparent proxy then?

My Squid boxes have an iptables rule like this:
```
/sbin/iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```
That intercepts outbound web traffic on port 80 and pushes it to Squid listening on localhost:3128.  That's what makes this a "transparent" proxy.  You don't need to configure the client browsers to use the proxy; it's handled automatically by iptables.

I hate FTP and avoid it like the plague.  Still if it is supposed to be transparent as well, I would think you'd need to push outbound port 21 requests through Squid in a similar way.

---

