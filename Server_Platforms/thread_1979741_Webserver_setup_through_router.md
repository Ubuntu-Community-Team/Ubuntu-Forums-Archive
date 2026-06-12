---
title: "Webserver setup through router"
date: 2012-05-14
forum: Server Platforms
---

### Post by chorvath on 2012-05-14
I have a Ubuntu server with PHP, Apache2 and all of that setup and working *on my LAN*.Meaning from any computer connected to the same router I can connect to 10.0.0.3 (My server). I have setup my router to forward requests at port 80 to 10.0.0.3 but when I try to connect to my (router)IP address 69.244.36.144 I get a "Connection was reset" error. Any clues to what I am doing wrong?[SIZE=1][/SIZE]

---

### Post by Tylerjd on 2012-05-14
Using the IP address that you gave, I got an It Works! Apache default page, so I would assume that you fixed it. 

On thing I would suggest when trying to test that kind of stuff is to use a device outside of that network, so say a smartphone on 3G or your friend's computer at their house.

---

### Post by chorvath on 2012-05-14
Thanks for the quick reply!

If that is true, then it is working and it is just my LAN that makes it not work.

---

### Post by volkswagner on 2012-05-14
Since it is not working on you LAN, it is likely a NAT issue.  You may be able to change the NAT setting on your Router.  

This may not be a big deal now, but if you want to use a domain name, you may want to be able to access from inside your land using a fully qualified domain name.

NAT settings may be found in the security tab on your router config.

---

### Post by Jonathan L on 2012-05-14
Hi Chorvath

> my router to forward requests at port 80 to 10.0.0.3 but when I try to connect to my (router)IP address 69.244.36.144 I get a "Connection was reset" error. Any clues to what I am doing wrong?I'm presuming you have your laptop on the same inside LAN, perhaps 10.0.0.192, and router as perhaps 10.0.0.1.

Are you trying to connect to 69.244.36.144 from 10.0.0.192?  It's quite usual for this not to work, for reasons which vary with the details of the router's setup.  Sometimes the router thinks 69.244.36.144 is itself, and it isn't running a web server, so you get an error.

From the same LAN, it's much more usual to connect to it directly ie at 10.0.0.3.  

As volkswagner says, watch for domain names.  When you have this set up in public as, perhaps,

```
www.yourdomain.com. A 69.244.36.144
```Then you won't be able to browser to it from your LAN.  The fix is normally either

[LIST=1]
[*]Run DNS internally with internal numbers ([www.yourdomain.com]("http://www.yourdomain.com"). A 10.0.0.3) which can be a lot of effort if you only have one or two servers
[*]Add entries in your /etc/hosts of your laptops, which is quick and easy unless you've got a lot of laptops
[/LIST]

Hope that's helpful.

Kind regards,
Jonathan.

---

