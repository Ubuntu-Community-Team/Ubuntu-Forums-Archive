---
title: "Mount and Unmount ISO Images into Ubuntu"
date: 2007-06-04
forum: Sudan Team
---

### Post by Y2J on 2007-06-04
Mount and Unmount ISO,MDF,NRG Images Using **AcetoneISO** (GUI Tool)

AcetoneISO is CD/DVD image manipulator for Linux.Using this tool it is very easy to Mount and Unmount ISO,MDF,NRG Images

**AcetoneISO Features**

    * Mount and Unmount ISO, MDF, NRG (if iso-9660 standard)

    * Convert / Extract / Browse to ISO : *.bin *.mdf *.nrg *.img *.daa *.cdi *.xbx *.b5i *.bwi *.pdi

    * Play a DVD Movie ISO with most used media players

    * Generate an ISO from a Folder or CD/DVD

    * Generate MD5 file of an image

    * Encrypt an image

    * Split image in X megabyte

    * Compress with High Ratio an image

    * Rip a PSX cd to *.bin to make it work with epsxe/psx emulators

    * Service-Menu support for Konqueror

    * Restore a lost CUE file of *.bin *.img


**Preparing Your System**

You need to install kommander ( it consists of an editor and a program executor that produce dialogs that you can execute), which is required by AcetoneISO. You also need p7zip (a file archiver with highest compression ratio) to compress and extract ISO images.

```
sudo apt-get install kommander p7zip
```

Install AcetoneISO in Ubuntu

First you need to download latest AcetoneISO .deb package from here:

```
http://kde-apps.org/content/show.php?content=44805
```

Now you should be having AcetoneISO-6.7.deb file you need to install this file using the follwoing command

```
sudo dpkg -i AcetoneISO-6.7.deb
```

This will complete the installation

Now you need to go to Application > Accessories > AcetoneISO

[IMG]http://www.ubuntugeek.com/images/iso/1.png[/IMG]

Once it opens you should see similar to the following screen

[IMG]http://www.ubuntugeek.com/images/iso/2.png[/IMG]

Good luck !

---

### Post by polaren on 2007-06-12
Works great in xubuntu 7.04

Thank you!

---

### Post by magaltavor on 2007-06-13
i think that Gmount-iso is also a good solution :

This is Gmountiso, a PyGTK GUI to mount your cd images

Gmount-iso is a small tool written using PyGTK and Glade. It allows you to easily mount your cd images. This is a frontend to the 'mount -o loop -t iso9660 foo.iso /mountpoint' command
Homepage: [http://www.crans.ens-cachan.fr/Syst%C3%A8meLinux/GmountIso](http://www.crans.ens-cachan.fr/Syst%C3%A8meLinux/GmountIso)
Version: 0.3-0ubuntu1 (gmountiso)
Gmount-iso integrates well into the Ubuntu desktop

---

### Post by Skavenger on 2007-06-14
> **Y2J said:**
> Mount and Unmount ISO,MDF,NRG Images Using **AcetoneISO** (GUI Tool)

...
i get this error when i run the program

[ATTACH]35332[/ATTACH]

i downloaded [this package]("http://http://kde-apps.org/content/download.php?content=44805&id=2")
is that ok?
> **magaltavor said:**
> i think that Gmount-iso is also a good solution :

This is Gmountiso, a PyGTK GUI to mount your cd images

Gmount-iso is a small tool written using PyGTK and Glade. It allows you to easily mount your cd images. This is a frontend to the 'mount -o loop -t iso9660 foo.iso /mountpoint' command
Homepage: [http://www.crans.ens-cachan.fr/Syst%C3%A8meLinux/GmountIso](http://www.crans.ens-cachan.fr/Syst%C3%A8meLinux/GmountIso)
Version: 0.3-0ubuntu1 (gmountiso)
Gmount-iso integrates well into the Ubuntu desktop
that page is not working


edit: nevermind, i downloaded [this package]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0-1~3v1ubuntu1_i386.deb"), its working fine now

thank you!

---

### Post by Y2J on 2007-06-14
> **Skavenger said:**
> 

edit: nevermind, i downloaded [this package]("http://http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0-1~3v1ubuntu1_i386.deb"), its working fine now

thank you!

I just want to correct your above link :

```
http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0-1~3v1ubuntu1_i386.deb
```

Thanks a lot :) !

---

### Post by zahris on 2007-06-16
i'm having problem when mounting any image files, it says the mount point is missing but and it did, but when i un mount it the folder is back.

i see there is 7 folder for mount point. then i tried to mount on all folder at same time, using different image files iso,ccd,bin,mdf,img, etc. and it just the same in all folder..

---

### Post by bulletxt on 2007-06-19
I think you have installed an old version of fuseiso. as written on kde apps, 

### Ubuntu users must not use fuseiso of rep since it's old and has bugs### 

this means you must download the new source and compile it, anyways acetoneiso2 will do it for you. as it seems you have messed up with things, the best thing to do is to uninstall fuseiso, and if running ubuntu feisty install fuseiso from trevinho rep find it here [http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0~3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0~3v1ubuntu0_i386.deb)

if you aren't running ubuntu feisty, then download sources from [http://ubiz.ru/dm/fuseiso-20061017.tar.bz2](http://ubiz.ru/dm/fuseiso-20061017.tar.bz2) and compile it.


after that in acetoneiso2 under help click on activate fuseiso, insert password and thats all.

I hope it helps you

---

### Post by Hork on 2007-06-20
Where do I download the stuff it requires?

---

### Post by bulletxt on 2007-06-21
the deb should install everything you need, if it doesn't use synaptic to manually get them. it's quite easy..

---

### Post by ABCDE on 2007-07-07
Acetone works generally good by me but I can not extract correctly an .img file: this is a programm with three files: one .img / one .ccd / one .sub (= from clone-cd?).
Only 70 p. c. of the main file (a .cab file) of the "img" can be extracted.

 All the other files (of the img)  are correctly extracted. +I can not extract the cdd and sub with Acetone.

This image disc works fine on windows with daemon tools...

I don't understand where is the problem

Thank for your help!
Abcde

---

### Post by KyyubiDX on 2007-07-13
something is not right with my acetone... no option seems to do anything and the list of isos is empty... any ideas? i'd appriciate some help...

---

### Post by yowshi on 2007-07-15
i am rather tired of noone posting 64bit solutions. i have fiesty amd64 anyway this is the problem i get when trying to run acetone2


acetoneiso2: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
 i am using this .deb AcetoneISO2_1.0-all.deb

---

### Post by catnappist on 2007-07-15
I like doing it this way, though I don't know what works with 64-bit:

Using loop Kernel Module to mount an .iso file: 
===============================================

I.	First, make the directory to load the .iso into using the following command:

sudo mkdir /media/isoimage

II.	Now add the loop module to your kernel, using the following command:

sudo modprobe loop

	To mount .iso image:

sudo mount filename.iso /media/isoimage/ -t iso9660 -o loop

	In the above command, replace path and filename.iso with your own. Noobies (like me), remember that terminal commands are case-sensitive!

	Now your .iso file should be mounted and accessible from your file manager, and listed with your other drives.

III.	To unmount .iso Image:

sudo umount /media/isoimage

Rebooting unmounts your file, requiring (if wanted) the reloading of the loop module (see II.) and remounting your file.

Helpful tip:

By opening VLC media player, then FILE -> Open disk -> Disk tab, and changing Device name to /media/isoimage, you can play video image files (movies) made by programs like k9copy and DVD-Decryptor. It reverts to the default DVD player when you close VLC.

Courtesy of (with edits and my undying gratitude):

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
:)

---

### Post by yowshi on 2007-07-15
i already know this command i would like something like daemon tools though (for windows ) that would do this for me because for example your cd specific command wouldnt work well for say a game on a dvd would it?

---

### Post by catnappist on 2007-07-15
I agree.  If there was a daemon tools for linux, I sure wouldn't be messing around with terminal commands or downloading stuff that only works for the experts.  Sorry.:(

---

### Post by yowshi on 2007-07-15
exactly and what about if the file isnt an iso what if it is a bin a cue or an img or any of the other numerous types of cd and dvd images

---

### Post by bulletxt on 2007-07-18
I think 64 bit users, when installing a pure 64 bit OS should know what they are doing. they come here saying acetoneiso2 doesn't work on 64 bit not knowing anything. AcetoneISO2 DOES run of course on 64bit OS.

as it is CLEARLY written on the download page (you guys should READ damn):


4 - 64-bit users

Install a package then:
-install libqt4-dev
-download AcetoneISO2-generic-src.tar.gz (Source download), uncompress,
enter src dir and compile:
qmake-qt4
make
Then replace /usr/bin/acetoneiso2 with the new acetoneiso2 file in src directory.

NOTE: if you get an error when doing qmake-qt4, simply type qmake.

---

### Post by yowshi on 2007-07-18
now whats with the asumtpion that just because my processor is 64 bit i know more then the average computer user? i mean it isnt like i have a choice which ubuntu architecture i get to use. believe me the first time i tried to install non 64 bit ubuntu it wouldnt even start installing

---

### Post by bulletxt on 2007-07-19
sorry I didn't mean to offend you or anyone else :)

I just wanted to say (i did it in a bad way i know) that when installing a pure 64bit OS there are a lot of things to know.
AcetoneISO2 is distributed as a 32 bit, its code is written in bash so it doesn't need compile. The problem in your case is that the GUI is written in QT4 and compiled on a 32 bit OS, so to get it to work on a 64 bit OS you just  have to compile the gui as written in previous post ;)

hope it works now :)


ps: The very good thing of the new AcetoneISO, is that it uses fuseiso to mount, so it is capable to mount ISO BIN NRG MDF IMG files! and the very cool thing is that they managed everything to mount images automatically without asking password inside their folder, and the QT4 display shows the name of the images mounted :)  it also does other interesting things :)

---

### Post by yowshi on 2007-07-19
actually fiesty was a pretty straight forward install on my system didnt need to know more then i did when i installed ubuntu on a non 64 bit system

---

### Post by cpangratzbg on 2007-07-24
Really nice app 


THANKS

---

