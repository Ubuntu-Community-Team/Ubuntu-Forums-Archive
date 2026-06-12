---
title: "muekow chroot error on client build"
date: 2009-09-10
forum: Server Platforms
---

### Post by inyoka on 2009-09-10
I have searched the forums and the web and have not found an answer to this which is both understandable and relevant.  I've installed a muekow LTSP server on 64bit Ubuntu 9.04, now I am trying to build a 32bit client from a CD Mirror.  Both the command I use and the error I receive are listed below. 

```
simon@muekow:~$ sudo ltsp-build-client --arch i386 --mirror file:///cdrom
NOTE: adding default dist and components to security mirror:
http://security.ubuntu.com//ubuntu jaunty main restricted universe multiverse
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on file:///cdrom...
I: Retrieving libatm1
I: Validating libatm1
W: Failure trying to run: chroot /opt/ltsp/i386 mount -t proc proc /proc
error: LTSP client installation ended abnormally
simon@muekow:~$ 
```
It is probably worth noting that if I install without the CD-ROM mirror setting I get the same error. :confused:  There is no /bin directory in "/opt/ltsp/i386", and from my understanding chroot needs this, but if so why might it not be created?

Any help would be gratefully received.

---

### Post by inyoka on 2009-09-11
I decided to build my own chroot environment using debootstrap.  I customized the instructions [here.]("https://help.ubuntu.com/community/BasicChroot") Changed everything in schroot.conf to use jaunty :
```
[jaunty]
description=Ubuntu Jaunty Client
location=/opt/ltsp/i386
priority=3
groups=sbuild, users
root-groups=root

```

 and this is what happened : 
```
simon@muekow:/$ sudo debootstrap --variant=buildd --arch i386 jaunty /opt/ltsp/i386 file:///cdrom
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on file:///cdrom...
I: Retrieving build-essential
I: Validating build-essential
I: Retrieving dpkg-dev
I: Validating dpkg-dev
I: Retrieving g++-4.3
I: Validating g++-4.3
I: Retrieving libstdc++6-4.3-dev
I: Validating libstdc++6-4.3-dev
I: Retrieving g++
I: Validating g++
I: Retrieving patch
I: Validating patch
W: Failure trying to run: chroot /opt/ltsp/i386 mount -t proc proc /proc
simon@muekow:/$
```
As you can see I get to the same error.  It also only created the following directories in /opt/ltsp/i386 : "debootstrap" "dev" "etc" "var" so still no "bin" directory.

Any help gratefully received.:confused:

---

### Post by inyoka on 2009-09-13
Okay so I tried a couple of things which may or may not help.  I completely reinstalled the terminal server and found something that may be relevant.

During a routine install of muekow on a 64bit server, I can only get the installation to build clients correctly if I do NOT setup the network settings during the installation.  If I enter an IP address and subnet mask etc.  then after trying to build the 64bit client it gives an error saying client build failed (or something similar, I got the error last thing on Friday).

If I do not setup the network it builds correctly.  This lead me to believe I might be able to use ltsp-build-client if I did not setup the network before hand.  However this was not the case and the installation continues to fail with the error listed above.

:guitar: < Jono Bacon

Okay if there are people reading this and they are unable to fix my problem there is something that would help me solve this problem by helping to experiment more.  

Question : How can I use ltsp-build-client with the /var/cache/apt/archives from a previous install?  I am using a cdrom mirror command ATM but would like to build from a local repo of packages.  It would be nice to get some input on this thread from someone other than me :)

---

### Post by inyoka on 2009-09-13
I answered my own question. 

Use the "Administrator > USB Startup Disk Creator" option (on a 32bit machine for 32bit clients etc) create a bootable usb drive.  Then copy the dists folder from the USB onto your hard.  For example I put mine in my home in a directory called archives "/home/simon/archives"

Then I used the following command :
```
sudo ltsp-build-client --arch i386 --mirror file:/home/simon/archives
```
This now enables me to use ltsp-build-client without needin a cd-rom or an internet connection.

---

### Post by cariboo on 2009-09-13
Couldn't you just have created the missing bin directory?

---

### Post by inyoka on 2009-09-14
Perhaps, I have tried copying a bin directory from another 32 bit computer, however its not just the bin directory that's missing.  There are 20 directories in the amd64 folder.  

From what I can tell the ltsp-build-client isn't building a standard ubuntu install, but a stripped down client with the ltsp client software installed.  You cannot run ltsp-build-client with an existing /opt/ltsp/i386 directory, so the command requires you to start from scratch.  

This would require me to run the command, and copy all the omitted directories across in the 2 seconds the command takes to produce the error.

Alternatively I could find a second computer, reinstall muekow in a 32bit envorinment and then copy the directory over, then go through the settings on the 64bit server to ensure it knows there is a 32bit client.  However I would prefer to just be able to run ltsp-build-client.  Somebody somewhere must have run the command at some point and had it work, right???

---

### Post by inyoka on 2009-09-14
My internet connection is pretty poor but I'm in the process of downloading Virtual box.  If I can install Muekow on that I'll copy the complete 32bit client environment over and see if I can jury rig it to work.  

I have to download the 32bit alternate jaunty first though and that may take me a day or so (the pleasures of living in Indonesia) anyway if anyone thinks of a fix in the meantime I'd rather avoid the downloading.  Otherwise I'll post again in a couple of days when I have something to report.

---

### Post by windependence on 2009-09-14
This project (muekow) doesn't look like it has been updated in over 2 years. I may be wrong, but what exactly are you trying to accomplish?

-Tim

---

### Post by inyoka on 2009-09-14
I am migrating an ageing Fedora 4 LTSP installation to Ubuntu. There tends to not be very many updates to LTSP, and Ubuntu's appears to be as new as anyone else's.  I just need a new OS so I can get security updates and reasonably recent plug-ins.

Ubuntu are still linking to it in their marketing, I would hope they wouldn't push it if it's a dead duck.  My clients are all PXE booting with no hard-disks, and no budget, so LTSP is the only option.  I really just want to get up to speed before deploying (or dist-upgrading to) 10.04.

---

### Post by inyoka on 2009-09-17
I have some problems with VirtualBox not capturing mouse input, or even some keyboard commands correctly.  The upshot being I cannot install LTSP 32bit server in VirtualBox.

I might format the server to 32bit, copy the i386 directory then re-install.  However I only have tomorrow before a week long holiday with no access to my office.  If that doesn't work then I think I will give up, at least until 10.04 when hopefully the bug will be fixed.

---

### Post by inyoka on 2009-09-28
Okay I'm back from my holiday, on Wednesday I'll try the 32 bit server install, and copying the chroot environment.  It seems a bit long winded but I guess its only a problem for people with 64bit servers.

It does seem as though muekow is a bit of a dead project though, which is a shame because its something of a poster child for Linux in general.

---

### Post by inyoka on 2009-10-02
Despite numerous power-cuts on an old laptop with neither a battery or a UPS, I have managed to install the 32 bit LTSP server.  Unfortunately, I cannot copy or archive the new /opt/ltsp/i386 folder due to the numerous symbolic links.

> sudo cp -Rd /opt/ltsp/i386/ /media/8GB-USB

and get this error a lot for different files:

> cp: cannot create symbolic link `/media/8GB-USB/i386/lib/terminfo/r/rxvt-m': Operation not permitted

Any help greatly appreciated.

---

### Post by Chuck181991 on 2009-10-11
I'm getting the same problem compiling on a 32-bit Ubuntu 9.04 server. 
----------------------------------------------------------------------------------------------
root@proximity:/media# ltsp-build-client --mirror file:///media/cdrom
NOTE: adding default dist and components to security mirror:
[http://security.ubuntu.com//ubuntu](http://security.ubuntu.com//ubuntu) jaunty main restricted universe multiverse
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on file:///media/cdrom...
I: Retrieving libatm1
I: Validating libatm1
W: Failure trying to run: chroot /opt/ltsp/i386 mount -t proc proc /proc
error: LTSP client installation ended abnormally
-----------------------------------------------------------------------------------------------

How ever, if you run the install without the --mirror option, it installs, just takes forever. Is the project 2 years old? That's too bad, it was a very good idea. I have had some luck with using EdUbuntu to install LTSP, that was back in Ubuntu 8.04 though. The other I have noticed is that if you install on a computer with a Desktop Enviroment, it uses the host computer's files and folders for everything, not so much /opt/ltsp/amd64(i386). I am not having much luck getting a Desktop working on the server, in practice. I did get it working in VirtualBox, I'll look and see what I did differently. To get the mouse and keyboard to work, I switched the Operating System. It seems to be random.

Heres what I'm working with today:
   Desktop:
     My personal desktop, much faster than the small server I have.
     AMD Phenom x4 9950 at 2.8 ghz
     4g DDR2 1066 RAM
     ASUS M3A32-MVP Deluxe
    Kubuntu 64-bit, 9.04
  Vanguard:
     An oldish laptop, still runs most Operating Systems well, but can't play games or anything.
     Acer Ferrari 4000
       AMD Turion 64, 2.2ghz
       1g RAM
    Kubuntu 9.04, 64 bit
  Poximity:
    My energy efficient server, slow as molasas but uses less power than my lightbulb.
      1.2 Ghz VIA Eden CPU
      1g DDR 400
      [http://www.newegg.com/Product/Product.aspx?Item=N82E16856107046](http://www.newegg.com/Product/Product.aspx?Item=N82E16856107046)
    Ubuntu server 9.04, 32 bit

-----------------------------------------------------------------------------------------------
You can't copy the /bin folder over, ltsp-build-client will give you an error telling you to delete the folder. And for making symbolic links, wouldn't it be wiser to use ln?
I'm very interested in getting this to work. If you find out the poblem, please let me know.

---

### Post by inyoka on 2009-10-12
That's strange, I can make a 32bit client on a 32bit server without any errors.  I wonder what is causing it.

I could use ln if I wanted to manually recreate every link that is not copied.  However I imagine there are a great many, and I would need to search for them first, not down their locations and targets and then recreate each individually.

I'll try again when 9.10 is released, don't really fancy cleaning up an Edubuntu install for an office.

I'm using a duel processor 64bit Dell sc1430, with hardware RAID.  Quite a different setup.  Also I get the error with or without the --mirror option.  

Did you setup your network settings during install, or afterwards?  The server seems to be setting up the environment during install fine, so I think something the install does after setting up the client causes the problem but I need more information.

---

### Post by inyoka on 2009-10-12
Okay it seems highly likely that the server is either trying to run a 32bit application from the chroot in the 64bit server environment, or vice versa.  This has to be related to the fact that we have two systems from two different architectures.

I am assuming that in order to simplify things ubuntu/canonical have tried to simplify configuration by sharing some processes between the server and client.  This would of course cause no problems at all, unless you have different server and client chip types.  I imagine they tested with the same architecture, didn't get an error and thought all was good.

Anyway I am going to try and log this with launchpad.

--Update or lack there of--

Hmm, considering Karmic will be out in 16 days perhaps it would be more productive of me to wait.  Don't imagine the developers have much time at the moment.  And I don't want to report something and find its not a problem in 9.10.  Couldn't find anything relevant in Launchpad, but I must admit I found it a bit confusing in there :) and I'm very busy doing other work atm.  If anyone finds something relevant on launchpad please let me know.

---

