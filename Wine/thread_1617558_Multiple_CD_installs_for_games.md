---
title: "Multiple CD installs for games"
date: 2010-11-09
forum: Wine
---

### Post by nightmicu on 2010-11-09
Greetings,

 I initially posted in Games & Leisure and it would appear that my thread was deleted? Anyway, I am having problems installing games that are on multiple CDs.

I have tried using the paid program that allows for playing Windows games under Linux (mentioning the name responsible for deleting my post?), as well as PlayOnLinux and Wine directly. All have the same problem, getting stuck when the installer asks for the second CD. I have tried manually ejecting the CD, using "wine eject -a," installing CD 1 from the hard drive with CD 2 in the CD drive, etc.. nothing seems to work.

I am running Ubuntu 10.10 and I have a SATA DVD drive. So far I have tried installing Call of Duty (first one) and NFS Underground 2. Any help would be greatly appreciated here.

Thanks,

Benjamin

---

### Post by mastablasta on 2010-11-10
your post was deleted because of this:
[http://ubuntuforums.org/showthread.php?t=359869](http://ubuntuforums.org/showthread.php?t=359869)
 
what game are you trying to install?
 
this advice is from diablo2 wine site:
It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command: 
*$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:* 
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or viewing your boot-log.
 
[B]For running the multi-disk install, it helps to run the install using the drive letter and to not switch your shell to the cdrom's path. For example: 
*~/.wine/drive_c$ wine "D:\setup.exe" (where D: is the assigned letter of your CD drive).* 
If you run while having a current working directory of /mnt/cdrom, for example, then you will lock the drive and you won't be able to eject the disk.[/B]

---

### Post by nightmicu on 2010-11-10
> **mastablasta said:**
> your post was deleted because of this:
[http://ubuntuforums.org/showthread.php?t=359869](http://ubuntuforums.org/showthread.php?t=359869)
 
what game are you trying to install?
 

So far I have tried to install Call of Duty (first version) and Need for Speed Underground 2.

> 
this advice is from diablo2 wine site:
It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command: 
*$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:* 
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or viewing your boot-log.
When I open Winecfg, the only drive listings are C: ../drive_c and Z: /

Here is what I see in fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5d289e71-b0c9-4f7f-983e-1abb5324155e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=67fdddc5-ee46-4f05-a5a8-0da026e51178 none            swap    sw              0       0

```> 
[B]For running the multi-disk install, it helps to run the install using the drive letter and to not switch your shell to the cdrom's path. For example: 
*~/.wine/drive_c$ wine "D:\setup.exe" (where D: is the assigned letter of your CD drive).* 
If you run while having a current working directory of /mnt/cdrom, for example, then you will lock the drive and you won't be able to eject the disk.[/B]So, in simpler terms, don't run the setup.exe program from the GUI file browser? I tried the above command and it said invalid file or directory, probably because of the absence of a CD drive in Wine.

I'm by no means a Linux pro here.. but it seems like a great deal of other folks are able to simply install and run these games, making me wonder if it's something hardware related.

Thanks, any more information you can provide would be appreciated. :)

-Benjamin

---

### Post by mastablasta on 2010-11-11
[http://www.winehq.org/pipermail/wine-users/2006-January/020073.html](http://www.winehq.org/pipermail/wine-users/2006-January/020073.html)
 
>  
>* you need to create a link in the ~/.wine/dosdevices directory to the directory *
>* where you mount the CDROM in, e.g.*
>>* [sle at sle3]("http://www.winehq.org/mailman/listinfo/wine-users"):~> ls -l .wine/dosdevices/*
>* [snip]*
>* lrwxrwxrwx 1 sle users 12 2005-11-26 18:36 r: -> /media/cdrom*
>* lrwxrwxrwx 1 sle users 17 2005-11-26 18:36 w: -> /media/dvd*
 

 
Probably still true. basically you need to tell wine where the CD drive is.
 
then the command should work. 
 
it might also be possible to right click the file and run it with wine, but problem is this command is necessary for multiple CD install.
 
 
edit: running wine through teminal will also give you output on any errors.
 
---
 
another option is to use a GUI for wine.

---

### Post by nightmicu on 2010-11-11
> **mastablasta said:**
> [http://www.winehq.org/pipermail/wine-users/2006-January/020073.html](http://www.winehq.org/pipermail/wine-users/2006-January/020073.html)
 

 
Probably still true. basically you need to tell wine where the CD drive is.
 
then the command should work. 
 
it might also be possible to right click the file and run it with wine, but problem is this command is necessary for multiple CD install.
 
 
edit: running wine through teminal will also give you output on any errors.
 
---
 
another option is to use a GUI for wine.

I'm still a beginner with Wine, although I have been able to install single CD or setup file programs without any problem. Can you explain how to create this link you speak of?

And how might I run Wine through terminal? I have tried accessing the DVD drive through Wine in terminal and it says file or directory not found -- no CD drives appear in Winecfg.

I have tried installing using PlayOnLinux and Cedega, everything gets stuck with the second CD. Just an update, I tried using a USB DVD drive and it did not make any difference. Was hoping that it was just an issue with the SATA DVD drive I have, may still be a hardware issue. This is a tricky problem because most of the posts I've found via Google are several years old -- as are the games I'm trying to play.

---

### Post by mastablasta on 2010-11-12
no problem i am also a beginner in wine and linux.
 
Have a look here at how to configure wine (for driver look under chapter 3.1.4):
[http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)
 
Have you tried the autodetect button in the wine config settings to find the CD drive?
 
to run wine programme though terminal first open the terminal found in applications. and then just type
 
```
wine "d:\setup"
```
 
will do if oyu have only one CD. otherwise you will need the command i posted before.
 
More here:
[http://wiki.winehq.org/FAQ#run_from_terminal](http://wiki.winehq.org/FAQ#run_from_terminal)
 
> 
**4.3. How should I start Windows programs from the command line?**
 
 
This will allow you to see messages from Wine that may help troubleshoot problems. 
Because Windows programs will often look for files in the location they were started from, when using the command line you should start them in a very specific way: "change directory" to the folder where the program is located and run the .exe file using **only** its filename. For example: 
```
cd '.wine/drive_c/Games/Tron'wine tron.exe
```In some cases you may wish to specify the full path to the program's .exe file. For example, if you need to install a program from multiple CDs, the previous method won't work (entering the directory in the terminal will prevent you from removing the CD). You can provide Wine with a DOS or Windows style path inside single quotes like so: 
```
wine start 'C:\Games\Tron\tron.exe'
```You need to use wine start if you specify a full path, because that allows Wine to set the working directory for the program if it needs it. You can also use double quotes, but you need two backslashes instead of one: 
```
wine start "C:\\Games\\Tron\\tron.exe"
```If you need to use a Unix style pathname, use the /Unix option to start, e.g. 
```
wine start /Unix "$HOME/installers/TronSetup.exe"
```For current Wine, once a program is installed, you can safely use any shortcuts that the installer has created. 
 
you basically put a path after wine and any necessary switches you need.

---

### Post by Ted_Kazynski on 2010-12-22
I have a problem with all of this Wine and Diablo2 stuff as well, I have a net book with no cd drive... therefore cannot mount an ISO to /media/cdrom. because it doesn't exist. I tried to mount the images with gmount and could install D2 but cannot play it because it says it's disc is not in the drive. I tried to install the expansion but got all the way through and it wanted me to insert the exp disc. but wouldn't recognize it. I tried making links to things but really dont know whats going on... lots of read only and not found messages.

Another thing is how am i supposed to mount a cd to a blank folder if it has a link file in it? and how do i make a link to a folder that isn't empty? Im in a catch 22. Thought about just buying an external cd drive... but Im sure it wouldnt work as smoothly as i want. (i've used linux for over a year, not much goes smooth as far as set up and installation goes.) 

Man, I really hate to love linux.

---

### Post by Perfect Storm on 2010-12-22
> I have a problem with all of this Wine and Diablo2 stuff as well, I have a net book with no cd drive... therefore cannot mount an ISO to /media/cdrom. because it doesn't exist. I tried to mount the images with gmount and could install D2 but cannot play it because it says it's disc is not in the drive. I tried to install the expansion but got all the way through and it wanted me to insert the exp disc. but wouldn't recognize it. I tried making links to things but really dont know whats going on... lots of read only and not found messages.

You can properly find a NoCD file for the game ( I can't link or find it for you as it against the forum CoC).

To mount the ISO's I can recommend furiusisomount then mount both ISO's at the same time.

---

