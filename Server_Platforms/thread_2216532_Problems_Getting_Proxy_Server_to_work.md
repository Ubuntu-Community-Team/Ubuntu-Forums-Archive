---
title: "Problems Getting Proxy Server to work"
date: 2014-04-12
forum: Server Platforms
---

### Post by dclake on 2014-04-12
Hi everyone, I am running Squid and for some reason I am  having problems getting the proxy server to work. I have activated squid on my server and configured my browser but I am getting an error on the  browser:



ERROR
The requested URL could not be retrieved

The following error was encountered while trying to retrieve the URL: [http://www.google.com/](http://www.google.com/)

    Unable to forward this request at this time.

This  request could not be forwarded to the origin server or to any parent  caches. The most likely cause for this error is that the cache  administrator does not allow this cache to make direct connections to  origin servers, and all configured parent caches are currently  unreachable.

Your cache administrator is webmaster.


How can I fix this?

---

### Post by SeijiSensei on 2014-04-12
You need to post the contents of squid.conf in [noparse]```
[/noparse] tags.  Before doing so I suggest removing any comments in the file like this:
[code]grep -v '^#' /etc/squid3/squid.conf | sed 's/^$//g'
```
That will display only lines that do not begin with a hash tag ("#"); the sed command removes empty lines.

---

### Post by dclake on 2014-04-12
This is the squid.conf file

> 


http_port 0.0.0.0:3128


visible_hostname (frontal)ebox.ibs.lan
coredump_dir /var/spool/squid3
cache_effective_user proxy
cache_effective_group proxy
access_log /var/log/squid3/access.log squid
cache_log /var/log/squid3/cache.log
cache_store_log /var/log/squid3/store.log

pid_filename /var/run/squid3.pid


cache_peer localhost parent 3130 0 no-query proxy-only login=*:nopassword

auth_param basic realm Zentyal HTTP proxy
auth_param basic program /usr/lib/squid3/squid_ldap_auth -v 3 -b dc=ibs,dc=lan -f "(&(uid=%s)(objectclass=posixAccount))" -p 390 -D cn=zentyalro,dc=ibs,dc=lan -w DVCHtryibL7xj7a=Dnwi -P
acl_uses_indirect_client on
acl authorized proxy_auth REQUIRED

acl from_localhost src 127.0.0.0/8 ::1
acl to_localhost dst 127.0.0.0/8 ::1


http_access allow to_localhost
follow_x_forwarded_for allow from_localhost
http_access allow from_localhost
forwarded_for on
log_uses_indirect_client on
always_direct allow to_localhost

never_direct allow all



http_access allow  all


http_access deny all
http_reply_access allow all



---

### Post by SeijiSensei on 2014-04-14
Given the error, I'd guess it has to do with the _direct items.  I don't have any of those directives in the cache I manage for a client.  Also, most configurations include a directive that defines the subnet for the local network and restricts access to the cache to that subnet.  Presumably "http_access allow all"  should make that unnecessary, but it opens you to the possibility that outsiders might be able to push traffic through your cache.

For reference, here is the suggested configuration that comes with the Squid documentation.  This is for version 3.1.10, though most if not all these directives have been in the default for quite some time:

```

acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines
acl SSL_ports port 443
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
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow localhost
http_access deny all
http_port 3128
hierarchy_stoplist cgi-bin ?
coredump_dir /var/spool/squid
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320

```

You'll notice there are no "_direct" items in that list. The "localnet" ACLs restrict access to the RFC1918 private addresses used on most LANs.  If you have a different local subnet, you'd need to add another localnet definition.

---

