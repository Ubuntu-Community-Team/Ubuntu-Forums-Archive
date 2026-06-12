---
title: "Ubuntu release beta does not support mh modem"
date: 2016-03-29
forum: Ubuntu Development Version
---

### Post by eltonw on 2016-03-29
Machine: Lenovo 15.6¨Laptop G50 (80E301GUUS) AMD A-Series A8-6410 (2.00GHz), 
Network controller: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter (rev 20)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
        Subsystem: Lenovo Device 3812


It's currently running Mint Linux 17.2, but updates identify as Ubuntu 14.04.

I recently downloaded the final beta : xenial-desktop-amd64.iso, and ran it as a "live CD". I was quite disappointed that _neither wifi nor bluetooth work with Ubuntu_. Being obliged to connecting a laptop via network cable is not really desirable in this day and age. I had hoped that the newer kernel (in this release) would work with my machine. Apparently, it does not. ly

**Is it too late to report this to the Ubuntu dev team?** If not how / where to report this?:confused:
FWIW: I got wifi / bluetooth works for me, but I dare not upgrade. Normally, I would prefer a fresh install, rather than update when a new version is released.

Kindly refer to this related link in the LinuxMint forums:[https://forums.linuxmint.com/viewtopic.php?f=53&t=204566&p=1075788&e=1075788](https://forums.linuxmint.com/viewtopic.php?f=53&t=204566&p=1075788&e=1075788)

---

### Post by slickymaster on 2016-03-29
*Moved to the ***Ubuntu Development Version*** sub-forum*

---

### Post by howefield on 2016-03-29
Moved to the "*Ubuntu Development Version*" forum.

> **eltonw said:**
> Is it too late to report this to the Ubuntu dev team?[/B] If not how / where to report this?:confused:

Report your issues here : [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by QIII on 2016-03-29
Your link requires a registration and login, which many will not bother with.

Could you please describe the discussion and resolution here?

No, it's not to late to report a bug.  Whether it will be fixed by the release is unknown.

---

### Post by eltonw on 2016-03-29
> **howefield said:**
> Moved to the "*Ubuntu Development Version*" forum.



Report  issues here : [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
Thank you. will do so immediately.

---

### Post by PaulW2U on 2016-03-29
> **slickymaster said:**
> *Moved to the ***Ubuntu Development Version*** sub-forum*
> **howefield said:**
> Moved to the "*Ubuntu Development Version*" forum.
It takes two of you now? :D
> **eltonw said:**
> **Is it too late to report this to the Ubuntu dev team?** If not how / where to report this?:confused:
Reporting bugs here may invoke discussion but will not bring any relevant information to the attention of the Ubuntu developers.

All bugs should be reported through Launchpad. See the [Reporting Bugs]("https://help.ubuntu.com/community/ReportingBugs") page on the Ubuntu wiki.

Hope that helps.

---

### Post by eltonw on 2016-03-29
> **QIII said:**
> Your link requires a registration and login, which many will not bother with.

Could you please describe the discussion and resolution here?

No, it's not to late to report a bug.  Whether it will be fixed by the release is unknown.

First, I **do** have an Ubuntu One account, but I was hoping to quickly report this. I'm a rather poor typist, and it's already  after midday.

Problem: the Lenovo G50 does not work with linux. ie. **no wifi or bluetooth** "out of the box". I am currently running Mint Linux 17.2. I'm neither a coder nor a developer.
I was kindly assisted by Jeremy B and provided a solution: [https://forums.linuxmint.com/viewtopic.php?f=53&t=204566&p=1075788&e=1075788](https://forums.linuxmint.com/viewtopic.php?f=53&t=204566&p=1075788&e=1075788)

I wouldn't mind taking the time to send in a report but I have to go out.

respectfully...

---

### Post by grahammechanical on 2016-03-29
If you are using Linux Mint & Linux Mint is based on Ubuntu then this problem is going to be in any version of Linux Mint based on Ubuntu 16.04. Have you tried using Additional Drivers to see if an WiFi driver is available for download?

Regards.

---

### Post by eltonw on 2016-03-30
> **grahammechanical said:**
> If you are using Linux Mint & Linux Mint is based on Ubuntu then this problem is going to be in any version of Linux Mint based on Ubuntu 16.04. Have you tried using Additional Drivers to see if an WiFi driver is available for download?

Regards.

I only briefly booted the USB stick on  which I burned the beta. I haven't actually installed it, so I didn't think of connecting via an ethernet to seek / download drivers. I was informed elsewhere that the newer kernels would support my modem. Currently I'm on 3.19.0-30-generic.

---

### Post by eltonw on 2016-04-02
> **grahammechanical said:**
> If you are using Linux Mint & Linux Mint is based on Ubuntu then this problem is going to be in any version of Linux Mint based on Ubuntu 16.04. Have you tried using Additional Drivers to see if an WiFi driver is available for download?

Regards. cable 

UPDATE:
Today, I booted an ran as a "live CD". Sure enough, there was **no wifi** connection. Therefore I used a wired connection, and to my surprise, **bluetooth** works.

Screenshot: [IMG]http://i63.tinypic.com/jaxrmc.png[/IMG]


I tried the Help in the Xenial live CD :

   5.Open the Terminal, type nm-tool and press Enter.
My result:
> 
ubuntu@ubuntu:~$ nm-tool
No command 'nm-tool' found, did you mean:
 Command 'dm-tool' from package 'lightdm' (main)
nm-tool: command not found
ubuntu@ubuntu:~$ sudo nm-tool
sudo: nm-tool: command not found


I cannot find (in the hardware settings of the beta) any option to search for drivers. What now?

---

