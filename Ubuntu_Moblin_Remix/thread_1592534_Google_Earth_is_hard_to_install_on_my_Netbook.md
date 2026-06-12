---
title: "Google Earth is hard to install on my Netbook"
date: 2010-10-10
forum: Ubuntu Moblin Remix
---

### Post by gccradioscience on 2010-10-10
I just installed Ubuntu 10.10.  Installation was a snap!    It was faster through a DVD-ROM than it was on a flash drive.   I will do this again for the next release.   

Problem is that I went to Google Earth's website, and wanted to download Google Earth 5.0 all there was, was a .bin file.   And I was thinking I know how to use it, so after I downloaded it,  it was available.   When I installed it by typing sh in the applications box, it started to show archive integrety... very good, and then it I got this Parser error saying it cannot install the software.    I am saying to myself.   What is this crap now?

I feel we need to get this problem addressed to Google Earth to come out with a release of 5.0 for a .deb file 
so it can be installed safely and fast.  They made Chrome available through the .deb file, why didn't they follow through with this?  Everyone wants Google Earth on their netbooks for travel, but these bin files are very time consuming to install.   You really have to know what you are doing.    I can install .deb files quicker than I can install .bin files.    

Google Chrome has a .deb file,   So can Google Earth.


gccradioscience@gccradioscience-AOA150:~$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
gccradioscience@gccradioscience-AOA150:~$

---

### Post by mikewhatever on 2010-10-10
GE is available as .deb through Medibuntu. Unfortunately, they don't have it for Maverick yet.

---

### Post by gccradioscience on 2010-10-10
So what am I supposed to do at the mean time?   Use my Windows OS for Google Earth??     When do you think it will be out?   Google Earth for 10.10???

---

### Post by mikewhatever on 2010-10-11
Apparently, there is a third way.
```
sudo apt-get install googleearth-package
```

If you have Windows installed, then sure, use it.

---

### Post by BigRedButton on 2010-10-11
Don't use googleearth-package.  It doesn't work for 5.0. I had the same problem and, as akward as it sounds, just 
```
sh GoogleEarthLinux.bin --force
```I had the same problem, so I tried forcing it just to see what would happen and everything works fine.  

I do advise EXTREME caution though, in using the --force or -f modifiers (on any command) unless you know how to undo what you're forcing the command to do.  When installing a program like this it really isn't all that dangerous, but anything requiring root privileges is EXTREMELY DANGEROUS, and could break your system.

lol ignore this post.  I apologize for the poor advice... I thought that was how I did it (it's been a while)
It was googleearth-package that I --force'd, and although it ran, the package it created was no good

---

### Post by petersfreeman on 2010-10-12
Using the --force switch does not work as it is not one of the options.  When I run 

```
sh GoogleEarthLinux.bin
``` 

I also get:

```
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'

```

I took the files out of the .bin archive but could not find what is causing the error.

Peter

---

### Post by gccradioscience on 2010-10-12
When I tried this : sudo apt-get install googleearth-package in the terminal I got this : 


gccradioscience@gccradioscience-AOA150:~$ sudo apt-get install googleearth-package
[sudo] password for gccradioscience: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
googleearth-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gccradioscience@gccradioscience-AOA150:~$ 


I wish my netbook had Windows, it's going to get XP installed back on the netbook and have Ubuntu 10.10 soon back in place.  Still, Google needs to fix this problem.  There are alot of disappointed people out there with just linux on their desktops, laptops or notebooks, and netbooks or nettops.

---

