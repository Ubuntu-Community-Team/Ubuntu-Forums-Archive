---
title: "Virtual Box won't install"
date: 2015-06-25
forum: Virtualisation
---

### Post by bucket81 on 2015-06-25
So I'm new to the Linux command line and Linux in general, a buddy of mine got a sweet deal on some old servers so I thought I would play. We are building the same systems and he found this [http://www.unixmen.com/install-oracle-virtualbox-and-manage-it-using-phpvirtualbox-on-ubuntu-15-04-headless-server/](http://www.unixmen.com/install-oracle-virtualbox-and-manage-it-using-phpvirtualbox-on-ubuntu-15-04-headless-server/) 

Looks simple enough, but I can't get past installing the build-essentials 

```
 chris@ubuntuchris:~$ sudo apt-get install build-essential dkms unzip[sudo] password for chris:Reading package lists... DoneBuilding dependency treeReading state information... DoneE: Unable to locate package dkmschris@ubuntuchris:~$ 
```

I also tried aptitude 

```
chris@ubuntuchris:~$ sudo aptitude install build-essential dkms unzip
Couldn't find any package whose name or description matched "dkms"
Couldn't find any package whose name or description matched "dkms"
The following NEW packages will be installed:
  binutils{a} build-essential cpp{a} cpp-4.9{a} dpkg-dev{a} fakeroot{a} g++{a} g++-4.9{a}
  gcc{a} gcc-4.9{a} libalgorithm-diff-perl{a} libalgorithm-diff-xs-perl{a}
  libalgorithm-merge-perl{a} libasan1{a} libatomic1{a} libc-dev-bin{a} libc6-dev{a}
  libcilkrts5{a} libcloog-isl4{a} libdpkg-perl{a} libfakeroot{a} libfile-fcntllock-perl{a}
  libgcc-4.9-dev{a} libgomp1{a} libisl13{a} libitm1{a} liblsan0{a} libmpc3{a}
  libquadmath0{a} libstdc++-4.9-dev{a} libtsan0{a} libubsan0{a} linux-libc-dev{a} make{a}
  manpages-dev{a} unzip
0 packages upgraded, 36 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/41.4 MB of archives. After unpacking 130 MB will be used.
Do you want to continue? [Y/n/?] y
Media change: Please insert the disc labeled 'Ubuntu-Server 15.04 _Vivid Vervet_ - Release amd64 (20150422)' into the drive '/media/cdrom/' and press [Enter].
```

This ends up asking for the disc, and when inserted just keeps asking for it when enter is pressed. My buddy actually installed this with aptitude. And he's up and running making fun of me...:mad:

I've tried searching but couldn't find much.

---

### Post by v3.xx on 2015-06-25
Think you hit on the problem.  Go to your software sources and make sure that cd/dvd rom is unchecked.

---

### Post by Bucky Ball on 2015-06-25
Erm, why don't you install it from the Software Centre or a terminal from the official Canonical/Ubuntu repositories? Always check there first. :)

There is no need to install it from a third-party.

```
sudo apt-get install virtualbox
```

... should be about all you need. Best to remove and repair anything you've installed or tweaked first.

---

### Post by bucket81 on 2015-06-25
Guess I should have put my version of Ubuntu server 15.04, how can I access my software sources?

---

### Post by Carpentr on 2015-06-25
As mentioned above, run the following command to see if you already have the repository to install VirtualBox:
```

sudo apt-get update
sudo apt-get install virtualbox

```

Sources can be located at:  
```

/etc/apt/sources.list

```
Edit with a text editor (Vi or Emacs for example)

---

### Post by bucket81 on 2015-06-25
My source.list file is empty.... I have deleted it and replaced it with a copy, but still comes up empty.

---

### Post by howefield on 2015-06-25
> **bucket81 said:**
> My source.list file is empty.... I have deleted it and replaced it with a copy, but still comes up empty.

It will be, try sources.list, not source.list

---

### Post by v3.xx on 2015-06-25
> **Bucky Ball said:**
> There is no need to install it from a third-party.
That would be first-party :P

---

### Post by Bucky Ball on 2015-06-25
> In computer programming, a third-party software component is a reusable software component developed to be either freely distributed or sold by an _entity other than the original vendor of the development platform._

... from Wikipedia, or ...

> Third party applications are programs written to work within operating systems, but _are written by individuals or companies other than the provider of the operating system_. 

From [here]("http://www.wisegeek.org/what-are-third-party-applications.htm"). Open Software and Updates> Other Software and look under 'Independent'.

Thanks.

Back to Virtualbox ...

---

### Post by bucket81 on 2015-06-26
So..... I tried to reinstall, kept getting a disk error. So I checked the disk what do you know its bad..... So made a new disk, reinstall and everything seems to be working.

---

### Post by Bucky Ball on 2015-06-26
Excellent. Please see the second link in my signature and enjoy! ;)

---

