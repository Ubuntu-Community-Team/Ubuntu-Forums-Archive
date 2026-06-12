---
title: "Instalar Ubuntu 16.04- 64 bits para dual boot con Windows 7 ultimate-64 bits"
date: 2017-06-05
forum: Software
---

### Post by Vero1 on 2017-06-05
Buenas a todos,

Tengo en un disco de 500 Gib instalado Windows 7- ultimate- 64 bits.
Quiiero instalar Ubuntu 7 ultimate-64 bits, para tener dual boot.

Mi pregunta es: Se puede particionar desde Ubuntu, con el LiveDVD?  porque leí que se podía particionar desde Windows pero no me convence. Estoy más práctica en Ubuntu con GParted.

He probado "reducir" el espacio que tiene asignado Windows pero de los 500 Gib me libera 224, cosa que no sé cómo puede ser si presuntante Windows no ocupa mas de 35 Gib.
Está bien que ya se instalaron más de 143 actualizaciones pero de igual forma me parece excesivo el lugar que se toma. Anulé esta operación.

Mucho agradecería me dijeran cuáles son los pasos a seguir porque  estoy con este problema hace unos días, sin saber realmente qué hacer y cómo.

Desde ya, muchas gracias y saludos.

---

### Post by oldfred on 2017-06-05
We are primarily an English site.

We do have some sub-forums that are using Spanish, but they are not very active.
[https://ubuntuforums.org/forumdisplay.php?f=183](https://ubuntuforums.org/forumdisplay.php?f=183)

Better if you can use English, and there may a local Ubuntu forum not directly part of this English site.
This looks more active, but I cannot read it.
[http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum)

Google translate says you want to install Windows.
If you want Windows 7, you need a primary (sda1 thru sda4) NTFS formatted partition with the boot flag. It cannot be a logical partition. And even if formatted with gparted/Linux you may need to reset format using Windows partition tools, installer or repair console to NTFS before installing, reformat or run chkdsk. There can be internal differences as NTFS has one version for XP and another for newer versions of Windows.

---

### Post by Vero1 on 2017-06-05
Hi oldfred and many thanks for your answer.
In first place Google translator is wrong.
I don´t want to install Windows.
I try to explain to you, in English, my problem and apologize for my not perfect English.

I have a hard disk of 500 Gib, where is installed Windows 7 - ultimate, 64 bits. I want to install, for dual boot, Ubuntu 16.04-64 bits.

Until now, when I had to make partitions, I always used GParted, but in this case I´ve read that partition has to do with Windows. Well I made it but after reducing, the unallocated space were 224 Gib. I was surprised because Windows originally needs, more or less, 35 Gib. It is true that I made update already but I don´t think after updating can remain 224 Gib of 500 Gib. Then I erased this change and left Windows.

I need somebody explain to me, step by step, the way of make my partitions for Ubuntu. I was browsing the Web since 2 days but there are to many information and I really prefer a human being to help me.

Thank you in advance for your comments. :-)

---

### Post by oldfred on 2017-06-05
Use Windows to shrink Windows and always reboot immediately after the shrink so it can run chkdsk.
But Windows puts some unmoveable files in the way sometimes.
        you want at least 30% free inside the NTFS partition for Windows to work well, so do not make too small.
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html) 

Do you have the 4 primary partition limit. Most Windows 7 systems are installed with BIOS/MBR and use all 4 primary partitions. One must be converted to the extended partition which acts as a container for all the logical partitions. Ubuntu will boot fine from a logical partition.
Post this from Ubuntu live installer's terminal:
sudo parted -l

Many backup and delete the vendor's tools partition as that is usually small. 
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD. 

I prefer to also separate operating systems from my data. I did this back with XP and still do this with Ubuntu.
Many also have a shared NTFS data partition with any data they may want in both Windows & Ubuntu. I moved all photos, Firefox & Thunderbird profiles to shared so I had same email & bookmarks. My wife used now discontinued Picasa in both Windows and Ubuntu until I turned off XP, years ago.

If just starting out the default install of / (root) and swap is all you really need. 
Bit more advanced is a separate /home. And then you can also add other partitions if desired, but most cannot be added when installing. I prefer to use gparted to create partitions, it seems a bit easier, but you can create them duing install with Something Else if you want separate /home.

      
 Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[URL="http://www.dedoimedo.com/computers/gparted.html"]http://www.dedoimedo.com/computers/gparted.html

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

      [/URL]
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
16.04 install screens
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first) 
    [URL="http://www.dedoimedo.com/computers/gparted.html"]
[/URL]

---

### Post by Vero1 on 2017-06-06
Hello oldfred,
Thanks again for your answer.
I will see the links.
Maybe I will have to bother you with some question. Hope not.
Greetings ):P

---

