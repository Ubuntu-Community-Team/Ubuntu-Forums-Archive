---
title: "HOW-TO: Fix F-Spot time adjustment via patch"
date: 2009-09-12
forum: Ubuntu Studio
---

### Post by seanlano on 2009-09-12
**Update:**A new tutorial _[can be found here]("http://ubuntuforums.org/showthread.php?p=8959657")_ for users with 10.04 Lucid Lynx LTS. This tutorial will not work with Lucid, since it uses F-Spot 0.6.1.5.

This is a tutorial, based on information gathered [here]("http://f-spot.org/How_To_Build_from_HEAD"), [here]("http://f-spot.org/How_To_Test_a_Patch") and [here]("http://www.sucka.net/2009/08/installing-adobe-cs4-in-wine/"). I chose to modify the original instruction at the first link so that we build and install the stable version, rather than the latest unstable version. Please read through the whole tutorial before you begin, so that you know what you are getting yourself in for. If you don't feel comfortable with this then don't take the chance, you might ruin something if you do it wrong. 

Also, I'm not that great with Ubuntu and all this building from source stuff, but this is what I did to fix the problem described on the F-Spot bugzilla. 

**Backup F-Spot db**
Just in case something screws up...
```
cp ~/.gnome2/f-spot/photos.db ~/.gnome2/f-spot/photos.db.Stable

```

**Remove existing F-spot**
We will be installing a different version of F-Spot, so we need to remove the old version first. 
```
sudo apt-get remove f-spot
```

**Install Prerequisite packages**
We need to make sure all dependencies are satisfied, so that we can compile and install the fixed f-spot. You will need to add **[this PPA repository]("https://launchpad.net/~mono-testing/+archive/ppa")** to your *Software Sources.* Visit the link and follow the instruction there.
**Update:** If you are using Ubuntu 9.10 Karmic Koala you do not need to add this repository, the main archives have the latest versions. 
Then:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mono-mcs libmono-cairo2.0-cil automake automake1.9 libtool
sudo apt-get build-dep f-spot

```
NOTE: You will need to have "Source Code" selected in *System->Administration->Software Sources*

**Create Directory for source code**
```
mkdir -p ~/source
cd ~/source
```
**Download Source code**
This will download the f-spot source code from whatever repository you have specified in your *Software Sources*. This will normally just be the main Ubuntu repo. 
```
apt-get source f-spot
```
NOTE: Do **NOT** specify "sudo" in front of this command, or the files will go to the wrong place.

**Get the patch**
```
cd f-spot*
wget http://bugzilla-attachments.gnome.org/attachment.cgi?id=107860 -O f-spot_no-utc-time_340903.patch
patch -p0 < f-spot_no-utc-time_340903.patch
```

**Compile, build, install**
```
./configure
make
sudo make install

```

Hopefully this has worked for you. It took me a while to get it right, the "./configure" and "make" commands kept failing because I didn't have the right prerequisites. If this happens for you, try using Synaptic Package Manager to locate and install the package that is called for. This my be a bit tricky, for example the first time I ran "make" it said that "/usr/lib/mono/1.0/mcs.exe was not found". I had to install the "mono-mcs" package to get this to work. You should try a similar approach if you encounter "file not found" errors during the compile and make stages.

Make sure you keep the ~/source directory, if you need to uninstall later, then run:
```
cd ~/source/f-spot*
sudo make uninstall
```

---

### Post by swdinesh on 2009-10-01
Hi "Sean", 

thank you for your tutorial.
I have a problem with my system. I run a ubuntu 8.10 64bit
I added the Mono-repository (with the key too). 
I installed all the packages except libmono-cairo2.0-cil
When i try to install it i receive the message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-i18n2.0-cil
  libmono-sqlite2.0-cil libmono1.0-cil
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

If i try to install it from synaptic i have it installed at 1.9.1 version and if i mark it as upgrade i receive this error message in the window that says i canno t upgrade:

libmono-cairo2.0-cil:
  Depends: libcairo2 (>=1.8.0-2) but 1.8.0-0ubuntu1.1 is to be installed


Do you have some suggestion about that?

Thank you 
Alex

---

### Post by seanlano on 2009-10-01
I did this successfully on a 9.04 32-bit system, and I think the problem is that 8.10 has an older version of libcairo2. I think it could be possible to fix this by installing the Jaunty version of the libcairo2 package, from here: [http://packages.ubuntu.com/jaunty/libcairo2]("http://packages.ubuntu.com/jaunty/libcairo2"). You might also need to install some of the listed dependencies on that page, such as [libdirectfb-1.0-0]("http://packages.ubuntu.com/jaunty/libdirectfb-1.0-0"). 

So, download the Jaunty version of libcairo2, and try to install it directly by double-clicking on the saved package. If it says that libdirectfb-1.0.0 or anything else is missing or the wrong version, then try to get those packages as well from the Jaunty package site. 


Finally, there is a chance that something could go wrong. Maybe the new versions of these packages will break older versions of other packages (but it's not likely). Just so you know, there is a small chance you might break your install, so do this at your own risk. You'll probably be fine though. :)

Good luck.

---

### Post by swdinesh on 2009-10-02
Thank you for you message.

I think i wait to do the change after my laptop reinstalling with 9.10 
I looked at the dependences but it´s too big replace with the new versions all the libraries involved so for now I wait...until 9.10 will be on my system then I´ll apply your guide.

thank you again
Alex

---

