---
title: "New install - can't boot. Comes up with Grub command line"
date: 2009-02-24
forum: Server Platforms
---

### Post by MountainX on 2009-02-24
I installed 8.10 64bit on a server with two raid cards plus 2 sata drives on motherboard. I made a separate /boot partition on a pass through drive hooked to the Areca controller.

After removing the CD and rebooting, I just get the grub command line. Using find, I did not find /boot/grub/menu.lst or /boot/grub/device.map.

I have tried changing the boot disk in the bios to get the right one without any success. The disk names in bios do not show up correctly, so I am having to guess which disk is which. I have tried all the options.

I've tried everything I can think of with no success. How can I get it to boot? (The install went fine.)

EDIT:
it looks to me like I will not be able to boot from the controller I wanted to boot from (the Areca 1220). I think my best choice might be to make a new /boot partition on another drive. What is the easiest way to do this? Thanks. (newbie here)

---

