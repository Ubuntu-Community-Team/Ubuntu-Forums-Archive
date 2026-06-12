---
title: "Root Kit"
date: 2006-04-03
forum: Server Platforms
---

### Post by 146lily on 2006-04-03
I've met a rookit in the wild, it mangled the contents of a 160gb portable hdd containing mp3's and avi's (and a couple of operating systems). Once the files were transfered to the hdd I could not delete them using winxp,   sudo root ubuntu and root suse 10 (correct permissions). At one point they appeared to be expanding (16gb) at which point I switch off the drive. They set themselves up using a folder named root. Fortunatly they do not appear to be able to spread by themselves and needed my help to move ](*,) . The problem is that once they got in all I could do was repartition and format. Backup's are vital, I can restore the data.....beware. A method is needed to delete these files. This is worse than my virus and trojan fights under windows, both windows and linux can be attacked.

---

### Post by h3llfyr3 on 2006-04-05
I'd be looking at rootkit revealer and chkrootkit both in synaptic to see what may have happened.

Sounds like they broke root though (needed to install a rootkit as it modify's the kernel) so you need to do full formats (including boot sector) and restore from backup.

The only rootkit i know that is cross platform is hydrogen which can be used on both windows and *nix.

---

