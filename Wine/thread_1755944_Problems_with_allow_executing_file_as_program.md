---
title: "Problems with allow executing file as program"
date: 2011-05-11
forum: Wine
---

### Post by boywithsling on 2011-05-11
I have tried to install two seperate .exe windows programs with wine, both times I have got this error: "the file is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run.". I have tried "properties/permissions/allow executing file as program" but I get the error "The permissions could not be changed". I have even used "sudo su" before I clicked the check box. I am using ubuntu 11.04 x64 bit. Any help would be appreciated.

---

### Post by ajgreeny on 2011-05-11
If the .exe file is on a CD or DVD you will not be able to edit its properties.  Copy it and all the other files from CD/DVD to your hard disk and you may get a bit further with the install.

---

### Post by Morbius1 on 2011-05-11
Wine doesn't care if the exe is executable.
Wine itself is incapable of determining if a Windows exe file has a Linux executable bit set.

Please see the following: [http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

I would go with option [2] in that link myself then you will never be bothered with this problem again regardless of where the exe is located.

---

### Post by boywithsling on 2011-05-12
ok, I got to the install wisard now but after the installation reached 65% I got the error: "The file Z:\addon\Content\Plugins\3dSeries\Galery.s3d could not be opened."

---

### Post by StrayEddy on 2011-05-12
Check-out in wine database if your windows program is supported first.
 
Here: [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by boywithsling on 2011-05-12
okay, it's supported with version 1.1.13, I have 1.2.2, is there any way to downgrade wine?

---

### Post by Dlambert on 2011-05-12
I would actually just upgrade to latest beta. Or try [Playonlinux]("http://www.playonlinux.com/en/").

---

### Post by boywithsling on 2011-05-17
have to reinstall ubuntu because I messed up Unity with ccsm ](*,) I think I'll go with 32 bit this time and see if it works better.

---

### Post by boywithsling on 2011-05-26
sorry for the long wait. apparently wine doesn't like Magix Movie Edit Pro 12, I tried using playonlinux but it didn't work either. I may try to learn how to write my own script in playonlinux if it's not too hard.

---

