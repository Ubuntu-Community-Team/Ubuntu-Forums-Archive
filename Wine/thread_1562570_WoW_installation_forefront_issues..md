---
title: "WoW installation forefront issues."
date: 2010-08-27
forum: Wine
---

### Post by mspuke on 2010-08-27
Before I even get into the wine version and EULA agreement issues I may or may not run into, I'm having a problem that I've yet to see any available help for. 

I have wine installed. When I stick the WoW dvd in the drive, both the desktop and .wine versions are only available in the Mac OSX install version. Yes, I've used the terminal to try and mount my drive in case any invisible EXE's would pop up, to no avail. 

I actually did receive an error in trying to mount the dvd manually. 

I'm a little new to this. 

Any ideas?

---

### Post by mspuke on 2010-08-27
No help? I was thinking maybe the mount command isn't functioning correctly. I used the whole sudo umount /dev/cdrom command, and then another unhide media/cdrom command to do it. 

The first command asked for my password and did nothing but remove the cd icon from my desktop and the other one just popped up a bunch of mounting information. I for some reason just can't get the windows version of the installer .exe to pop up. :/

---

### Post by mspuke on 2010-08-27
Welp. I fixed this problem by myself. If anyone else is having similar annoying issues with the correct installer being there when you put the cd in; i had to use a different code than most the guides i looked at provided to mount the iso.

 sudo mount -o remount,unhide /dev/cdrom

is what I ended up using. I simply put the dvd in, used that code to mount and
reopened the cd file and all was there! Thanks for all the help guys.

---

### Post by cwwilson721 on 2010-08-28
The original thing you were instructed to 'type in' at the terminal ("cli") probably would have worked perfectly fine if you UNMOUNTED THE DISK FIRST.

It's a common mistake

---

