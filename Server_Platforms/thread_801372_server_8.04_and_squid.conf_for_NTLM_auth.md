---
title: "server 8.04 and squid.conf for NTLM auth"
date: 2008-05-20
forum: Server Platforms
---

### Post by turbolad on 2008-05-20
Hi all,

This is my first proper go with a Linux distro so go easy on me.

OK what I want to do is make a Proxy Server which I can assign rights through Active Directory Groups.

Progess so far is I have squid and dansguardian working.
I have also managed to add the Ubuntu Server to my Windows 2003 Domain. I can run all the necessary wbinfo commands - which work.

What I can't do is get squid.conf to do any sort of authentification. When I try, the proxy just gives me no internet access on my windows box. Any tutorials or output's I've found have been for older versions of squid and apparently some of the commands aren't supported now?

Edit:
Here is my squid.conf (im using lastest samba, squid, dansguard, everything) I get no errors when restarting my squid with this file but nothing shows up on Internet Explorer.
```
auth_param ntlm program /usr/lib/squid/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param basic program /usr/lib/squid/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours

auth_param ntlm program /usr/lib/squid/ntlm_auth --helper-protocol=squid-2.5-ntlmssp --require-membership-of="DOMAIN\Domain Users"
auth_param basic program /usr/lib/squid/ntlm_auth --helper-protocol=squid-2.5-basic --require-membership-of="DOMAIN\Domain Users"
auth_param ntlm children 5

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl ntlm_users proxy_auth REQUIRED
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access allow ntlm_users
http_access deny all
icp_access allow all
http_port 3128
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
hosts_file /etc/hosts
coredump_dir /var/spool/squid

```

---

### Post by turbolad on 2008-05-21
Anyone any Ideas?

---

### Post by turbolad on 2008-05-22
Anyone? :(

---

### Post by turbolad on 2008-05-23
helloooooooooooooooooooooooooooooooooooooooooo
{waits for echo to come back}

---

### Post by lunatico on 2010-03-18
> **turbolad said:**
> helloooooooooooooooooooooooooooooooooooooooooo
{waits for echo to come back}

hello hello hello hello..... ;)

---

