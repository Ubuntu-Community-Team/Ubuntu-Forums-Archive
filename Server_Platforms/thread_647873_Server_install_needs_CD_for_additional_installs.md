---
title: "Server install needs CD for additional installs?"
date: 2007-12-22
forum: Server Platforms
---

### Post by razorfrog on 2007-12-22
I have a server install up and running almost pefectly - but I have a strange problem. Whenever I try to apt-get install anything, I'm asked to put the  7.10 disk in the cd rom drive. The exact prompt is:

*media change: please insert the disk labeled 'Ubuntu-Server 7.10 _Gutsy Gibbon_ -Release i386 (20071016)' in the drive '/cdrom' and press enter*

As I don't like driving over to the server daily, how can I fix this?

Thanks so much!


RESOLVED - sorry! [this]("http://ubuntuforums.org/showthread.php?t=395391&highlight=please+insert+the+disc+labelled") post cleared that up

---

### Post by p_quarles on 2007-12-22
Easy. Open up the repository list:
```
sudo nano /etc/apt/sources.list
```
and comment out the two lines beginning with "deb cdrom:[Ubuntu . . ." You comment them out by placing the "#" in front of the line.

The CD is enabled as a repository by default because the servers usually get swamped at the time of a distribution upgrade.

---

