---
title: "WoW on Linux [SOLVED]"
date: 2009-03-24
forum: Wine
---

### Post by beatzz on 2009-03-24
First things first, you need at least Wine 1.1.17. To upgrade/install the latest version of Wine.

**_Update/Install Wine 1.1.17 or higher_**

 1. Remove the wine that comes with Ubuntu (if you've installed it)
```
sudo apt-get remove wine
```

2. Open a terminal and type:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

3. Type:
```
sudo kate /etc/apt/sources.list
```

4. Add one of the following to your sources.list
```
## Wine, Ubuntu Hardy Heron (8.04):
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main
```

```
## Wine, Ubuntu Gutsy Gibbon (7.10):
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main
```

```
## Wine, Ubuntu Feisty Fawn (7.04):
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main
```

```
## Wine, Ubuntu Edgy Eft (6.10)
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

```
## Wine, Ubuntu Dapper Drake (6.06)
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main
```

5. Type the following:
```
sudo apt-get update
```

6. Type the following:
```
sudo apt-get upgrade
```

7. To install wine either type:
```
sudo apt-get install wine
```

Or by using the Synaptic Package Manager under System->Administration.

**_Installing WoW_**

Depending on if your using CD's or DVD's there are 2 different mounting procedures for each disk you have. 

**If the installation disk is a CD**
```
sudo umount /media/cdrom0
```
```
sudo mount /dev/cdrom /media/cdrom0 -t iso9660 -o ro,user,unhide,uid=`id -u`
```

**If the installation disk is a DVD**
```
sudo umount /media/cdrom0
```
```
sudo mount /dev/cdrom /mnt/cdrom -t udf -o ro,user,unhide,uid=`id -u`
```

Every time you switch your disks out, you must un-mount then re-mount them with the appropriate command. This ensures all hidden files on the disk that are necessary to install are available for the installer.exe

**_If you get a black screen in game_**
When I set my effects down to low it fixed it. This is as far as I go w/ this tutorial, beyond this good luck.

---

### Post by beatzz on 2009-03-25
This covers the black screen
[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/comment-page-2/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/comment-page-2/)

---

