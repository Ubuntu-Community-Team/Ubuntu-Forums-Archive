---
title: "Windows vs Linux"
date: 2005-09-06
forum: Server Platforms
---

### Post by gmf on 2005-09-06
Using Linux I can read and write NTFS and Fat32 partitions. When I use Windows I must use special programs ( ExpolreFS ) to use Linux partition. I have a question:
[B]
How I can block access to my Linux partition from Windows??[/B]

 I have both Xp and Ubuntu om my PC. I

---

### Post by Tiede on 2005-09-06
I think this qualifies more as a feature request than a security issue... If you want you can always try blocking it with a password... I guess.

---

### Post by gmf on 2005-09-06
I think it is scerurity issue. I'm owning a Pc, but my family is using it. The usually use Win Xp and they are irresponsible. They can install some virus or spyware. I want to protect my Linux partition.

how can I use password here ??

---

### Post by ep0niks on 2005-09-06
First, there's no chance in getting viruses and spyware to your linux system. Second, your Windows based ext3 viewer is.. simply a viewer so you can only read the files on it.

---

### Post by LordHunter317 on 2005-09-07
You can't do this, so it's not even worth discussing.

Your only solution is to keep people you don't want accessing your data off your computer (not likely) or encrypt it (simply overkill).

---

### Post by wmcbrine on 2005-09-09
Once upon a time, I bought a used drive that had no partition table. After fooling around with it for a bit, instead of making a new partition table, I just mke2fs'd the whole thing; so when I mounted it, I had to mount /dev/hdb, instead of /dev/hdb1 or such. This worked fine in Linux.

Coincidentally, I then discovered that, by not using a partition table on the drive, I'd made it quite unreadable to any Windows ext2fs utility I could find. Call it security through obscurity, perhaps. :)

---

### Post by Tiede on 2005-09-12
Nice! I will think about this when I am buying my new HD for the Family Computer! But wait... Shouldn't that be qualified as a bug...that will (surely) be fixed in the next release of the ext2fs Windows utilities? I am quite bummed...

---

### Post by LordHunter317 on 2005-09-12
[QUOTE=Tiede]Shouldn't that be qualified as a bug...[/quote]Nope, no bug.  Definite feature.  Won't ever go away.

There's no way to protect your data from being read if *physical* security is compromised other than to encrypt it.

---

### Post by GTvulse on 2005-09-12
gmf in my experience, Windows ext2/3 tools are not able to read ext3 partitions with extended security attributes as, for example, created by RHEL4/CentOS4 (I have CentOS installed in my box for work reasons) and probably Fedora Core 3/4 (but haven't used the latter therefore I can't speak with certainty in the case of FC distros). If you can manage to acitvate SELinux and extended ACLs in an ext3 partition, it will be unreadable from Windows.

---

### Post by Muhammad on 2005-09-13
[QUOTE=gmf]Using Linux I can read and write NTFS[/QUOTE]

I didn't know that was possible...

---

### Post by GTvulse on 2005-09-13
[QUOTE=Muhammad]

[QUOTE=gmf]
Using Linux I can read and write NTFS
[/QUOTE]
I didn't know that was possible...[/QUOTE]
Linux native writing support is very limited yet, but there are commercial (as in proprietary) solutions that do work. E.g., [Paragon's Linux NTFS drivers.](http://www.ntfs-linux.com/).  There are as well hacks that use the original Microsoft NT filesystem drivers, namely [Captive](http://www.jankratochvil.net/project/captive/). The latter works on the same principles as ndiswrappers. Yet, Captive is very much a 2.4.x kernel module and requires some facilities not compiled by default in a 2.6 kernel. Considering the effort, you may or may not be up to the task of installing Captive. If you are not, Paragon's software is a safe alternative.

---

