---
title: "Cinepaint Install in Edgy"
date: 2006-10-30
forum: Repositories &amp; Backports
---

### Post by Osvaldo on 2006-10-30
Hi.

I can't install Cinepaint on Edgy. (x86) (original repositories + Universe + Multiverse + Automatix)

The message:

cinepaint:
 Depends: libgutenprintui1-1 (>=5.0.0~rc2) but it is not installable

Thanks for your help.

Best regards

Osvaldo

---

### Post by ChrisNiemy on 2006-11-01
same problem here :(

---

### Post by Bender the Robot on 2006-11-01
I got the same message and the  way I managed to do the install was by using 'synaptic' to remove all the installed 'libgutenprintui' files and install 'libgutenprintui 1-1', which I got from here - [http://packages.debian.org/testing/libs/libgutenprintui1-1](http://packages.debian.org/testing/libs/libgutenprintui1-1)

I don't know, whether, or not, it will work for you but good-luck.:-k

---

### Post by fsnk on 2006-11-18
I am using 64-bit Edgy and am getting:
```

The following packages have unmet dependencies:
  cinepaint: Depends: libopenexr2c2 (>= 1.2.2) but it is not installable
             Depends: cinepaint-data (= 0.19-1-1build1) but 0.20-1-2 is to be installed

```

---

### Post by secretlondon on 2006-11-18
We know about this and it is here:

[https://launchpad.net/distros/ubuntu/+source/cinepaint/+bug/65457](https://launchpad.net/distros/ubuntu/+source/cinepaint/+bug/65457)

A fix has been submitted and is awaiting release.

In future - submitting bugs on the bug tracker will ensure that someone looks at them - nobody looks in the forums.

---

### Post by ariel on 2006-11-19
> **Bender the Robot said:**
> I got the same message and the  way I managed to do the install was by using 'synaptic' to remove all the installed 'libgutenprintui' files and install 'libgutenprintui 1-1', which I got from here - [http://packages.debian.org/testing/libs/libgutenprintui1-1](http://packages.debian.org/testing/libs/libgutenprintui1-1)

I don't know, whether, or not, it will work for you but good-luck.:-k


Thanks! your solution worked great for me

---

### Post by inexistentia on 2006-11-19
> **ariel said:**
> Thanks! your solution worked great for me

When I opt to remove this in synaptic it tells me it's going to remove ubuntu-desktop as well.  Did you have any issues with this?

---

### Post by Sanguineus on 2006-11-29
> **Bender the Robot said:**
> I got the same message and the  way I managed to do the install was by using 'synaptic' to remove all the installed 'libgutenprintui' files and install 'libgutenprintui 1-1', which I got from here - [http://packages.debian.org/testing/libs/libgutenprintui1-1](http://packages.debian.org/testing/libs/libgutenprintui1-1)

I don't know, whether, or not, it will work for you but good-luck.:-k

Actually, I could install libgutenprintui1-1 without removing any of those other version libraries and it worked fine. Cinepaint installs without errors. :)

---

### Post by Osvaldo on 2006-11-29
Yes, you can install it and then Cinepaint.

Thanks for the help.

Best regards,

Osvaldo

---

### Post by larsemil on 2006-12-27
> **inexistentia said:**
> When I opt to remove this in synaptic it tells me it's going to remove ubuntu-desktop as well.  Did you have any issues with this?

ubuntu-desktop is a metapackage. removing it will not delete anything from your system. installing it will install a bunch of packages to have a desktopenvironment. 

good luck!

---

### Post by bartbr on 2006-12-27
> **Bender the Robot said:**
> I got the same message and the  way I managed to do the install was by using 'synaptic' to remove all the installed 'libgutenprintui' files and install 'libgutenprintui 1-1', which I got from here - [http://packages.debian.org/testing/libs/libgutenprintui1-1](http://packages.debian.org/testing/libs/libgutenprintui1-1)

I don't know, whether, or not, it will work for you but good-luck.:-k

Another temporary solution (more ubuntu ;) ) is add into source.list :
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

And only:
sudo apt-get update
sudo apt-get install cinepaint  ( now without conflicts :D )

regards
ps: without remove any package.

---

