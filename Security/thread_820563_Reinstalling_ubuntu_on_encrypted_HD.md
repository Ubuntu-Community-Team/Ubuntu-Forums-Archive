---
title: "Reinstalling ubuntu on encrypted HD"
date: 2008-06-06
forum: Security
---

### Post by kchen on 2008-06-06
Yesterday night, I was trying to set up Kubuntu-KDE4 with full partition encryption, but grabbed the KDE3 version of hardy instead. Rather than doing an aptitude install of kde4-desktop, I decided to download the alternate KDE4 CD and do a clean install.

I figured that since I had already set up the encrypted partition with LVM2, the alternate-installer will recognize this and ask me for my passphrase to mount the partition. Then, I can simply ask the installer to mount and install into the logical volumes.

Unfortunately, this didn't happen. The Alternate-installer allowed me to select my encrypted partition and overwrote it instead of simply mounting it.

Thankfully, I have backups of everything so there is no data loss. However, is there a way I can ask the alternate-installer to mount my encrypted partition rather than setting a new one? Perhaps I can escape to the command line and manually mount the partition first, then go back to the alternate-installer?

I welcome any suggestions / comments!

---

