---
title: "Problem - Physically Removing a data disk will prevent a system boot"
date: 2010-10-12
forum: Server Platforms
---

### Post by Digifreakske on 2010-10-12
Hey all,

I started a thread at the dutch ubuntu forum but wanted to address a larger community.
I'll try to translate what i wrote but sorry for my crappy english. 
For the dutch people here that don't understand what i'm trying to say: [Link to the thread]("http://forum.ubuntu-nl.org/server-en-netwerk/ubuntu-server-schijven-fysiek-verwijderen-zonder-fstab-edit-te-moeten-doen/")

Here goes. First of all i'll sketch the situation:

Ubuntu server runs well when all the data disks are mounted correctly and you can find my fstab file at the end of this post.
When all the fstab entry's can find their physical disks, all goes well.

Problems occur when i shutdown the server and remove a physical disk.
I didn't edit fstab by # the entry's for that particular disk.
When booting in this situation, the server won't come online.

This is what i find on the screen at boot:
fsck utils-..
/dev/sda1 clean ... ==> That means that the system disk is mounted correctly.
After that, all i see is a blinking vertical cursor.
No CLI access, nothing.

My system disk is mounted correctly but it seems that he keeps waiting for the disk that is removed (because there is still an entry in fstab)

What i would like is:
That he skips the entry of the disk that isn't found and that the server can come online without that disk.

I really found out that the not-commented entry's of the removed disk
cause the not-boot problem.
I wanted to explain how i found that out but that was long.
It comes to lots of shutdowns, often pulling the power of the disk and (un)commenting the entry's in fstab for that disk.

I've been trying to think of a good search string all day so i can find information on the internet but i gave up.

I hope you guys can help me out.
Here is my fstab file:

#Systeem disk
UUID=43b6e27d-8c8c-4725-84dd-3fe2f7c553df     /                 ext4       errors=remount-ro    0       1
UUID=f4730416-109f-4a95-b5b1-5f7be6571731     none            swap      sw                         0       0

#Data disk 1
UUID=F898EE8798EE442A                               /media/Maxtor250GB-SATA-Disk1Paar1                      ntfs     defaults     0     0
/media/Maxtor250GB-SATA-Disk1Paar1             /home/fredje/Maxtor250GB-SATA-Disk1Paar1-Films       none    bind          0     0
/media/Maxtor250GB-SATA-Disk1Paar1             /srv/ftp/Schijf1-Films                                              none    bind          0     0

#Data disk 1 is still ntfs, i know and it works well. I want to solve these problems before i convert all my windows data disks to xfs.

#Data disk 2
UUID=da615817-c244-4e08-9f0b-fb41efb528bc     /media/Maxtor250GB-SATA-Disk2Paar1                             xfs      defaults     0     0
/media/Maxtor250GB-SATA-Disk2Paar1                /home/fredje/Maxtor250GB-SATA-Disk2Paar1-BackupFilms    none    bind          0     0


Can anybody help me out?
I'm just guessing: disable fsck or edit fstab in some way or different ways of mounting the disks ......

Thx anyway!

Digifreakske

---

### Post by fatbotgw on 2010-10-13
As far as I know, the only way of disabling the automatic mounting of a drive is to comment it out in fstab.

I might have missed it, but which drive are you physically removing?

---

### Post by Digifreakske on 2010-10-13
I want to be able to remove Data disk 1 or 2 or both without having to edit fstab.

---

### Post by dtfinch on 2010-10-13
Pressing the 's' key (for "skip") should get past the boot mount wait freeze.

Adding the "nobootwait" mount option to the data disk fstab entries should prevent future freezes.

---

### Post by Digifreakske on 2010-10-13
I'll add that nobootwait to fstab and see what happens.

Thx guys,

Digifreakske

---

