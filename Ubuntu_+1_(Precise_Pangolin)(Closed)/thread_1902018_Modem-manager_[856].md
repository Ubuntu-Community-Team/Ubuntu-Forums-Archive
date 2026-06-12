---
title: "Modem-manager [856]"
date: 2011-12-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sammiev on 2011-12-29
It seems Ubuntu+1 is taken for ever to shut down. ( extra 60 to 90 seconds ) I checked to see what was holding on exit and it shows modem-manager [856] caught signal 15 shutting down. 
Is this a current bug or problem anyone else having?
Thanks

---

### Post by effenberg0x0 on 2011-12-30
I was, some time ago, when we began testing PP. I uninstalled network-manager, network-manager-gnome, modem-manager and manually setup an IP in /etc/network/interfaces and DNSs at /etc/resolv.conf. VPN / SSHFs connections / mounts are all moved to scripts I manually run as needed. It's a desktop, fixed in place, that only connects to one wired router, and gets a fixed IP based on MAC, so it makes no sense for me to use this stuff.

This is a fast machine, ssd, etc, but even so, it was taking  something like 30 seconds to shutdown before I removed these things.

Once I got rid of the eventual boot/shutdown issues, it became clear that developers did something to speed things up in PP. I never had faster boot / shutdown times as I do now. Shutting down takes about 5 seconds. I just hope it keeps this way until release.

---

### Post by mc4man on 2011-12-30
You may be affected in whole or part by this, though it started in 11.10 & continues into 12.04

Seems to increase normal shutdown/restart times by about 5-6X, here that means 2 to 12 secs.
I don't use Network Manager, (Wicd), so no longer affected & am back to 2 sec's most of the time. (there are other factors that can occasionally increase the time.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)

---

### Post by sammiev on 2011-12-30
Thanks Folks.

---

