---
title: "IDE RAID1 booting question"
date: 2005-10-17
forum: Server Platforms
---

### Post by BajanGerry on 2005-10-17
Hi guys, I have a question relating to booting a RAID1 IDE configuration after one of the drives fails. I have a Ubuntu 5.10 installation that has two IDE drives one on each IDE channel. I have setup Ubuntu using the "server" option and configured RAID1. The PC boots fine and all is well but there is a problem that I do not understand. If I simulate a drive failure on the IDE channel 1 drive by disconnecting the drive I am not able to boot from the second IDE drive. Is this normal or is there something I missed? Do I have to manually install Lilo or Grub onto the second drive? I assumed that the RAID would have doe that for me but maybe not. Can someone point me in ther direction fo a document that deals wit this question? All I have read so far does not address this so i am a little lost.

Thanks for any help guys,

Gerry.

---

### Post by LordHunter317 on 2005-10-17
If you use GRUB, you have to manually install it.  This is a major PITA.

IF you use LILO, you just have to set root=/dev/md0 (or whatever RAID it is) and it will do the right thing.

---

### Post by BajanGerry on 2005-10-18
So if I understand you correctly I will have to install Lilo on both of the individual IDE drives? Should I do this before I create the RAID?

---

### Post by LordHunter317 on 2005-10-18
No, install the LILO package.  Edit /etc/lilo.conf and make your root device /dev/md0.

Run /sbin/lilo.  LILO will then automatically install itself on all members of the RAID-1 array.

---

### Post by BajanGerry on 2005-10-19
Ok, followed your instructions but unfortunately Lilo did not install on the first IDE drive which originally had Grub. Fortunately this is a testing environment that I am working with so I am going to re-install Ubuntu from the start again and try to select Lilo instead of Grub, not sure if that is an option during the installation, can't remember seeing it.

---

### Post by BajanGerry on 2005-10-20
It Worked! I did a server-expert installation and selected Lilo instead of Grub after creating the RAID 1 container. I tried booting with the first hard drive disconnected and it all came up perfectly. Guess that will get me going now, just going to do more tests to see if I can break it again before I put this configuration on a rel time server.

Thanks for your help LordHunter.

---

