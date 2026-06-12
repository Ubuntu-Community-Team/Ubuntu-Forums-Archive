---
title: "Can't get Wake on LAN to work"
date: 2010-08-03
forum: Server Platforms
---

### Post by HittingSmoke on 2010-08-03
I'm trying to get WOL to work on my web server built on an ASUS P4A800D-X motherboard (which supports wol).

I have it enabled in my BIOS and I've tried several different tools with no results, including my dd-wrt based router which has this functionality built into the firmware.

All the guides I've read say it has to be enabled in the driver settings in the Windows Control panel before it will work, but I'm running Ubuntu Server 10.04.

Is there any special steps that must be taken in the OS to enable my web server to power on from the LAN? I've never used this feature before and would like to just shove my web server in a corner some where and have 100% remote control from my main PC.

---

### Post by HittingSmoke on 2010-08-03
Found the solution to my own problem while searching for info on server hibernation.

```
sudo apt-get install pm-utils ethtool
```

Run
```
sudo ethtool -s eth0 wol g
```

and add it to /etc/rc.local to run at boot.

After running this command my server wakes properly from a powered off state when sending a magic packet.

[Source]("http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html")

---

