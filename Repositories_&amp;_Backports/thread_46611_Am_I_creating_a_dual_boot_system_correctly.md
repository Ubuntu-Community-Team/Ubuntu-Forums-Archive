---
title: "Am I creating a dual boot system correctly?"
date: 2005-07-05
forum: Repositories &amp; Backports
---

### Post by viciouspoultry on 2005-07-05
I want to make a Daul boot system between Ubuntu and Windows XP so far I have done the following:

I resized my Main Windows Partition and with it I made a Linux Patition. To do this I used Partition Magic.

I am Downloading the iso right now.


I think this is what I have to do once I boot the cd:

I select to install in my Linux partition is that right?


Should this create a working dual boot system or not?

Thank you

---

### Post by frodon on 2005-07-05
Yes it will create a dual boot without problem, don't worry about that. But be careful that if you have NTFS partitions for your datas you will not be able to write on it with linux (only read). Also your linux partition (where you will install ubuntu) will not be visible with windows.

---

### Post by viciouspoultry on 2005-07-05
The partition I made is FAT32 so everything will be ok, right? Or is there something else I have to do

---

### Post by frodon on 2005-07-05
[QUOTE=viciouspoultry]The partition I made is FAT32 so everything will be ok, right? Or is there something else I have to do[/QUOTE]

No just follow the install, it will format automaticaly your linux partition in the good format. Basicly you just need space for your linux partition (between 5 and 10Go) and format your partition with your datas (video, music, photos , ...) in FAT32 if you want to have a full support with linux. 
That's all !

Don't hesitate to post questions if you have problems, when you've finished to install ubuntu you will find here most of informations you need  : [http://ubuntuguide.org/4.10/index.html](http://ubuntuguide.org/4.10/index.html)

---

