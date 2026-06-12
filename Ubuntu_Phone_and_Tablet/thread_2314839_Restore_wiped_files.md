---
title: "Restore wiped files"
date: 2016-02-24
forum: Ubuntu Phone and Tablet
---

### Post by regis-sarle on 2016-02-24
Hello,

I recently stuck my phone (BQ Aquaris e4.5 ubuntu edition) and had to reflash it. Of course, I've lost a lot of data which I really want to recover. And this is my question : how to recover wiped/deleted files from /home/phablet ?

From the phone, I tried to use standard tools like foremost or scalpel on ssh connection but they are not available with apt-get on the phone.
From an Ubuntu desktop, the BQ connected to it and mounted as mtp:// I tried to use foremost to retrieve the data but foremost uses an input file (such as /dev/sdx), and the phone is mounted as 'mtp://[usb:003,030]/Aquaris%20E4.5%20Ubuntu%20Edition' which does'nt work with foremost... From there I tried to make a symbolic link to the directory mtp:// but symbolic link is not created.

Any other ideas ?

Thanks.

---

### Post by T.J. on 2016-02-24
Hi!

There are several tools available, including testdisk and photorec.  There are others, but I can't remember the names presently.  I'm sorry to say that in using the phone you have probably reduced your chances of recovering data significantly, as the phone will overwrite erased areas of the card the more you use it.  If possible, you should copy the card or replace it until you can recover your lost files.  If you use it too much, it is likely recovery will be impossible.

---

### Post by regis-sarle on 2016-02-25
Hi, 

Well as I wrote, I tried to use standard tools but my problem is how to mount the built-in memory on the desktop ?

When you plug the device in your Ubuntu desktop, it'is recognized as mtp device and you can access it through a link like this one : mtp://[usb:003,030]/Aquaris%20E4.5%20Ubuntu%20Edition. 
The tools need an input file and not a link.

---

### Post by T.J. on 2016-02-27
I'm afraid that mtp mount is outside my personal experience, but it should be really simple if you have an internal or USB card reader.  It should treat it as another drive, probably mounted under /media/ in a directory with your username.  You will then to use tools that access the partitions, not specific files.  The files themselves have been deleted and are not accessible without accessing the drive's partition or data surface.

---

### Post by krusty8 on 2016-02-29
I have no personal experience with this, but I've seen this German website talking about recovering data from a Ubuntu Touch device:
[https://wiki.ubuntuusers.de/Ubuntu_Touch/Sicherung_und_Wiederherstellung/#Datenrettung](https://wiki.ubuntuusers.de/Ubuntu_Touch/Sicherung_und_Wiederherstellung/#Datenrettung)
At the core, they copy the partition they are interested in with adb and dd over:

```
 adb shell  'echo 'PASSWORT' | sudo -S dd if=/dev/block/mmcblk0p7 bs=4k conv=noerror,sync' > ~/Dokumente/backup-touch-mmcblk0p7-home.iso
```

 After that they employ recovery tools on the desktop. Specifically they mention a tool called PhotoRec.

You'd have to see which partition is the correct one for you. 

Hth!

---

### Post by regis-sarle on 2016-04-04
Hi [**[COLOR=#000000]krusty8[/COLOR]**]("http://ubuntuforums.org/member.php?u=1314053"),

It worked. The process you gave me gave me the opportunity to restore some files (unfortunately not the ones I wanted). But this is really helpful.

Thanks again.

---

