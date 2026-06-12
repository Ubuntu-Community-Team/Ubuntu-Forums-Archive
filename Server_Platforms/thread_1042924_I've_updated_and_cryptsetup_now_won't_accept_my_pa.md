---
title: "I've updated and cryptsetup now won't accept my passphrase."
date: 2009-01-18
forum: Server Platforms
---

### Post by xls on 2009-01-18
Greatings Ubuntu server community,

I have Ubuntu driving a six disk software raid-five file server with full system encryption.  It has been operating without issue for quite some time.  I cannot recall exactly which version of Ubuntu I installed, but I've updated it from time to time.

Just recently I've updated it from 8.04 to 8.10 and now during the boot process it does not seem to accept my disk encryption passphrase.  The precise message I receive is “cryptsetup: cryptsetup failed, bad password or options?”  The entire root file system is encrypted.  There are no other partitions so the booting processes ends here.

I'm absolutely certain that I'm inputting my passpharse correctly so I fully believe there to be a simple misconfiguration when I updated between 8.04 to 8.10.  I have a healthy curiosity and I am very interested to learn more about how Ubuntu, Linux, and computers work, however, this issue has me quite puzzled.

I suppose I could use an Ubuntu Live CD to check the /boot partition as that is not encrypted.  I also don't see why I couldn't persuade the Ubuntu Live CD to mount my encrypted software raid in the event that I need to preform data recovery.  Since root never gets decrypted to begin with, I believe the problem to rest solely in the /boot partition.  However, I haven't a clue as to what to look for.

Any suggestions as to how I should troubleshoot my issue would be greatly appreciated.  Thank you for taking time to ponder my quandary.

---

### Post by xls on 2009-01-25
I've read up on the boot process and I feel that it has something to do with initrd.  I'm looking into what initrd does and how to correct it.

---

