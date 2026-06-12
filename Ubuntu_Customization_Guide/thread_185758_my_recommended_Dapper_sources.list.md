---
title: "my recommended Dapper sources.list"
date: 2006-06-01
forum: Ubuntu Customization Guide
---

### Post by ubuntu_demon on 2006-06-01
**I'm posting this as a forum user and not as a staff member. First read the entire post before doing anything. Not all of these repositories are official. This is all on your own risk. Please be careful.**

This is the source.list which I recommend for average users (as well as new users) running Dapper. 

The average user has no ppc or amd64. So this sources.list isn't intended for those architectures. This sources.list isn't intended for servers. 

If you are still using breezy then you should **upgrade to Dapper first before using this sources.list**. You should take a look here prior to upgrading :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

After you have done this guide you can take a look here :

**Ubuntu Customization Guide - Quick Start** :
[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

That being said here it is :

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
## only uncomment it if you need it
## deb http://archive.canonical.com/ubuntu dapper-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

```

**First start the terminal (Applications -> Accesoires -> Terminal).**

To use this sources.list replace your sources.list with this one using your favorite editor. Do the following command in the terminal :
```
gksudo gedit /etc/apt/sources.list
```

Then do this command to take the new sources.list into effect do the following command :
```
sudo aptitude update && sudo aptitude upgrade
```

It can't hurt to include the src repos in case you might need them later. If you are on a slow internet connection I would advise to remove them.

In the end users can and should make their own informed decision about what they put in their sources.list. 

**Some information :**

**Ubuntu Customization Guide - Quick Start** :
[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

Ubuntu Customization Guide
[http://www.ubuntuforums.org/forumdisplay.php?f=159](http://www.ubuntuforums.org/forumdisplay.php?f=159)

You can also generate a sources.list here :
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Information about backports :
[http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)
[http://backports.ubuntuforums.org/wiki/index.php/Main_Page](http://backports.ubuntuforums.org/wiki/index.php/Main_Page)
[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

information about how to install software in Ubuntu :
[I]
Add/Remove - the basic method[/I]
[I]
The easiest way of installing a package is to use the 'Add/Remove' tool. Click Applications --> Add/Remove... to start it. First, find the package or packages you want to install. You can search for a keyword, such as 'email', or look through the categories shown on the left hand side of the window. Once you've found a package you want to install, tick the box next to its icon. You can do this for as many packages as you like.

Once you've finished choosing, click the Apply button at the bottom of the window. Another window will pop up, showing all of the packages you've selected and asking if you'd like to apply the changes. To install the packages, click Apply. You'll then be asked to type in your super-user/administrator password. Once you've entered it, another window will appear informing you of the installation progress. Once this has finished, click Close. Your new programs are installed, ready to use![/I]

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[http://www.beginningubuntu.com/software_1.html](http://www.beginningubuntu.com/software_1.html)


Information about commandline packagemanagement :
[https://wiki.ubuntu.com/CommandLinePackageManagement](https://wiki.ubuntu.com/CommandLinePackageManagement)

HOWTO fix problems regarding broken dependencies :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

**discuss my recommended Dapper sources.list :**
[http://www.ubuntuforums.org/showthread.php?p=1076241](http://www.ubuntuforums.org/showthread.php?p=1076241)

---

