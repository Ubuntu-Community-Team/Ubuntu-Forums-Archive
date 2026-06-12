---
title: "Ubuntu , VirtualBox Migrating Windows XP (Tips)"
date: 2008-04-01
forum: Virtualisation
---

### Post by rossy65 on 2008-04-01
I've spent 4 days on this, attempting to migrate Windows XP from my DELL 620 laptop onto Ubuntu "gutsy" release.  Here is what I found, that other newbies might find helpful.

  The "virtualbox" distribution from the web (binary only) has usb support and is newer (1.5.2) than the "Open Source Edition"  Virtual-box-ose.  I had some minor issues with cockpit error and was switching back and forth between the two releases.  USB is not supported in the ose flavor.  If you do switch packages back and forth as I did... the *.xml files are not 100% compatable.  They can be tediously hand edited.. but I don't recommend it.

The Newer *cool* version does not appear to support VBoxManage and at one point I was told to re-install virtual-box-ose.  This could be a path issue, but you may have problems.  So the ose flavor is good for cloning vdi images, but the binary only dist is good for USB support.  Swapping back and forth causes ANGUISH... so try to avoid doing that unless you have no other choice. 

Google search terms that help:
 MergeIDE
 bootcfg
 fixmbr
 fixboot

  It might also be useful to have a bootable CD that allows hacking passwords, but I didn't say anything about this.
Once you attempt to do a "Recover" of an image in my case that is used for work, you need to get around the Admin password to fix the registry to make it work as a client image.  

I found that for the DELL D620 there are two partitions, so BOOT.INI needs to be edited to get anywhere.  This isn't mentioned anywhere as I suspect most users aren't trying to migrate onto using a Dell laptop.  bootcfg is the command to fix this...

I found that the clonevdi command is VERY time consuming.
VBoxManage clonevdi existingImage.vdi Newimage.vdi

I'm not 100% through this effort.

The merge.bat file extracts driver stuff from the /i386 directory this is handy.  The merge.reg files poke the registry.  There are some good websites that walk through different methods to poke the registry 
[http://www.solriche.co.uk/files/misc/move_xp.html](http://www.solriche.co.uk/files/misc/move_xp.html)

was one of them.

FYI... in the Recovery console, you can't do much outside the C:\WINDOWS directory... so it's handy to copy the folder from MERGEIDE.zip into this directory so you can get to it from the recovery console.  (Thank's Microsoft for making this so easy!).

Now I finally know why I have so much difficulty porting older Windows disks to newer hardware through the years.... its DESIGNED to break as a copy protection methodology... Thanks again Microsoft.

-- R

---

