---
title: "Dul booting xp and ubuntu on eee pc help"
date: 2010-07-14
forum: Ubuntu Moblin Remix
---

### Post by bocaccio on 2010-07-14
I have asus eee pc netbook and wanna dual boot xp and ubuntu netbook remix or whatever is suitable for it in ubuntu. I have 250gb hdd and will make 3 partitions
Does anyone have any issues with netbook remix 10.4?
XP
"Linux"
Data
 
Can ubuntu read NTFS or should i make the Data partition FAT32?
 
Thanks

---

### Post by HenneBaby02 on 2010-07-14
> **bocaccio said:**
> I have asus eee pc netbook and wanna dual boot xp and ubuntu netbook remix or whatever is suitable for it in ubuntu. I have 250gb hdd and will make 3 partitions
Does anyone have any issues with netbook remix 10.4?
XP
"Linux"
Data
 
Can ubuntu read NTFS or should i make the Data partition FAT32?
 
Thanks

Ubuntu uses it's own partition so if you are gonna split partitions, leave it unformatted. Though you can just install ubuntu in windows and when you reboot you can choose between Windows XP and Ubuntu (As if your partitions were split). If you mean read NTFS as in a NTFS formatted USB flash drive for example, yes. If you mean read NTFS as if it will install on NTFS formatted partition. It will overwrite it to either ext. 3 or ext. 4.

EDIT: As far as netbook, i never tried that.

---

### Post by WitchBlade on 2010-07-17
> **bocaccio said:**
> I have asus eee pc netbook and wanna dual boot xp and ubuntu netbook remix or whatever is suitable for it in ubuntu. I have 250gb hdd and will make 3 partitions
Does anyone have any issues with netbook remix 10.4?
XP
"Linux"
Data
 
Can ubuntu read NTFS or should i make the Data partition FAT32?
 
Thanks

im just finished installing dual boot win 7 and ubuntu.10.04.. im using wubi so no need to create partition for it..

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
@ OP
You have the right idea. That's how I have my lappy partitioned, and yes, make the data partition NTFS so windows and ubuntu can both read/ write to it.

@ witchblade
I've seen and heard of lots of problems with WUBI for long term use (including having them on my own). I, as well as many others, view WUBI as one step better than the live CD for hardware compatibility testing. After you've ascertained that you're happy with its performance you're best off setting up a true dual boot. Just my $.02

---

### Post by bocaccio on 2010-07-18
I let it split the hdd down the middle for 7 and ubuntu. I am REALLY considering using gparted to erase 7 and just keep ubuntu. (my first long term experience with linux; getting really sick of windows)

The only problem is i'll need to either use vnc and use my desktop from here (my netbook/ubuntu) and/or use virtualbox and run windows to use the apps i need. Here is why I will need windows apps.

Currently i am in classes with AIU online and obviously i use office apps alot. I have never tried oo.org apps I am sure they're similar if not VERY similar; just don't know if school will accept them as word docs, powerpoint presentations. and anything else i'll need.

Other than that I love ubuntu am sick of windows even though 7 rocks!!! Fact is 7 lags on my netbook and ubuntu runs like an orgasm!!

I hope that I am actually learning "linux environment" from ubuntu.

---

### Post by KdotJ on 2010-07-18
bocaccio, did you install using WUBI? or did you do a real install on your disk?
As for Office, if you need it for such reason, you should have a look at WINE. It allows you to run (not all) Windows programs "natively" under ubuntu. Looking at [THIS]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10") page, Microsoft word works pretty well under WINE

---

### Post by bocaccio on 2010-07-18
> **KdotJ said:**
> bocaccio, did you install using WUBI? or did you do a real install on your disk?
As for Office, if you need it for such reason, you should have a look at WINE. It allows you to run (not all) Windows programs "natively" under ubuntu. Looking at [THIS]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10") page, Microsoft word works pretty well under WINE
Thanks so much!! I'll check out wine asap. I did not use wubi. I did an actual install. I guess worst case scenario i could run a killdisk and then install ubuntu solely and then just install all that i have back on here. but i did see something on ubuntu where you can make a disc to save your state as it is.

---

