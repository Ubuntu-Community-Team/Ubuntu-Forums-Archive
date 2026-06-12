---
title: "Spare PC as firewall?"
date: 2012-02-19
forum: Security
---

### Post by streetjedi on 2012-02-19
Hello everyone, this is my first post on Ubuntu Forum, hope I'm writing in right category, if not I'm sorry, feel free to move my thread to the right one.

So..the question is...I have a spare PC, Intel CPU 2x2,4GHz, 4GB RAM, HD graphics and audio, HDMI port, 2xLAN card, DVDRW rom, card reader, ATX size and so on.. My plan is to keep running Ubuntu 11.04 on it, and add XBMC and/or MythTV (and hopefully UbuntuTV soon, when Ubuntu 12.04 comes out) and turn it into HTPC. 
But since HTPC won't consume all of system resources I would like to use this PC as a firewall too (at the same time, 24/7). My first idea was to use DevilLinux, but I'm not sure can I run Ubuntu with media center at the same time with it, so I'm asking you if you have some better ideas. This PC will be connected directly to router, and on second LAN card will be switch so I can connect the rest of PCs (both Windows and Ubuntu) in my home LAN. 

Thanks :)

---

### Post by Iowan on 2012-02-19
It's probably just me, but I'd rather have my firewall on a separate, dedicated box.
The folks in the [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") subforum might have better insight.

Moved.

---

### Post by streetjedi on 2012-02-19
Thanks for reply, of course, running a firewall on separate box and from live CD would be much better idea (+ backup server on another box), I can totally agree with you about that, but in this case, for home use, with 8 PCs and without some important data that needs to be kept in safe, lets just consider (thinking of budget) I'd like to have those two functions in the same box for now.

---

### Post by Dangertux on 2012-02-19
Personally, I wouldn't put both in the same box, for the reason that a firewall (particularly with 8 PC's worth of traffic) is going to be doing a lot work , it doesn't go well with another high intensity application like a mediacenter.

Can you do it, sure, would I ? No not really.

Hope this helps.

---

### Post by streetjedi on 2012-02-19
Yeah, it does, but when I tested xbmc, it requires only 70mb of ram, and almost nothing of cpu.  Lan does have 8 PC's, but to be honest...max number of working PC's at the same time is 2 or 3 which are used just for regular web surfing. DevilLinux requires 128mb of ram and 333MHz of cpu, that's why I thought to combine those two functions in one box (2x2.4GHz and 4GB of RAM) until I get new box just for firewall. Policy is going to be drop all, with few exeptions, because it'll be just a test box for now. I know it's not the perfect combo, but I think this box can take it.

---

### Post by Dangertux on 2012-02-19
It will work it just might not perform optimally

---

### Post by streetjedi on 2012-02-19
Yeah, that's possible. Well, there's only one way to find out, hehe  :-) thx for the reply

---

### Post by JKyleOKC on 2012-02-19
FWIW, I'm replying from a box that's my firewall, LAN router, FTP server, VirtualBox host for eight virtual machines, and also serves as my primary workstation. It all "just works" and the only time I see problems is when I'm running a VM that is i/o-bound and takes up more than 100% of my CPU. That "more than 100%" comes from a monitor that doesn't calculate usage of a dual-core CPU properly; if both cores are fully used it reports 200% usage.

This box has a dual-core AMD processor and 3 GB of RAM; if it had less in the way of resources it might not handle the full load as transparently as it does. Also only one of the 8 VMs is ever active at any one time, and most are usually in "saved" state taking no resource other than disk space. The FTP server sees minimal use, also.

What you suggest is quite practical, although not the ideal situation from a security standpoint...

---

### Post by streetjedi on 2012-02-22
> **JKyleOKC said:**
> FWIW, I'm replying from a box that's my firewall, LAN router, FTP server, VirtualBox host for eight virtual machines, and also serves as my primary workstation...

so, you actually connect all your other PCs in network to that box. I suppose you're running Ubuntu on it and some kind firewall (firestarter?). If we ignore HTPC for the momenttt, and I'll use my box as a firewall only, which firewall would you recommend? Which one are you using?

---

### Post by spynappels on 2012-02-22
Firestarter is no longer maintained and is not recommended for use anymore.

You can use IPTables to accomplish what you want, but a little practice is required to get what you want to work. 

If you have no experience with this, you could have a look at using a purpose built installer like Zentyal which installs Ubuntu and allows you to easily set up different services such as a firewall.

Oh, and make sure you bind all services which you do not want to be publically accessible to the LAN NIC rather than the WAN NIC.

Edit: Smoothwall is another option but not Ubuntu based.

---

### Post by streetjedi on 2012-02-22
Yeah, I noticed Firestarter isn't the right thing for this task. I'll try with IPTables, thanks :-)

---

### Post by JKyleOKC on 2012-02-22
> **streetjedi said:**
> so, you actually connect all your other PCs in network to that box. I suppose you're running Ubuntu on it and some kind firewall (firestarter?). If we ignore HTPC for the momenttt, and I'll use my box as a firewall only, which firewall would you recommend? Which one are you using?I'm actually running Xubuntu, which has the XFCE window manager instead of Gnome but is otherwise identical at the o/s level. My firewall is simply the built-in "iptables" capability; I created the rules initially using "webmin" but then manually edited them.

Firestarter, UFW, GUFW, and all the other firewall programs are simply front ends for the iptables capability that's built into the kernel, so the choice of which to use (or whether to use any of them rather than rolling your own rule set) is mostly one of personal preference. Because I'm using this box as the router in addition to being the firewall, I chose to roll my own. However I had already learned how by using a similar setup on a Mandriva box for some eight years, before switching to Xubuntu.

---

### Post by streetjedi on 2012-02-22
That's what I wanted to know, Xubuntu with XFCE or Ubuntu with Gnome, it doesn't really matter as long as it is OS, because box isn't that bad at all, and I would like to have both OS and firewall, instead of just firewall which is running from live CD. I don't want to "spend" all the resources on firewall only, since it can run on some weaker box too.

---

### Post by hunterkasy on 2012-02-23
I run a firewall server in my home that is running smoothwall a linux firewall server

---

