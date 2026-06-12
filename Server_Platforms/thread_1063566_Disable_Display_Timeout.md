---
title: "Disable Display Timeout?"
date: 2009-02-08
forum: Server Platforms
---

### Post by kevin11951 on 2009-02-08
On the server edition of ubuntu, the screen will powersave if you dont type anything for a long time, i want to disable this... but how?

---

### Post by ymo on 2009-02-08
This may help (in particular #9 and #14).

> Linux Console Private CSI Sequences
The following sequences are neither ECMA-48 nor native VT102. They are native to the Linux console driver. Colors are in SGR parameters: 0 = black, 1 = red, 2 = green, 3 = brown, 4 = blue, 5 = magenta, 6 = cyan, 7 = white.
ESC [ 1 ; n ] 	Set color n as the underline color
ESC [ 2 ; n ] 	Set color n as the dim color
ESC [ 8 ] 	Make the current color pair the default attributes.
ESC [ 9 ; n ] 	Set screen blank timeout to n minutes.
ESC [ 10 ; n ] 	Set bell frequency in Hz.
ESC [ 11 ; n ] 	Set bell duration in msec.
ESC [ 12 ; n ] 	Bring specified console to the front.
ESC [ 13 ] 	Unblank the screen.
ESC [ 14 ; n ] 	Set the VESA powerdown interval in minutes.
I suspect that setting the duration to zero will achieve what you want.

---

### Post by kevin11951 on 2009-02-08
> **ymo said:**
> This may help (in particular #9 and #14).


I suspect that setting the duration to zero will achieve what you want.

??? what do i do?

---

### Post by tubezninja on 2009-02-08
Actually, I think you're going to want to edit your /etc/console-tools/config file.  Look for this line:

```
BLANK_TIME=30
```


And change the value to 0 for 'never.'

You'll also want to make sure that BLANK_DPMS=off

---

### Post by kevin11951 on 2009-02-08
> **scaredpoet said:**
> Actually, I think you're going to want to edit your /etc/console-tools/config file.  Look for this line:

```
BLANK_TIME=30
```


And change the value to 0 for 'never.'

You'll also want to make sure that BLANK_DPMS=off

i dont have a console-tools folder :confused:?

EDIT: i installed console-tools, and changed the values, we shall see...

---

### Post by ymo on 2009-02-08
Then you probably need to install the console-tools package.

Before doing that you can test the using the CSI sequences I mentioned like this:

echo "^[[9;0]"

where the string inside the quotes is typed

control-v control-[ [ 9 ; 0 ]

Edit: I see you have installed console-tools. Do let us know how it goes.

---

### Post by kevin11951 on 2009-02-08
> **ymo said:**
> Then you probably need to install the console-tools package.

Before doing that you can test the using the CSI sequences I mentioned like this:

echo "^[[9;0]"

where the string inside the quotes is typed

control-v control-[ [ 9 ; 0 ]

Edit: I see you have installed console-tools. Do let us know how it goes.

didnt work :(

---

### Post by KiLaHuRtZ on 2009-12-26
Ever figure this out?  I'm trying to accomplish the same thing...

---

### Post by cleszczak on 2010-06-12
I also had the same problem.  I did some searching on the web and found that by using the setterm command, you can change the powersave and blank settings for the current user.  Unfortunately I noticed that the settings get cleared whenever the server is rebooted.  My solution to that was to add the following lines to the end of the ~/.profile file for the user that normally signs in to the server.

```
setterm -powersave off
setterm -blank 0
```

It's working for me now, even though I'm sure there is a better way to do this.  Since I'm still somewhat of a Ubuntu n00b this is the best I have to offer.

---

### Post by tanturia on 2010-06-29
If the only problem was the computer locking when it times out to the screen saver then you can just go into system>>preferences>>screensaver and un-tick "lock screen when screensaver is active".

There is no need to mess around in the terminal if that was the problem?

---

### Post by Diego318 on 2010-08-03
Hey guys, I'm having this same issue.  I have unchecked every screen timeout and screen saver option in setting/system settings/screen saver/power management.  The screen STILL times out!  It shuts off my TV when im watching a movie; really annoying...

I'm going to try [cleszczak]("http://www.gs1.ubuntuforums.org/member.php?u=1094008")'s suggestion.

---

### Post by ricey155 on 2011-02-18
cheers for the info 

quick search and this did the job thanks

---

### Post by MAFoElffen on 2011-03-31
> **tanturia said:**
> If the only problem was the computer locking when it times out to the screen saver then you can just go into system>>preferences>>screensaver and un-tick "lock screen when screensaver is active".

There is no need to mess around in the terminal if that was the problem?
I'm revisting this--I've been looking for where to change this (what file or command line option)... A search finds a few answers, but confusing for what I and others here are looking for in Ubuntu Server where the attached Monitor blanks out.. So I'm researching this and trying to work this out.

Ubuntu Server 10.10- There is no GUI, so the answer that said go to (the GUI's) "system>preferences>screensaver"... No comment.  

Ubutnu Server graphically Is TTY based.  Even if you install one of the GUI desktops onto it (ubuntu-desktop, kubuntu-desktop, xubuntu-desktop) and boot tty > start the GUI > enable or disable the GUI's screensaver-- after the default timeout, the server's console "will" blank out the screen.

There has to be something set somewhere.  Where someone above said to edit the file /etc/console-tools/config... There is not even a /etc/console-tools directory present, so that is not it.  There is a /etc/console-setup directory, but I do not see a config file in it.

If I log in remotely through ssh, I can enter the terminal "setterm"  commands to turn off the power savings mode and timeout-- in that  terminal session (which is remote), but it still has no effect on the  monitor of the physical machine.

> **cleszczak said:**
> ...Unfortunately I noticed that the settings get cleared whenever the  server is rebooted.  My solution to that was to add the following lines  to the end of the ~/.profile file for the user that normally signs in to  the server.
```
setterm -powersave off
setterm -blank 0
```It's working for me now, even though I'm sure  there is a better way to do this.  Since I'm still somewhat of a Ubuntu  n00b this is the best I have to offer.
Doesn't seem to work. Researching this through the setterm man page, the command
```
setterm -blank [0-60] 
```says it is for virtual terminals... and it does seem to have no effect on the local console session from the command line.

If I enter the command
```
setterm -powresave off 
```at the console command line...frustratingly, does not work.  In fact entering both does nothing.

So... has anyone found where to do this in Server 10.10?

---

### Post by MAFoElffen on 2011-04-01
So all above was tried with failure, But I continued and finally got this to work.

Okay, here goes.

On this "test install" of Ubuntu Server 10.10, I have the Server installed with 3 GUI desktops: ubuntu-desktop, kubuntu-desktop and xubuntu-desktop.  I didn't want to lose my classic server text console.  Yes, the screen powering off was an inconvenience for my tests.  I created a menu item in /etc/grub.d/40_custom to be able to boot into text mode. I went through many areas of configuration files and command line options until I found what I was looking for...

I researched the Grub Linux Kernel boot options and came up with this- I changed my text mode menu item in  /etc/grub.d/40_custom to try out these options:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#
# Menu Items to Start Server in Text Console
#
menuentry 'Ubuntu Server, with Linux 2.6.35-28-generic, Text Console' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f88fbd8a-c917-4f12-b495-7927fa320a2c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=f88fbd8a-c917-4f12-b495-7927fa320a2c ro quiet [COLOR=RoyalBlue]**nosplash apm=off text**[/COLOR]
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu Server, with Linux 2.6.35-22-generic, Text Console' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f88fbd8a-c917-4f12-b495-7927fa320a2c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f88fbd8a-c917-4f12-b495-7927fa320a2c ro quiet [COLOR=RoyalBlue]**nosplash apm=off text**[/COLOR]
    initrd    /boot/initrd.img-2.6.35-22-generic
}
##
##  Menu Entry for TTY Serial Console
##
menuentry 'Ubuntu Server, with Linux 2.6.35-28-generic. Serial Console' --class ubuntu --class gnu-linux --class gnu --# # class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f88fbd8a-c917-4f12-b495-7927fa320a2c
    serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1
    terminal --timeout=30 serial console
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=f88fbd8a-c917-4f12-b495-7927fa320a2c ro quiet splash apm=off console=ttyS0.115200n8 console=tty0
    initrd    /boot/initrd.img-2.6.35-28-generic
}

```Notice the kernel boot line for these 3 kernel boot options:
  [COLOR=RoyalBlue]text[/COLOR]           - you want to use this (instead of  the Single, S, s or -s options, which would boot in a text mode- but in a single user mode...)
  [COLOR=RoyalBlue]nosplash[/COLOR]     - will boot without the splash image
  [COLOR=RoyalBlue]apm=no[/COLOR]     - use this or noapm, either will turm the autopower management off.

Another option not shown here is using "vga=xxx", where modes 264-268 are text modes. 264 (0108h) is 80 columns x 60 rows , 265 (0109h) is 132x25, 266 (010Ah) is 132x43, 267 (010Bh) is 132x50 and 268 (010Ch) is 132x60. The capability of these all depend on your video card and motitor.

And presto-- It now works nice.  For testing, I boot into text mode > Log In.  Powersave Mode is disabled and the monitor stays on.  Then, if I start a GUI:
```

sudo start gdm

```(See [COLOR=YellowGreen][COLOR=SeaGreen]Side Note[/COLOR][COLOR=Black] below[/COLOR][/COLOR]) Then it goes to the GUI's graphical logon, with all three GUI's as a dropdown option to control which one to boot into.  What happened before was that the monitor went into powersave mode even if the screensaver was configured not to go into powersave mode and still powered down before or after  any of the gui screensavers ever went on... Now it plays nice, powersave is disabled and screensavers work correctly.

Exiting out of the GUI is done by opening up a terminal and:
```

sudo stop gdm

```(See [COLOR=SeaGreen]Side Note[/COLOR] below)Which them shuts down the GUI without shutting down the server-- getting me back the the text console.

[COLOR=YellowGreen][COLOR=SeaGreen]Side Note[COLOR=Black]-[/COLOR][/COLOR]:[/COLOR] Starting and stopping the GDM in the past was done from the commandline via
```
sudo /etc/init.d/gdm start  
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart

```but "changes" seem to have caused problems with this now.  Doing this now brings up errors referring to upstart changes.  What does seem to work now is:
```

sudo start gdm
sudo stop gdm
sudo restart gdm

```

---

### Post by MAFoElffen on 2011-04-08
Had this worked out for bersion 10.10, but-->  This now re-openned and not solved for Ubuntu Server Natty 11.04beta1!  ](*,)

Maybe this might be worked out for the RC, but I guess we'll see.

---

