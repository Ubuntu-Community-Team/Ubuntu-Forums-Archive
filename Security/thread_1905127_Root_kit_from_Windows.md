---
title: "Root kit from Windows"
date: 2012-01-06
forum: Security
---

### Post by KidFlash1904 on 2012-01-06
I contracted a root kit on Windows XP, called Alureon according to Avast!. I had a Ubuntu Live CD luckily that I had been procrastinating to use to install Ubuntu, so I booted from the CD, and backed up some images, songs, and videos to a flash drive. Afterwards, I installed Ubuntu from the CD by selecting the option to use the entire disk. So I think that it should be eliminated and powerless in Linux anyway, however I'm still a little paranoid. Did the Linux installation really delete everything that was on the hard disk (including the root kit)? And would just connecting the flash drive and using an anti-virus to scan the files suffice or do I have to worry about auto run like in Windows? I really don't want anything like that to happen again, so I am bumping up my security settings and such.

---

### Post by OpSecShellshock on 2012-01-06
In this case it seems pretty unlikely that anything that could run would have survived the installation. That particular trojan is made for running in Windows. The files that you saved prior to installing Ubuntu are also unlikely to present a risk.

Now, the malware that was detected is designed to harvest credentials for things, so be sure to reset any passwords for web-based services like email, chat, and any other site you have to sign into. It also changes DNS settings in order to achieve its goals apparently, but since you have completely installed a new OS that's no longer relevant.

---

### Post by Ms. Daisy on 2012-01-06
> **KidFlash1904 said:**
> I really don't want anything like that to happen again, so I am bumping up my security settings and such. Regarding this bit, if you'd like to learn some basic information about ubuntu security, see [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by iisjman07 on 2012-01-08
Yes your malware should be completely gone. I'm an IT technician and have run into Alureon before, and if I remember correctly the newer versions include a master boot record (MBR) infection as well as a standard rootkit from the system partition. When you install ubuntu, if you selected to use the entire disk, the partition would have been formatted and the MBR replaced by GRUB.

---

