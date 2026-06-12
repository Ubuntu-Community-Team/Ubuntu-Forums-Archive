---
title: "Large memory leak in nm-applet?"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hvbakel on 2012-02-11
I'm seeing the memory usage of nm-applet increase by about 2-3 Mb per minute in an up to date Precise, climbing to >200Mb in just an hour after it's started. I think the size/rate of the leak has to do with the number of wireless networks that are detected (60+ at my home). I filed the following bug and it would be great if anyone with the same problem could confirm it: [https://bugs.launchpad.net/bugs/930491](https://bugs.launchpad.net/bugs/930491)

---

### Post by geojorg on 2012-02-11
I have it to.

---

### Post by dino99 on 2012-02-11
wicd is a better choice

---

### Post by mc4man on 2012-02-11
Seems pretty bad - went from 14 - 50 in about 30 min, 16 avail. here

---

### Post by keithpeter on 2012-02-11
Hello hvbakel and all

My testing box is a PC with a wired connection with vanilla Ubuntu install updated today. I ran top and plugged in a Netgear WG111v3 wifi dongle to see what happened.

After an hour, nm-applet was showing 25Mb RES use up from 16Mb RES with the wired connection. 

There are only 3 wifi connections visible here, one of those being mine, so that scales about right at 3Mb per hour per connection. Rebooting and just using wired, the RES remains stable at 16MB. 

With 60+ connections visible, you need a foil helmet :twisted:

I shall add myself to the bug.

@dino99 Might use wicd on a minimal 12.04 install with dwm/dmenu/lightDM/Thunar on a netbook once precise is released. Had problems with it in 10.04.

---

### Post by hvbakel on 2012-02-11
Yeah, no shortage of access points when you're living in a condo...

---

### Post by grahammechanical on 2012-02-11
I also have this. Nm-applet memory usage was at 25% and rising when I checked with Top. What is more I could not disconnect with the nm-applet menu. It would not disconnect either the wired or wireless connection or disable networking or wireless.

I have rebooted and the memory usage is slowly creeping up from under 1% to more than 3%. If I wait long enough I might get an idea of when the menu stops working. Then I will join the bug report.

At more than 9% of 1GB memory usage the nm-applet menu becomes unresponsive and it is not possible to use the menu to disconnect. What is more if the menu is left open then it blinks out of existence briefly and then re-appears.

Regards.

---

### Post by mc4man on 2012-02-11
I've stopped the leak here (80MB/hr before) by downgrading network-manager-gnome to the previous 0.9.1.90-0ubuntu7
Initially did all related network-manager packages to previous, but at least here the package that's causing is just that one

So after 15 min.
doug      4485  0.2  0.4 215844 14884 ?        Sl   17:31   0:00 nm-applet
doug      4869  0.0  0.0   4368   836 pts/0    S+   17:32   0:00 

doug      4485  0.0  0.4 215844 14884 ?        Sl   17:31   0:00 nm-applet
doug      5611  0.0  0.0   4368   836 pts/0    S+   17:46   0:00

Edit: previous is here
[https://launchpad.net/ubuntu/+source/network-manager-applet/0.9.1.90-0ubuntu7](https://launchpad.net/ubuntu/+source/network-manager-applet/0.9.1.90-0ubuntu7)

---

### Post by screaminj3sus on 2012-02-11
> **dino99 said:**
> wicd is a better choice

I used wicd when I wanted a light XFCE install on arch, and I don't see why so many people recommend it over networkmanager. For me the only advantage was less dependencies. Functionality wise networkmanager was better.

---

### Post by ronacc on 2012-02-11
I'm on amd64 with gnome-shell ( repo not ppa ) my network-manager-gnome shows as 9.2.0+git ....0ubuntu1 , showing 6.4 mb mem after 3+hrs , I'm out in the boonies so only 1 wireless network , my own .

---

### Post by mc4man on 2012-02-11
That package is just plain bad here, checking on gnome-shell the mem increase is the same (16 available here

It also does something quite odd here - if I expose the top menu from the indicator (unity), & leave it exposed it will flash every 5 sec's or so. Some of those flashes expose 2 add.menu options. Normally too fast to read, did a screen record and grabbed a frame that shows in vlc
(probably not related to mem use though at best weird, the 2 'flashing' options are 'enable Mobile & enable Wimax..

---

### Post by prana on 2012-02-11
I am running into the same issue and added a me too to the bug report. What is the process to downgrade the network manager package and keep it downgraded until this is resolved?

Thanks.
Prana

---

### Post by VinDSL on 2012-02-11
> **dino99 said:**
> wicd is a better choice
+1

> **screaminj3sus said:**
> I used wicd when I wanted a light XFCE install on arch, and I don't see why so many people recommend it over networkmanager.
Currently using 4.5 MB  :)

---

### Post by screaminj3sus on 2012-02-11
> **VinDSL said:**
> +1


Currently using 4.5 MB  :)

[img]http://i.imgur.com/fQGXE.png[/img] :P

This memory leak is a bug in alpha software, normally networkmanager doesn't use much resources.

---

### Post by VinDSL on 2012-02-11
> **screaminj3sus said:**
> 
This memory leak is a bug in alpha software, normally networkmanager doesn't use much resources.
Forgot to mention...

Reason #2:  

network-manager doesn't work on this machine, e.g. no network connections, Lan or Wan.

Works fine on Linux 3.1 kernel, but not on Linux 3.2 kernel (Ubuntu patched nor Liquorix).

Actually, I *think* I'm going to stick with Wicd.  I've grown to like it!

Anyway, I don't want to hijack the thread.  Just agreeing with dino...

---

### Post by prana on 2012-02-16
Seems to be fixed now with the latest updates. Can anyone else confirm?

---

### Post by mc4man on 2012-02-17
> **prana said:**
> Seems to be fixed now with the latest updates. Can anyone else confirm?
Here it also seems pretty much fixed, now very small increase of no real concern.
Previously with 16 -20 avail. it was a steady 1MiB+ per min

---

### Post by IPEX-731BA5DD06 on 2012-02-17
Not fixed for me;

it loaded the applet fine, no need to prompt it too.

But memory leak still there, up to 502 Mb's and climbing, when I killed the applet.

Can't edit network connections either.

---

### Post by cariboo on 2012-02-17
@IPEX~, you neglected to tell us what type of network connection you are using, is it wired, or wireless?

---

### Post by IPEX-731BA5DD06 on 2012-02-17
sorry, using a mobile broadband connection, 3G, it actually reached 1.7 Gig of memory another time while I was playing a game that hung, only found out by accident. This was using Precise 12.04, this seems to get the worst of it.

1st time I've seen the swap file actually used!!!

Applet connects automatically, but still grabbing all the memory it can. Had a look at the memory map for the applet, seems to be loading everything x 3 at least some even more. Using Oneiric 11.10, I have dual boot.

---

### Post by JordanH on 2012-02-24
Hi guys,

edit 2:  *awwww* crud, sorry, found this thread through a search and didn't notice it was in Ubuntu +1 forum.  Sorry, my post is irrelevant.

I've been noticing the nm-applet memory leak for a long while now.  I'm up to date on Ubuntu 11.04, running GNOME Desktop v 2.32.1

nm-applet runs away with memory; It's been up 6days 14:53 and is using 653M resident, 995M virtual.  I have had this up well over 1GB.

A secondary issue that may be related, is that it won't let me switch wifi networks; Perhaps because of open connections but it behaves like I don't have authority to do that.  If I kill nm-applet, then restart it, I can log into one network, then switch to a second no problem but after a certain amount of time it locks up again.

Edit: Point being it's not fixed yet and we're still seeing issues.

---

