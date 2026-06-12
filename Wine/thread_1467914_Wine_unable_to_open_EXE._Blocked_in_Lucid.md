---
title: "Wine unable to open EXE. Blocked in Lucid ?"
date: 2010-05-01
forum: Wine
---

### Post by Blur-king on 2010-05-01
Had install wine but has problem trying to install exe file. Keep getting this message

"The file '/home/dada/Desktop/SoftonicEN_FFSetupSoftOnic.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

Any ideas?

---

### Post by note32 on 2010-05-01
right click on the .exe and go to properies i think you have to uncheck read only or something like that

---

### Post by tgm4883 on 2010-05-01
Actually, you right click, go to properties, and check the box next to executable

---

### Post by Blur-king on 2010-05-01
Thanks. Got it :)

---

### Post by kerry_s on 2010-05-01
properties-> permissions, check> allow executing file ...

---

### Post by note32 on 2010-05-01
> **tgm4883 said:**
> Actually, you right click, go to properties, and check the box next to executable

thats what i ment

---

### Post by andygait on 2010-05-01
> **tgm4883 said:**
> Actually, you right click, go to properties, and check the box next to executable


Many thanks. 

I was having the same problem trying to get Spotify to load.

Thanks again. :)

---

### Post by Madspyman on 2010-05-01
This works as a fix per exe. What about for content that's on a cd/dvd? I know you could always copy the content to the hard disk, and fix it that way, but It'd be nice to be able to install programs from a cd/dvd.

---

### Post by ZBREAKER on 2010-05-01
Yep, exactly...trying to install an old game (Unreal) from cd and the solutions above do not work for the setup.exe on the game disk.

Anyone?

---

### Post by mc4man on 2010-05-01
from a cd - 3 of a number of solutions
If you run from a terminal then there should be no issue w/ wine /path/to/.exe
Ex.
wine /media/COD1/Setup.exe

create a new custom launcher - r. click on the .exe, open with other application -> use a custom command
for the command this will do.
wine

Then either r. click - open with wine or r. click - properties - open with and set the default to wine - then a d. left click on any .exe will work.

Edit the default launch command for wine
as it is now 
Exec=cautious-launcher %f wine start /unix 

change to 
Exec=wine start /unix %f

Edit
if doing a multi-disk install then these are 2 ways I've found (by default lucid has no fstab entries anymore for cd/dvd drives and wine obviously can't dtect the drive.
quoting from other post

> I just did a multi-disc install on lucid 2 different ways so it's possible.

The first way (without an fstab entry), I created a 'drive' in winecfg - D: with an address matching the mount point of the cd - /media/<volumelabel> and proceeded as normal

The second way, I created a fstab entry, restarted, had winecfg detect the drive and again no issue

---

### Post by ZBREAKER on 2010-05-02
mc4man...many thanks...your solutions worked perfectly:)

---

### Post by blchinezu on 2010-05-03
> **mc4man said:**
> 
[...]
Edit the default launch command for wine
as it is now 
Exec=cautious-launcher %f wine start /unix 

change to 
Exec=wine start /unix %f
[...]

  right... and how could the default launch commands be changed? where are the command files to be found?

---

### Post by mc4man on 2010-05-03
> default launch commands be changed

```
gksu gedit /usr/share/applications/wine.desktop
```

If a wine update happens to change back then just redo, no big deal
(a custom launcher will never be affected an update to wine

---

### Post by blchinezu on 2010-05-03
thanks

---

### Post by union two levers on 2010-05-03
nope still having problems trying to load programmes from a cd still telling me off for trying to load from an untrusted source...didn't have any problems with jaunty.any ideas please..simple instructions needed i ain't an expert...cheers

---

### Post by mc4man on 2010-05-03
> .simple instructions needed

this is about the simplest method I can think of

Put your cd in the drive, when the icon shows up on the desktop right click on it -> browse folder.
When the window pops up showing the cd contents make sure it's not fullscreen

Then open a terminal, type wine and hit the space bar on keyboard

Then with your mouse grab the .exe you wish to run and drop it into the open terminal box

Then simply click your mouse anywhere in the terminal box to return focus and press enter on the keyboard

---

### Post by james1986 on 2010-05-04
Im having this problem in Xubuntu 10.04.

However there is no checkbox under the permissions tab like there is in ubuntu.  Is there a way around this?

thanks

---

### Post by YokoZar on 2010-05-04
Even simpler instructions: Install the Wine Team PPA.  I've disabled cautious launcher there because I really hate it, but unfortunately the security team won't let me put something nice in Ubuntu proper until I can replace it.

---

### Post by twright on 2010-06-06
IMO this was a terrible decision - making it impossibly obscure to run applications is no substitute for security. The current state is completely unworkable.

Now for a constructive proposal, why not copy the way android does this?

If there were a chance that a better alternative would be accepted, I could program something.

---

### Post by auxbuss on 2010-06-16
Has anyone raised a bug against this do you know?

---

### Post by tgm4883 on 2010-06-16
> **auxbuss said:**
> Has anyone raised a bug against this do you know?

It's not a bug. It's a feature.


Well, technically I guess it is a security decision

---

### Post by syed.rakib.al.hasan on 2010-09-09
[SIZE=2]> **kerry_s said:**
> properties-> permissions, check> allow executing file ...

i tried doing this. but i have the following issues:


[LIST=1]
[*]when i right-click -> properties -> permissions, i see that the owner is root and i see that all the options are inactive (visible only... cannot be interacted with)..... whereas is i am the only user (username:blahblah) on this pc and i myself AM the root..... screenshot1 is given
[*]when i open up nautilus as administrator (as in, as root), i rightclick -> properties -> permission..... i see that all the options are now active and i can interact with them...... when i try to change the user to MY username:blahblah, it says that operating is not permitted..... whereas my username IS the username with ROOT privelleges...... screenshot2 is given......
also when i simply try to click the checkbox for "Allow executing file as program" from here, it moves back to the unchecked state immediately
[/LIST]
 
what do i do????


[IMG]http://i52.tinypic.com/r8f42b.jpg[/IMG]
** image 1**




[IMG]http://i54.tinypic.com/ogjfp5.jpg[/IMG]
**image 2**



[/SIZE]

---

### Post by AnimatroniK on 2010-12-28
> **mc4man said:**
> this is about the simplest method I can think of

Put your cd in the drive, when the icon shows up on the desktop right click on it -> browse folder.
When the window pops up showing the cd contents make sure it's not fullscreen

Then open a terminal, type wine and hit the space bar on keyboard

Then with your mouse grab the .exe you wish to run and drop it into the open terminal box

Then simply click your mouse anywhere in the terminal box to return focus and press enter on the keyboard

You're a GOD!
Thanks, You helped me too :))

---

### Post by mafredd03 on 2011-11-20
> **tgm4883 said:**
> Actually, you right click, go to properties, and check the box next to executable

I checked it but it unchecked by it self right after i unchecked it, i need help please,:confused:

---

### Post by mafredd03 on 2011-11-20
> **note32 said:**
> thats what i ment

on ubuntu 11.04, i am checking the box to execute but, then is unchecked by it self right after i checked it. i need help :confused:

---

### Post by sffvba[e0rt on 2011-11-20
> **mafredd03 said:**
> on ubuntu 11.04, i am checking the box to execute but, then is unchecked by it self right after i checked it. i need help :confused:

Best to start a new thread for your issue, this one is for Lucid and not Natty.

*Back to **sleep** old thread...*


404

---

