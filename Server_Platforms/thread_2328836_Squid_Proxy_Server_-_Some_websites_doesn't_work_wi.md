---
title: "Squid Proxy Server - Some websites doesn't work with squid"
date: 2016-06-24
forum: Server Platforms
---

### Post by Trustgig on 2016-06-24
I have been successfully using squid on a small home network (Ubuntu 12.04) except for not being able to access certain some adult websites (like redt***, xhams***, ***nhub).

I can ping and download those websites with wget.

```
root@server1:~# wget xhams***.com
--2016-06-24 21:13:05--  http://xhams***.com/
Resolving xhams***.com (xhams***.com)... 88.208.18.30, 88.208.29.24, 2a02:b48:4000:d::1, ...
Connecting to xhams***.com (xhams***.com)|88.208.18.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.3'


    [ <=>                                   ] 57,565       341K/s   in 0.2s


2016-06-24 21:13:05 (341 KB/s) - `index.html.3' saved [57565]
```

But when I try to open those websites with squid, the browser gives me errors.

```


[h=3]Cannot connect to the website[/h][COLOR=#000000][FONT=Segoe UI]Please make sure: 

- You have entered the correct URL. 
- You are connected to the Internet.
- Your firewall is properly configured.
- The website is not encountering any technical problem at the moment.
[/FONT][/COLOR]

[COLOR=#000000][FONT=Segoe UI]Error code 324 (net::ERR_EMPTY_RESPONSE)[/FONT][/COLOR]
```



  
When I alter the browser connection settings to allow for a direct connection with the Internet I can access these sites without problems.  Why is this happening?

---

### Post by SeijiSensei on 2016-06-25
Sounds like you have a blacklist enabled somehow.  Please post your squid.conf file inside [noparse]```

```[/noparse] tags.  Before posting, remove all the comments with this command:
```
grep -v '^#' /etc/squid/squid.conf | grep -v '^$' > squid.conf.clean
```
and post squid.conf.clean.

---

### Post by Trustgig on 2016-06-25
I changed nothing on my vps. It just happened 2 days ago. After that I was using for about 2 years without any problem.

Here is my squid.conf

```


auth_param basic program /etc/webmin/squid/squid-auth.pl /etc/webmin/squid/users

acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
acl passx proxy_auth REQUIRED
acl allip src 0.0.0.0-255.255.255.255
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny !passx
http_access allow allip
http_access deny all
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320
cache_effective_user proxy
http_port 3128
dns_v4_first on
forwarded_for off
cache_effective_group proxy
via off
forwarded_for delete
follow_x_forwarded_for deny all




```

> [COLOR=#4B4B4B][FONT=Roboto]SeijiSensei[/FONT][/COLOR]

---

### Post by Trustgig on 2016-06-25
> **SeijiSensei said:**
> Sounds like you have a blacklist enabled somehow.  Please post your squid.conf file inside [noparse]```

```[/noparse] tags.  Before posting, remove all the comments with this command:
```
grep -v '^#' /etc/squid/squid.conf | grep -v '^$' > squid.conf.clean
```
and post squid.conf.clean.

I can access any website like youtube facebook google yahoo etc... Also I wanna add something. When I was looking for alternative proxy script, I saw glype php proxy script on google, but I didn't let me in. I don't know if this is helpful. 

[TABLE="width: 100%"]
[TR]
[TD="bgcolor: #FFFFFF"]**[www.glype.com](www.glype.com) is protected by BlockScript.**

BlockScript is security software which protects websites and empowers webmasters to stop unwanted traffic.

Your request was blocked because you appear to be accessing this website from a hosting provider network, proxy server, or VPN server.

[/TD]
[/TR]
[/TABLE]

---

### Post by Trustgig on 2016-06-25
> **Trustgig said:**
> I can access any website like youtube facebook google yahoo etc... Also I wanna add something. When I was looking for alternative proxy script, I saw glype php proxy script on google, but I didn't let me in. I don't know if this is helpful. 

[TABLE="width: 100%"]
[TR]
[TD="bgcolor: #FFFFFF"]**[www.glype.com]("http://www.glype.com") is protected by BlockScript.**

BlockScript is security software which protects websites and empowers webmasters to stop unwanted traffic.

Your request was blocked because you appear to be accessing this website from a hosting provider network, proxy server, or VPN server.

[/TD]
[/TR]
[/TABLE]


Now I'm sure this is not it. Because I can access adult websites with tor browser. But with tor browser glype.com is not opening. 

**[www.glype.com](www.glype.com) is protected by BlockScript.**

				BlockScript is security software which protects websites and empowers webmasters to stop unwanted traffic.

				Your request was blocked because you appear to be accessing this website from a Tor exit node.

---

