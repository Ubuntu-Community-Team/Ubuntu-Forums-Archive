---
title: "OK to partition with Beta version?"
date: 2009-11-09
forum: Ubuntu Moblin Remix
---

### Post by Devi 710 on 2009-11-09
I would like to make a small partition to run UMR 9.10 or the standard Moblin v2.1 (if I can get wireless and trackpad working) on my Dell Mini 10v that is currently running the full Ubuntu 9.10 (so formated to ext4).

I ran a live session of 9.10 and was going to partition using gparted, but it started asking about a "space after" and I wasn't sure, so I chickened out.

I though it best to just try to install from a USB using Moblin v2.1 or UMR, but they are both very Beta. So is this a bad idea? Has anyone partitioned and installed using these images? Is it safe?

Devi

---

### Post by celticbhoy on 2009-11-11
How is your hard drive partitioned just now?

If you want to feel safe then create a second partition using your current install, and then point UMR to it during install.

---

### Post by Devi 710 on 2009-11-11
Thanks for the advice. 

I actually went ahead and did the partition with the UMR (karmic daily release) install. It went fine, but the downside is that it isn't GRUB 2.0, it a beta grub 1.something.

Once I finally decide on an OS, I will start from scratch and format my whole HD. Moblin is very cool, but still needs a lot of work.

---

### Post by EzeAris on 2009-11-11
I've read that you solved the problem, but I wanted to say that it's OK to partition with Beta version, I didn't have any trouble.. I believe that the Partition Software (i'm not sure if it is GParted too) that's included isn't beta like all the distro :)

---

### Post by Devi 710 on 2009-11-11
Thanks for the info. I'll keep that in mind when I am playing around with other beta OSes.

---

### Post by xurizaemon on 2009-11-17
What is up with Grub on UMR? I installed UNR and UMR (partitioned both times using the Live USB). Ubuntu Netbook Remix has the Grub I'm used to, with config in /boot/grub/menu.lst ... Ubuntu Moblin Remix has /etc/grub.d/ but nothing obvious in /boot.

---

### Post by Devi 710 on 2009-11-17
I really don't know what's up with UMR. All I know is I am stuck with Grub Beta 1.97 or something. I make changes to grub through Startup Manager, so I never look for the config file.

I am not using UMR anyway as the internet browser doesn't work, neither does Firefox. Wireless is working, I can install things, but no internet :p

---

### Post by celticbhoy on 2009-11-17
> **xurizaemon said:**
> What is up with Grub on UMR? I installed UNR and UMR (partitioned both times using the Live USB). Ubuntu Netbook Remix has the Grub I'm used to, with config in /boot/grub/menu.lst ... Ubuntu Moblin Remix has /etc/grub.d/ but nothing obvious in /boot.

UMR is using grub2 as all karmic installs should have.

If you search the general forums you will get help on grub 2

---

### Post by celticbhoy on 2009-11-19
> **Devi 710 said:**
> I really don't know what's up with UMR. All I know is I am stuck with Grub Beta 1.97 or something. I make changes to grub through Startup Manager, so I never look for the config file.

I am not using UMR anyway as the internet browser doesn't work, neither does Firefox. Wireless is working, I can install things, but no internet :p

This is Grub2.

---

