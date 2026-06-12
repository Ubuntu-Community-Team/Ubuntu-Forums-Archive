---
title: "No initrd.img generated on update/upgrade"
date: 2024-02-08
forum: Server Platforms
---

### Post by iturnaround on 2024-02-08
**# currently running**
Ubuntu 22.04.3
kernel 5.15.0-94 
[B]
# TLDNR; question[/B]

What can I copy to another machine to check the original machine will boot properly, or to test fixing boot errors?
What folders would I need other than /boot? Or should I just clone the whole thing as an image?
[B]
#issue[/B]

I was previously on Ubuntu 20 lTS, kernel 5.4.171
 
When I updated and upgraded and ran do-release-upgrade 
NO /boot/initrd.img-* for the 5.15.0-94 was created, but the grub was automatically updated to look for it.

The result was a kernel panic on boot.

**#details**

After investigation, the update also bricked any kernel from booting back to 5.4.0-121. (kernels like 5.4.0-171 were toast despite having their initrd.img intact)

I booted into recovery mode with 5.4.0-121,
manually create the initrd for the newer kernel with "mkinitramfs"
and manually recreated the initrd.img file for the other kernels with "mkinitramfs".
and "update-grub" 

Then they all worked.

Nothing special about the update and upgrade process.

**#Question**

After getting the new version to boot, cleaning up unused packages caused 5.4.0-121 to be removed, and grub to be automcatically updated.

I'm nervous about rebooting it, since recent automatic grub updates caused boot failures. Without the safty net of 5.4.0-121, I won't be able to get back in without using a live cd. 
(5.4.0-121 is not able to reinstalled, with the message saying it is unfindable and obsolete.)

What can I copy to a different machine to test boot fixes?
 What folders would I need other than /boot? Or should I just clone the whole thing as an image?

---

### Post by ian-weisser on 2024-02-08
> **iturnaround said:**
> I'm nervous about rebooting it, since recent automatic grub updates caused boot failures. Without the safty net of 5.4.0-121, I won't be able to get back in without using a live cd. 

Create a new safety net: Take a the couple minutes to create a LiveUSB.

Sooner or later, everybody needs to know how to properly backup their data, and how to rebuild their services on a newly-installed system.
Anybody who doesn't know how to do those two things is fettering themselves.
Relying upon cloning and updates is relying upon hope. Sometimes folks are fortunate. Sometimes not.

---

### Post by iturnaround on 2024-02-08
I take your point that the ability to rebuild faster from scratch would  be ideal. It's somewhere in the todo list, and moving up the list I  guess.
That being said, things are backed up, and rebuilding is prepared for....I just don't want to give myself a headache I don't have to. 
Repairing the box where it is, is more annoying than diagnosing and determining next course remotely at the moment

---

