---
title: "Hosting Providers that support Ubuntu"
date: 2006-08-07
forum: Server Platforms
---

### Post by sclough on 2006-08-07
I'm seriously considering moving off of my currently hosted dedicated server and moving to one that runs ubuntu.  I'm currently running FreeBSD.  This is not a FreeBSD vs. ubuntu server thread, I'm just wanting to run ubuntu right now.  Anyway, what I need is a reliable dedicated server.  I admin my own box, so I just lease a dedicated server each month.  I don't need top shelf really fast stuff, but I would like reliable hardware.  I've had a dedicated server with my current hosting provider for over 2 1/2 years with no hardware problems, so I'm very happy but they have raised their rates on new equipment and they don't support ubuntu right now although if I don't find anywhere else, I'll probably just see if they will install it for me since I'm self supporting anyway.

Anyway, short version is that I'm wondering if anybody has any experience with a solid, reliable host that has good rates and supports ubuntu servers.

---

### Post by joncellini on 2006-08-08
Linode does. I've been hosting with them since February and quite happy :)

---

### Post by sclough on 2006-08-08
Thanks for the link, but I'm looking for a dedicated server host, not a VPS.

---

### Post by sclough on 2006-08-10
In case anybody else is interested in this, Hivelocity supports debian and specifically told me they would install ubuntu for me on a dedicated server.  Their site is [http://v2.hivelocity.net/](http://v2.hivelocity.net/) .  They have a pretty good reputation on web hosting talk ([www.webhostingtalk.com)](www.webhostingtalk.com)), and if you check out the adversiting forums there they have a pretty good offer going on now for dedicated servers.  Just FYI for anybody that may be interested...

---

### Post by wdaniels on 2006-09-06
Take a look at [http://dedicated.zentekmedia.com/ordernow.asp](http://dedicated.zentekmedia.com/ordernow.asp)

Very cheap and they will install Ubutu for you.  I was a little concerned because there are relatively few details of the service given on the website and they seem unusually flexible and inexpensive, but so far service has been good, prompt and personal, and I'm very happy with my server :)

No idea yet about the extent or quality of support.

Though it's not mentioned on the site, there is no setup charge.

---

### Post by sclough on 2006-09-07
Wow that price is pretty low :shock: 

I did a quick search on webhostingtalk and didn't see anything about them.  Normally servers with those specs go between $60-70 a month.  What datacenter are then in?  What's the SLA?  

I ended up getting a server from 800hosting.  They are in a good datacenter and have a pretty good reputation.  They wouldn't install ubuntu on it because it was a "desktop" distro.  The did a minimal sarge install for me though and I remoted in, installed ubuntu on another partition, setup grub to boot from that partition and have since blown away the debian install.  So I'm happily running ubuntu server 8) .  They told me it was fine if I did that, but apparently for the initial install they only deal with what they are used to which is Debian, Fedora, Centos and RHEL.

---

