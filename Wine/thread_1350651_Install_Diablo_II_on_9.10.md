---
title: "Install Diablo II on 9.10"
date: 2009-12-09
forum: Wine
---

### Post by neigun on 2009-12-09
Hi Guys 

Has anyone had any luck in installing Diablo II in 9.10 64 bit? Currently I'm running Wine 1.1.31 and the drives are all detected OK.

The command lines suggested in Wine HQ, [http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49), give the following:

neil@neil-desktop:~$  ln -s /media/cdrom0~/.wine/dosdevices/d\:\:  
ln: creating symbolic link `./d::': File exists
neil@neil-desktop:~$ ~/.wine/drive_c$ wine "D:\setup.exe"
bash: /home/neil/.wine/drive_c$: No such file or directory
neil@neil-desktop:~$ 

Its actually installer.exe on CD 1, but this gives the same results, and Wine HQ gives the above command line.

dynacrylics post (which is pretty old now and for feisty), [http://ubuntuforums.org/showthread.php?t=443821](http://ubuntuforums.org/showthread.php?t=443821), gives the following:

neil@neil-desktop:~$ wine /media/cdrom[0]/install.exe
wine: cannot find '/media/cdrom[0]/install.exe'
neil@neil-desktop:~$ 


Thanks in anticipation Neil

---

### Post by beastrace91 on 2009-12-09
From my experience using Wine with Diablo 2 - you do not need to symlink your /media/cdrom0 to a Wine D:\ drive. Simple put the disc in your drive, then navigate to the location of the install files using nautilus, right-click on the setup.exe and select "Run with Wine" (Or if you want to use terminal you can run it from there as well just us **cd** to find the directory of the cdrom and then **wine setup.exe** to get the installer going)

Also I'd recommend updating your Wine version sooner rather than later - I know form personal experience 1.1.31 gave me issues with a few of my games that worked fine on other version.

Regards,
~Jeff

---

### Post by neigun on 2009-12-09
Jeff

that is what I would normally do. However, I get access denied on this occasion.

Neil

---

### Post by Soulcage on 2009-12-10
Check "Users and Groups" (system > admin > users and groups) for "use cd-rom drives" it might be off...

---

### Post by neigun on 2009-12-10
Sorry I probably wasn't to clear.

I can open the CD from the icon on the desktop but the installer.exe has a cross by it, which I assume means the system cannot read it. In properties the execute box has a horizontal line through it and is greyed out as are the various folder access groups.

Neil

---

### Post by beastrace91 on 2009-12-10
Maybe its not ideal but if you want just register your key @ battle.net and use the automated downloader for D2 - I know it works fine.

~Jeff

---

### Post by neigun on 2009-12-11
Thanks Jeff!

The game downloaded a dream; though I don't know why the install.exe file was blocked on the CD.

---

### Post by beastrace91 on 2009-12-11
> **neigun said:**
> Thanks Jeff!

The game downloaded a dream; though I don't know why the install.exe file was blocked on the CD.

At any rate now you can loose the CDs - I know I lost mine awhile ago after registering on battle.net :)

~Jeff

---

### Post by biggles7268 on 2010-02-17
I can't seem to get the blizzard downloader to work.  It tells me to choose a path to save the files, but won't let me select anything.

---

