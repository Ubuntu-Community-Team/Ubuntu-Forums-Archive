---
title: "Jumpy Pen behavior on Toshiba Portege M700"
date: 2010-07-18
forum: Ubuntu Studio
---

### Post by BackBONE7 on 2010-07-18
Hi,  i hope i´m in the right Section. I´m using Ubuntu Studio (32bit) but this post is all about Penabled Wacom & Xinput and alike.

... this is kinda like a dual purpose post. It can help the unexperienced user to get the Pen Buttons on his M700 right, and it can help me to get rid of a little annoying glitch (if hopefully anyone has an Answer) 

There are 2 OS on my Toshiba Portege M700. The M700 was shipped with Vista witch i really don´t like, so i downgraded to XP. Thats because i didn't had the best experience with VST´s under Wine + Wineasio.
Ubuntu beats windows when it comes to GFX. Blender Runs about 3 times faster then it does on XP. And Mypaint and Gimp are easy to obtain via Synaptic..

Now here is the part where it gets interesting to you guys out there. While on XP all most nothing worked out of the box, Ubuntu just did it like it was meant to run solely on this machine. On XP not even the Internet worked (had to download the driver form Linux to make it work).
The only Part that was a little bit screwed was the Buttons on the Pen ( no right-click), and the Display Buttons don´t work at all. The touch-screen worked like a charm.

Since Ubuntu Studio don´t have a Xorg.conf, i decided to do it a little bit different. (kinda don´t want to force a Xorg.conf to the system   :))
In a console i found out the Id of the Pen via >**xinput list**<, the Printout showed that the device id of the Pen is 14.
Next i entered >**xinput get-button-map 14**< the buttons are mapped 1 to 32 and we have to switch this a bit.
>**xinput set-button-map 14 1 3 2**< does the trick. Now the button on the Pen acts a the right mouse button, and the eraser as middle click.
Put this line in a Text-File, make it executable and put it into **Startup-Programs **and you good to go. Of course you can add more commands in there, like altering the Pressure Curve and such...

So far so good...
now the annoying part when i draw in Mypaint, sometimes the cursor jumps in the lower left corner for a second, witch leaves a nasty line from where i paint to the corner.
This is really bad. I played with different settings and thought that reducing velocity scaling to 5.000000 helped, but the annoyance keep on coming :mad:

In Gimp pressure sensitivity dos not work.In all other App´s its all good.

Anyone had the same problem and get rid of it? Any ideas?

---

### Post by Favux on 2010-07-18
Hi BackBONE7,

You'd be better off using xsetwacom commands in a script at startup.  What release of Ubuntu are you using?

Doesn't the Toshiba Portege M700 have touch also?  Is that working?  What's the output of 'xsetwacom list'?

In Gimp did you configure the extended input devices?  That should give you pressure.

---

### Post by BackBONE7 on 2010-07-18
Yup, the touch worked out of the box. The only issue is that i can´t manage to get calibration working. The cursor is now always a little bit off. But the offset is the same on the whole screen and i got used to it. I still want to calibrate though.

Gona try xsetwacom now. I let you know what happened....

EDIT: seem to me like its the exact same thing. Can you explain to me why i´m better off this way?

---

### Post by Favux on 2010-07-18
I'm going to guess you're in Lucid (10.4).

A xsetwacom script should allow finer control.  Since Lucid doesn't have wacomcpl (Wacom Control Panel) and its auto-generated xsetwacom script .xinitrc it's the best alternative.  You'd end up with something close to the HP TX2000 one attached below.  We can work on one specific for the M700.

The TX2000 is usb while the M700 is serial, so your touch coordinates may be the same as stylus and eraser.  In serial tablets the signal is multiplexed.  You should be able to find general coordinates in Xorg.0.log in /var/log when the wacom drivers initialize the digitizer and touch screen.

If that doesn't straighten everything out we may need to update xf86-input-wacom.  There have been a lot of additions and fixes to xsetwacom and recently a flurry of fixes for ISD4 serial tablet pc's.

---

### Post by BackBONE7 on 2010-07-18
Nice,

all i needed to do was to change the ID´s to make the script work, however i needed to comment the topx/y and bottomx/y out of the touch section. The given values made the touchscreen unusable.
I tried to get new values out of xinput_calibrator , but it looks like i´m still to new to linux to get the installation right. There is no deb for it, as far as i know.

The annoying jumps to the lower left corner still remain.

---

### Post by Favux on 2010-07-18
Sounding good!  I wonder if the touch screen coordinates are the same as the stylus?

Yeah I downloaded and installed xinput calibrator.  It seems to work but I'm not sure you do much better than the values in Xorg.0.log.  I didn't play with it enough to find out.  I can see if I kept some notes if you really want it.

So you got pressure working in Gimp?

With the jumps it sounds like maybe you need to clone the git.  Up to you.  See II. at the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  One thing to watch out for is I believe the 'Option "ForceDevice" "ISDV4"' is obsolete with the update.  So you might want to first comment it out in 10-wacom.conf.

---

### Post by BackBONE7 on 2010-07-18
Yeah, pressure in Gimp is working. I just had to switch the Pen on in the options.
Its a little hard to use, but it should be good after fiddling with the Pressure curve.

I will take a look at the Bamboo-how-to. There is Probably already the right solution somewhere on the Internet. Just have to find it :D

EDIT: ForceDevice commented out dos not make any difference. I just tried to use the pen from my Wacom Art-Pad, witch worked on the M200,
and it does work on the M700 as well, the Jumpy behavior is the same though.

---

### Post by Favux on 2010-07-18
Your 'xinput --list' along with how you needed to modify the .xsetwacom.sh would help for a M700 version.

---

### Post by BackBONE7 on 2010-07-18
Just cloned the git as suggested, but the Jumps remain.
 

Here is the xinput list:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

```All i modified ws the ID numbers. I changed the Coordinates for stylus and eraser, and commented the Coords for touch out.
```

## Device names and ID numbers from 'xinput --list'.

## stylus = ID 14 = "Wacom ISDv4"
xsetwacom set 14 Suppress "2"  # data trimmed, 1-100
xsetwacom set 14 RawSample "4"  # default is 4, 1-?
xsetwacom set 14 ClickForce "6"  # 1-21
xsetwacom set 14 PressCurve "5 10 90 95" # default is 0,0,100,100
xsetwacom set 14 TPCButton "on"
xsetwacom set 14 Mode "Absolute"  # or Relative
xsetwacom set 14 Button1 "1"  # left mouse click
xsetwacom set 14 Button2 "3"  # right mouse click
xsetwacom set 14 Button3 "2"  # middle mouse click
xsetwacom set 14 topy "61"
xsetwacom set 14 topx "155"
xsetwacom set 14 bottomy "16421"
xsetwacom set 14 bottomx "26252"

## eraser = ID 12 = "Wacom ISDv4 eraser"
xsetwacom set 12 Suppress "2"  # data trimmed, 0-100
xsetwacom set 12 RawSample "4"  #default is 4
xsetwacom set 12 ClickForce "6"  # 1-21
xsetwacom set 12 PressCurve "0 10 90 100" # default is 0,0,100,100
xsetwacom set 12 Mode "Absolute"  # or Relative
xsetwacom set 12 Button1 "1"
xsetwacom set 12 topy "61"
xsetwacom set 12 topx "155"
xsetwacom set 12 bottomy "16421"
xsetwacom set 12 bottomx "26252"

## touch = ID 13 = "Wacom ISDv4 93"
xsetwacom set 13 Touch "on" # default
#xsetwacom set touch Capacity "1" # default ??
xsetwacom set 13 Suppress "2"  # data trimmed, 0-100
xsetwacom set 13 ClickForce "1"  # 1-21, default is 1
xsetwacom set 13 TapTime "250"  # default is 250 ms
xsetwacom set 13 Mode "Absolute"  # or Relative
xsetwacom set 13 Button1 "1"
#xsetwacom set 13 topy "61"
#xsetwacom set 13 topx "155"
#xsetwacom set 13 bottomy "16421"
#xsetwacom set 13 bottomx "26252"

## Developed with daulpavis

```

---

### Post by Favux on 2010-07-18
That's disappointing.  I suppose it's possible it's a bug in My Paint.  You could try reinstalling it.  Or maybe something more esoteric like Gtk+.

OK, that's enough to build a .xsetwacom.sh for the M700.  Thanks.

---

### Post by BackBONE7 on 2010-07-18
Your welcome!

However, it has nothing to do with MyPaint. Same behavior in Gimp.
Probably i have this behavior always, but it only gets obvious while Painting.
Thats the only time this thing leaves a Mark. Whenever the Cursor jumps, it jumps right back to the Pentip.

O.K. i´m done for today. See you next time...

---

### Post by Favux on 2010-07-18
Alright.

Seems to me some serial tablets with touch were having a similar problem with Xournal a while ago.  Solutions was to turn touch off:
```
xsetwacom set 13 Touch "off"
```
If that works you can use a toggle touch script in a launcher.

Attached is a first pass at a M700 .xsetwacom.sh script.  Let me know what you think.

---

### Post by BackBONE7 on 2010-07-20
Now I´m really confused! I tested the new file and for some reason the right mouse button is not working. The only lines that differ from the old file are comments.

About disabling the Touchscreen....
I did that with my first startup script (the one that used xinput) , and put 2 shortcuts on my Desktop, one to turn it off, and one to turn it on. The Jumpy behavior was present.
Now with  xsetwacom everything is a bit unusual. If i just use the console to turn it off, it just does what it suppose to do, turning off the Touch, leaving the rest intact.
I updated my little shortcuts to scripts using xsetwacom, and thats where it got weird,
double Touch on the Icon, turned touch off as wanted, however the Left-Mousebutton cease to exist as well. No leftclick with the Pentip, the Eraser, not even the touchpad. Rightclick remained fine. 
Touch turned off using the console, still does not change the Jumpy pen.

---

### Post by Favux on 2010-07-20
None of that should be happening.  Maybe the ID numbers are changing?  Check in 'xinput --list' and make sure the ID numbers are the same and stay the same with rebooting or hotplugging.  If they don't use the "Device names" with the quotes.

---

### Post by BackBONE7 on 2010-07-20
..... this is one of my proud moments, when I have to admit that i did something stupid.
I didn´t made the new Script executable, thus it never run, therefore the proper Keymaping was never invoked.
What mind me is not that i did this mistake, its that it took me so long to figure it out.
Anyway it was easy to fix, now it works great, except for the Jumps in the lower corner, witch still occur.

---

### Post by Favux on 2010-07-20
Well, last thing to try is to add some debug lines and see if anything informative shows up in Xorg.0.log.  You'd add to the stylus section:
```
xsetwacom set 14 DebugLevel "12"
xsetwacom set 14 CommonDBG "12"
```

---

### Post by BackBONE7 on 2010-08-07
Nothing turned up in the log. ether.

Anyway.... i finally turned my back to Ubuntu Studio for several reasons.
I started to use Ubuntu Studio cause i wanted to make music with it. Seams to me
that it is still to unstable to create an reliable production environment. 

I had trouble with the file-system. Sometimes when i opened a folder, the system froze.
On a folder with about 800 files, it sometimes took more then fife minutes to respond to mouse or keyboard events.

Virtualbox wasn't running, i simply could not get it to work.

No i installed,Ubuntu 10.04 LTS , i got rid of the dual boot madness, and have XP running inside a virtual machine. (for the very few apps that i use, that don't work under Linux, nor under Wine)

Your script works perfect here too. It was just a matter of seconds to make the penbuttons right.
However i have the same trouble with the pen-jumps. It is driving me mad.](*,)
I am starting to think that its the Toshiba hardware.

Since i am not under Ubuntu Studio anymore, i guess you want see me inside this section anymore.;)

---

### Post by Favux on 2010-08-07
Hi BackBONE7,

You're probably right, since you no longer have Ubuntu Studios you might want to start a new post in Hardware and Laptops.  Summing up the info. so far.

Speaking of hardware, I think the M700 has a pretty recent CPU, what is it?  Maybe the number of motion events are overwhelming it?  If so if you change RawSample from the default 4 to 10 or 20, that may help.

Did you remember to update xf86-input-wacom?

---

