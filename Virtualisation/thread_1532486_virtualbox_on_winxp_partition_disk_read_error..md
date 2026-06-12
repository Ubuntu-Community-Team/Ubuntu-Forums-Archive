---
title: "virtualbox on winxp partition: disk read error."
date: 2010-07-16
forum: Virtualisation
---

### Post by wahr on 2010-07-16
I've been at this for a couple hours now and am terminally confused.

I have an xp and ubuntu dual boot setup on a thinkpad t60, and am trying to run xp as a guest machine because of (explatives deleted) exchange 2007 servers.

I do some google-fu and create a VMDK which passes muster with virtualbox's utility, allowing me to map to the physical drive.

Here are the particulars.

I created 2 separate vmdk's, 1 for the lone xp partition /dev/sda1 , and 1 for the full drive /dev/sda .

the one for the xp partition fails to even make it to a boot screen, simply sits there at a prompt which doesn't respond to input.

the one for the full drive happily transitions into the grub menu, but goes screwy from there. If I try to go into ubuntu (booting a second time from the same drive) it will go to the same blank screen as the lone xp vmdk.
If i go to the thinkpad default nt recovery partition it will start to boot, and die because it's graphics are 16 bit, not 32.
If I go to the xp drive from grub it dies with a Disk Read Error.

At this point I can't find any reference on it. Any virtualization pros out there have ideas.

---

