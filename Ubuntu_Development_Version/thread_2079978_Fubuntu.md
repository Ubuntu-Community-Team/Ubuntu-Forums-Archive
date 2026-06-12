---
title: "Fubuntu"
date: 2012-11-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-02
Running rr using fvwm-crystal.

```

ventrical@ventrical:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring
ventrical@ventrical:~$ 

```

---

### Post by ventrical on 2012-11-03
Can't believe it! If anyone remembers how their fresh install of Win95  ran on their old machines then that is how Raring works with the new 3.7.x-xRC3 kernel on this old iron using desktop fvwm-crystal.

```

ventrical@ventrical:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:11.0 USB controller: NEC Corporation USB (rev 41)
00:11.1 USB controller: NEC Corporation USB (rev 41)
00:11.2 USB controller: NEC Corporation USB 2.0 (rev 02)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI 3D Rage Pro AGP 1X/2X (rev 5c)
ventrical@ventrical:~$ uname -a
Linux ventrical 3.7.0-030700rc3-generic #201210310756 SMP Wed Oct 31 12:04:40 UTC 2012 i686 i686 i686 GNU/Linux
ventrical@ventrical:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring
ventrical@ventrical:~$ 

```

---

### Post by VinDSL on 2012-11-03
> **ventrical said:**
> Can't believe it! If anyone remembers how their fresh install of Win95  ran on their old machines then that is how Raring works with the new 3.7.x-xRC3 kernel on this old iron using desktop fvwm-crystal.
You're getting blue screens?!?!?

---

### Post by Lars Noodén on 2012-11-03
W95 used to bluescreen almost hourly for me.  I have a hard time remembering which was worse W95 or W98, though.  Can you cause the bluescreen by doing anything in particular?  I used to use FVWM-crystal a lot but never once had any stability problems with it.

---

### Post by ventrical on 2012-11-03
> **VinDSL said:**
> You're getting blue screens?!?!?


hahaha..lol.. No .. no blue screens .. it was when I loaded that olde 95 CD and it was pretty fast demo. Sorry for not being clear about..

  It just works real fast for a 600MHz Celeron.

---

### Post by ventrical on 2012-11-03
> **Lars Noodén said:**
> W95 used to bluescreen almost hourly for me.  I have a hard time remembering which was worse W95 or W98, though.  Can you cause the bluescreen by doing anything in particular?  I used to use FVWM-crystal a lot but never once had any stability problems with it.

Lars,

 I didn't mean it that way. fvwm-crystal works great. The old win95 had this demo and off the install disk it would run really good  (in certain cases) on old MMXP1/166MHz with 64MB of SDRAM.

lol

---

### Post by Lars Noodén on 2012-11-03
Ok.  Glad to hear.

---

### Post by ventrical on 2012-11-03
My central point about this  is that Raring and the newer kernel RCs can be used on 'old iron' in a feasible and economic fashion. Fvwm-crystal is not that bad of a DE and installing MATE-DE from the ppa is even better.

 Overall, the trend of Canonical and Ubuntu in general is to not obsolete older hardware and machines. Actually the newer kernel enhances the experience.  Certainly it is not Unity 3D or 2D but it is still a working and employable system (as I continue to test) so appears that there is really no need to get rid of the older towers or laptops just yet especially if one is running a tight budget. . I am supervising 11 different systems (real boxes - no virtual boxes) and I get bored once in  while and I like to bring out the older hardware because it is a challenge.

 Regards,
Ventrical

---

### Post by cariboo on 2012-11-03
This may be one of the benefits of having Ubuntu Everywhere, Mark stated that he would like to see the desktop run on tablets, phones and TV sets. Meaning there won't be a specific distribution for each device. Hopefully this will mean that better resource usage will trickle down to Ubuntu on the computer too.

---

### Post by ventrical on 2012-11-03
Well said.  I have noticed that there is a definite performance increase on higher-end units using Kubuntu flavour with the new 3.7.x-xRCxs. At the moment I can't document entirely what services and processes actually are running more ecomomically but, from cursory inspection of cpu and memory using 'gnome-system-monitor' , if it is accurate, then that could be preliminary evidence. 

 I had been surveying some new machines with the Windows 7 OS and noticed that the task-manager will still not correctly display the load balance between an HT dual-core processor.  It will show two usage windows but the graphs are both duplicates of each other.

 Testing rr with gnome-system-monitor has reported a decreased load on both processors besetting concurrently both 1 to Zero. That's a hard act to follow. 

I can see performance also in single core non-ht units . Overall memory and cpu usage are better utilized.

regards,
ventrical

---

### Post by Slug71 on 2012-11-03
> **VinDSL said:**
> You're getting blue screens?!?!?

> **Lars Noodén said:**
> W95 used to bluescreen almost hourly for me.  I have a hard time remembering which was worse W95 or W98, though.  Can you cause the bluescreen by doing anything in particular?  I used to use FVWM-crystal a lot but never once had any stability problems with it.

:lolflag::lolflag:

---

### Post by jerrylamos on 2012-11-04
> **cariboo907 said:**
> This may be one of the benefits of having Ubuntu Everywhere, Mark stated that he would like to see the desktop run on tablets, phones and TV sets. Meaning there won't be a specific distribution for each device. Hopefully this will mean that better resource usage will trickle down to Ubuntu on the computer too.
Maybe this is heresy - I've got a 10.1" tablet, fast, Android, even a keyboard, but what I can do with a PC runs rings around the tablet.  My concern is the "computer ubuntu desktop" will be compromised by what will work on the "tablet ubuntu desktop".

Having said that, in releases and development ubuntu's past, I've used LXDE and 2D to get efficient response.  Currently on RR I'm using unity/compiz O.K.  Compiz overhead on what I just tried is 5% or less.

p.s. as a bystander watching Windows 8.  My wife's running website support on XP using Dreamweaver.  Her concern is will "upgrading" to Windows 8 require re-installing Dreamweaver etc.?  Dreamweaver $$ is not available on Linux.

---

### Post by cariboo on 2012-11-04
> **jerrylamos said:**
> Maybe this is heresy - I've got a 10.1" tablet, fast, Android, even a keyboard, but what I can do with a PC runs rings around the tablet.  My concern is the "computer ubuntu desktop" will be compromised by what will work on the "tablet ubuntu desktop".

Having said that, in releases and development ubuntu's past, I've used LXDE and 2D to get efficient response.  Currently on RR I'm using unity/compiz O.K.  Compiz overhead on what I just tried is 5% or less.

p.s. as a bystander watching Windows 8.  My wife's running website support on XP using Dreamweaver.  Her concern is will "upgrading" to Windows 8 require re-installing Dreamweaver etc.?  Dreamweaver $$ is not available on Linux.

I don't think you have to worry about the desktop becoming the same as a tablet or smart phone. Both of those devices are designed for consuming content, while the desktop computer and laptops are designed for creating content.

As for Dreamweaver on Windows 8 there shouldn't be a problem, if it is only installed on the system running Windows 8, it would be the same as running it on any other system. The only way I could see it being  problem, is if you don't have the original installation media, or are missing the registration key. If you have used up all your installation instances, you can usually contact Adobe, and get them to issue a new registration key.

---

