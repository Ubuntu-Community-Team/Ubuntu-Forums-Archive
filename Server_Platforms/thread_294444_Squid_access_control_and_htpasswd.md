---
title: "Squid access control and htpasswd"
date: 2006-11-06
forum: Server Platforms
---

### Post by zds on 2006-11-06
When configuring Squid to use NCSA user authentication (see: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Password_Authentication_Using_NCSA]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Password_Authentication_Using_NCSA") ) you will need the Apache tool htpasswd. If you do not have Apache installed on your system, attempting to execute htpasswd in a terminal will result in "Command not found" because that command is not installed. 

Do not despair.

The apache2-utils package (easy to find by searching Synaptic) will install this (and other) utility bins.

Don't make the mistake I made and attempt to install the enticing alternative package libapache-htpasswd-perl, It (for a reason unknown to me) won't make the utility available.

Relevant portions of my squid.conf:

[I]auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/passwd

acl all src 0.0.0.0/0.0.0.0
acl auth proxy_auth REQUIRED

http_access allow auth
http_access deny ald[/I]

The purpose of this is that it requires the user to authenticate himself to the proxy (via the browser or program interface). In common desktop settings the authentication interface is a standard username/password popup. It's cheap and easy proxy security. 

Good luck.

---

