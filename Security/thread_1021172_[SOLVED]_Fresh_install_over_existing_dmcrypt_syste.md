---
title: "[SOLVED] Fresh install over existing dmcrypt system"
date: 2008-12-25
forum: Security
---

### Post by MaddMatt on 2008-12-25
Hey all, 

I have a habit of installing fresh copies of Ubuntu rather than upgrading, due to my previous problems with upgrades. But, the last time I did a fresh install I did so using a DM-Crypt system over LVM. 

So, I am now trying to upgrade to 64 bit Intrepid via a fresh install over my old encrypted / partition (I keep all of my data in a separate encrypted /home partition). 

Trying to install from the alternate 64 bit Intrepid cd doesn't put the installer through a scan-the-harddisk-to-see-whats-there mode, and so my encrypted partitions were jumbled. So, what I did instead was run the 'recovery' side of the disk, to the point where it had me unlock my partitions. I then hit 'escape' to get out of the recovery prompt, skip to the partitioning, and then proceeded to have it install the disc. 

All was fine and good until the actual installation of Ubuntu happened - at which point it hangs at 6% (with two different burns of the MD5 verified image - looks like a bug in the installer). So what I had it do instead was just install the base without gnome, Ubuntu etc. at all- I figured I could just use apt afterward. This didn't work either, and now the system soft-hangs after grub while giving a [usb somethingerather failed] error, and never makes it to a prompt, but still responds to cntrl-alt-del.

So really, I just broke my system - the data on my /home is still there, I just can't get a new copy of Ubuntu installed. Does anyone have experience doing this sort of thing? Thanks for the brainstorm ideas. 

M

---

### Post by MaddMatt on 2008-12-30
OK - well so far I think that I am having a GRUB problem - Would someone do me a favor and post their menu.lst from an Intrepid install using LUKS / DM-Crypt? Thanks, 

M

---

### Post by RansomStark on 2009-01-02
I had all sorts of issues installing with 64bit 8.10 alternate CD with anything to do with encryption. I dropped back to 8.04 to get the install to work and then had to go the upgrade path.

---

### Post by MaddMatt on 2009-01-03
Sounds like that may be the issue, as I have only been trying 64 bit 8.10 alt disks. Did you install 64 bit 8.04 and upgrade? Everything really worked fine? And did you install over a previous encrypted system? Thanks for the note, I'll give it a shot. 
(Day 14 without Ubuntu)

---

### Post by MaddMatt on 2009-01-07
Alright, so I got the 64 bit 8.04.1 install disc to install over my previously encrypted system (with a seperate /home partition). Everything seemed to go without problems, except that my system is not booting. It seems to be soft-hanging after working with some 'usbcore' business... I say soft-hang because it responds to cntrl+alt+del to reboot the system, but it never gets to the actual unlocking of the system. I think this may be some sort of kernel vs. MacBook Pro problem, so I'm going to post this there. Thanks for the advice about the 8.04 64 bit disc!
M

---

### Post by MaddMatt on 2009-01-09
I finished everything and wrote a howto here: [http://ubuntuforums.org/showthread.php?p=6520811](http://ubuntuforums.org/showthread.php?p=6520811)
Please let me know if you see changes. Thanks!

---

### Post by hyper_ch on 2009-01-09
howtos belong into the tutorial section so that they first will be reviewed!

---

### Post by MaddMatt on 2009-01-09
Hi Hyper_ch, thanks for the heads up! I'll ask for it to be moved. Cheers!

---

### Post by hyper_ch on 2009-01-09
you don't encrypt your swap?

Or will this be automatically the case in recovery mode?

---

### Post by MaddMatt on 2009-01-09
> **hyper_ch said:**
> you don't encrypt your swap?

Or will this be automatically the case in recovery mode?

Yes, I do encrypt my swap, and as long as you have the LVM set up properly, the recovery partitioner detects and enables the swap automatically. This is for a re-installation, so I am assuming that the person had their system set up properly to begin with.

---

