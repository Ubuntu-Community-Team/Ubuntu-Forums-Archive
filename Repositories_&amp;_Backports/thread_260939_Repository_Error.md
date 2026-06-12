---
title: "Repository Error"
date: 2006-09-19
forum: Repositories &amp; Backports
---

### Post by mattfender on 2006-09-19
I have an error that is occuring when I reload my repositories:

cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
 

Perhaps it has something to do with trying to install R-project.

Any help would be great

---

### Post by Isoss on 2006-09-20
open your sources.list and then comment/remove the lines where you find cdrom then run 
```
sudo apt-get update
``` in terminal

---

### Post by juneym on 2006-09-20
sorry, my post was OT -- mods please delete this message.

---

### Post by juneym on 2006-09-20
*** Sorry! this post isn't supposed to be for this thread ***

Here is the content of my source.list (/etc/apt/sources.list)

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free


---

### Post by Isoss on 2006-09-20
Try these:
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

```
run update then. Your repos didn't seem right. but anyway, try this after you backup your old ones.

---

### Post by juneym on 2006-09-20
Yes, I was confused but thank you! My original post is [here.](http://ubuntuforums.org/showthread.php?p=1522274)

---

### Post by Isoss on 2006-09-20
did it work?

---

### Post by Isoss on 2006-09-20
juneym you confused me also, I thought you're mattfender, the original poster. mattfender .. as I told you, just try to comment out or remove the lines where you find "cdrom" in your /etc/apt/sources.list

---

### Post by juneym on 2006-09-20
I think it's working :) Thank you! I'm downloading the package right now.

---

### Post by mattfender on 2006-09-20
> **Isoss said:**
> juneym you confused me also, I thought you're mattfender, the original poster. mattfender .. as I told you, just try to comment out or remove the lines where you find "cdrom" in your /etc/apt/sources.list

thanks lsoss, but when I put in that command it says "permission denied" , so then I tried Sudo /etc/apt/sources.list, and it says "command not found"
 I've viewed the list before but I am having trouble now

---

### Post by Isoss on 2006-09-21
mattfender, sources.list is a text, not a command, so you must open it with a text editor

so if you are using ubuntu(gnome) run ```
sudo gedit /etc/apt/sources.list
```
so if you are using Kubuntu (kde/ubuntu) run ```
sudo kate /etc/apt/sources.list
```
then the text editor will open up the text file and you'll see many lines like:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
So one or two of those start with "cdrom" ... before these lines put # which will tell apt to ignore this repository ... usually they are placed at the top of the file. Save and close then run ```
sudo apt-get update
```

---

### Post by mattfender on 2006-09-21
That's perfect, I've done that before and I knew there was somethign I was doing wrong this time. Thanks a million!

---

