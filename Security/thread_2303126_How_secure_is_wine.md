---
title: "How secure is wine?"
date: 2015-11-16
forum: Security
---

### Post by markodd on 2015-11-16
I need to use a graphing software that's only available for windows. Instead of having to create a different partition, I'm thinking about using wine. 

How secure is wine? I hate to use software that's not available for linux but this time, I really need to do it.

Does something installed by wine have access to my /home partition? What about the other files in the system?

---

### Post by TheFu on 2015-11-16
WINE is an API compatibility layer to provide an interface to linux that appears to be windows.  Windows viruses have been installed through WINE. If those virii recognize WINE then the risk to the system is about the same.

Any files that your userid can access could, in theory, be accessed and/or harmed.

If the machine is powerful enough perhaps running a copy of Windows inside a VM is an option? There are some negatives to Windows inside a VM:
* cost of the microsoft license
* Graphics performance isn't ready for high-end CAD/Photoshop on normal PCs
* Extra RAM dedicated to a complete Windows OS+apps+virtual GPU

But if you have a high end C2D with 4G of RAM and 25G-60G of storage, it should be fine for MS-Office type applications.  Definitely follow a Virtualbox or KVM tuning guide to get the best performance.  The defaults can provide bad performance on spinning disks. For SSDs it doesn't matter.

---

### Post by kurt18947 on 2015-11-17
Do you know the application you need to run will work with WINE? Some do (mostly)work,  many more do not. If you have an adequate machine - and it doesn't take a fire breathing monster, just a processor from the last 5 years and 4 GB+ RAM, Windows in a VM seems to work pretty well. There are some unfamiliar steps running Windows in Virtualbox like having to 'approve' each USB drive for Windows to access it but once familiar it works pretty well and guarantees compatibility. It also makes it easy to reinstall Windows if something untoward would happen to the Windows install. Just export the Windows appliance to external storage after setting up.

---

### Post by mastablasta on 2015-11-18
wine doesn't work as root. and windows viruses do not work in Linux. but you can get a rootkit that works in Linux and pass it on to Linux. maybe. 

I mean If you install a program from known source and the use wine to run it then you are fine. it's not like you will get attacked. but a windows virus might install & run via wine as well. so you just don't do it. in fact you might need to put some extra effort into it to get it run in wine. and if you feel a bit paranoid you can always install antivirus. wine has access to /home. 

see this [http://ubuntuforums.org/showthread.php?t=2206130](http://ubuntuforums.org/showthread.php?t=2206130)
and this (under 11): [http://wiki.winehq.org/FAQ#head-3cb8f054b33a63be30f98a1b6225d74e305a0459](http://wiki.winehq.org/FAQ#head-3cb8f054b33a63be30f98a1b6225d74e305a0459)

---

### Post by adagio on 2015-11-21
My own experience of wine applications that access the Internet is not good (not being able to conclude anything more concise than that at the moment I'm afraid).  There is firejail [https://l3net.wordpress.com/projects/firejail/](https://l3net.wordpress.com/projects/firejail/) which could be configured for wine I would guess [edit: there appears to be support out of the box], I will also be running Internet accessing applications over an encrypted/ anonymous connection.

---

### Post by SeijiSensei on 2015-11-21
All of the important pieces of wine from the user's perspective live in $USER/.wine. If some goes awry, you can always blow the entire directory away.  If you're worried, create a new user in Ubuntu and use it to run wine.

---

### Post by TheFu on 2015-11-21
Could apparmour be used to limit outside ~/.wine/ access by WINE programs?
BTW- ~/.wine/ is just the default location. WINEPREFIX sets which top level directory will be used. Sometimes it is necessary/convenient to have different WINEPREFIX areas for different programs.

---

### Post by SeijiSensei on 2015-11-21
[http://wiki.winehq.org/SecuringWine](http://wiki.winehq.org/SecuringWine)

To me, the default mapping of Z: to the top of the Unix filesystem tree is the most obvious security flaw in wine. While it's true that wine operates within the confines of ~/.wine, any malevolent program can write anywhere in the filesystem with the user's privileges by writing to Z:.  I'd certainly not run wine as the root user for that reason and many others.  You can disable the Z: mapping in winecfg, but some configuration files expect it.  In .wine/user.reg, all the Microsoft fonts are mapped to files in Z:\usr\share\fonts.  If you remove Z:, you'll have to make a separate copy of those fonts in ~/.wine or create a directory in ~/.wine that contains symlinks to the actual files.

Here's a discussion of whether the Z: drive should be abolished by default: [http://ubuntuforums.org/showthread.php?t=1517566](http://ubuntuforums.org/showthread.php?t=1517566)

The Z: drive itself is just a symbolic link in ~/.wine/dosdevices:
```

seiji@black-beauty:~/.wine$ ls dosdevices/ -l
total 0
lrwxrwxrwx 1 seiji seiji 10 Nov 21 17:44 c: -> ../drive_c
lrwxrwxrwx 1 seiji seiji  8 Nov 21 17:44 d:: -> /dev/sr0
lrwxrwxrwx 1 seiji seiji  1 Nov 21 17:44 z: -> /

```

---

### Post by adagio on 2015-11-22
There is a note on wine security in this document [https://wiki.ubuntu.com/BasicSecurity#Linux_Vulnerabilities](https://wiki.ubuntu.com/BasicSecurity#Linux_Vulnerabilities) - the answer in a nutshell (thanks to mastablasta for the link).

---

