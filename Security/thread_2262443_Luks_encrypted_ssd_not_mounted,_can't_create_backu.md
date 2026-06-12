---
title: "Luks encrypted ssd not mounted, can't create backup header"
date: 2015-01-24
forum: Security
---

### Post by robert154 on 2015-01-24
First of all, I am newb. Please forgive me.

I wiped Windows 8.1 with Ubuntu 14.04 and chose to encrypt my ssd during installation process (because it seemed like an awesome idea at the time) and went through the post-installation optimization instructions at [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first).

Everything is good, Ubuntu runs fine... BUT I learned about the need to create a backup for my luks header. Following the instruction from 
(1)  [https://www.lisenet.com/2013/luks-add-keys-backup-and-restore-volume-header/](https://www.lisenet.com/2013/luks-add-keys-backup-and-restore-volume-header/)
(2)  [https://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions](https://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions)

I am running into the following problem...

when I type 'cryptsetup luksDump /dev/sdb3' I get the response 'Device /dev/sdb3 doesn't exist or access denied.'

However, using Gparted I see two partitions: one that contains several unformatted sections to preserve ssd, another that contains Ubuntu ('/dev/sdb1', '/dev/sdb2', and '/dev/sdb3'). The first two have mount points '/boot/efi' and '/boot' respectively but the third, '/dev/sdb3', has no mount point and right click>information reveals that it is not mounted indeed. It also says 'Linux Unified Key Setup encryption is not yet supported' at the bottom of the window.

I am confused because upon booting I have to enter a password and it says sdb3 crypt setup was successful yet it is not mounted and I cannot run the aforementioned command for cryptsetup. 

If someone could explain what is going on here and point me in the right direction that would great!

---

