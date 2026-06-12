---
title: "Linux kernel 3.2.0-22+23 and Radeon HD6770 dual screen."
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Smask on 2012-04-18
Something changed with 3.2.0-22 because I can't use my secondary display anymore. Dual screen works with 3.2.0-21. (I'll have to run a script to add a mode that fits for my monitor. It's an old VGA LCD screen connected to DVI-1 using an adapter.) but using newer kernels, xrandr says that there is nothing connected to DVI-1.

3.2.0-22, 3.2.0-23 (pae and non pae):
```
lg@lg-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      59.9*+
   1280x1024      85.0     75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       85.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600        85.1     75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-1 disconnected (normal left inverted right x axis y axis)
lg@lg-desktop:~$ 

```The screen works in mirror mode during POST and in the Grub boot menu, then blank until the graphics initializes for the login screen and then off.

3.2.0-21:
```
lg@lg-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      59.9*+
   1280x1024      85.0     75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       85.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600        85.1     75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-1 unknown connection 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   680x384       119.6    119.9  
   576x432       120.1  
   512x384       120.0  
   400x300       120.6  
   320x240       120.1  
   1280x1024x     59.9* 
lg@lg-desktop:~$
```

---

### Post by Smask on 2012-04-19
Bad VGA cable...

Now it even identifies resolution and hardware correctly, Chi Mei Optoelectronics (Video7). No need for xrandr scripts anymore.

So newer kernels than 3.2.0-21 is stricter at hardware identification?

---

### Post by mcellius on 2012-04-19
Arrrrgh!  That's the worst!  It's the easiest sort of problem, yet it's usually only after a lot of frustration that the real problem is identified.  I'm glad you got it fixed and that things are now working well.

---

### Post by buteomont on 2012-04-21
I have the ***_exact_*** same problem, and I never even thought about the cable being the problem until I read your post.  I actually had a VGA extension cable on that display to make the display reach the tower unit, so I moved the tower closer and took off the extension.  Hah! Now Precise Pangolin recognizes my display and puts in the right parameters!  Huzzah!
:guitar:

Now the bad news, it still doesn't allow me to actually *use* the display.  When I view the display parameters they are there now, and are correct.  But the display still goes dark just before the login screen appears, and stays dark thereafter until reboot.  I know the desktop extends to that display because sometimes applications open over there, and I have to use the start-s key combination to be able to move them to the other display.

Did you have to do anything else to get the 2nd screen to work?

---

### Post by Smask on 2012-04-22
Nope, just using the standard screen configuration tool. What does xrandr say?

```
lg@lg-desktop:~$ xrandr
```
Oh, and I forgot to ask what driver do you use? Open source or binary blob?

---

### Post by buteomont on 2012-04-22
I'm using the open source drivers.  I was considering the proprietary ones, but only as a last resort.  If that's the difference between our systems I'll definitely try them though.

```
david@studyHP:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3040 x 900, maximum 8192 x 8192
VGA-0 connected 1440x900+1600+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        75.0     72.8     72.8     66.7     60.0     59.9  
   720x400        70.1  
DVI-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 250mm
   1600x900       60.0*+
   1280x1024      60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  

```

---

### Post by Smask on 2012-04-22
It's the 1440x900 VGA screen, right?

What happens if you try:

```
xrandr--output VGA-0 --mode 1280x800
```Does the screen go active? If so, try to set your video mode in the sceen configurator.
Does the screen go dark again? Then the card uses a timing the screen doesn't like. You'll have to create a new video mode for your display.

---

### Post by buteomont on 2012-04-22
Yes, it's the VGA one.  I tried setting it like you said (and also tried a few of the other modes) but nothing made the screen come back on.

To be clear, during the boot process the screen works fine (as a duplicate of the other one), but when the purple screen disappears they both go black for a few seconds, then the DVI display comes back with the login screen whilst the VGA display says "no input" and goes to sleep with a yellow power LED. The only way to wake it is to reboot again, and the cycle repeats.

I had this working with dual displays under Oneric for a few hours (it's a long sad story) with the binary drivers (even with the bad cable) before installing Precise so I know the hardware is capable.  Maybe I should try the binary drivers; I hesitate because they are a pain to remove completely if they don't fix the problem.

One difference between our systems is that mine has the Radeon HD6530D chips and yours I believe use the HD6770 ones.  Are you using the OSS drivers or the proprietary ones?

---

### Post by Smask on 2012-04-22
6770 on Gallium3D (open source).

Do you have a kernel older than 3.2.0-22 still on the computer? Try boot using that one. 3.2.0-22 and newer are stricter when handling screen hardware.

---

### Post by buteomont on 2012-04-23
No, this is a fresh installation of Precise Pangolin.  

Oh well, I guess I'll give the binary drivers a shot.  Thanks for the help!

---

### Post by buteomont on 2012-04-24
FYI (and anyone else trying to get two displays working on a Radeon graphics display), installing the binary drivers (System Settings -> Additional Drivers) did the trick.  Note that there are two options in there - the only difference between their descriptions is that one has "(post-release updates)" appended to it.  I tried installing that one and it failed; I guess it is JUST the updates, not the driver *with* the updates. Would be nice if it said that.  But installing the other one and rebooting a couple of times enabled the other display.  Since it's working I'm not going to chance installing the other one unless a serious problem shows up!

One other thing I found out (again, why is this such a secret?) is that the regular "displays" application is still in the system settings, but no longer works after installing these drivers.  You have to open a terminal window and enter "sudo amdcccle" to configure the displays after installing the drivers.

Hope this helps someone! ):P

---

