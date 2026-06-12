---
title: "Diablo 2 Problem!"
date: 2010-12-21
forum: Wine
---

### Post by RoflHaxBbq on 2010-12-21
I have Ubuntu 10.10 and Wine 1.3(I think) installed on my system.

First I tried inserting Diablo 2 disc 1, then typing into terminal:
```
wine /media/
``` then pressing tab, and it finishes it off as:
```
wine /media/Diablo\2\Disc\1
``` or something similar to that.
I then finish it off as ```
wine /media/Diablo\2\Disc\1/installer.exe
``` Or something likes that.

The installer opens, I click through the prompts, it starts installing, and soon after asks me for disc 2. I right click on the desktop on the icon, and click eject. I insert disc 2, It comes up on the desktop as an icon, and its location is /media/Diablo 2 Disc 2, then I try click ok on the installer box that is asking me for disc 2. Nothing happens at all when I click ok. I cancel the install.

When I open winecfg and go to drives, I can add a drive D:\, but the problem is that when I insert a disc, it comes up as /media/*name of disc* instead of /media/cdrom0 or whatever. So I cannot install Diablo 2 because whenever I insert the next disc it's location is different to the previous one.

Help please?

-RoflHaxBbq

---

### Post by mastablasta on 2010-12-22
hello, check here : [http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49)
 
(scroll down the page) 
to see this:
> 
For running the multi-disk install, it helps to run the install using the drive letter and to not switch your shell to the cdrom's path. For example: 
*~/.wine/drive_c$ wine "D:\setup.exe" (where D: is the assigned letter of your CD drive).* 
If you run while having a current working directory of /mnt/cdrom, for example, then you will lock the drive and you won't be able to eject the disk.

 
also check any other good advices (like how to switch certain shortcuts so the game doesn't freeze every now and then).
 
 
To the East, always to the East.... :-)

---

### Post by RoflHaxBbq on 2010-12-22
Thanks for the reply, but that isn't my problem (I was following that tutorial!).

I should have explained myself more.

I believe the location of my cd drive stays the same, I thinks it's dev/hdc or something, but it's mount point changes depending on the disk.

For example, If I insert a Warcraft 3 CD, It's mount point would be /media/Warcraft III (Or similar). So if the mount point is changing, then it makes it impossible to set a drive letter (D:\) for the CD drive.

If the mount point always stayed at /media/cdrom then it would be easy, because it stays the same.

So perhaps I could open up winecfg after inserting each CD and changing the drive letter D: location to the location of the current disc?

---

### Post by mastablasta on 2010-12-23
you say you were following it yet your commands are different than in the tutorial.
 
what you do is basically you tell wine that anything that mounts on cdrom will be in WINE known as D: drive and CD at that. 
 
and again your commands for example wine /media/Diablo\2\Disc\1 are not in the tutorial i linked.

---

### Post by buzzmandt on 2010-12-23
you could try installing using playonlinux
> sudo apt-get install playonlinux
> playonlinux

---

### Post by garyhibdon on 2011-01-08
not sure if you have gotten this to work yet, but all you really have to do is the following coding:


/media/ 
then press tab and it should read the disc to fill it in. after it does, add /installer.exe at the end of it.

this will start the installation.
let it run through it until the prompt for the second disc. then go back to your terminal and do the same thing again. 
on mine, as i started to access the cd drive it loaded automatically but you may have to do this manually for each disc. not that difficult though. hope it helps!!

---

