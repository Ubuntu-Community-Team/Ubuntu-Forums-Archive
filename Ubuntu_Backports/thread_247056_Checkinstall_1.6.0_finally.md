---
title: "Checkinstall 1.6.0 finally"
date: 2006-08-30
forum: Ubuntu Backports
---

### Post by ashrack on 2006-08-30
Can anyone tell me why 1.6.0 wasn included already in Dapper, since it was release August 10th, 2005??

---

### Post by mlind on 2006-08-30
> **ashrack said:**
> Can anyone tell me why 1.6.0 wasn included already in Dapper, since it was release August 10th, 2005??

Maybe because developers have lives too? ;)
(btw. using checkinstall is baad..)

---

### Post by ashrack on 2006-08-31
Checkinstall is pretty sweet for personal use or for sharing DEBS created with CHECKINSTALL to a group of ppl. If the proper way of crating DEB packages would be much much simplified than CHECKINSTALL really wouldnt be neccessary.

---

### Post by oliverb on 2006-08-31
Exactly how baad?

I've got a couple of source tarballs I want to install and I like the idea of being able to uninstall them easily later.

---

### Post by glennric on 2006-09-01
This version from the backports has some problems.  It puts a lot of leading spaces in the package information, and then the installation fails because of this.  You can change most of the information, except the requirements.  If you try to change them it doesn't.  The leading spaces then prevent installation from succeeding.

---

### Post by ashrack on 2006-09-02
GLENNRIC
Really?
I haven't had any problems thus far with the CHeckInstall from backports. And I've already compiled over about 7things so far. Thanks for the headsup anyway

---

### Post by glennric on 2006-09-02
> **ashrack said:**
> GLENNRIC
Really?
I haven't had any problems thus far with the CHeckInstall from backports. And I've already compiled over about 7things so far. Thanks for the headsup anyway

Maybe it is just something wrong with my system.  All I know is I get things like

```
This package will be built according to these values:

0 -  Maintainer: [ root@glennric ]
1 -  Summary: [         Playable implementation of the Settlers of Catan
        Pioneers Client
        Pioneers Help
        Pioneers AI Player
        Pioneers Console Server
        Pioneers GTK Server
        Pioneers Data
        Pioneers Meta Server
        Pioneers Game Editor ]
2 -  Name:    [                 pioneers ]
3 -  Version: [         0.10.2 ]
4 -  Release: [         1 ]
5 -  License: [ GPL ]
6 -  Group:   [                 Amusements/Games
                Amusements/Games
                Amusements/Games
                Amusements/Games
                Amusements/Games
                Amusements/Games
                Amusements/Games
                Amusements/Games
                Amusements/Games ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ pioneers ]
9 -  Alternate source location: [  ]
10 - Requires: [        pioneers-server-data
        pioneers-server-data
        pioneers-server-console
        pioneers-client, pioneers-server-data ]

Enter a number to change any of them or press ENTER to continue:
```
I can change numbers 1-9 to get rid of the leading spaces and other wierd things, but I can't change number 10 no matter what I do.  Then it fails to build the package.

Edit:  It seems that this new version of checkinstall is getting this information from a spec file, and it is not reading the file properly.  If I use checkinstall to install software that doesn't have a spec file this doesn't happen.

---

### Post by ashrack on 2006-09-02
send me the source and I will try it tomorrow, if I get the time. Have lots of studying ahead of me/

---

### Post by glennric on 2006-09-02
I have been able to compile this software with the new checkinstall, but I had to remove the spec file.

---

