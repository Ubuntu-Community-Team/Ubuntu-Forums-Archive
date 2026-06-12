---
title: "Server System Wide HTTP proxy"
date: 2011-12-09
forum: Server Platforms
---

### Post by rubicks on 2011-12-09
I searched several threads on here, but they were all about getting apt to work through a proxy and I want to have it work system wide.

I tried editing ~./bashrc with these two lines <edited for privacy>:
http_proxy=http://<user>:<pass>@<host>:<port>
export http_proxy

Then i tested with this <once again edited for privacy>:

~$ wget whatsmyip.org
--2011-12-09 17:36:32--  [http://whatsmyip.org/](http://whatsmyip.org/)
Resolving <host>... <ipaddress>
Connecting to <host>|<ipaddress>|:<port>... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
2011-12-09 17:36:32 ERROR 407: Proxy Authentication Required.

im using Ubuntu 10.04.3 LTS

---

### Post by rubicks on 2011-12-11
If it helps anyone to help me, this is where I found the bashrc thing, but it didn't work in my case.  Probably because of the authentication.  I tried the way it showed, but it seems like the proxy wants me to log in again or something.

[https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy)

---

### Post by Ms. Daisy on 2011-12-11
Are you using polipo or tor, or is it a web-based proxy? I'm in the process of learning how tor & polipo work, so I can't help you quite yet. But maybe we can help each other.  I'll let you know if I find anything of use in my research.

---

### Post by rubicks on 2011-12-19
its web based.  I got it to work on my laptop running osx, i had to authenticate in the settings and in firefox.

---

