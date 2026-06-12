---
title: "Ubuntu CE/ e-sword installation problem"
date: 2008-01-16
forum: Ubuntu Christian Edition
---

### Post by father_je on 2008-01-16
hello, can anybody help me, i have installed esword-ubuntu_1.6_all.deb using GDebi Package installer, now all i have is the esword icon in my accessories and when i try to launch it nothing happens, but the esword module manager works fine, pls. can anybody help me to install esword in ubuntu ce, do i have to run the module manager and download the bibles before it will work, thank you very much

---

### Post by jonathonblake on 2008-01-17
> **father_je said:**
> now all i have is the esword icon in my accessories

The new version of e-Sword was released either today or yesterday.

This version breaks:
* The e-Sword installer;
* The e-Sword Module Installer;

For some stupid reason, Ubuntu won't install on my computer, so I can't rewrite the scripts to fix it.  :(

I'm using the Live CD.  :)

#####

For those who want to fix it, e-Sword 7.9.3 looks for user files in both "c:\users and settings\user-name\My Documents\e-Sword"  and "c:\Program Files\e-Sword"

The recommendation is that one only puts topical files that one is in the process of editing in "c:\users and settings\user-name\My Documents\e-Sword" .  I'm not sure if all Memory resources, Prayer Lists, Bible reading Plans, and Verses Lists have to go in "c:\users and settings\user-name\My Documents\e-Sword", or if they can go in c:\Program Files\e-Sword.

xan

jonathon

---

### Post by david_kt on 2008-01-28
> **father_je said:**
> hello, can anybody help me, i have installed esword-ubuntu_1.6_all.deb using GDebi Package installer, now all i have is the esword icon in my accessories and when i try to launch it nothing happens, but the esword module manager works fine, pls. can anybody help me to install esword in ubuntu ce, do i have to run the module manager and download the bibles before it will work, thank you very much


You can try this "how to" to install latest version of esword (794) and using latest wine (o.9.54). It could install e-sword and even it's modules without any problem. Furthermore, you could install it on any ditro you want, as long as it could run wine.

```
http://ubuntuforums.org/showthread.php?t=404042
```

If any of you have any issue, send PM to me.

DK

---

