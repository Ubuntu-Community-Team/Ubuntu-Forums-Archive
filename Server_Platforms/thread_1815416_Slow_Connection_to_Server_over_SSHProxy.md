---
title: "Slow Connection to Server over SSH/Proxy"
date: 2011-07-31
forum: Server Platforms
---

### Post by NamiJason on 2011-07-31
Im running Ubuntu 10.04, currently living out of the country from where my server is located.  We have a 4 Mbps dsl connection that speedtests fine to the closest server, and if we test from our present location to the speedtest.net server closest to our server the speed is great as well.  

When I SSH in to my server and setup a socks 5 proxy the speed goes through the floor.  We barely get .2 Mbs.  Whether I use putty or terminal from our mac, they both get the same slow speed.  

I've searched the forums and google extensively, but I haven't been able to come up with anything yet.  Any help to get me moving in the right direction would be appreciated.

---

### Post by pclausen on 2011-08-14
I had (and have) almost the same problems. Mine is that ssh in intranet is slow but internet acess quite OK, which does not really make sense... Anyways here goes my findings

Issues:
1) Disable ipv6 [www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html]("www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html") This enhanced speed quite a bit

2) In /etc/ssh/sshd_config set
```

UseDNS no 
```
This enhanced my login time

3) I had an issue with my /etc/hosts file - check that its correct

I still suspect that my intranet ssh slows down after some uptime, but I cant figure out which process is bugging me - at least after doing the above I have full speed after reboot...

---

### Post by HermanAB on 2011-08-14
Howdy,

My tricks:
1. Select the Blowfish cypher.
2. Compress the headers.
3. Change the default MTU size of the ethernet adaptor from 1500 bytes to 1000 bytes.

Hope that helps!

---

