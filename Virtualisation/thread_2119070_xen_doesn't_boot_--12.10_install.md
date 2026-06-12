---
title: "xen doesn't boot --12.10 install"
date: 2013-02-22
forum: Virtualisation
---

### Post by ersatzsplatt on 2013-02-22
I have a fairly new intel motherboard (hopes of getting SR-IOV working on xen).

When I install and try to boot xen over 12.10 ubuntu, I see the expected xen text scroll and then ... stall at black screen.
After a LONG time after one boot, I see:
[  367.571827] BUG: soft lockup - CPU#9 stuck for 23s!  [swapper/0:1]
(yeah, I know that should be about 6 minutes)
trying to switch to simple virtual terminal screens doesn't work at all.

Everything works like a champ with a "normal" boot (vs. xen).

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)     ?
That's not working out for me at all.

I have to use the big button to cycle the system.  Are there xen logs I can see and share when booting into linux?  ... or something?

when I boot the same xen disk on another (older and less powerful) system, I am able to boot xen ... mostly.  the graphical screen comes up with a mouse pointer (responsive to movement) on a black background.  There is a blinking underline cursor at the top left corner.  I am able to go to virtual terminals and login.  this confirms the lines I'm hoping for per:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)
when I type
sudo xm list

It still is a big problem for me that I don't have graphical environment working and even a bigger problem that the newer system doesn't boot xen.
Is there some ubuntu xen mailing list I can reference / work with?
I can contribute debugging effort and help xen to work with newer systems.
Is there some place I can get source code for the package used by
apt-get install xen-hypervisor-amd64
?
Is there some process to go through for filing a bug?  ubuntu xen does not work on hardware that ubuntu itself supports.
Some good tips or references would be much appreciated.

---

### Post by typoworx-de on 2013-05-28
Hello,

I can confirm the problem here, too. No working solution yet! XEN loads and after extracting the boot-image it results most often in a automatic reboot.

Do you have some solution here?

---

### Post by heiko_s on 2013-05-31
See [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013") the red warning in the first post about 4.1.3-3ubuntu1.5. Use the "force version" option in Synaptic (or apt-get) to downgrade to an older release of the following packages:
```
libvirt-bin libvirt0 libxen-4.1 libxenstore3.0 python-libvirt xen-docs-4.1 xen-hypervisor-4.1-amd64 xen-system-amd64 xen-utils-4.1 xen-utils-common xenstore-utils
```

Let me know if it works.

---

