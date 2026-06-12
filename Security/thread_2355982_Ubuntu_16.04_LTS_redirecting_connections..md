---
title: "Ubuntu 16.04 LTS redirecting connections."
date: 2017-03-18
forum: Security
---

### Post by etrnal on 2017-03-18
So some background on the situation.
I just removed rootkits from my windows pc's 2 days ago and completely wiped all of the hard drives and they are no longer in use.  I did a shred on my desktop hd and switched completely to ubuntu 16.04 LTS yesterday. I decided this morning after installing a new router to monitor wireshark a bit and noticed primarily via wellsfargo.com that I was definitely being redirected still. Not just that but it seems like my connections are all redirected out of the country before they get to the destination. This seems to be happening even after I switched my dns to google servers on this pc and my router.

I'm pretty new to this but it looks like something might be pretty wrong here even if it isn't to do with my dhcp, maybe my router? If anyone could please help point out what might be wrong and how to fix it i would be eternally grateful! Thanks!

*Edit* Also I should include that my router logs are also saying that there is a DDOS spoof attack with my ip address. Which might be completely irrelevant. Also when I was rerouted going to wellsfargo.com it sent me a bunch of packets from ip 72.81.21.200 which i looked up and from what i discovered is a passive dns. Mind you this was primarily noticeable through my ISP's dns. Then I switched to googles dns's and that disappeared but I am still getting redirected.

---

### Post by sgian on 2017-03-19
You can reset your router to default settings, usually with a pin or something on the back.  Then you will need to set your router up again.  After you reset your router, make sure nothing that might be infected, like a modem, windows or android device, connect to the router unless you know it is clean.  Also check for updates for your router firmware.  Somehow your router got infected quickly, either through a device or someone knowing your static IP.

You might want to edit out your ip in your post.  The ip addresses in your post came back with strange results to me.  One is a video game company that went bankrupt in 2003, and another is a company that supposedly sells zero day vulnerabilities to whomever.  You can check for yourself at [https://www.arin.net/](https://www.arin.net/)

---

### Post by etrnal on 2017-03-20
Wow thanks man. Sounds like someones trying to mr.robot me lol.

---

### Post by bashiergui on 2017-03-22
Change the default login password on your router, too. Bots scan the internet incessantly looking for routers they can log into using default credentials and join to a botnet.

---

