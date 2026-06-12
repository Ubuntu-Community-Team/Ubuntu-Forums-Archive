---
title: "Lubuntu 20.04 user's opinions."
date: 2020-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2020-05-18
Hello Ubuntu Forums,


Title says it ***"Lubuntu 20.04 user's opinions".***

My Linux computers are all old discarded computers pieced together with parts from other discarded computers. ***(Frankenstein Builds)***

Intel Core 2 duo E7500 (2.93GHz) processors / Intel integrated graphics adapters (Intel 4 Series Integrated Graphics (Intel G41) / 4.0GB DDR2 or DDR3 memory and mechanical hard drives.

I'm using ***Lubuntu 20.04*** and like it.


Thanks

---

### Post by i-choose-linux on 2020-05-22
Out of curiosity, I happened to try Lubuntu a few days ago.  To be fair I only spent a few hours with it.  But it is not my cup of tea.  I come from Mate, Xfce, Cinnamon experience and Windows also years ago.  I have a lot of machines and some with your specs.  You could be running Xfce or Mate if you chose to.  I think a lot of what we like or dislike is a matter of what we are accustomed to.  I have spent quite a bit of time with Ubuntu and Gnome desktop.  I have never liked it but the more I used it the less I disliked it.

Bill

---

### Post by guiverc on 2020-05-22
I'm not sure I can really respond to this. I think I was using Lubuntu 20.04 LTS less than two days before I *bumped* myself to *groovy* *gorilla* (I was running *focal fossa* about six months before its release date though; ie. since late October 2019).

Lubuntu (LXQt) is my default system, and where I'm most comfortable  (XFCE or Xubuntu would be a close second; Xubuntu/XFCE & Ubuntu/GNOME desktops are installed too, but this box usually remains on LXQt)

I have six c2d machines that I use in testing Ubuntu and *flavors*, two I've used today in testing Lubuntu, plus another I've used for my own stuff today.

I don't have *Frankenstein* builds, but my primary system is
```
dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
```
the format is how I list boxes in QA-testing '*box (cpu, ram, gpu)',* details from `lshw`, I've never noted cpu or ram speeds.

My opinions on LXQt.  I do like it, and love that it's light, it's functionality and it stays out of the way (until I want it)

[B]Lightness: 
[/B]
I have an old thinkpad t43 (pentium m i686), and thinkpad r50p (pentium m i586) that I still use, and on those I noticed how MATE as it moved to GTK3 had slower performance. XFCE was slower in porting to GTK3 which I felt was nice, as there was longer before it too slowed on those really old thinkpads (and their 1gb of ram). I expected to feel a speed loss when Lubuntu moved from LXDE (GTK2) to LXQt (Qt5), but was pleasantly surprised!  It was different yes, and to remain RAM efficient (necessary on 1gb laptops) it meant I had to change apps used.. but the performance was I felt good (too hard to compare with LXDE on same boxes due to app changes I felt; subjectively comparative though).  This is historical now, as those old thinkpads cannot use Lubuntu 20.04 LTS (not amd64).

On my main box (c2q-9400) it runs LXQt, XFCE & other desktops fine having more RAM & cpu grunt, but light Lubuntu/LXQt is nice.

---

### Post by poorguy on 2020-05-23
Yeah I know I can be running a different desktop environment however I'm really liking LXQT.

It took me a few days of learning some how to about the LXQT ways of doing things.

 The user documentation that is available for Lubuntu 20.04 is awesome and really explains how to well.

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

LXQT is really fast and stable although does have a few minor quirks but nothing that will keep me from using it.

I was under the impression that LXQT was a lot heavier than LXDE although I haven't really noticed that.

Other desktops and window managers I use are Xfce and Gnome and LXDE and IceWM.

I agree what we like is what we are accustom to using.

---

### Post by i-choose-linux on 2020-05-23
Yes, it is all about what you like best.  But from a technical standpoint the latest Lubuntu uses about the same resources as Xubuntu.  I think Lubuntu no longer describes their DE as light weight.  They are in the middle weight category.  I also think that the very light weight distros are going to pass into the history books because the machines that they resuscitate are so lacking in processing power that they can't work efficiently on the internet.  I have an old Pentium 4 machine here from 2004.  I only keep it around as an example of what the old processors are capable of.  That Pentium 4 will run AntiX pretty well.  It will even kind of load LibreOffice apps.  I want to try using a text only browser on the machine.  Never experimented with those browsers.

Bill

---

### Post by poorguy on 2020-05-23
I use a lot of old computers but nothing as old as a Pentium 4.

I have used texted base browsers and light weight browsers such as dillo and netsurf and they work OK although somewhat limited.

I don't think lightweight desktops or Window Managers are going to go away anytime not everyone wants or needs eye candy and some of us actually prefer a simple dull boring menu.

Give Abiword a look at for an alternative to Libreoffice writer.

---

### Post by guiverc on 2020-05-24
> **i-choose-linux said:**
> But from a technical standpoint the latest Lubuntu uses about the same resources as Xubuntu.  I think Lubuntu no longer describes their DE as light weight. 

I personally believe Lubuntu with LXQt is lighter than XFCE, though in my current setup, the difference doesn't really exist, as I use a mixture of GTK apps as well as Qt, wasting memory in my app choice requires GTK libs to be in memory on a Qt desktop. On laptops with less memory I'm more careful.

I still have a pentium 4 box I use to test x86 ISOs on, and on that old & slow box (which does far out perform the pentium M laptops), Lubuntu 19.04 (& 19.10) performed better than the respective Xubuntu releases (I wanted to experience all GTK3 Xubuntu on x86/i686 so bumped 19.04 system(s) to 19.10  (the box has 3 hdds, with about 8 Ubuntus). It's been handy of late, as it actually still has a floppy drive! (`calamares` has an issue with floppies), but we've only probably one more x86 set of ISOs in test - so it's days maybe limited.


The L in Lubuntu still refers to Light (let alone the first letter of LXDE & LXQt both meaning Light), the [New Direction blog]("https://lubuntu.me/taking-a-new-direction/") still highlights that (let alone many assurances on Lubuntu's discourse; maybe it could have been clearer).

---

### Post by poorguy on 2020-05-24
> **guiverc said:**
> 
The L in Lubuntu still refers to Light (let alone the first letter of LXDE & LXQt both meaning Light), the [New Direction blog]("https://lubuntu.me/taking-a-new-direction/") still highlights that (let alone many assurances on Lubuntu's discourse; maybe it could have been clearer).


Your link I've read before but didn't mind reading again pretty much says it spot on.
My 10 year old computers are dual core processors and have at least 4.0GB of memory.

I can run Ubuntu 18.04 or Ubuntu 20.04 on most of my 10 year old computers with the specs mentioned in my 1st post.
 I prefer the lightweight Linux distros and really like LXQT and LXDE user interface / window managers.

One of my favorite lightweight distros is LXLE because of it's desktop.
I'm kinda waiting to see what they will turn out using Ubuntu 20.04 base.

---

