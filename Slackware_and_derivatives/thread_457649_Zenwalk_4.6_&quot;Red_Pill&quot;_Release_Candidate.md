---
title: "Zenwalk 4.6 &quot;Red Pill&quot; Release Candidate 1 Released"
date: 2007-05-28
forum: Slackware and derivatives
---

### Post by ThinkBuntu on 2007-05-28
JP and co. quietly leaked the RC1 ISO of Zenwalk May 24th, and it has yet to show on DW, or in its own topic in the Zenwalk forums for that matter. Can't wait for the final release! What's notable is that this is hosted on Zenwalk, and it's the first time I can remember them hosting any of their software on their own.

[Zenwalk 4.6 RC1 Image and MD5Sum (directory)]("http://download.zenwalk.org/people/jp/SNAPSHOT-24052007/")

---

### Post by arox on 2007-05-29
Who cares anyway 

I'm using Zen 4.6 since beta1 and upgrading from snapshot once in a while :)

---

### Post by ThinkBuntu on 2007-05-29
Well, I beat you. I used Zenwalk from the pre-beta 1 snapshot (some very early testing that was more official than a snapshot, but less so than a beta, although never labelled an Alpha). But I can't say anything, as I'm on openSuSE now. Bleh. I can't wait until ZW starts adding the nice usability features for wireless and suspend so I can use ZW full-time.

---

### Post by angryfirelord on 2007-06-19
What wireless card are you using?

---

### Post by ThinkBuntu on 2007-06-19
> **angryfirelord said:**
> What wireless card are you using?
Atheros, using a madwifi driver. Virtually all user-friendly desktop Linuxes include this driver (kernel module), and it's a cinch to add to Arch, Debian, and even Zenwalk. The pain is using it: Zenwalk has no system tray applet, so to use networks you need to enter your root password every time through Wifi Radar. I could handle that...but Wifi radar clogs up my system so badly that it becomes virtually unusable, and I have yet to successfully connect to a network with it. And sorry to say, iwlist + iwconfig won't cut it for me...

---

### Post by angryfirelord on 2007-06-19
Well, I don't know about wifi radar, but you have to edit your */etc/rc.d/rc.inet1.conf* file. Here's an example:
```
# Config information for ath0 (using dhcp):
IFNAME[1]="ath0"
IPADDR[1]=""
NETMASK[1]=""
USE_DHCP[1]="yes"
DHCP_HOSTNAME[1]="mywirelessbox"
```

---

