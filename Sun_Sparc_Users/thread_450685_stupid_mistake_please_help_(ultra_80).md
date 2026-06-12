---
title: "stupid mistake please help (ultra 80)"
date: 2007-05-21
forum: Sun Sparc Users
---

### Post by didijeeeke on 2007-05-21
Hey ,

I did make a stupid mistake in the bios settings of my sun ultra 80.
I did try to change the default video card... but it did not work.
I get no screen anymore at all.

I tried to remove the cards one at the time.

I did search inside for a battery or cmos reset switch but could not find one.

Pleas help.

---

### Post by daller on 2007-05-21
Take out the backup/CMOS battery, and wait for about 5 minutes, and put it back in! - It will erase any user settings, and revert to factory default!

---

### Post by didijeeeke on 2007-05-21
well thanks for your resonse but like said it is a sun system.
It has not battery or cmos reset switch

---

### Post by hartz on 2007-05-22
> **didijeeeke said:**
> Hey ,

I did make a stupid mistake in the bios settings of my sun ultra 80.
I did try to change the default video card... but it did not work.
I get no screen anymore at all.

I tried to remove the cards one at the time.

I did search inside for a battery or cmos reset switch but could not find one.

Pleas help.

If the keyboard is active you can use STOP-N to reset the OBP defaults.

If the keybaord is not working you can try this:
Power-off, then power-on.  When the diag LED starts to flash, press and hold the power button for a few seconds (I think 3 seconds)
Note: The key must not be in DIAGS or LOCK position for this to work.

If this does not work:
Remove the Graphics card to force it back to Serial TTY.
Connect a Serial-cross-over cable from the Management port to the serial port on another machine.
depending on what the "other" machine is;
Windows: Use "Hyperterminal"
Linux: Use "gkermit" or similar
Solaris: use "tip"

The settings on the serial port is 9600, No Parity, 8 bits.

Once you get a connection, send a break to get to the OBP.  The enter 
```
set-defaults
reset-all
```

---

### Post by didijeeeke on 2007-05-23
> **hartz said:**
> If the keyboard is active you can use STOP-N to reset the OBP defaults.

If the keybaord is not working you can try this:
Power-off, then power-on.  When the diag LED starts to flash, press and hold the power button for a few seconds (I think 3 seconds)
Note: The key must not be in DIAGS or LOCK position for this to work.

If this does not work:
Remove the Graphics card to force it back to Serial TTY.
Connect a Serial-cross-over cable from the Management port to the serial port on another machine.
depending on what the "other" machine is;
Windows: Use "Hyperterminal"
Linux: Use "gkermit" or similar
Solaris: use "tip"

The settings on the serial port is 9600, No Parity, 8 bits.

Once you get a connection, send a break to get to the OBP.  The enter 
```
set-defaults
reset-all
```

Sry your help was very good explained but i still have some questions.

I want to try the serial connection but i wil need to solder a cable or buy one.
So my question is: Is the terminal connection always active or do you need to activate it first in openboot.

I am getting realy scared i tried lot's of time stop - D and power button  but nothing works
I hope did not brick my sun :( 

O and is it possible you need to press a confirm key when pressed stop -D
I don't see any screen so mayby that's why stop d isen't working

---

### Post by hartz on 2007-05-23
You did NOT brick your sun.  You CAN recover from this.

**Unplug the keyboard**.  This will ensure that the "screen" and "keyboard" devices reset to serial.

Does your Sun have a management card (And SC or an RSC card, with two ports that look like ethernet ports, one marked as <...> and the other marked as 10101 or something like that?)

When you turn on the computer, output is immediately on the serial and/or management card first.  If you set the OBP input-device to something else, it will try to switch, but it will revert to serial if it is unable to switch.

Remember that Suns sometimes use Male DB25 connectors on the serial cable - I can't remember what the Ultra 80 has got.

---

### Post by didijeeeke on 2007-05-26
ok i found the solution.

I unplugged the nvram and started the sun without nvram.
Later i putted the Nvram again and decided to do the stop + N trick

but you need to do the stop + N like this 

you press stop + N 5 seconds before you start the system
after 5 seconds poweronn the sysem ( i had to use my feet lol  :p)
Then hold stop + n until the openboot apears an d that worked

but somehow before i removed the Nvram and plugged it back in it did not work.

Thanks for your help this sun is such a nice machine.

Now i only need to get X window system working.

---

### Post by deserthowler on 2007-05-27
What kind of monitor are you using?  What kind of video card?  I had a terrible time getting video to go with Debian Sarge and a mono-sync monitor and a Creator 3D card.  I did get it going.  I'll have to go back and see what I did for sure though if this your problem.

Earl

---

