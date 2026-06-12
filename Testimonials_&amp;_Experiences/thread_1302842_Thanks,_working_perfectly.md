---
title: "Thanks, working perfectly"
date: 2009-10-27
forum: Testimonials &amp; Experiences
---

### Post by leolion on 2009-10-27
I had a laptop that one day wouldn't boot. Reinstalling or fixing XP wouldn't work because for no apparent reason it had lost a file (it wasn't a virus, it just crashed) and basically I needed a later version of XP to get past a pci.sys error to reinstall. Couldn't even get into safe mode. Much trouble later I got XP running but even with all the manufacturers drivers it just wouldn't find various pieces of hardware so in mild desperation I thought I'd try Ubuntu.

Here's what happened: I put the CD in, it installed, I rebooted picked Linux and it found my wireless network immediately, one password later everything was up and running and working smoothly. I'm really pleased, I was expecting to have to spend an evening sorting out all the hardware but as far as I can tell it quietly sorted everything out in a way that XP SP3 completely failed to do. It's preinstalled with programs that I already use so I really didn't have much to do at all.

I just wanted to say thanks to everyone involved because if there wasn't Linux that laptop would still be sat on a shelf rather than going to someone who will really appreciate it. My only regret is that I installed it after XP so I now have to choose between the two at boot up when I know I've got no reason to use it again. I suppose the only way to fix that is to wipe it clean now and start again isn't it?

---

### Post by VoodooLoveDog on 2009-10-27
There are various ways to deal with your problem. I strongly suggest to wipe clean (don't forget to back-up your data!) and do a fresh install.

---

### Post by coffeecat on 2009-10-27
> **leolion said:**
> My only regret is that I installed it after XP so I now have to choose between the two at boot up when I know I've got no reason to use it again. I suppose the only way to fix that is to wipe it clean now and start again isn't it?

Not necessarily. You could simply delete all the Windows files and use the Windows partition as a data partition. You don't even need to reformat it because Ubuntu can read and write to the MS NTFS filesystem quite reliably.

If you want that partition mounted at bootup so you don't have the hassle of going to the Places menu each time you need to access it, just start a support thread and someone will take you through the easy edit of a system file (/etc/fstab) that you need.

And getting rid of the Windows entry on your grub boot menu is just another simple system file edit - that could be dealt with on the same  support thread if you want.

Welcome to Ubuntu and welcome to the forum. :)

---

### Post by leolion on 2009-10-27
Thank you I think I will ask about doing that, it would be good to know how to do that.

---

### Post by MarcusW on 2009-10-27
I think formatting to another filesystem (ext3, ext4 for example) is a better idea though, if you don't mind loosing all files on that partition. A good program for that is Gparted. (available in synaptic)

---

