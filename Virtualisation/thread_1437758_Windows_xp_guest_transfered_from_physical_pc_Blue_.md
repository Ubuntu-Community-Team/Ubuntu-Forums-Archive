---
title: "Windows xp guest transfered from physical pc Blue screen"
date: 2010-03-24
forum: Virtualisation
---

### Post by altometer on 2010-03-24
SOLVE: changed HDD controller to ICH6. Don't know why it worked, but it is beautifull.



This seems to be a bit of an insane problem. I have already spent several days attempting to fix this. Also note, while it may seem that it would be easier to just build a new virtual xp, there are several pieces of software on the XP machine that will take weeks to re-validate. 

My setup.:
Dell Dimension 9200
Physical XP machine being converted to virtual:
```
Windows Xp Professional Edition sp3 with all of the latest updates
Intel core 2CPU 6300@1.86GHZ 
2GB of ram
Physical Address Extension

```
Ubuntu HOST machine:
```
Ubuntu 9.10 64bit
virtualbox 3.0.8_OSE
Intel Core 2 quad CPU Q9400@2.66GHZ
8GB of RAM
```

I have attempted to create the image using both, vmware converter and self image. 
I have also attempted running the image in windows' virtualbox, as well as Ubuntu's.

Both have caused the Blue screen error:
> 0x0000007B (blah,blah,blah,blah)

Research of this showed that it was most likely the IDE controller set to PIIX4 instead of 3. I attempted using the PIIX3, and a sata controller both of which still result in a Blue screen.

Edit: I have attempted changing the number of CPU's on the virtual machine from 1 to 2. No change.(yes virtualization of hardware is enabled in the bios)

I have also attempted expanding a new hal.dll from the xp disc, performed a chkdsk /r on the virtual machine, and attempted replacing the system hive.

I am able to mount the .vmdk file as a second hardrive on a working machine, and browse the files. I am also able to boot to a cd.(for instance, Hiren's ubcd)

Any help would be greatly appreciated.

EDIT: Forgot to mention, the Blue screen appears shortly after the windows xp loading bar splash screen.

---

