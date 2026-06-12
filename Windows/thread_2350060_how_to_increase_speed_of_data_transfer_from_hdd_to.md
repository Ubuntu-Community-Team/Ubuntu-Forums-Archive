---
title: "how to increase speed of data transfer from hdd to pendrive ?"
date: 2017-01-21
forum: Windows
---

### Post by thomas52 on 2017-01-21
normally when i copy some amount of data from my hard drive to my pen drive i get a slow speed of** 2 to 3 Mbps** ? 
is there any possible way to increase the speed of data transfer in windows PC?
please help me ....thanks

---

### Post by HermanAB on 2017-01-21
Yes, buy a better pen drive.  They come with different write speed ratings, though those figures can be hard to find.

---

### Post by Bucky Ball on 2017-01-21
> **thomas52 said:**
> is there any possible way to increase the speed of data transfer in windows PC?

Has this got anything specifically to do with Ubuntu? Anyway, as above from HermanAB.

---

### Post by wildmanne39 on 2017-01-21
*Thread moved to **Windows**.*

---

### Post by sudodus on 2017-01-21
See this link and links from it about the read and write speed of USB pendrives,

[FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

After writing many times to a USB pendrive, it can get slower than it was originally. Then it is possible to overwrite the whole drive with zeros and restore the original speed (or almost the original speed). But don't do it too often, maybe when the speed is reduced to half of the original speed. See this link,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by thomas52 on 2017-01-21
which type of pendrive formatting method should we use ? there are many options like [COLOR=#ff0000]**fat32 , ntfs , exfat** [/COLOR]etc ....[COLOR=#0000ff]**which one do you people prefer?**[/COLOR]. thanks !

---

### Post by sudodus on 2017-01-21
It depends on how you intend to use the pendrive. If you want to transfer data between linux and Windows, I would suggest NTFS. If you want to include to and from a Mac OS, I would suggest FAT32. If you work only with linux, ext4 is a good file system.

---

### Post by thomas52 on 2017-01-22
okay sir thanks a lot !!

---

### Post by kurt18947 on 2017-01-22
> **thomas52 said:**
> which type of pendrive formatting method should we use ? there are many options like [COLOR=#ff0000]**fat32 , ntfs , exfat** [/COLOR]etc ....[COLOR=#0000ff]**which one do you people prefer?**[/COLOR]. thanks !

One thing that has caused me grief in the past is permissions when formatting flash drives. If the file(s) are not user specific - things like pics or generic text files, I find it easier to use FAT32 or perhaps NTFS. Those don't carry user permissions and can be opened on any machine.

---

