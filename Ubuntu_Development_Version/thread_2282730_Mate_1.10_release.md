---
title: "Mate 1.10 release"
date: 2015-06-16
forum: Ubuntu Development Version
---

### Post by v3.xx on 2015-06-16
I really expect this release to show up anyday as a update/upgrade for 15.10.

Or not?

---

### Post by grahammechanical on 2015-06-16
Ubuntu has a feature freeze date of August 20th. I have no idea if that applies to the flavours although I suspect that it does. So, I suggest "any week" is better than "anyday." The developers will certainly want it out in the wild in time to fix any thing that needs fixing before release day.

Regards.

---

### Post by v3.xx on 2015-06-17
Ok  grahamm ..

I'll take this as the official gossip till told different :D

---

### Post by v3.xx on 2015-06-18
From Wimpy
> 
Having completed the last steps of release engineering for MATE 1.10 itself, and completed the MATE 1.10 packaging for Arch Linux, I am now doing the lions share of the work to package MATE 1.10 for Debian Experimental. I'd say I am about 80% through that and my Debian sponsor (technical team for a Debian Developer who reviews/uploads packages) has uploaded about half of those packages to Debian Experimental. Progress is good &#9786;

When all the MATE 1.10 packages are in Debian experimental, I'll sync them to the Ubuntu 15.10 archive. I would estimate that the Ubuntu MATE 15.10 daily images will include MATE 1.10 in 2 or 3 weeks.

[https://ubuntu-mate.community/t/mate-1-10-when/1133/5](https://ubuntu-mate.community/t/mate-1-10-when/1133/5)

---

### Post by QDR06VV9 on 2015-06-18
I have a sneaking hunch he will back port to Trusty.
That is just me talking.
But as Micheal J Fox would say "Your Kids are going to Love It";)

---

### Post by v3.xx on 2015-06-21
GTK3 support is going to be iffy.

---

### Post by v3.xx on 2015-07-14
I asked the question today in the Mate forum.

The reply:
> The feature freeze for 15.10 is scheduled for around the end of August, so if it's going to be in Wily it should be there by then.

---

### Post by v3.xx on 2015-08-01
> [h=3][FONT=arial][SIZE=2]Where is MATE 1.10?[/SIZE][/FONT][/h] It is coming soon, here's why.
 I am an upstream MATE developer, which means I know stuff. There are good reasons why MATE 1.10 is not in Ubuntu MATE 15.10 or other PPAs right now. Here are some of them:
 
[LIST]
[*]The upstream MATE team planned for MATE 1.10 bug fix point releases. Those are now all released, as of a few days ago, and include significant improvements to the help documentation and many bug fixes.
[*]I have elected to sync MATE packages from Debian into Ubuntu without any modifications. I do this because I am a MATE maintainer for Debian.
[*]The Debian MATE team have uploaded most of the MATE 1.10 packages to Debian experimental about two months ago. Bugs have been found and fixed.
[*] [This bug is being crushed]("https://bugs.launchpad.net/ubuntu-mate/+bug/1392502") and means that most packages need significant modification, it takes time.
[/LIST]
 In short, I don't want to release stuff when I know significant changes are coming. But as you can see, lots of work on MATE 1.10 has been going behind the scenes.


[https://ubuntu-mate.org/blog/ubuntu-mate-wily-alpha2/](https://ubuntu-mate.org/blog/ubuntu-mate-wily-alpha2/)

---

### Post by QDR06VV9 on 2015-08-13
[COLOR=#ff0000]**WARNING TESTING ONLY**[/COLOR]
Please don't ask me how I did this. So far I have only had this running for a few hours now. (with a few apport errors popping up)
After about 6hrs worth of compiling and using outside packaging sources I have Mate 1.10 working smoothly almost. (just a few glitch's):D
Now this is done on Ubuntu 14.04.3 LTS 64 Bit.
Will report back as I progress.(If I progress LOL)
Here it is so far.
```
me@me-Aspire-M3300:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

me@me-Aspire-M3300:~$ inxi -Fxz
System:    Host: me-Aspire-M3300 Kernel: 4.1.4-040104-lowlatency x86_64 (64 bit, gcc: 4.8.4) 
           Desktop: N/A Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M Bios: American Megatrends version: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20741.9 
           Clock Speeds: 1: 2600.00 MHz 2: 2600.00 MHz 3: 2600.00 MHz 4: 2600.00 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GT 520/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 355.06 Direct Rendering: Yes
Audio:     Card-1: NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: Creative Labs SB Audigy driver: snd_emu10k1 port: e800 bus-ID: 04:05.0 
           Sound: Advanced Linux Sound Architecture ver: k4.1.4-040104-lowlatency
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller driver: sky2 ver: 1.30 port: c800 bus-ID: 02:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 2500.5GB (1.0% used) 1: id: /dev/sda model: WDC_WD5000AADS size: 500.1GB 
           2: id: /dev/sdb model: WDC_WD20EADS size: 2000.4GB 
Partition: ID: / size: 227G used: 25G (12%) fs: ext4 ID: swap-1 size: 6.44GB used: 0.00GB (0%) fs: swap 
           ID: swap-2 size: 6.44GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 200 Uptime: 2 min Memory: 452.3/5967.2MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
me@me-Aspire-M3300:~$ [COLOR=#0000ff]caja --version
MATE caja 1.10.0[/COLOR]
```
Lets see how far I can keep this up and healthy.
This is just a test so Please don't ask(got bored).:p
Here is one of my problems for now.
No VLC for me;)
> vlc : Depends: libgles1-mesa (>= 7.8.1) or
                libgles1
       Depends: libgles2-mesa (>= 7.8.1) or
                libgles2

Regards

---

### Post by v3.xx on 2015-08-13
Just updated.  Mate 1.10 is here :)

---

### Post by v3.xx on 2015-08-14
Update

Have been informed by the mate community that there are still about 20 more packages to go before m1.10 will be complete.

---

### Post by QDR06VV9 on 2015-08-14
> **v3.xx said:**
> Update

Have been informed by the mate community that there are still about 20 more packages to go before m1.10 will be complete.
Did you have any held packages?

---

### Post by v3.xx on 2015-08-14
Just one

Flash for firefox

---

### Post by QDR06VV9 on 2015-08-14
Hhuumm.
I get this
> The following packages have been kept back:
  conky-all libavfilter-ffmpeg5 ubuntu-mate-core
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Conky i have pinned.

But I show Mate  [IMG]http://i.imgur.com/qH7SnuT.png[/IMG]

---

### Post by v3.xx on 2015-08-14
I have not updated yet today.  Maybe something new.

---

### Post by QDR06VV9 on 2015-08-14
Ok Thanks:D

---

### Post by v3.xx on 2015-08-14
```
apt-cache policy mate-desktop
```

shows

1.10.1-1

---

### Post by QDR06VV9 on 2015-08-14
Yep same.
 I will bet you have not enabled proposed yet.

---

### Post by v3.xx on 2015-08-14
No, I have not.  But later today, after I get my honey-do list updated :D

---

### Post by QDR06VV9 on 2015-08-14
> **v3.xx said:**
> No, I have not.  But later today, after I get my honey-do list updated :D

Yes Sir Those honey-do's   Take top priority.;)
Regards

---

### Post by v3.xx on 2015-08-14
Ok runrickus, I have proposed opened up and zero packages held back.

Using the Main server.

---

### Post by QDR06VV9 on 2015-08-15
> **v3.xx said:**
> Ok runrickus, I have proposed opened up and zero packages held back.

Using the Main server.
Yep Wily got sorted out last nite.
Side Note: Trusty with mate 1.10 is still up and  kicking
It is amazing the abuse this OS  can handle.
However I do not think I will do anything like this again.(I guess I should never say never.;))
Regards

---

