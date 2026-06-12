---
title: "squid security ideas and a strange listeing port"
date: 2009-04-30
forum: Server Platforms
---

### Post by pred2k on 2009-04-30
hi, i installed the squid proxy on my root-server to provide my friends and me a little more browsing anonymity (hiding the private ip-adress).
Also i setup openvpn with certificates for connecting to the root-server and acessing the proxy.
My changes at the squid.conf are:

```
http_port 10.8.0.1:3128
```
other changes at the config where:
```
icp_port 0
htcp_port 0
# disabled logging
access_log none
cache_log none
cache_store_log none

# useless because squid only listen on 10.8.0.1, but whatever
acl vpn src 10.8.0.0/255.255.255.0
http_access allow vpn
http_access allow localhost
...
forwarded_for off
...
# hide the proxy
header_access From deny all
header_access Via deny all
header_access Proxy-Connection deny all
header_access X-Forwarded-For deny all
```

after that netstat -lp | grep squid shows me:
```
tcp        0      0 10.8.0.1:3128           *:*                     LISTEN      30579/(squid)
udp        0      0 *:60628                 *:*                                 30579/(squid)
```
That the heck ist that second udp-Port for? The Status is not LISTEN like the other, but that the Local Adress is * is strange.
The Port is random, is changes in a range at every proxy-restart.
EDIT: OK, i found out that it is used to query dns if icp is used. But how to disable it?

ps aux | grep squid
```
root     30576  0.0  0.0   5080   696 ?        Ss   10:20   0:00 /usr/sbin/squid -D -YC
proxy    30579  0.0  0.2   8296  5764 ?        S    10:20   0:00 (squid) -D -YC
```
why squid is located in a sbin direcotry and is running as root?
what is that process (squid)? Why the brackets?
EDIT: ok, i also find out that processes in ()-Brackets are unprivileged processes. Whatever that means in detail.

Do you have any ideas for securing the proxy or advanceing the anonymity?

---

### Post by pred2k on 2009-05-04
i tried to diable the udp Listen Port by setting
```
udp_outgoing_address 127.0.0.1
```
But after that, the proxy doesn't work anymore.
I also searched the web alot, but still no solution.

Here are my important changes at my squid.conf.
I commented some lines and added a few questions.
```
# listen only on VPN-tun-Device
http_port 10.8.0.1:3128
# i dont use neighbor caches
icp_port 0
htcp_port 0
# No logging
access_log none
cache_log none
cache_store_log none
# Changing the client_netmask resulting that - if logging is activ for some season - the last number if the IP-Adress ist always 0.
client_netmask 255.255.255.0
...
acl vpn src 10.8.0.0/255.255.255.0
http_access allow vpn
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all # Should this be ".. deny all" because i dont use icp?
...
forwarded_for off
header_access From deny all
header_access Via deny all
header_access Proxy-Connection deny all
header_access X-Forwarded-For deny all  # Not the same like "forwarded_for off"?
header_access Server deny all  # What's this header for?
header_access Link deny all  # What's this header for?
#header_access User-Agent deny all  # I dont use it and i dont overwrite the user-Agent. It causes some problems.
# Better use the Extention "User Agent Switcher" for Firefox
#header_access WWW-Authenticate deny all   # I dont use it. htaccess logins wouldn't work anymore.
#header_access Referer deny all  # I dont use it. causes some problems. Better use the Extention "RefControl" for Firefox.
```
There are much more Header-Manipulations, but which make sense and dont cause Problems on many sites?

i'm also intrested to run squid in a chroot jail. but dont know what i need to do. I'm looking for a good howto

---

