---
title: "Could Ubuntu be as Knoppix?"
date: 2005-06-24
forum: The Cafe
---

### Post by tseliot on 2005-06-24
Hi, yesterday I downloaded Knoppix 4 (DVD) and I hadn't tried any Knoppix yet. I think it's an incredible distro as it recognised all my hardware (or at least made it work without bothering me.

1) It didn't ask me anything (well I had to set the English language as  German was the default)

2) I have a nvidia 6200 PCI-E but I didn't want to use the command that allows Knoppix to use the appropriate driver, so it used a generic driver. Not only haven't I had any problem of visualization but also Knoppix centred my LCD monitor automatically (something I have to do everytime I boot Ubuntu instead of Winslows. However I just have to press a button in order to make my monitor centre automatically (so this isn't a dramatical issue)
3)My sound card isn't recognised but it is used by means of atiixp driver (out of the box)
4) The the greatest feature I've found (for my computer): my PATA and SATA harddisks (no distro that I managed to install on my PC is able to do that, at least not out of the box with my motherboard: I've tried Ubuntu, Fedora 3, Mandriva 64 and 32, Xandros, DSL, Kurumin, Debian Sarge 3.1 64 and 32 bit, etc.) are recognised and I can access them just by clicking the links on the desktop. That's amazing for me.

5) In the menu of KDE (3.4.1) there is an option to turn DMA on on the devices you want. This saves me the time to use hdparm command line every time (this way is more user friendly)

6) Lots of programs are installed by default (it's a 4gb DVD) and there are more insteresting features Ican't mention here.

I haven't tried to install it permanently (the usage from live DVD is so smooth that you can almost forget you're using a live DVD). I know Ubuntu Live cd is based on knoppix (a previous version) (please correct me if I'm wrong) and I haven't tried yet.

My question is  could Ubuntu work like Knoppix 4 as far as compatibility (and maybe even ease of use) is concerned (or out-of-the-boxability  ;-) ) ?

It would make things much easier for complete newbies (Kurumin distro has even a program that can be launched while using the livecd in order to install it permanently) and then more experienced users could customise it as they like. Or perhaps a newbie version of Ubuntu based on Knoppix could be released (help requests and problems would be cracked down in this forum).

This is just my thought about Ubuntu, my favourite distro which has the potential to be better and user frendlyier (more than Winslows) even with the most "esotic" hardware.

Please share your thoughts and try Knoppix 4 to see what I mean.

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=tseliot]
1) It didn't ask me anything (well I had to set the English language as  German was the default)[/QUOTE]

I think the Ubuntu live CD is the same way. 

> 
2) I have a nvidia 6200 PCI-E but I didn't want to use the command that allows Knoppix to use the appropriate driver, so it used a generic driver. Not only haven't I any problem of visualization but also Knoppix centred my LCD monitor automatically (something I have to do everytime I boot Ubuntu instead of Winslows. However I just have to press a button in order to make my monitor centre automatically (so this isn't a dramatical issue)

I think its because Knoppix ships with the real Nvidia driver (and I don't know how legal it is in U.S., Knoppix hasn't cared in the past). When I install the real Nvidia driver in Ubuntu the same thing happens.

> 
3)My sound card isn't recognised but it is used by means of atiixp driver (out of the box)

Yeah....fixing the sound system is my biggest hope for Breezy.

> 
4) The the greatest feature I've found (for my computer): my PATA and SATA harddisks (no distro that I managed to install on my PC is able to do that, at least not out of the box with my motherboard: I've tried Ubuntu, Fedora 3, Mandriva 64 and 32, Xandros, DSL, Kurumin, Debian Sarge 3.1 64 and 32 bit, etc.) are recognised and I can access them just by clicking the links on the desktop. That's amazing for me.

Part of that might be the newest kernel....but yeah...thats cool.

> 
5) In the menu of KDE (3.4.1) there is an option to turn DMA on on the devices you want. This saves me the time to use hdparm command line every time (this way is more user friendly)

I wish we would just ship with DMA enabled. I don't know why we dont.

> 
My question is  could Ubuntu work like Knoppix 4 as far as compatibility (and maybe even ease of use) is concerned (or out-of-the-boxability  ;-) ) ?


Well...not as far as the propreitary stuff goes, but for the rest yeah. I think the plan in the future it to make the Live CD the install CD as well....like MEPIS.

---

### Post by weekend warrior on 2005-06-24
> I think the plan in the future it to make the Live CD the install CD as well....like MEPIS. [Gnoppix](http://www.gnoppix.org/) has this ready now.

"Developer version 1.0.1 is out (2005-06-18 )
The Gnoppix project presents developer version 1.0.1. As a new feature the liveCD is now installable, run as bootoption "install" in order to install gnoppix to your harddisk. Download it [here](http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/gnoppix-1.0.1-i386.iso) "

---

### Post by sonny on 2005-06-24
[QUOTE=tseliot]I haven't tried to install it permanently (the usage from live DVD is so smooth that you can almost forget you're using a live DVD). I know Ubuntu Live cd is based on knoppix (a previous version) (please correct me if I'm wrong) and I haven't tried yet.[/QUOTE]
I've tried the Ubuntu Live CD, and I found it heavy, it takes longer than knoppix to load, after the loading everything is perfect, but still have to wait longer.

---

### Post by tseliot on 2005-06-25
I'm downloading Gnoppix right now. I'll post my impressions.

Bye

---

### Post by tseliot on 2005-06-25
well, Gnoppix runs just like Ubuntu (on my PC) as it shows (in system monitor) the Cpu is working at it's 52-56% even if no process is active. This is a problem I managed to solve only in Ubuntu 64 (in Ubuntu 32 the trick doesn't work). (in every other distro (that work on my PC) I didn't find this annoying issue.

I have to be honest: all the distros I've tried can't recognise my full ADSL bandwidth (I'm connected through a router modem netgear) but only half band (almost 600Kbps out of 1.250MBps). Same thing as before: it works only in Ubuntu 64bit after solving the problem with the CPU (a bug known as the double clock CPU speed). Neither Knoppix can make it work.

I guess I'll stick to Ubuntu (even if I can't use KDE due to incompatibility with nvidia drivers of my geforce 6200).

My computer is definetely too new and too Linux unfriendly (at the moment).

---

