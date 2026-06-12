---
title: "Wine Mess"
date: 2011-05-20
forum: Wine
---

### Post by Xalltar on 2011-05-20
Hello all ...

I gotta little problem here.
I've tryed to install Wine to lauch programs I need such as MS Office for Visio, or Eagle and so one ...
BUT, PowerPoint for exemple just doesn't launch himself. Nothing happens ...

And I got some graphical glitches in Word (such as a Black Menu Bar) ... can't fix that.

I've reinstalled many times and i'm getting tired of that.
Is wine a good, working solution ?
Is it normal those bugs ?

Is a virtual machine a better solution ? In so far as I have also W7 installed on my computer but I'm willing to go on full Ubuntu asap ...

Well, if anybody has any clue it would be very kind of him :)

---

### Post by dniMretsaM on 2011-05-20
What version of MS Office? I know that '07 seems to work well, not sure about 2010 or 2003.

---

### Post by Elfy on 2011-05-20
Thread moved to Wine.

---

### Post by Xalltar on 2011-05-20
Thx for moving and sorry btw ...

Hum ... i'm using 2007 ... shall I try 2010 ?

Wine has installed a lot of stuff in the "installed programs section". I can't remove them (nothing happends). How can I purge ONLY the MS Office stuff ?

---

### Post by bobwyajnr on 2011-05-20
> **Xalltar said:**
> Thx for moving and sorry btw ...

Hum ... i'm using 2007 ... shall I try 2010 ?

Wine has installed a lot of stuff in the "installed programs section". I can't remove them (nothing happends). How can I purge ONLY the MS Office stuff ?

If you using the default WINEPREFIX (sounds like you are :P). If you want to completely delete all the programs you installed in WINE type:
```

rm -Rf ~/.wine
mkdir ~/.wine

```
If on the other-hand you want to selectively delete programs you have installed in wine type:
```

wine uninstaller

```
or launch this app from your main (Gnome) menu.

It sounds like you are new to Ubuntu :D I would recommend installing Windows in VirtualBox. There are guides to doing this in the [Ubuntu Community: VirtualBox documentation]("https://help.ubuntu.com/community/VirtualBox") and also [COLOR="Orange"]Bing[/COLOR]):P may find some for you!!

I am afraid WINE also tends to scatter Windows program icons and program shortcuts all over the main Linux filesystem (outside the "Windows filesystem" it creates in each WINEPREFIX). You can delete the menu entries and desktop shortcuts by hand if you want.

I would recommend heading over to [WineHQ]("http://www.winehq.org/") and reading the documentation in there. [Wine FAQ]("http://wiki.winehq.org/FAQ") and [Wine user guide]("http://www.winehq.org/documentation").

To be comfortable using WINE you need to be a fairly confident UNIX user - who is not afraid of a BASH shell (and knows what a BASH shell is!) Getting Windows applications to run - in WINE - can take a lot of perseverance. It's worth getting familar with though. Applications run in WINE are decorated by your Window manager (KVM, Gnome or Unity) and have direct access to the native Linux file-system - so they are much better integrated with your native Linux applications then say a Virtual Machine run application...

Sounds to me like you're rushing a move from Windows to a Linux distro. You might be better running a newbie friendly variant of Ubuntu ([Linux-Mint]("http://www.linuxmint.com/") or [Zoran OS]("http://zorin-os.com/")) in a Virtual Machine on Windows 7 (VirtualBox is cross-platform and will work on Windows 7). This would give you time to get familiar with using a Linux-based OS.

Sorry for rambling on. Hopefully I've pointed you in the right direction. :popcorn:

Bob

---

### Post by Mr. Shannon on 2011-05-20
If you have trouble figuring out wine (like I did) then you can use **Play On Linux**, a front end to wine that makes installing some programs very easy (including MS Office).  I used it on 10.10 and it worked pretty well.  I did not try PowerPoint though.  Now I just use LibreOffice and on very rare occasion a virtual machine.

A virtual machine will definitely give you less hassles but you will need a real windows disk with a valid licence (recovery disks probably won't work), you will have to boot it up when you wan't to use it, and a Windows XP virtual machine with updates and Office installed runs me a little over 11 gigabytes.  So a virtual machine is less convenient, but it will probably work better than wine.

---

