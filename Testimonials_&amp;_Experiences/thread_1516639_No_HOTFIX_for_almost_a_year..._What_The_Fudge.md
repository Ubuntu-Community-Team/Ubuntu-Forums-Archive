---
title: "No HOTFIX for almost a year... What The Fudge?"
date: 2010-06-24
forum: Testimonials &amp; Experiences
---

### Post by mrtymek on 2010-06-24
Hello.
It's right about time to fix those problems.
Ubuntu has ambitions to be a popular desktop OS, and me as a consumer  would like to point out a couple of things. Exactly a couple.
No sound after waking up from stand-by mode, and no sound if I turn the  system volume below 17% or sth...

I know this problem is out there since a while. I know, there are some  kludges to at least the "no sound on wake-up" issue, but long time ago  I've chosen Linux because of the out-of box support for hardware, and  now it seems, that actually Ubuntu - the most popular distro around I  guess, stays behind Windows with hardware support...

How come, that since the release of 9.10 I have not received a hotfix,  or an update which would remove those problems?

There are different types of consumers out there, and I, for one, really  love to listen to music... It's playing almost all day long. It really  bothers me if I can't go down to 4-6% volume at night, because the sound  disappears below 17% but it is still too loud at 18%. I have to  move my shiny metal *** all the way to the speakers, or the amp, to  turn the volume down to be quiet enough at late time...

When I go out i usually don't even pause the music, but just turn the  comp to stand-by, and after coming back, the music starts playing  again... I mean it used to, cuz now it's impossible since 9.10. 

Let me repeat: How come, that there have not been an update, or a hotfix  which would remove the problem?
Tell me, how am I supposed to recommend that OS to a newby friend, or  something?
Sorry for the tone, but Canonical wants Ubuntu to be a user friendly and  popular OS, and as one, it needs more attention to customer... Does it?

some techs for your inspection peeps.
They were fresh installs, both 9.10 and 10.4
```

mrtymek@mrtymek-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory  Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI  Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio  Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI  Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface  Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E)  IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E)  SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller  (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
mrtymek@mrtymek-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 047d:1076 Kensington SlimBlade Media Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2  Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass  Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel  UVC Webcam
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B  Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mrtymek@mrtymek-laptop:~$ 



```

---

### Post by 3rdalbum on 2010-06-25
You'd be very lucky to get more than simple bugfixes for older versions of Ubuntu. The current version of Ubuntu is 10.04, not 9.10.

Also, have you reported the bug?

Some bugs take time. More critical bugs that affect more people, will get priority over more minor bugs such as yours. If you'd like to speed the process along, I hear that Ubuntu is looking for more people to do bug triage?

---

### Post by WinterRain on 2010-06-25
Try 10.04 (clean install) and do updates immediately.

---

### Post by mrtymek on 2010-06-27
I should've been more clear on that one, although I did write that
> They were fresh installs, both 9.10 and 10.4
I am currently using 10.4 from a fresh install, and to give you the scope of time I mentioned that the problem first appeared with 9.10.

---

### Post by negativ on 2010-06-28
But at least we got new themes and artwork, and that's what counts. :roll:

---

### Post by oldsoundguy on 2010-06-28
check your mute and output volume .. some of the recent updates have muted the sound on a couple of my computers, but left it alone on a couple of others.

---

### Post by Stavro on 2010-06-28
If you are really into music then you should ultimately find line-level output settings on the volume mixer and keep it that way; then invest in some quality desktop speakers which have there own volume/tone control on them. It is much nicer and quicker to use a physical volume control and sound is at an optimum.

---

### Post by mrtymek on 2010-07-02
Well. My speakers have a physical volume control, but sometimes when I'm in different parts of the room it's just more convenient to use the laptop's volume buttons...
I found the problem now. I have noticed strange behaviour when opened alsamixer.

So when I use the gnome's volume control it goes like this...
on 100% MASTER and PCM are both 100%. Then until 17% the MASTER volume goes down, while PCM stays in the area of 98% - 100%.
Then the gnome's vol control reaches 17% the MASTER volume is at 0% (that's when the sound mutes) and the PCM keeps going down until it reaches 0 as well...

Clearly, the gnome's volume control is doing it wrong.
I would suggest to do this (starting from the bottom)
at 1% - PCM1% MSTR1% then keep raising both until PCM reaches about 80% (to preserve sound quality), when MSTR reaches 100% and more volume is needed, raise the PCM to the end...

BTW - seeing the PCM jumping from 98% to 100% and back all the time makes a bad impression...

---

### Post by mrtymek on 2010-07-02
There is another thing as well...
I was pissed of about the router in my house, but just recently realized what the problem really is, when I started an MCSA course, and Silverlight (Moonlight) didn't work on ubuntu. So i had to dualboot Windows on my computer for the first time in like 5 yrs, and found out, that WiFi works billions times better, and uses full capacity and is completely reliable, unlike on ubuntu, where I get 2Mb out of my 10Mb broadband, and it breaks all the time, usually causing disruptions to my flatmates... And if it doesn't break, it goes down to 1Mb, and the pings are so cosmic, that sometimes I don't even get to check my email...
I'm using a Raltek RTL8187b and read on the boards, that they messed up the driver module... So what choice for me? switch to another distro? My 30 days grace period for Windows is going to end soon, so no more internets for me?
That makes me a sad panda... :(

---

### Post by dE_logics on 2010-07-02
Try Sabayon... that might solve your problems.

Ubuntu always has bits and pieces of problems everywhere and I fail to understand why. Furthermore it's getting worst with every release; the newbies argue without knowing the insides and we don't have the time to talk to them, so they never understand.

What Ubuntu does well is simplify the install procedures and that 'software center'... these things are mostly relevant to the windows migrants.

---

### Post by MCVenom on 2010-07-02
> **negativ said:**
> But at least we got new themes and artwork, and that's what counts. :roll:
Your attempt at biting satire has been noted and ignored. :P

---

### Post by MCVenom on 2010-07-02
> **dE_logics said:**
> Try Sabayon... that might solve your problems.

Ubuntu always has bits and pieces of problems everywhere and I fail to understand why. Furthermore it's getting worst with every release; the newbies argue without knowing the insides and we don't have the time to talk to them, so they never understand.

What Ubuntu does well is simplify the install procedures and that 'software center'... these things are mostly relevant to the windows migrants.
My position on Sabayon is this: *If you want to use Gentoo, then just use Gentoo.* :P

---

### Post by Chame_Wizard on 2010-07-02
[Ubuntu 10.04.1 will be released on 29 July 2010.]("https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1")

Contains a lot of updates/upgrades/fixes.

---

### Post by dE_logics on 2010-07-03
> If you want to use Gentoo, then just use Gentoo.

I don't use Sabayon. I use Gentoo and I find lots of difference between Sabayon and Gentoo including the fact that it's package manager is faster than apt.

---

### Post by mrtymek on 2010-07-03
> **Chame_Wizard said:**
> [Ubuntu 10.04.1 will be released on 29 July 2010.]("https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1")

Contains a lot of updates/upgrades/fixes.

The thing is, there's a big chance I will loose my mind trying to download it... cuz as I mentioned before, the RTL8187 module is messed up.
Anyway, by the time 10.4.1 is released I should be getting a new comp, and I'm not just that sure if I would be coming back to ubuntu...

---

### Post by dE_logics on 2010-07-03
> **mrtymek said:**
> The thing is, there's a big chance I will loose my mind trying to download it... cuz as I mentioned before, the RTL8187 module is messed up.
Anyway, by the time 10.4.1 is released I should be getting a new comp, and I'm not just that sure if I would be coming back to ubuntu...

This is a good idea you know... but I've lost hope, I don't expect anything anymore...

---

### Post by cariboo on 2010-07-06
With op's final post, nothing else needs to be said. Closed.

---

