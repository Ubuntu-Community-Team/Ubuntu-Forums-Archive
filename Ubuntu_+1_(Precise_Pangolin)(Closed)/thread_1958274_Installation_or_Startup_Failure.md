---
title: "Installation or Startup Failure"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by longbeard on 2012-04-13
I downloaded beta2 desktop i386 yesterday and installed it on a system where there also exists an installation of 10.04 LTS (on separate partitions). I have a GRUB version on FD device (showing "1.98-1ubuntu13") which collects various OS start options on startup. I also have a GRUB, or so it seems, in the MBR now. 

With both startup methods launch of the Penguin fails. This is the output:

error: fd1 cannot get C/H/S values.
error: file not found
error you need to load the kernel first

After "Enter" the GRUB menu reappears (in case I started from FD).
Any suggestions what the problem might be?

Doesn't look very good to me.

---

### Post by fantab on 2012-04-14
When you installed beta2 how did you install GRUB? Did you install on the partition or disk or FD device?

If it was installed by default then probably the new Grub is on Partition. See if you load your penguin without FD device...

Also update FD grub.

---

### Post by longbeard on 2012-04-15
1)
I installed just normal and I have a GRUB 1.98 on the hdd boot sequence. On startup this gives me a list of kernels, mainly from my 10.04 LTS which work ok. Then, very down the list, I have an entry "2.6.38-8-generic" on the partition where 12.04 is installed, but I think this is from a previous installation of an older Ubuntu. This produces the error mentioned.

2)
Second I have a floppy disk with a special GRUB 1.97.2 (since some time unchanged). On startup on the floppy it gives various option. The first being a general "Ubuntu/Linux" option works ok and I can start 12.04. The second option "Any OS" lists "3.2.0-20-generic-pae" which also works ok.  The third option "Grub Config Files" again only leads to the mentioned error.

3) Summary
While the situation appears a bit complicated here it is clear that the regular 12.04 installation has produced a non-startable system and I need a third party aid in order to start it. Just for the record .. :popcorn:

---

