---
title: "w32codecs"
date: 2005-08-02
forum: Repositories &amp; Backports
---

### Post by dhjohnson on 2005-08-02
Hello

I used all of the terminal commands in the "How to install Multimedia
Codecs" section of the Ubuntu Guide site, but wasn't able to install
the w32codecs.  Does anyone have an update for this?  There's a file on my
desktop that's taunting me for not being able to play it.  ;)

I'm running x86.  I also loaded the extra repositories.  At the terminal, I get

david@ubuntu:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
david@ubuntu:~$

As one might guess, I am also unable to find it in Synaptic.

---

### Post by Juergen on 2005-08-02
>  I also loaded the extra repositoriesHow?
After you edit the config-file you have to do a 'sudo apt-get update' to load the package-lists. Did you do that?

You should also update regularly to get the current package-lists for the security-updates...

If you did the update, try to search in synaptic for the package.
How many packages are shown if you click on 'Status' and then mark 'All'?

---

### Post by kosmic on 2005-08-02
[QUOTE=dhjohnson]Hello

I used all of the terminal commands in the "How to install Multimedia
Codecs" section of the Ubuntu Guide site, but wasn't able to install
the w32codecs.  Does anyone have an update for this?  There's a file on my
desktop that's taunting me for not being able to play it.  ;)

I'm running x86.  I also loaded the extra repositories.  At the terminal, I get

david@ubuntu:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
david@ubuntu:~$

As one might guess, I am also unable to find it in Synaptic.[/QUOTE]

Add the Backports repository to your etc/apt/sources to get w32codecs :)

didn't see that this post was already answered, sorry, thake the steps above to install w32codecs

---

### Post by dhjohnson on 2005-08-02
[QUOTE=Juergen]How?
After you edit the config-file you have to do a 'sudo apt-get update' to load the package-lists. Did you do that?

You should also update regularly to get the current package-lists for the security-updates...

If you did the update, try to search in synaptic for the package.
How many packages are shown if you click on 'Status' and then mark 'All'?[/QUOTE]

I loaded the repositories using Synaptic, and then reloaded the packages list.  Do I have to manually edit whatever the file is to get *ALL* of the repositories?  I'm not in front of my machine right now, so I am unable to tell you how many packages are available.  But I do update often, especially when I get a security update email.

Also, to Juergen, I used to live in Bad Kreuznach when I was a kid.

Thanks for the help.

---

### Post by ghostintheshell on 2005-08-02
Here's my /etc/apt/sources.list file:

 ```

## Ubuntu officialy supported (Restricted copyright) ##

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

## Ubuntu community maintained (Universe) ##

deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Ubuntu non-free (Multiverse) ##

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Kubuntu (KDE) ##

deb http://kubuntu.org/ hoary-updates main
deb http://kubuntu.org/hoary-kde342/ hoary-updates main

#deb http://dinton.no-ip.org/ kubuntu main
#deb-src http://dinton.no-ip.org/ kubuntu main

## Backports ##

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
#depreciated - deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

## Skype ##

deb http://download.skype.com/linux/repos/debian/ stable non-free

## Marillat ##

#deb ftp://ftp.nerim.net/debian-marillat/ stable main 
#deb ftp://ftp.nerim.net/debian-marillat/ testing main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main

``` 

more infos here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by chazm on 2005-08-03
Did you do the xine-ui steps below the multimedia codecs on UbuntuGuide? That's how I got my wmv's to play. Here's my sources.list also:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates after final release
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Extra deb
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

If you need to edit it, enter: sudo gedit /etc/apt/sources.list

:)

---

