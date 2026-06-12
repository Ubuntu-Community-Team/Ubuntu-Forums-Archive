---
title: "Sun Blade 2500 red...no beep at start up...fans run forever"
date: 2008-04-09
forum: Sun Sparc Users
---

### Post by Verdin on 2008-04-09
Hello there,

I got this machine, as my workplace was replacing the workstations with Window machines.

It has a Tritec DG-2 graphics card.  I was initially able to install Ubuntu server edition for SPARC then I did the apt-get to add Kubuntu.  I could never get anything to display on the screen when I did startx.

I tried to do some testing using Suns manual for this machine and now when I boot it up the fans run at full blast and nothing displays on my monitor...I can't even get the OK with Stop-A.

I assume it's something wrong with it's booting in OpenBOOT but I don't know what.

Any suggestions?

---

### Post by mecki on 2008-04-11
Hello

How long did you wait. I don't know about the blades, but my enterprise takes up to 5 min until anything happens.

If still nothing works then try if you get another nvram

three years ago I used a Ultra 30 and when the rtc battery was empty, nothing worked at all. unfortunately you can't change batteries you have to change the nvram.

good luck
mecki

---

### Post by PointyWombat on 2008-04-11
Even without system disks you should be able to get to the OBP. Power on the box while holding down Stop-N and hold for a few seconds until keyboard lights flash. This will reset NVRAM contents to their default values. On second though, this being a Blade, it has a USB keyboard so in that case, power on the system, and wait until you see the keyboard lights flash and you hear a beep then hit the power button twice quickly.

For a blade 2500, you shouldn't have to wait for more than 15 seconds for OpenBoot message on the display.

---

### Post by Verdin on 2008-04-11
Well, I let it run for about 1 hour again and finally got some stuff on the monitor.  I think it was taking a long time because I set it to run some diagnostics.

I don't think Ctrl+N works on USB keyboard.

I'll start a new post for my other issues.

thanks

---

### Post by PointyWombat on 2008-04-11
Yeah, Stop-N should work, but there maybe more to it. You should connect a serial terminal to the serial port. There may be info going to the console via tty instead of the display. I don't think that anything should take an hour, even it diag-level is set to max. if you finally get to OBP, you should reset it to defaults (type 'set-defaults' at the OK prompt).

---

### Post by Verdin on 2008-04-13
Anyone know of a graphics card that will run with this machine?  (Sun Blade 2500 red)  I just bought a EVGA e-GeForce 6200 card and put it in and get the same thing as before....computer just runs with all the fans going and never beeps.  Stop+A/Stop+N don't work.  I put the old card back in and can again get to the server command line.

This card is Nvidia chipset which is supposed to work with Ubuntu but I guess not with UltraSPARC.  I can't find any 64bit graphics cards except for one from Sun for $300.  Maybe I should just throw this thing in the garbage.

---

### Post by PointyWombat on 2008-04-14
Wanna sell it?

---

### Post by Verdin on 2008-04-14
I've given up on Ubuntu since I can't find a driver for this card and gone back to Solaris 10, however pkgadd just gives me errors when I try to install the drivers.

---

### Post by PointyWombat on 2008-04-14
Drivers for what? What video card is in that 2500? It's likely an XVR-100, 500, 600, or 1200. I doubt anything else will work, other than maybe standard vga for basic console. Which pkg gave an error?

---

### Post by Verdin on 2008-04-14
It's a Tritec DG-2 card.  This used to be a Siemens workstation.  Our company had a bunch of them with this graphics card in it.  I'd like to get a Sun graphics card but they are $300 and up on Suns website.

I downloaded the drivers from the Tritec website:
[http://www.tritec.de/index.php?id=0031&idsub=2&skat=Graphiccards]("http://www.tritec.de/index.php?id=0031&idsub=2&skat=Graphiccards")
  
I also followed their directions for installing the drivers:

"7. Select the directory of your Solaris version and use the pkgadd command to install the driver package.
# cd Solaris_2.7
# pkgadd -d . TRTCdg2.u TRTCdg2w TRTCdg2cf
8. Reboot"

I just get:
pkgadd: ERROR: no package associated with <trtcdg2.u>

I emailed them last night and they responded that I should unpack the zip folder on Solaris instead of unpacking it on Windows and burning it to CD.  I'd like to just wget it from the Tritec website then unpack it on the Sun machine but I can't get wget to work even though it's on the machine.

---

