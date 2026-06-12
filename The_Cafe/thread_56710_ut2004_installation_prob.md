---
title: "ut2004 installation prob"
date: 2005-08-13
forum: The Cafe
---

### Post by daejavu on 2005-08-13
hi .. im trying to instal UT2004  ... i run the linux-installer.sh prog .. and then after entring the serial it starts the installation ..
but after just one second it ask "Please mount the UT2004 Play CD".

in my dvd there are 6 folders names CD1 to CD6 in which all the cds were copied ..means that the dvd contains a collection of all the 6 cds .. the game canbe installed from windows but it says to mount the play cd after start installation !!

what to do ?

---

### Post by sapo on 2005-08-13
hehe its a very dumb stuff with the ut2k4 installation

just copy the install.sh to a folder in you pc and run it from there... it will work ;)

---

### Post by daejavu on 2005-08-14
i tried to copy the WHOLE game in the linux partition and install it from there but unfortunately the goddam installer says the same thing !!  :|

---

### Post by sapo on 2005-08-14
[QUOTE=daejavu]i tried to copy the WHOLE game in the linux partition and install it from there but unfortunately the goddam installer says the same thing !!  :|[/QUOTE]

lol.. dont copy the whole game.. copy just the installer.. it worked here without problems after copying the installer  :-P

---

### Post by daejavu on 2005-08-14
did that too ... and it says the same thing .. !!

woooo .. .wait a minute !! 
did u meant that cp JUSSTTT the install file  i.e.  linux-installer.sh  into the hdd and run that ?

---

### Post by sapo on 2005-08-14
[QUOTE=daejavu]did that too ... and it says the same thing .. !![/QUOTE]

thats wierd [img]http://ubuntuforums.org/images/smilies/eusa_think.gif[/img]

---

### Post by daejavu on 2005-08-14
woooo .. .wait a minute !!
did u meant that cp JUSSTTT the install file i.e. linux-installer.sh into the hdd and run that ?

---

### Post by sapo on 2005-08-14
[QUOTE=daejavu]woooo .. .wait a minute !!
did u meant that cp JUSSTTT the install file i.e. linux-installer.sh into the hdd and run that ?[/QUOTE]

yes.. just the install.sh

did you copy the full DVD?  :|

---

### Post by daejavu on 2005-08-14
i got bad news dude .. i tried that and it failed as well   

heres whats happening in case somethins missed ... 

i throw the dvd in the drive.. 
it auto mounts it on /media/cdrom1/     (i got 2 roms so i got cdrom,cdrom0,cdrom1)
i cp the installer
run it 
and it says please mount the play cd in the drive   ](*,)

---

### Post by crane on 2005-08-16
Hey man just did some searching for you and found something. Enter this command before executing the installer.
export SETUP_CDROM=/media/cdrom/ 
or
export SETUP_CDROM=/media/dvd/ 
My dvd player is mounted under /media/cdrom/ But I would check to make sure it's not mounted under /media/dvd/

Just put in the disk and go to you media file and see where the ut2k4 cd is mounted.

I'll put this or at Linux gaming Clan forums as well.

---

