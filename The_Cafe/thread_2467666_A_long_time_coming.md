---
title: "A long time coming"
date: 2021-10-03
forum: The Cafe
---

### Post by sports fan Matt on 2021-10-03
Hello all, after my latest HP computer decided to die (no operating system found and the fact I can’t upgrade it to windows 11 because it is too low powered) i’ve decided to install Ubuntu 20.04 on a Toshiba L875. My question ~ are Toshiba‘s still reliable in the installation process? And the only version I have on the laptop I think is 10.04 I have to check. I know it’s obsolete, So I assume grabbing the ISO off the website is the best option? And feel free to move it to installation and upgrade if one feels the need.

---

### Post by Frogs Hair on 2021-10-03
If it is the version with 8Gb of ram and an i5 you could run any flavor of Ubuntu. See the Ubuntu Community link on the top of the page. Even with 4Gb of ram you should be fine.

---

### Post by sports fan Matt on 2021-10-03
Yeah I thought so but it’s been about three years since booted it. I’ll know tomorrow when /if The power supply works which I think it will.

---

### Post by ybelin77vbern on 2021-10-06
> **Frogs Hair said:**
> If it is the version with 8Gb of ram and an i5 you could run any flavor of Ubuntu. See the Ubuntu Community link on the top of the page. Even with 4Gb of ram you should be fine.
With modern needs for the web, any computer with less than 4gb is doomed to lag

---

### Post by TheFu on 2021-10-06
> **ybelin77vbern said:**
> With modern needs for the web, any computer with less than 4gb is doomed to lag

I think this is not correct, but it would depend on what the person considers "modern needs".  Just by blocking some ads, the entire web gets much faster.  Disable Javascript for almost all websites and it gets even faster.  Javascript is optional. Always remember that.  We can use a light browser

My desktop is configured with dual cores and 4G of RAM.
Right now, it is using 1.2G of RAM with thunderbird, firefox, libreoffice, a password manager and about 10 terminal sessions (2 local, 8 to remote systems).

```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       1.2Gi       209Mi       8.0Mi       2.5Gi       2.4Gi
Swap:         4.1Gi        17Mi       4.1Gi

```

It is very responsive, but I run a limited GUI, not Gnome3 and not KDE.  If the correct GUI is selected, there is little that cannot be accomplished on 4G of RAM for anyone that isn't expected to edit 1080p (or higher) videos, but just wants to to normal browsing and office stuff.  Any system with 1400 Passmarks, should be fine.

It is fairly stable too.  I reboot when there is a new kernel, but leave it running the rest of the time - lots of things happen in the background, especially overnight.  From top:
```

top - 16:26:42 up 3 days, 21:49,  1 user,  load average: 0.01, 0.07, 0.07
Tasks: 187 total,   1 running, 186 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.3 us,  0.3 sy,  0.0 ni, 97.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3936.1 total,    203.6 free,   1221.2 used,   2511.2 buff/cache
MiB Swap:   4200.0 total,   4182.2 free,     17.8 used.   2431.5 avail Mem 
```

Working fine here.

---

### Post by Frogs Hair on 2021-10-08
> **ybelin77vbern said:**
> With modern needs for the web, any computer with less than 4gb is doomed to lag

Been running Ubuntu Budgie on systems with 4 to 8Gb of ram without any noticeable limitations for years. Now that I have built a new system with 16Gb I find it has more to due with drive speed than the increase in memory. One drive being mechanical and the other an nvme.2. I can't comment on less than 4Gb.

---

### Post by T6&amp;sfpER35% on 2021-10-09
> [COLOR=#000000]any computer with less than 4gb is doomed to lag[/COLOR]
i have 3gb ram , and my machine is flying thank you
=d>

---

### Post by sports fan Matt on 2021-10-12
So I have the new parts for the supply which should be installed tomorrow just been busy with real life to focus on it but it should work. I may look into using a lighter browser I haven&#8217;t decided yet.

---

### Post by TheFu on 2021-10-12
A few friends run MX Linux and a few others run Bohdi Linux.  Both of these are very light and don't have systemd's overhead, while still being ubuntu-based - so APT is still there and they use the LTS releases.

The Bohdi install is on an old, slow, Dell all-in-one (monitor + PC in a single package).  It seems to use 30% less CPU when doing video stuff which doesn't use any hardware decoding from the integrated GPU.

He tried Xubuntu, Lubuntu, Mint, and a few others before deciding that Bohdi was the lighest.  On his normal machine, he's a Linux-Mint user and isn't planning to change. I tried to get him to look at tinycore, but he decided that was just too hard to use - which I can't blame him. He's right.  At our LUG, almost every week, we load up a new desktop distro and take a look around.  Sometimes we'll put it on a VPS and provide remote desktop access into the system so people can try it out themselves with a dedicated userid.

---

### Post by DuckHook on 2021-10-12
> **TheFu said:**
> &#8230;a few others run Bohdi Linux.  Both of these are very light and don't have systemd's overhead, while still being ubuntu-based - so APT is still there and they use the LTS releases.

The Bohdi install is on an old, slow, Dell all-in-one (monitor + PC in a single package).  It seems to use 30% less CPU when doing video stuff which doesn't use any hardware decoding from the integrated GPU&#8230;
Bodhi is awesome. I've installed it on a few ancient laptops belonging to friends. They love it. Gives new life to what would otherwise be e&#8209;waste. Light on resources, fast, versatile, pretty, user&#8209;friendly. "Dances like a butterfly, stings like a bee."

Highly recommended.

---

### Post by TheFu on 2021-10-12
[s]Another option to Bohdi, is to use one the the ChromeOS clones. This is like the OS used on Chromebooks, but with all the proprietary google stuff removed. All together, it is called "chromiumOS" and because it was designed to run on very cheap, low-end, chromebooks with just 16GB of total storage, it is very light.  There are a few distros of it.  I think "CloudReady" is a very popular version. There are a few others.  ChromeOS is tightly tied to the hardware - that's why it is probably THE most secure OS in the world today that still has a network stack and connects to the internet.  ChromiumOS is very similar, but because it doesn't mandate any specific hardware, it will run on many, many, more types of systems.  Of course, it has all the limitations that ChromeOS has too, but it is definitely simple enough for almost anyone to pick up and use who has used a browser before.

[https://www.howtogeek.com/128087/how-to-run-chrome-os-in-virtualbox-and-try-out-chrome-os-before-buying-a-chromebook/](https://www.howtogeek.com/128087/how-to-run-chrome-os-in-virtualbox-and-try-out-chrome-os-before-buying-a-chromebook/) is a 2019 article about running ChromiumOS inside a virtual machine.  Very useful for online banking ... cough.
[/s]

Turns out that running these inside a VM isn't trivial anymore. Sorry to waste everyone's time.  However, for an old laptop, I would still suggest taking a look for a few hours if you have minimal needs.  Mainly it will be an internet browser with access to google-apps, gmail, webmail, and social network stuff, etc. ... but the entire web too.  That can be great for people who aren't too tech savvy and aren't interested in becoming or spend **any** money at all.

---

### Post by sports fan Matt on 2021-10-15
A new plan of attack. Thoughts? Will be easier or hard to run focal fossa[INDENT][INDENT][INDENT][PHP][HTML][/HTML][/PHP][/INDENT][/INDENT][/INDENT] on this

---

