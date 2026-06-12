---
title: "HOWTO: Install fldigi with hamlib and FLTK"
date: 2007-03-09
forum: Tutorials
---

### Post by dberg on 2007-03-09
This tutorial will show you how to install fldigi, a program for controlling amateur radio transceivers.

These instructions have been compiled from instructions given at:
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")
[http://www.w1hkj.com/FldigiHelp-1.3/Installing.html]("http://www.w1hkj.com/FldigiHelp-1.3/Installing.html")

The download location given is not guaranteed to be the newest version of each piece of software but they should work together. Search if you want to make sure you have the most up to date version!

First we will install hamlib:

Download the archive [here.]("http://www.n9drb.com/linux/hamlib-1.2.6.1.tar.gz")

Now in the terminal:
```
sudo aptitude update
```
If you do not have build essential installed then use this:
```
sudo aptitude install build-essential
```
Now navigate to the location of the downloaded archive, then
```
tar -xvzf hamlib-1.2.6.1.tar.gz
cd hamlib-1.2.6.1
./configure
make
sudo make install
```
I prefer to use checkinstall which you can get with:
```
sudo aptitude install checkinstall
```
Then replace
```
sudo make install
```
with
```
sudo checkinstall -D
```

Next we will install FLTK:
Download FLTK [here.]("http://www.n9drb.com/linux/fltk-1.1.7-source.tar.gz")
Now navigate to the location of the downloaded archive.
Now in the terminal:
```
tar -xvzf fltk-1.1.7-source.tar.gz
cd fltk-1.1.7-source
./configure --enable-threads --enable-xft --enable-localjpeg --enable-localpng --enable-localzlib
make
```
then
```
sudo make install
```
or
```
sudo checkinstall -D
```

Now for fldigi, download [here.]("http://www.n9drb.com/linux/fldigi-1.32.src.tar.gz")
Navigate to the location of the archive.
In the terminal:
```
tar -xvzf fldigi-1.32.src.tar.gz
cd fldigi-1.32.src
make CFG=Release

```
Now we need to move the binary file to the bin. Be sure to replace "extractionlocation" with the location that you downloaded the archive to.
```
sudo mv extractionlocation/fldigi-1.32.src/Release/fldigi /bin
```
Now you should be able to run the program by:
```
fldigi
```

Errors I had and how to fix them:
While trying to install FTLK the first time I got this error
```
checking for X... no
configure: error: Configure could not find required X11 libraries
./configure: line 8268: exit: aborting.: numeric argument required
./configure: line 8268: exit: aborting.: numeric argument required
```
To fix this I had to install xorg-dev by searching in synaptic and installing it.

I received this error when trying to run fldigi the first time
```
fldigi: error while loading shared libraries: libhamlib.so.2: cannot open shared object file: No such file or directory
```
This is what fixed it
```
sudo apt-get install --reinstall libhamlib2
```

To configure fldigi the first time you run it try the instructions given [here.]("http://www.w1hkj.com/FldigiHelp-1.3/Configuring.html")

If you have problems or find errors in this tutorial, post them here and I or someone else can try to help.

Good luck!

---

### Post by jomiz80 on 2007-03-20
AWESOME!  Thanks for the how-to.

I'm installing [Monica]("http://www.pcbypaul.com/software/monica.html") to try and get a descent gamma correction on my LCD monitor.  The Monica software has support for FTLK, and I couldn't get the package to 'compile?'. (I'm pretty new a linux.) Anyways, it turns out that I just needed to install the xorg-dev package, like you suggested.

---

### Post by pa3dsc on 2007-04-27
Thanks Perfect howto
Including the error I also encountered.
Regards Martin

---

### Post by stevehaines on 2007-06-27
Failed at "sudo checkinstall -D". Here is the error message:

Selecting previously deselected package hamlib.
(Reading database ... 119140 files and directories currently installed.)
Unpacking hamlib (from .../hamlib_1.2.6.1-1_i386.deb) ...
dpkg: error processing /home/steve/hamapps/hamlib-1.2.6.1/hamlib_1.2.6.1-1_i386.
deb (--install):
 trying to overwrite `/usr/bin/nm', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/steve/hamapps/hamlib-1.2.6.1/hamlib_1.2.6.1-1_i386.deb

Any hope for me now?? 73 de Steve ZP9EH

---

### Post by jimwatson on 2009-01-31
> **dberg said:**
> 
I received this error when trying to run fldigi the first time
```
fldigi: error while loading shared libraries: libhamlib.so.2: cannot open shared object file: No such file or directory
```
This is what fixed it
```
sudo apt-get install --reinstall libhamlib2
```



Typing 'sudo ldconfig' after installing the hamlib libraries should get rid of the above error.  ldconfig creates the links and cache to the system's shared libraries.

Thanks for the pointers.  I got fldigi up and running on 8.10 last night.  I compiled fldigi and hamlib from source (to get the latest versions) and used the ubuntu version of fltk.

---

### Post by vladislavua on 2009-03-12
when installing Fltk I get this error after the first piece of code:

vladislav@vladislav-desktop:~$ cd fltk-1.1.7-source
bash: cd: fltk-1.1.7-source: No such file or directory
vladislav@vladislav-desktop:~$ ./configure --enable-threads --enable-xft --enable-localjpeg --enable-localpng --enable-localzlib
bash: ./configure: No such file or directory

Are there any files you need to install FLTK? Sorry I am new to this.

---

### Post by Taffman on 2011-05-23
When trying to install Hamlib, and get to the stage where I enter the 'make' command in terminal I get the following error:

make: *** No targets specified and no makefile found. Stop.

I'm a Linux newbie so would appreciate help from anyone who can spot what I'm doing wrong?

---

### Post by kd5mkv on 2011-10-22
Download the binary from fldigi site .bin and ./fligi-3.21.16.bin and bang your finished. steve kd5mkv

---

### Post by kd5mkv on 2011-10-22
Download the binary from fldigi site .bin and ./fligi-3.21.16.bin and bang your finished. steve kd5mkv

---

