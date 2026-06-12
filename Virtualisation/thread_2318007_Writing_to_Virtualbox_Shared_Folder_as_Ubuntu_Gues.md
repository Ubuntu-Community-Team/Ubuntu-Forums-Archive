---
title: "Writing to Virtualbox Shared Folder as Ubuntu Guest"
date: 2016-03-22
forum: Virtualisation
---

### Post by samuelrey010 on 2016-03-22
I just fired up an Xubuntu 14.04 guest with guest additions 5.0.16 with the intent to share data with my Windows 10 host. [Referencing this guide]("https://forums.virtualbox.org/viewtopic.php?t=15868"), I was able to mount the folder properly. However, my user does not have permissions to write to the folder.

Even when I ran ```
sudo mount -t vboxsf -o rw,uid=1000,gid=1000 share ~/host
```
I had to use sudo to write to it.

I've tried opting out of auto mount, adding that line to /etc/rc.local and making myself a part of the vboxsf group all to avail. The interesting thing, though, is that it seems that I own anything I write to the folder.

```
psycho@virtual:~$ ls -lhr Videos/
total 7.9G
-rwxrwxrwx 1 psycho psycho 2.9G Mar 19 14:31 TheImitationGame.mp4
-rwxrwxrwx 1 psycho psycho 1.5G Mar 16 20:34 StarTrek.mp4
-rwxrwxrwx 1 psycho psycho 701M Mar 19 13:37 RushHour.mp4
-rwxrwxrwx 1 psycho psycho 602M Mar 20 00:37 InglouriousBasterds.mp4
-rwxrwxrwx 1 psycho psycho 985M Mar 19 13:39 GoneGirl.mp4
-rwxrwxrwx 1 psycho psycho  504 Mar  2 22:05 desktop.ini
dr-xr-xr-x 1 psycho psycho    0 Mar 18 01:47 Captures
-rwxrwxrwx 1 psycho psycho 1.3G Mar 18 00:16 AceVentura.mp4

psycho@virtual:~$ touch Videos/test
touch: cannot touch &#8216;Videos/test&#8217;: Permission denied

psycho@virtual:~$ sudo touch Videos/test
[sudo] password for psycho: 

psycho@virtual:~$ ls -lhr Videos/
total 7.9G
-rwxrwxrwx 1 psycho psycho 2.9G Mar 19 14:31 TheImitationGame.mp4
-rwxrwxrwx 1 psycho psycho    0 Mar 22 01:30 test
-rwxrwxrwx 1 psycho psycho 1.5G Mar 16 20:34 StarTrek.mp4
-rwxrwxrwx 1 psycho psycho 701M Mar 19 13:37 RushHour.mp4
-rwxrwxrwx 1 psycho psycho 602M Mar 20 00:37 InglouriousBasterds.mp4
-rwxrwxrwx 1 psycho psycho 985M Mar 19 13:39 GoneGirl.mp4
-rwxrwxrwx 1 psycho psycho  504 Mar  2 22:05 desktop.ini
dr-xr-xr-x 1 psycho psycho    0 Mar 18 01:47 Captures
-rwxrwxrwx 1 psycho psycho 1.3G Mar 18 00:16 AceVentura.mp4
```

Appreciate any direction on how to solve this. Thank you!

---

### Post by ajgreeny on 2016-03-22
Do you have the "Guest Additions" installed in the VBox manager?
I presume you do or the folder would not even show, if I remember correctly.

---

