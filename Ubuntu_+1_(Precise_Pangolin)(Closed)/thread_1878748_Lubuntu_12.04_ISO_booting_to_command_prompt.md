---
title: "Lubuntu 12.04 ISO booting to command prompt?"
date: 2011-11-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jerrylamos on 2011-11-10
I've got Precise Pangolin upgraded from a fresh install of Ubuntu Ocelot Unity-2D working O.K. so far, probably not much changed code in Pangolin.  Response is a little slow, not as good as Lucid Lynx. 

It's a Thinkpad T40 1.5 GHZ Pentium 784 MB memory so I thought I'd try Lubuntu Ocelot to upgrade to Lubuntu Pangolin.

No go.  Lubuntu latest Ocelot .iso CD Live boots to command line.

No desktop.

This Ocelot Lubuntu CD booted on my fast tower just fine, so the CD's O.K. 

Now what??  Can't enter a ubuntu-bug because ubuntu-bug insists on a running GUI.  I can get a ubuntu-bug report but the Launchpad folks need the formatted version from a fully running desktop.  Catch 22.  If I had a fully running desktop I wouldn't be filing a bug.

Anything to try?  If Lubuntu Ocelot doesn't work, doesn't make any sense to upgrade it to lubuntu Pangolin.

Thanks, Jerry

---

### Post by lucazade on 2011-11-10
Jerry, as a t40 owner, I can tell you that lubuntu<>ubuntu is not that different in performances. What you can see are different startup times but 2D rendering for the desktop and video playback is the same.

What make a difference with that specs are:
- KMS for old radeon reduce fps (so adding radeon.modeset=0 to kernel params fix this)
- disable metacity compositor (gconf-editor -> apps/metacity/ -> disable compositor_manager)
- custom xorg.conf with better EXA settings like the following:


```
Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"radeon"
	Option 		"AccelMethod" "EXA"
	Option 		"AccelDFS" "True"
	Option 		"DynamicClocks" "off"
	Option 		"EnablePageFlip" "True"
	Option 		"MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I hope this thinkpad will live forever, probably the best laptop I've ever used and even with low specs outperforms a lot of machines nowaday.

---

### Post by amjjawad on 2011-11-10
> **lucazade said:**
> Jerry, as a t40 owner, I can tell you that lubuntu<>ubuntu is not that different in performances. 

I do hope you are talking about a particular machine NOT general observation. 
Lubuntu vs Ubuntu Performance wise could be a lot different. Anyway, this kind of discussion is NOT meant to be in here but just to make it clear for anyone else who might read your post.

Thanks!

P.S.
P4 3GHz (2MB Cache) - 2GB RAM **and** P4 3GHz (1MB Cache) - 512MB RAM = Lubuntu works much different than Ubuntu on these two machines.

---

### Post by sffvba[e0rt on 2011-11-10
Posts moved to own thread as requested... (as it is a support request and falling out of the specific topic of the other thread)


404

---

### Post by lucazade on 2011-11-10
it was a general observation and also about that particular machine.

gtk2/3 apps performs the same way on ubuntu's gnome and lubuntu's lxde.. the gtk engine for theming is shared (murrine/unico) and themes' features affect performances in the same way. (check gtkperf for bench)

kernel, xorg, system services and friends are the same so no differences also here, what really change are session components (DE, WM, daemons) that for lxde are really lighter respect gnome. So lxde has a lower footprint in ram and slightly faster gui session but common apps like a browser works exactly in the same way.

anyway like you said we are a bit ot ;)

EDIT: thx for moving posts

---

### Post by ronacc on 2011-11-10
its not just a specific machine I just got the same thing on my amd64 desktop with an nvidia 7600gs . installed from the nov 7 daily as that was the latest as of this AM .

---

### Post by effenberg0x0 on 2011-11-10
Maybe they took the "keep a light interface" goal to an extreme? 

:)

---

### Post by ronacc on 2011-11-10
ah yes the new minimalist look :D

---

### Post by kansasnoob on 2011-11-10
> **jerrylamos said:**
> I've got Precise Pangolin upgraded from a fresh install of Ubuntu Ocelot Unity-2D working O.K. so far, probably not much changed code in Pangolin.  Response is a little slow, not as good as Lucid Lynx. 

It's a Thinkpad T40 1.5 GHZ Pentium 784 MB memory so I thought I'd try Lubuntu Ocelot to upgrade to Lubuntu Pangolin.

No go.  Lubuntu latest Ocelot .iso CD Live boots to command line.

No desktop.

This Ocelot Lubuntu CD booted on my fast tower just fine, so the CD's O.K. 

Now what??  Can't enter a ubuntu-bug because ubuntu-bug insists on a running GUI.  I can get a ubuntu-bug report but the Launchpad folks need the formatted version from a fully running desktop.  Catch 22.  If I had a fully running desktop I wouldn't be filing a bug.

Anything to try?  If Lubuntu Ocelot doesn't work, doesn't make any sense to upgrade it to lubuntu Pangolin.

Thanks, Jerry

About this:

> Lubuntu latest Ocelot .iso CD Live boots to command line.

Probably this bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837)

---

### Post by amjjawad on 2011-11-10
> **kansasnoob said:**
> About this:



Probably this bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837)

[http://ubuntuforums.org/showthread.php?t=1877867](http://ubuntuforums.org/showthread.php?t=1877867)

and yes, it's a known bug :)
However, I couldn't produce it when I used Live-USB. You can read my comments on that bug :)

---

### Post by kansasnoob on 2011-11-10
> **amjjawad said:**
> [http://ubuntuforums.org/showthread.php?t=1877867](http://ubuntuforums.org/showthread.php?t=1877867)

and yes, it's a unknown bug :)
However, I couldn't produce it when I used Live-USB. You can read my comments on that bug :)

I hope you mean it's a "known" bug :)

I'm the one that reported it and I can assure you it's quite hard to reproduce. I think it's somewhat hardware related because I could only reproduce it on one out of three sets of hardware I use.

It's a tough bug to fix but the work-around is easy:

```
sudo service lxdm start
```

---

### Post by amjjawad on 2011-11-10
> **kansasnoob said:**
> I hope you mean it's a "known" bug :)

My bad, yes, I meant "known" :)


> I'm the one that reported it and I can assure you it's quite hard to reproduce. I think it's somewhat hardware related because I could only reproduce it on one out of three sets of hardware I use.

I don't think so. I have to P4 PCs. One of them has falling CD-Drive. Lubuntu 11.10 Live-CD worked perfectly on the machine with good CD-Drive while it did not on the other one. Before, Lubuntu 11.04 Live-CD didn't work on any of these two PCs.
 
I don't really know what is going on? however, with Lubuntu 11.10, it seems less to happen. With Live-USB, I never had this issue on both PCs. I'm sure I updated the report with these info.

> It's a tough bug to fix but the work-around is easy:

```
sudo service lxdm start
```

I have different work-around but all is good :)

---

### Post by cariboo on 2011-11-10
> **amjjawad said:**
> My bad, yes, I meant "known" :)

I have different work-around but all is good :)

Aren't you going to tell us what your work around is?

---

### Post by amjjawad on 2011-11-10
> **cariboo907 said:**
> Aren't you going to tell us what your work around is?

You didn't check post #10, I guess :)

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot#Desktop_ISO_boot_to_a_terminal_prompt](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot#Desktop_ISO_boot_to_a_terminal_prompt)

[http://ubuntuforums.org/showpost.php?p=11398602&postcount=35](http://ubuntuforums.org/showpost.php?p=11398602&postcount=35)


Again, on Live-USB, this problem does NOT occur.
Sometimes, it doesn't occur too from Live-CD and my guess it has to do with the CD-Drive itself.

---

### Post by amjjawad on 2011-11-14
> **sigirl said:**
> So lxde has a lower footprint in ram and slightly faster gui session  but common apps like a browser works exactly in the same way.

You can use the same browsers you used to use with other DE's but overall performance IMHO depends on many factors.

Real test to reveal that is to have two identical machines, one is running Lubuntu and other say Ubuntu. I haven't done that and not planning to do because simply, I'm a Lubuntu User and I don't really care about something like that. I do care about overall performance for the whole system, stability, easy to use, etc.

---

