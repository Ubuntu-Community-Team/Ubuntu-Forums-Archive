---
title: "Setup complete! No such partition!"
date: 2010-04-28
forum: Server Platforms
---

### Post by stray on 2010-04-28
I installed Karmic Koala last night on an old box I'm going to be using as a home server. I dropped a new HDD in it and ran the setup. I got all the way through setup, the CD popped out and it told me to restart. When I did, I got a "no such partition; rescue>" message right after the BIOS. Figuring I'd done something wrong, I wiped the HDD, re-ran setup and got the same error.

The weird thing is that when I did a test run with the old 18GB HDD, it worked fine. Setup completed and Ubuntu came up perfectly after restart.

What am I doing wrong with this new HDD?

---

### Post by arrrghhh on 2010-04-28
What are you selecting for the partitioning?  Are you doing manual or just letting the setup choose how to slice up your drive?

Either way it shouldn't matter, but obviously there's some potential for mistakes if you do it manually.

Also, has the drive been wiped and the partition table deleted?  I'm assuming you're starting with a fresh drive, nothing else on it here.

---

### Post by BobVila on 2010-04-28
How big is the new HDD? If it's ginormous and you don't put a small (250mb-ish) /boot partition at the front of the drive, you can hit that error. (I've run into it in the past - it's infuriating). Go through the setup again, manually partition the drive, and make sure that /boot is the first partition on your new drive.

Typical simple setup:
/boot - ~250MB
swap - a few GB - adjust to your preference, based on available RAM
/ - leftover available space

---

### Post by stray on 2010-04-28
The new HDD is a 500GB PATA (IDE) drive.

I chose the default (guided: use the entire drive and set up LVM) option in setup.

> **BobVila said:**
> How big is the new HDD? If it's ginormous and you don't put a small (250mb-ish) /boot partition at the front of the drive, you can hit that error. (I've run into it in the past - it's infuriating). Go through the setup again, manually partition the drive, and make sure that /boot is the first partition on your new drive.

Typical simple setup:
/boot - ~250MB
swap - a few GB - adjust to your preference, based on available RAM
/ - leftover available space
Should these all be Logical or Primary partitions? How do I jive it with LVM? Do I even need LVM?

---

### Post by BobVila on 2010-04-28
I'd still set the /boot partition at the front of the drive; it <i>should</i> clear it up. If it doesn't and it turns out to be grub2 related, someone else will need to chime in - I haven't taken that plunge yet.

---

### Post by stray on 2010-04-30
Well, sure enough, /boot has to be on its own partition at the start of the drive. Thanks, folks.

---

