---
title: "Apache - Accessing multiple virtual hosts locally"
date: 2008-01-27
forum: Server Platforms
---

### Post by four2theizz0 on 2008-01-27
Hi,

I'm hosting multiple domains abc.com, def.com, ghi.com on gutsy and have come across this problem.  Everything runs fine externally, and i can access each domain on its own and it will take me to the directory that the site exists.  I have vpn to my workplace so i can check that from home.  However, when i am at home, i am unable to access anything but the first site in teh cites-enabled directoy, i know that iis how apache defaults when its not working correctly.

So basically I have to go to 127.0.0.1(or whatever my local ip is) and i can only see abc.com no matter what.  

I actually have two questions, how do i make it so i can just type in abc.com as well as how do i access each host separately AND be able to type in abd.com or def.com or ghi.com LOCALLY.

I have read around and seen silimar problems but the fixes have not helped me.

in my /etc/hosts file i have
```
4.2.0.3 abc.com def.com ghi.com
```
4.2.0.3 is the local ip

any help would be greatly appreciated

---

### Post by MJN on 2008-01-27
What you've done should work. You are using a private IP address as your local address I take it (but then why hide it?)

Many routers support NAT loopback i.e. the ability for internal clients to access internal services (machines) using the external WAN IP address. This make things much easier as your clients then behave just like everyone else on the Internet and perform a DNS query and connect to the returned address.

Mathew

---

### Post by four2theizz0 on 2008-02-10
Hey Man,

Just wanted to say thank you, my problem wa sas you suspected....the NAT loopback.

I am using OpenWRT on a linksys router.  I found this link for anyone else having this problem in here....it was just one line in my /etc/firewall.user 

[http://forum.openwrt.org/viewtopic.php?id=4030](http://forum.openwrt.org/viewtopic.php?id=4030)

mbm answered it

Thanks again
:guitar:

---

