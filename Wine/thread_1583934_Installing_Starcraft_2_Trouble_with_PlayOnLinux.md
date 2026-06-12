---
title: "Installing Starcraft 2? Trouble with PlayOnLinux"
date: 2010-09-28
forum: Wine
---

### Post by Waveridr85 on 2010-09-28
Hello, everyone.  I am new here, new to playonlinux, and new to Ubuntu as well.  

First are there any alternatives to installing starcraft 2 without PlayOnLinux?  If not:

I was hoping for a little bit of guidance installing Starcraft 2 on PlayOn Linux.  I have the dvd version. 

What I am doing: 
-Open POL 
-Click Install 
-Search & find SC2, click apply, and click forward once the POL installer pops up. 
-I select the dvd version (dvd is inserted into multidrive) 
-When it asks where is my cdrom mounted, I select cdrom0 (options are cdrom; cdrom0, PlayonLinux; & other) 
-A terminal like thing pops up and asks me to enter the following: 

sudo umount /media/cdrom0 && sudo mkdir -p  /media/PlayOnLinux/ && sudo mount -o ro,unhide,uid=1000  /media/PlayonLinux/ 

I enter it exactly. 
, then it asks for my password and I enter it. 

It then tells me: 
Cant find /media/PlayOnLinux/ in /etc/fstab or /etc/mtab 


Anyone have an Idea what is going on? 

If at all possible, can you please explain with newbie details.   Like your telling your grandma how to fix it.  I am very unacknowledged  as far as linux terms go.   

Sorry, and thanks a ton.

---

### Post by philinux on 2010-09-28
Moved to Wine forum.

---

### Post by sunny69 on 2010-09-28
[http://www.retrohive.com/2010/08/20/play-starcraft-ii-linux/](http://www.retrohive.com/2010/08/20/play-starcraft-ii-linux/) see if it can help you .... :)

---

### Post by Half-Left on 2010-09-28
StarCraft 2 is platinum so you shouldn't have to do anything to get to install and play.

I recommend you just use Wine and it works just like Windows. PlayOnLinux uses a different prefix to Wine, so you might get issues.

---

### Post by Waveridr85 on 2010-09-29
> **sunny69 said:**
> [http://www.retrohive.com/2010/08/20/play-starcraft-ii-linux/](http://www.retrohive.com/2010/08/20/play-starcraft-ii-linux/) see if it can help you .... :)

I followed that, but once I am in POL.  I get the issue when it asks me to run that command in the command window that pops up.

---

### Post by beastrace91 on 2010-10-01
> **Half-Left said:**
> StarCraft 2 is platinum so you shouldn't have to do anything to get to install and play.


This is not an issue with POL but with the DVD disc Blizzard uses. The digital downloader works fine - that is why the game is "platinum"

@OP As for your remounting issue, the command play on Linux is telling you is missing an argument. It should be:

sudo umount /media/cdrom0 && sudo mkdir -p /media/PlayOnLinux/ && sudo mount -o ro,unhide,uid=1000 **/dev/cdrom0** /media/PlayonLinux 

Give that a try and see if it allows you to install from the disc after running it.

Cheers,
~Jeff Hoogland

---

### Post by Kaboontu on 2011-09-09
late, but, u should try giving not the cdrom device,
but the exact place 
like SC2-L100-D1

---

### Post by adrianch00 on 2011-09-29
POL doesn't work for me.. I can get it on wine installer perfectly fine.. Check this link for help: [http://wrerase.wordpress.com/2010/08/02/how-to-install-starcraft-2-on-ubuntu-10-4/](http://wrerase.wordpress.com/2010/08/02/how-to-install-starcraft-2-on-ubuntu-10-4/)

however I can't play the game. some error with directx 9.0 saying I can't run the game without it.

---

### Post by IparryU on 2012-06-06
This is how I had to set everything up:
in winetricks, check the following boxes for install:
.NET 2SP2
directx9c (this is not the exact name, but look for the main directx install)
d3dxof
devenum
dsound
dxdiag
dxdiagn

all the d3dx files should be checked off i would assume. I am waiting for all the patches to download right now. thus far the install has been smooth. will update when i get some results.

---

