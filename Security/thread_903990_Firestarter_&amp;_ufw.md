---
title: "Firestarter &amp; ufw"
date: 2008-08-28
forum: Security
---

### Post by emarti on 2008-08-28
I installed firestarter with using synaptic package manager. it works. is there relationship between firestarter and ufw? 

I write this command to sure that firestarter is works correctly. Is this need? 

> sudo ufw enable
Firewall started and enabled on system startup

if not true, firestarter and ufw are different program.

Sorry bad english :)

Respectly from Turkey!

---

### Post by jerome1232 on 2008-08-29
UFW and Firestarter are both front-ends to the default firewall iptables.

They are not aware of each other and will not reflect each others status.

**If** you need a firewall I would use ufw over firestarter, firestarter is a dead project.

---

### Post by hyper_ch on 2008-08-29
do you actually need to alter the default configs for iptables?

---

### Post by rogeriopvl on 2008-08-29
instead of firestarter I would recommend Gufw, it's a graphical front-end to ufw and easy to manage.

htttp://gufw.tuxfamily.org

---

### Post by jerome1232 on 2008-08-29
Along hyper_ch's point I would recommend reading this thread, gives you a better insight on things that actually make your computer more secure. On the average Desktop firewalls aren't a concern

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by emarti on 2008-08-29
Is the ufw sufficiency to protect?

---

### Post by jerome1232 on 2008-08-29
Well are you running any services on your computer in need of protecting?

I don't have any need of a firewall anymore but yes UFW is sufficient for blocking ports, I used to use it to block a few services on my home server from the internet and just allow connections from within my lan.

---

### Post by kat_ams on 2009-11-26
> **jerome1232 said:**
> UFW and Firestarter are both front-ends to the default firewall iptables.

They are not aware of each other and will not reflect each others status.

**If** you need a firewall I would use ufw over firestarter, firestarter is a dead project.

Are you sure... there is nothing on the firestarter website to indicate that it's a dead or even a dying project.

[URL="http://www.fs-security.com/download.php"]http://www.fs-security.com/download.php
[/URL]

Also Firestarter has more features that UFW like RealTime monitoring of incoming and blocked connections.

---

### Post by pbhj on 2009-11-26
> **kat_ams said:**
> Are you sure... there is nothing on the firestarter website to indicate that it's a dead or even a dying project.

[URL="http://www.fs-security.com/download.php"]http://www.fs-security.com/download.php
[/URL]

Also Firestarter has more features that UFW like RealTime monitoring of incoming and blocked connections.

[http://sourceforge.net/mailarchive/message.php?msg_name=alpine.LNX.2.00.0908010914120.12338%40quad.local.lan](http://sourceforge.net/mailarchive/message.php?msg_name=alpine.LNX.2.00.0908010914120.12338%40quad.local.lan)

---

### Post by bodhi.zazen on 2009-11-26
> **kat_ams said:**
> Also Firestarter has more features that UFW like RealTime monitoring of incoming and blocked connections.

UFW has those features as well, it is called logging ;)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

If you want to monitor your network traffic, tell me, what does the information firestarter is telling you mean ?

I advise you use snort ;)

---

### Post by Scholar-code on 2009-11-27
I am facing a issue with ufw, I searched over the forum but, failed to get appropriate solution for this.
The issue is ufw status goes inactive when ever I reboot my PC?
Whenever I enable it, it says "Firewall is active and enabled on system startup" but, it actually never does.
Any suggestions?

---

### Post by bodhi.zazen on 2009-11-27
> **Scholar-code said:**
> I am facing a issue with ufw, I searched over the forum but, failed to get appropriate solution for this.
The issue is ufw status goes inactive when ever I reboot my PC?
Whenever I enable it, it says "Firewall is active and enabled on system startup" but, it actually never does.
Any suggestions?

What makes you think it is not working ?

Did you install another tool to configure your firewall ? If so, they often conflict. For example, if you have firestarter installed it conflicts with ufw.

You would need to remove firestatrer with the purge option.

---

### Post by Scholar-code on 2009-11-28
> **bodhi.zazen said:**
> What makes you think it is not working ?
Actually, when ever I restart my PC, it goes to inactive, when I checked it with 
```

sudo ufw status

```Again I have to enable it, to make it active.

> **bodhi.zazen said:**
> 
Did you install another tool to configure your firewall ? If so, they often conflict. For example, if you have firestarter installed it conflicts with ufw.

Thanks for letting me know that, I did installed firestarter and was using it.
> **bodhi.zazen said:**
> 
You would need to remove firestatrer with the purge option.
Thanks, I will try it. And come up with result. :]

---

### Post by Scholar-code on 2009-11-28
:-] Now it works like charm.
Thank you bodhi.zazen.

---

### Post by bodhi.zazen on 2009-11-28
You are most welcome =)

---

### Post by RT236 on 2010-03-17
> **bodhi.zazen said:**
> You are most welcome =)

Thanks for this discussion.  I had had exactly the same question and had been searching a lot.  I too now removed/purged Firestarter, installed gufw, enabled, and now ufw lists as enabled after a boot.  Thanks!

---

### Post by bodhi.zazen on 2010-03-17
I filed a bug report on this, it remains in the "undecided" category

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/404600](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/404600)

---

### Post by d3v1150m471c on 2010-03-17
> **jerome1232 said:**
> 
**If** you need a firewall I would use ufw over firestarter, firestarter is a dead project.

Dead and still ever effective. I hated ufw. Graphical front-end with 3 options...I'll pass

---

### Post by bodhi.zazen on 2010-03-17
> **d3v1150m471c said:**
> Dead and still ever effective. I hated ufw. Graphical front-end with 3 options...I'll pass

If firestarter works for you there is no reason to change. However if you do develop an issue with firestarter it is unlikely to be resolved as you will see on any of the lists of bug reports, on Ubuntu or otherwise.

So if you have problems with firestarter you may want to look again at ufw / gufw.

If you choose not to use ufw / gufw that is your choice, **but please do not spread mis information about ufw or gufw**. Obviously these tools have many more then 3 options.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by RT236 on 2010-03-17
> **bodhi.zazen said:**
> I filed a bug report on this, it remains in the "undecided" category

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/404600](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/404600)

I just indicated now on Launchpad on your bug report that I have similar bug.  Thx!

---

