---
title: "&quot;Waiting for network configuration&quot; error live DVD or USB"
date: 2014-01-19
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2014-01-19
I'm trying to install Lubuntu trusty daily iso on an old Acer Travelmate laptop, celeron cpu, 512MB ram, ATI 9000M graphics, which runs earlier versions up to 12.10 easily (not tried 13.04 or 13.10) and the boot to live system always fails with the system freezing at "Waiting for network configuration".

I have tried with a wired network, and with wireless adapter unplugged, and I have waited for a long time but nothing ever happens.

Anyone got any ideas how to get the live system to boot on this machine; is there a way to avoid the network configuration happening at live bootup stage, or am I just going to have to accept defeat?

---

### Post by sudodus on 2014-01-22
This might be a temporary bug in the daily build or a driver problem with the ethernet chip. What chip is it?

Have you tried the same iso in another computer?

Or tried the Ubuntu mini iso, that uses a different way to configure the network?

---

### Post by ajgreeny on 2014-01-22
Is there a mini iso of 14.04?  I couldn't find one when I looked.

---

### Post by sudodus on 2014-01-22
[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/57691/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/57691/downloads)

It is a little confusing, but I think the netboot iso is an alias for the mini iso (and vice versa)

Furthermore, it is probably not updated daily as the desktop isos, but anyway, I think it can be worth testing.

---

### Post by ajgreeny on 2014-01-22
Now the link to the iso on that page you linked to is giving me a 
> Not Found
The requested URL  /ubuntu/dists/trusty/main/installer-i386/20101020ubuntu278/images/netboot/mini.iso  was not found on this server.

error.  What is going on?

PS:
The ethernet chip is a Realtek RTL-8139 which has always worked fine so far in the versions I have thrown at it.  Wireless is a Netgear WG511v2 which needs ndiswrapper to work, and is working fine in all the versions so far where I have tried it, up to 12.10.

---

### Post by howefield on 2014-01-22
> **ajgreeny said:**
> Now the link to the iso on that page you linked to is giving me a error.

Try one of these..

```
http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/devel/main/installer-i386/current/images/netboot/mini.iso
```
```
http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/devel/main/installer-amd64/current/images/netboot/mini.iso
```

---

### Post by sudodus on 2014-01-23
Sorry, the link was goofed, it contained a double http:// for some reason. I fixed it last night, and it should work now. So you should be able to get the current trusty mini iso either from there or from *howefield*'s links

I think it is a bug in the daily build, that needs to be reported to be fixed. If noone has reported it to Launchpad already, maybe you have time to do it :-)

---

### Post by ajgreeny on 2014-01-24
OK, bug filed at [Bug #1272429 &#8220;Trusty daily live ISOs will not boot; &#8220;Waiting for...&#8221; : Bugs : Ubuntu]("https://bugs.launchpad.net/ubuntu/+bug/1272429")

---

### Post by ajgreeny on 2014-03-31
A quick update after trying many times to get 14.04 working on this old laptop.

I kept trying new versions of the trusty iso updated with zsync, used the alternate install CD, and finally used the mini install iso, and not one of them managed to boot to a working system.

As very much a last resort I installed lubuntu 13.10, updated it fully then used the alternate install CD to update the saucy to trusty.
At reboot I had the same problem as before.
So I rebooted and chose the 13.10 kernel in grub, which at last led to a successful boot to the GUI, and a fully working system.

So, it seems that it is kernel 3.13.0-# that is the problem for my hardware. I have no idea what is behind that difficulty, as none of my other machines have had any hint of a problem, just this celeron with the ATI 9000M graphics.  I even tried the boot option ```
live video=radeonfb:1024x768-32@60
``` as found at [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC) just as a final attempt to boot but that did not help in any way.

Anyway, I now have 14.04 running well but with the 3.11.0-# kernel.  I will shortly attempt to install the new 3.14 kernel final release to see if that is any more successful.

EDIT:
I have just installed the 3.14 kernel, but it was a complete failure, just the same as the 3.13 version, so I appear to be stuck with the 3.11 default from saucy, which luckily works well.

I have tried to update the bug I filed but it is now expired so am unable to do so.

---

