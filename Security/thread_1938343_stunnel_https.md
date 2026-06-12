---
title: "stunnel https"
date: 2012-03-09
forum: Security
---

### Post by skippercanfly on 2012-03-09
Hi folks,

I am new at this forum so forgive me if I am posting this in wrong category.

I am trying to setup stunnel and use it for https.

First I created server.crt and server.key with openssl
"openssl req -new -x509 -days 3650 -nodes -out server.crt -keyout server.key"
Then i configured the /etc/stunnel/stunnel.conf
When i try to start the service it always says "You should check that you have specified the pid= in you configuration file"
I have set the location for the pid file. I googled but I couldn't find a solution.

Here is my configuration file.

sslVersion = SSLv3

chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
pid = /stunnel4.pid

socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1

debug = 7
output = /var/log/stunnel4/stunnel.log

[https]
cert=/etc/stunnel/server.crt
key=/etc/stunnel/server.key
accept  = 443
connect = 127.0.0.1:81
xforwardedfor=yes
TIMEOUTclose = 0

Any idea for what i have configured wrong :/ ?

Thnx in advance

ubuntu 11.04
stunnel4

---

### Post by lisati on 2012-03-10
*Thread moved to **Security Discussions**.*

---

