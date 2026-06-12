---
title: "Can someone help me with chroot or (and) cloning a os to a virtual machine?"
date: 2019-04-16
forum: Virtualisation
---

### Post by usernamoi on 2019-04-16
i de-configured something in my ubuntu-studio os, and i want to 

A 
either know how to properly mount  the right folders using chroot to use firefox so i can recover the bookmarks, and also be able to run cairo-dock to check my personal settings; if possible, also manually change the order of kernels since i improperly installed a few kernel deb files manually, so i could try restart the system with another one. 

or B
learn how to clone and use the original partitions with a virtual machine, so i can use it to check my files there, see what i can recover or copy, before resetting the system.

ive already seen i few tutorial about chroot, but i dont want to try them without a bit of help since they are too old, and i know very basic things about linux. 

ex. 
[https://www.youtube.com/watch?v=XTyY3in5r6Q](https://www.youtube.com/watch?v=XTyY3in5r6Q)
[https://www.youtube.com/watch?v=VfyvF1cnYdE](https://www.youtube.com/watch?v=VfyvF1cnYdE)

Thanks.

---

### Post by TheFu on 2019-04-17
Best to ask 1 question per thread.  

chroot has NOTHING to do with accessing storage. Nothing. Most people switched to using Linux containers instead of chroot about 5 yrs ago.  chroot has a number of flaws.  There are a few different tools which do almost the same things as a Container, but without all the hassles.
```
firejail --private firefox 
```
but why not just copy the bookmarks.html file? Did firefox change how they deal with bookmarks recently?  Copy that file, then import it into a new FF instance.

BTW, firefox installs are completely portable. You can move an install to a new userid or a different system and do whatever you like.

Virtual machines ... There is no need to put storage things into a VM to access the storage.  Just mount it and copy off what you need.  You can boot from any Ubuntu-installer flash drive or DVD and access the storage, if that is the issue.  Sorry, you've lost me on the virtual machine part. I use virtual machines for almost everything and have for almost 15 yrs now.  

Or are these trick questions?

---

### Post by usernamoi on 2019-04-19
They arent trick questions:
 im more or less a noob who ignores the right approach to solve a few problems. 

The problems are these:
- lost access to my main ubuntu based system, because: 
-- boot wont reach login screen from trying to install improperly some files (deb files for a kernel i manually downloaded).
-- grub works but the window with alternative kernels wont show (will start another screen pointing to a different problem, likely a consequence).
-- manually change the kernel that auto-loads with grub from a liveusb, so i can try to restart the system with it.
-- boot repair offers an option to reinstall the last kernel used, but since my problem started from trying to install manually a kernel, i dont think this could be a good option and could complicate things more; so, if theres i way to use boot-repair to install a different kernel than the last used, that would be great.

the options i thought to at least recover files, while i try to solve them were:
solved 
- finding how to recover things at /home 
(which was encrypted, but i could recover the folder with "sudo ecryptfs-recover-private --rw ")

partially solved
- since firefox configuration files are under home, but im unsure how could i try to open them from a liveusb (without chroot) or where are the addons and their settings to try to load them also from a liveusb, i havent tried this approach.

not solved 
- check firefox bookmarks from the original system to generate a backup html (i think this could be possible through chroot from an old tutorial i watched), and also check the addons to back them up and their settings (like adblock filters, stylus themes, and a list of speed dials); this is why after checking a bit of chroot tutorials though that i could use it, or a vm to check everything i had installed.
- how to mount with the same method other files which might be encrypted outside home (maybe only home was encrypted from standard installation options, but i ignore how to check if other encrypted folder exists under root "/" ). if there arent encrypted files under root, and no folders that need to be recovered there (fonts, personal themes and other things i ignore that could be there), then i can skip this.
- mount with chroot, or using a vm, the same settings i used to be able to see them and back them up including cairo-dock settings and list of tools, and software to either search it again, or just repeat the configuration after resetting the system.

additional objectives
- learn if its possible and how could i could install xenial tools and software in more recent distros like bionic based, so i could install a more recent os, but be able to experiment and use the outdated or abandoned projects that only reach xenial compatibility oob.
- how to create appimages for some of those outdated programs.

---

### Post by TheFu on 2019-04-19
> partially solved
- since firefox configuration files are under home, but im unsure how could i try to open them from a liveusb (without chroot) or where are the addons and their settings to try to load them also from a liveusb, i havent tried this approach.

Copy your HOME and you have everything for firefox. Only binary plugins won't work, but most addons will and all the data is in there.  I don't remember where they are specifically, but you can use **locate** to find the directory.  On mine it is ~/.mozilla/firefox/  ~/ ==== $HOME

Thunderbird and all the addons for it work the same way.

I've moved FF and thunderbird between Windows, Linux and OSX installations a few times.  Just make certain you maintain the owner, group and other permissions (stay on Unix file systems, not NTFS or FAT-whatever) to be the userid on the "target" machine and put the entire directory structure inside the expected location for that OS.

Forget chroot. You don't need it.  Srsly.  YOU DON'T NEED OR WANT IT.  It has nothing, nothing, nothing to do with any solution to get data off storage.





Nothing.

---

### Post by TheFu on 2019-04-19
> how to mount with the same method other files which might be encrypted outside home

If you didn't go out of your way to put something outside your HOME, then it wasn't put there.  The only exceptions would be packages that you installed manually. 
Themes, which I never use, go to standard places for themes.  

You still don't need/want chroot.  I think you don't know what chroot does and where it is useful.

Just boot from a live-boot flash drive (also called an Ubuntu Installer) - use the same version of the OS, but the GUI doesn't matter too much, then copy anything you want to keep off to Unix storage.  Don't use NTFS or FAT32/vFAT/exFAT since none of those will retain the owner, group and permissions. That metadata is 50% of the stuff necessary to put the files back.  The data alone isn't sufficient.


People new to Linux shouldn't be installed kernels outside the normal, patching, techniques.

Good luck.

---

### Post by TheFu on 2019-04-19
You've shot your install in the head. 
That's a good way to learn, by fixing it.
But the main lesson seems to be missed.  Get backup religion before it is too late.  With good backups, all of this would have been a minor inconvenience.  If you use encryption, you definitely need good backups.

If you want to learn Linux, it is best to follow some structured learning, because skills build on previously learned skills over and over and over and over. Backups would be a skill needed years before learning to manually install a kernel.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is where I usually send people who have shown some interest beyond point-n-click stuff.  If you want to learn Linux administration, LPI has 201 and 202 courses and there are free training materials online.

I use lots of virtualization.  When projects die or are abandoned, there is usually a good reason. If you'd like to take over for the project team, I bet they'd love to help get you started with a 15-30 min primer, but don't expect them to teach you to code.

---

