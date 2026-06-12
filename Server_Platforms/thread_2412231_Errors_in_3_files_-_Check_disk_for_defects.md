---
title: "Errors in 3 files - Check disk for defects"
date: 2019-02-09
forum: Server Platforms
---

### Post by aljames2 on 2019-02-09
When trying to install to my SSD from my bootable USB stick, I always run the check disk for defects option before installing and I continue  to get this error.  
I hesitate to install and spend all the setup  time when I know there is this nagging error on my mind.
After a lot of  search I found this but not sure if this is what I am experiencing?    [https://bugs.launchpad.net/subiquity/+bug/1810633](https://bugs.launchpad.net/subiquity/+bug/1810633)

I'm inclined to wait at this point for 18.04.2 unless there is a workaround?  I've considered going back and getting the July release of 18.04.1 and then
update/upgrade.

I have verified my download is clean and USB is verified. I have tried writing the USB using Ethcer, Rufus, & Unetbootin and all return the same error.
I have also tried multiple USB sticks and same problem.

---

### Post by TheFu on 2019-02-09
You can download the ISO, manually validate that the **sha256sum** matches, then use **dd** to copy the contents onto a flash drive and install from that.  This won't fix a bad flash drive or incompatible USB controller or flaky port.

As for setting up a new install, you've lost me there.  Just backup your HOME directory and the list of apps installed, **apt-mark**.  Moving to a new computer or doing a fresh install is 30-45 min. Lots of ways to accomplish this - aptik, deja dup, duplicity, rdiff-backup, fsarchiver, clonezilla. Which you pick depends on your needs. There must be 30 more options.  Lots of threads about backups in these forums with links to what others do and their backup scripts.

---

### Post by aljames2 on 2019-02-10
This is my first install.  I’m trying to get past this file error message so I can complete my installation.  The sha256sum did match.  I’m going to wait for the .2 release on Thursday and see what happens.

---

