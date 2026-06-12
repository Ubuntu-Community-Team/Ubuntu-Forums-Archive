---
title: "2nd Data drive to have encryption"
date: 2008-06-15
forum: Security
---

### Post by d80zoom on 2008-06-15
I am about to upgrade my current system and will have my first IDE drive of 80gb which will hold the operating system (Hardy), and all programs, games, etc. My second drive will be a SATA 250GB that I will use for storage of all of my personal files in which I want FULL ENCRYPTION. I am not much worried about the IDE drive, as I can always reinstall the os. But I want all of my files to be kept private and available no matter what happens to the IDE disk.

My plan is to install Hardy first, and leave the SATA drive disconnected, and format it after the installation to eliminate any install problems. I have looked online for guides but have not found any for something as simple as this. I am not dual booting, using RAID or anything else. Is there anything that I need to know before I do this?

---

### Post by hyper_ch on 2008-06-16
well, if you want to protect all your data you'll need to encrypt more than just the second drive... you also need to encrypt the swap and the /temp folder and maybe some other things... otherwise there will always a few parts of the data that are unencrypted....

However just encrypting your /home folder (which I think you want to setup on the second drive) will encrypt a lot of personal data.

Here's a small guide of mine:  [http://ubuntuforums.org/showthread.php?t=404346](http://ubuntuforums.org/showthread.php?t=404346)

Maybe you don't need to load the three modules... if you do, then the "aes" changed to "aes_common" or "aes_generic" (look at the comments).

---

