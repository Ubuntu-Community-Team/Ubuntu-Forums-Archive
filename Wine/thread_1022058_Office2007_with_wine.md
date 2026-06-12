---
title: "Office2007 with wine"
date: 2008-12-26
forum: Wine
---

### Post by hirohitosan on 2008-12-26
I have no experience with Wine. I installed the last version from repositories 1.0.1 and I want to run MS Office 2007. As I read some tutorials I must install Office2007 using wine. The tutorials that I read are a little old for wine 0.9.58

My Office installation is on my HDD in /home/MS Office Enterprise 2007.exe

How to install office?

Just 
```
$ wine /home/MS Office Enterprise 2007.exe
```

thanks

---

### Post by albinootje on 2008-12-26
> **hirohitosan said:**
> 
My Office installation is on my HDD in /home/MS Office Enterprise 2007.exe

How to install office?

Just 
```
$ wine /home/MS Office Enterprise 2007.exe
```


See here for more details : [http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html](http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html)

And you should cd into the install-location, and then run "wine".

---

### Post by dragos_iliescu_2005 on 2008-12-26
You can find comments on Office installation with wine here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992")

---

### Post by hirohitosan on 2008-12-26
> **albinootje said:**
> See here for more details : [http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html](http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html)

And you should cd into the install-location, and then run "wine".
Thanks I read that but I was wondering if it's same for wine 1.0.1?
And it is said that I have to install CrossOver Games, but this is a commercial software?

---

### Post by albinootje on 2008-12-26
> **hirohitosan said:**
> Thanks I read that but I was wondering if it's same for wine 1.0.1?
And it is said that I have to install CrossOver Games, but this is a commercial software?

Hmmm, sorry, I read that install guide too quickly :(

This thread seems to have come to the same conclusion that MS-Office-2007 cannot be easily installed with plain Wine :
[http://ubuntuforums.org/showthread.php?t=385632](http://ubuntuforums.org/showthread.php?t=385632)

And as a side-note.
I have nothing to do with the makers of CrossOverLinux called CodeWeavers, but what I've read in the past is that they are a kind of small and friendly company which supplies rather cheap software+support, while at the same time they're supporting and giving back to the Wine project.

---

### Post by abn91c on 2008-12-26
Openoffice.org 3.0 will open/run MSO2007 files, doccument, presentations.

---

### Post by p_quarles on 2008-12-26
Moved to the Wine section.

---

### Post by hirohitosan on 2008-12-27
Thanks guys. It seems not so easy to install Office 2007 through wine. 
I use MS Office for all my colleagues use it and we sometimes exchange Office files. Using Open Office will damage the files, especially big files with tables, figures and fields. 


BTW
I succeed to install Office 2003 and works fine with no problems

---

