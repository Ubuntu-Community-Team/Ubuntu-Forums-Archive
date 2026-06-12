---
title: "Ubuntu 12.04 64bit with Xen, console issue"
date: 2012-11-07
forum: Virtualisation
---

### Post by TurboBee on 2012-11-07
I just did a fresh install of Ubuntu 12.04 64bit and installed xen as per the directions here:
[https://help.ubuntu.com/community/XenProposed](https://help.ubuntu.com/community/XenProposed)

After a reboot my console appears to be spewing dmesg output over and over at a rate so fast that I can't type anything on the console.  Here is a picture I was able to take of my KVM output (note I checked this on a regular monitor too and it was the same).
[IMG]http://geo.animounted.net/xenconsole.png[/IMG]

I'd like to point out that everything prior to getting to the login prompt looks normal, even the regular dmesg output that you get on boot.  Once I hit login it starts shooting that output out like crazy.  Any ideas?

EDIT: I'd like to point out that I can login via SSH with no problems.

---

