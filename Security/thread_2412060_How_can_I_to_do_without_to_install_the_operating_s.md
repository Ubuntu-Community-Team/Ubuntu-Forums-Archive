---
title: "How can I to do without to install the operating system?(encrypt the disk)"
date: 2019-02-07
forum: Security
---

### Post by rregorr on 2019-02-07
I installed the Ubuntu in two desktops. In one of them, I encrypted the disk during the installation of the Ubuntu, and during the boot process, I type a password to decrypt. In the another desktop, I didn't encrypt it during the installation. But, after, I regretted it. I would like to set the second computer the same as the other. That is, encrypt too, in such a way, that is ask a password during the boot to decrypt the disk.
How can I to do without to install the operating system?
Thank you.

---

### Post by TheFu on 2019-02-07
TL;DR probably not.

Longer version:

If you are an expert beyond my skills, maybe, but why not just capture a list of installed packages, backup the data, do a fresh install, then reinstall the data?  Should take 30-45 minutes.

If you created separate partitions during the original install and have lots of empty space elsewhere for /home and /var, it could be faster.

Please, if you use any form of encryption, please, please, have excellent backups and fully tested restore processes. If anything bad happens, only a backup will be useful. On encrypted disks, data recovery tools are useless.

---

