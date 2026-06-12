---
title: "Display problem with s-video out shows messed up screen, looks like woven cloth"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-04-04
Green, red,white, blacks looks like weave of cloth screen on a TV.
Boots with bios text perfect.
x1300 pro ATI card.

About 20 times I was in display properties and one time on mirroring screens, it worked. Lost that on a reboot.
So it can work and should work but does not work.

It does work all the time in windows 7, so its a bug not the hardware.

Any way I can force it to play nice?

---

### Post by sdowney717 on 2014-04-04
took a camera picture to show the small monitor playing me-tv with no ability to change channles and the crt tv showing cloth look

It did work one time in ubuntu, miraculous  I think.

I am bumping into 2 major usability issues, cant change channels, cant watch TV. So unless both get fixed, it is back to windows for this PC, or maybe I could try 13.10 Saucy instead.

---

### Post by frank18 on 2014-04-04
> **sdowney717 said:**
> took a camera picture to show the small monitor playing me-tv with no ability to change channles and the crt tv showing cloth look

It did work one time in ubuntu, miraculous  I think.

I am bumping into 2 major usability issues, cant change channels, cant watch TV. So unless both get fixed, it is back to windows for this PC, or maybe I could try 13.10 Saucy instead.

Did you change the display resolution to 800x760!

---

### Post by sdowney717 on 2014-04-04
> **frank18 said:**
> Did you change the display resolution to 800x760!

no, all I did was use the Displays gui and set to 1024 by 768.

I found this page that fixed it for now. I tried some suggested commands which did not work,

But this did work,
scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 800x600 

scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x758600 
^[[3~xrandr: cannot find mode "1024x758600"

scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x758 
xrandr: cannot find mode "1024x758"

scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x768 
scottmsi478@scottmsi478-desktop:~$ 

Now I have a good picture on the TV
So what is wrong with the Displays gui and svideo?

[http://www.kirsle.net/blog/kirsle/linux-s-video-nightmares](http://www.kirsle.net/blog/kirsle/linux-s-video-nightmares)

```
scottmsi478@scottmsi478-desktop:~$ xrandr --output S-video --set load_detection 1
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  31
  Current serial number in output stream:  31
scottmsi478@scottmsi478-desktop:~$ xrandr --output S-video --set tv_standard ntsc
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  31
  Current serial number in output stream:  31
scottmsi478@scottmsi478-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+   75.1     70.1  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
S-video connected 1024x768+1024+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       59.9* 
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 800x600 
scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x758600 
^[[3~xrandr: cannot find mode "1024x758600"
scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x758 
xrandr: cannot find mode "1024x758"
scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x768 
scottmsi478@scottmsi478-desktop:~$ 

```

---

### Post by sdowney717 on 2014-04-04
Here is picture to prove it is now working on svideo TV

But why cant Display gui make it work and commandline can make it work?
Bug?!
Probably, lately everything seems to be buggy, even windows 7.

Will it stick on a reboot, does ubuntu still use xorg.conf, is there something to do to make this easier for someone who would just want to use this to watch TV?
Will It need some kind of boot script to run to execute this commandline xrandr?

I still have the me-tv weird no can change channels, no can view guide problem.

---

### Post by sdowney717 on 2014-04-04
I wonder if Diplays gui is setting the svideo TV out to some unsupported parameter so the TV goes woven cloth look.
The little monitor is set to 1024 by 768, which is native.
All I did was select mirror the displays, then got the messed up screen.

Then when I ran

scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 800x600 

A proper 800 by 600 image appeared on TV

Then when I ran 

scottmsi478@scottmsi478-desktop:~$ xrandr --addmode S-video 1024x768 

A proper 1024 by 768 image appeared on TV
I would mark it solved, but I dont feel it is solved, the Displays gui should have worked.

---

### Post by sdowney717 on 2014-04-04
Still a bug, not working again on reboot.

And this time running xrandr command in terminal did not fix the TV out, messed up screen.

But at least I was able to show you it CAN work.

So I have no idea what to do anymore with it.

Bugs are depressing, and I wonder about things like this which few people will use ever being made right.

---

### Post by 23dornot23d on 2014-04-04
Have you tried using arandr

I tend to use it on one of my displays as it creates a small script that I just double click after going  into the desktop to get my second monitor set
which is a 32" flat screen TV ..... but for some reason it never seems to pick up properly on one system I use.

So using arandr script which is generated by clicking to save it then on the (open button) I know open means save on this program ( odd )

[ it will normally save the file into .screenlayout - but just by changing it to point to the Desktop to save it - gives you the script to double click
   when you need to change resolution - or monitor positions left to right should they not start up in the correct places at login. ] 

[B]sudo apt-get install arandr

arandr[/B]

---

### Post by sdowney717 on 2014-04-04
I installed it and it did not help.

I just went back to displays, and mirrored and it is working.
But it is buggy because it works when it wants to work, not when I want it to work.

I looked and see no xorg.conf, would it help to have one?

A TV has no edid when using svideo, maybe xorg is getting confused.

---

### Post by 23dornot23d on 2014-04-04
> 
I looked and see no xorg.conf, would it help to have one?


I only ever use the xorg.conf when I have a Nvidia driver loaded .... which it will then help with .....

---

### Post by sdowney717 on 2014-04-04
logged out and it is borked again :(

I guess I cant use Ubuntu for this as an HTPC, have to stick with windows 7.

When you want to watch TV, you dont want to have to do a lot of troubleshooting every time.

---

### Post by 23dornot23d on 2014-04-04
Can you give us a screenshot of arandr running and show us what you see ............

is it just - Default

or

is it something like - HDMI

or something different ?

I have tried two versions - 32 bit Ubuntu shows Default .......... and I cannot do a lot with this setup

But the 64 bit Ubuntu shows LVD and HDMI ........ this I can use and do things with like swapping screens from side to side
and changing more things ......... guess its how the computer picks up the TV edid though and I do not know what instructions
will now give you that information ..........

I can do it on my other setup using the Nvidia programs ...... 

only seems to work on older versions of ubuntu ...... (nvidia-xconfig ? has it been removed now)

**/usr/lib/nvidia-current/bin/nvidia-xconfig --query-gpu-info --nvidia-cfg-path=/usr/lib/nvidia-current**


```

  Number of GPUs: 1
  
  GPU #0:
    Name      : GeForce 9300M GS
    PCI BusID : PCI:1:0:0
  
    Number of Display Devices: 3
  
    Display Device 0 (CRT-0):
       EDID Name             : LG W1946
       Minimum HorizSync     : 30.000 kHz
       Maximum HorizSync     : 61.000 kHz
       Minimum VertRefresh   : 56 Hz
       Maximum VertRefresh   : 75 Hz
       Maximum PixelClock    : 90.000 MHz
       Maximum Width         : 1360 pixels
       Maximum Height        : 768 pixels
       Preferred Width       : 1360 pixels
       Preferred Height      : 768 pixels
       Preferred VertRefresh : 60 Hz
       Physical Width        : 410 mm
       Physical Height       : 230 mm

Display Device 1 (DFP-0):
     EDID Name             : AUO
     Minimum HorizSync     : 54.715 kHz
     Maximum HorizSync     : 54.715 kHz
     Minimum VertRefresh   : 60 Hz
     Maximum VertRefresh   : 60 Hz
     Maximum PixelClock    : 96.300 MHz
     Maximum Width         : 1440 pixels
     Maximum Height        : 900 pixels
     Preferred Width       : 1440 pixels
     Preferred Height      : 900 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 370 mm
     Physical Height       : 230 mm 				 			

Display Device 2 (DFP-1):
     EDID Name             : ORN ORION
     Minimum HorizSync     : 14.000 kHz
     Maximum HorizSync     : 46.000 kHz
     Minimum VertRefresh   : 47 Hz
     Maximum VertRefresh   : 61 Hz
     Maximum PixelClock    : 80.000 MHz
     Maximum Width         : 1920 pixels
     Maximum Height        : 1080 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 720 pixels
     Preferred VertRefresh : 50 Hz
     Physical Width        : 160 mm
     Physical Height       : 90 mm 


```

---

### Post by sdowney717 on 2014-04-04
shows default and yes it is 32 bit.
That program looks to be similar to displays under settings.

The TV wont have any EDID data, it is a CRT TV.
This is in an upstairs room next to my regular ubuntu pc. 
I put together some old parts to make another HTPC on the very cheap.
Since this is a pentium 4 3.2ghz 478 socket AGP system with 2gb ddr, it wont be a screamer, but it works ok for watching live TV using a PCI tuner, recording, and watching recorded TV from the other HTPC downstairs off the LAN. It works well in win7 running WMC.

I did go ahead and upgrade the video card from an x1300 pro to a HD 2600 pro and have not tried it again with ubuntu.

---

### Post by 23dornot23d on 2014-04-04
> 
That program looks to be similar to displays under settings.


It is - but it allows a auto script to be generated that will run by double clicking it .......... I find this quite useful.

I used to just put a script in .config/autostart/

but that only gives me one choice.

The way I have mine set up now - is to keep 3 scripts in a folder for screen settings on the desktop.

one for 1366 for the laptop
one for 1280 for the TV

and 1280-1366 ..... which sets them up one alongside the other in the correct places.

So it works out ok for mine now on my night time set up ..... which is the one I tend to use the most ......... so I am happy
and that is also the 64 bit one as main OS ........ but I can switch and choose to many OS's on a external usb SSD

I found Knoppix 7.0.5 does the same thing but it actually runs the cube and compiz brilliantly from install ..........

But I still have to use arandr to generate the same scripts that I need ......... and it too works well.

+++++++++++++++++++++++++++++++++++

Maybe one day some tabs on the top of the screen will appear ......... that we just have to click on to choose monitors.

But until that time it seems like user made scripts are the only solution ........ ( that I have found so far that work )

---

### Post by sdowney717 on 2014-04-05
well, putting in the better video card HD 2600 PRO and it works on svideo.
Came up immediately on booting ubuntu.
Worked on login and log out.

I have read that the x1300 pro is fully supported in ubuntu with the free driver, but I dont think so, it is not perfect.
The card is older, but works in win7, so I lean towards a software bug in the driver.

---

### Post by 23dornot23d on 2014-04-05
Good to see you found a solution ..... thats the main thing ..... often many options to get the results we need nowadays.

---

