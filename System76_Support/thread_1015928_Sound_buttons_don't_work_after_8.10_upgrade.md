---
title: "Sound buttons don't work after 8.10 upgrade"
date: 2008-12-19
forum: System76 Support
---

### Post by andrewdied on 2008-12-19
I have a serval performance, and recently upgraded from 8.04 to 8.10.  I noticed that my quick-buttons on the laptop for mute and volume up/down no longer work.  I get the gnome popup, showing sound up/down, and mute/unmute, but that isn't tied into the actual sound anymore.

I checked System > Preferences > Keyboard shortcuts, and they are still set for XF86AudioMute, etc.  (screenshot attached)

I have installed / setup compiz, but I didn't see any sound features associated with that.  I don't have a .Xmodmap being loaded, either.

And yes, I moved from XFCE to regl'r gnome.  I like the scale effect with compiz.

Is there somewhere else I should check for what the XF86* shortcuts are hooked in to?

---

### Post by thomasaaron on 2008-12-19
There have been a lot of hosed keymappings with the upgrade from 8.04 to 8.10. Some folks have managed to fix this by going to System > Prefs > Keyboard > Layout and, in the bottom listbox, changing their keyboard type to EvDev-Managed Keyboard.

It doesn't make a whole lot of since to me, but you might want to try it out.

---

### Post by weverjames on 2008-12-19
i thought that buying a laptop from  system 76 would save you from those problems

---

### Post by thomasaaron on 2008-12-19
*sigh*

---

### Post by andrewdied on 2008-12-19
> **thomasaaron said:**
> There have been a lot of hosed keymappings with the upgrade from 8.04 to 8.10. Some folks have managed to fix this by going to System > Prefs > Keyboard > Layout and, in the bottom listbox, changing their keyboard type to EvDev-Managed Keyboard.

It doesn't make a whole lot of since to me, but you might want to try it out.

I just tried that (screenshot attached) but that didn't take.  I also tried logging out and in, but that didn't kick it correct.

As I messed with the keyboard shortcuts, I noticed that the web browser button is now XF86HomePage, rather than XF86WWW.  I have no idea where this is set, but maybe it's part of the problem.

---

### Post by Guille Damke on 2008-12-20
Did you try running the system76 last driver? Probably it works.

---

### Post by andrewdied on 2008-12-20
> **Guille Damke said:**
> Did you try running the system76 last driver? Probably it works.

No, I hadn't done that yet.  I was running 2.2.7, and from looking at the repository I saw that 2.2.9 was available.  I installed that, rebooted, but the sounds keys still don't work, unfortunately.

---

### Post by thomasaaron on 2008-12-22
Andrewdied,

Did you try going to System > Prefs > Keyboard Shortcuts, and assigning the Vol up and Vol down to those buttons? (I re-read the thread, but I'm not quite clear on if you tried that.)

---

### Post by andrewdied on 2008-12-22
> **thomasaaron said:**
> Did you try going to System > Prefs > Keyboard Shortcuts, and assigning the Vol up and Vol down to those buttons? (I re-read the thread, but I'm not quite clear on if you tried that.)

Yup, I did try that.  I went in and reset them in case I hadn't kicked hard enough there before, but am getting the same result.  

One oddity is that in the animation gnome gives you, I'm either at zero, middle, or full on volume.  I'm pretty sure that before the 8.04 to 8.10 upgrade I had more gradients.

---

### Post by thomasaaron on 2008-12-23
I'm not sure what's going on. I'm traveling at the moment and don't have your computer model to test with.

One last thing to try... If that doesn't work, you can either do a clean install or please bump this thread next Monday, and I'll do a more thorough investigation.

Go to System > Prefs > Sound, and make sure all the pull-downs are set to Pulse Audio.

---

### Post by Pobega on 2008-12-23
If you're seeing the GNOME popups it may be raising/lowering the wrong audio channel. Open a terminal and run `alsamixer` to see which channel is actually changing.

If it's not PCM, Front or Main then you should probably look around /etc/acpi/ for your hotkey event files.

---

### Post by andrewdied on 2008-12-24
> **Pobega said:**
> If you're seeing the GNOME popups it may be raising/lowering the wrong audio channel. Open a terminal and run `alsamixer` to see which channel is actually changing.

If it's not PCM, Front or Main then you should probably look around /etc/acpi/ for your hotkey event files.

Ok, I think this is getting on the right track.  Alsamixer didn't show any volume changes for any of the channels.  I looked in /etc/acpi/voldownbtn.sh, and that led me to /usr/share/acpi-support/key-constants.  key-contants had this to say about volume numbers:

```
andrew@bun-bun:/etc/acpi$ grep -i vol /usr/share/acpi-support/key-constants 
KEY_VOLUMEDOWN=114
KEY_VOLUMEUP=115
andrew@bun-bun:/etc/acpi$ grep 176 /usr/share/acpi-support/key-constants 
KEY_EDIT=176
andrew@bun-bun:/etc/acpi$ grep 174 /usr/share/acpi-support/key-constants 
KEY_EXIT=174
andrew@bun-bun:/etc/acpi$ grep 160 /usr/share/acpi-support/key-constants 
KEY_CLOSECD=160

```

I had used an .Xmodmap file for xfce (and am not using it now).  I had completely different keys for the volume:

```

keycode 160 = XF86AudioMute
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume

```

Later I'll try changing the codes in the key-constants file, but not tonight.  Thanks for the tip.

---

### Post by gmh on 2009-01-22
I had the same problem with a Serp 4 and Ubuntu 8.10 upgrade.

sudo gedit /usr/share/acpi-support/key-constants 

Went down the list and changed the values from;

KEY_MUTE=113
KEY_VOLUMEDOWN=114
KEY_VOLUMEUP=115 

to;

KEY_MUTE=160
KEY_VOLUMEDOWN=174
KEY_VOLUMEUP=176

All is now well with the keyboard shortcuts.

Hope this helps anyone with the same problem.

---

### Post by andrewdied on 2009-01-23
> **gmh said:**
> I had the same problem with a Serp 4 and Ubuntu 8.10 upgrade.

sudo gedit /usr/share/acpi-support/key-constants 

Went down the list and changed the values from;

KEY_MUTE=113
KEY_VOLUMEDOWN=114
KEY_VOLUMEUP=115 

to;

KEY_MUTE=160
KEY_VOLUMEDOWN=174
KEY_VOLUMEUP=176

All is now well with the keyboard shortcuts.

Hope this helps anyone with the same problem.

Did you do anything else besides change the values?  I edited the file, rebooted, and even then it the volume & mute didn't change the volume.  I also reset the keys in keyboard shortcuts but that didn't work, either.

Does your volume in the top right look like mine?

---

### Post by Guille Damke on 2009-01-25
Andrewdied,
I think you still have the volume issue. I reread your first post. If you still get the gnome-popup when hitting volume up/down and mute, it means that the keys are mapped correctly, so don't change them or their constants. 
The problem, as some people said before, is in the channel you are changing, I had this problem once.

Go to System>Preferences>Sound, look where it says "Default Mixer Tracks". In "Devices" choose the one that has "alsamixer", in my case: "HDA Intel (Alsa mixer)".
Then, select "Master" from the list that is right below. The instructions for selecting tracks are at the bottom of that window, but you usually want to control "master" with the keyboard volume keys.

---

### Post by gmh on 2009-01-25
Even with the original key-mapping, I still had the gnome pop ups on the screen, they just were never hooked into any channel.I had run into the problem of having the wrong channel set in a previous version of Ubuntu, so that was one of the 1st things I had checked. 
By changing the values in /usr/share/acpi-support/key-constants I got mine up and running and I really only tried it because I had exhausted everything else I could think off.

---

### Post by andrewdied on 2009-01-25
> **Guille Damke said:**
> Andrewdied,
I think you still have the volume issue. I reread your first post. If you still get the gnome-popup when hitting volume up/down and mute, it means that the keys are mapped correctly, so don't change them or their constants. 
The problem, as some people said before, is in the channel you are changing, I had this problem once.

Go to System>Preferences>Sound, look where it says "Default Mixer Tracks". In "Devices" choose the one that has "alsamixer", in my case: "HDA Intel (Alsa mixer)".
Then, select "Master" from the list that is right below. The instructions for selecting tracks are at the bottom of that window, but you usually want to control "master" with the keyboard volume keys.

That was it!  The issue was that I didn't have "Master" selected at the bottom of the dialog in System > Preferences > Sound.  Nothing was selected, actually.  I selected Master and closed the dialog, then the mute and up/down keys worked.  

Pobega had been on the right track, I just couldn't figure out how to hook the "Device" into the "mixer track".  I still don't know what that all really means, but it's working now.  Additionally, the up/down volume goes through much smaller sound increments.  When the volume wasn't hooked into the track all I had was nothing / middle / full.

---

### Post by jprovostla on 2009-02-22
> **gmh said:**
> I had the same problem with a Serp 4 and Ubuntu 8.10 upgrade.

sudo gedit /usr/share/acpi-support/key-constants 

Went down the list and changed the values from;

KEY_MUTE=113
KEY_VOLUMEDOWN=114
KEY_VOLUMEUP=115 

to;

KEY_MUTE=160
KEY_VOLUMEDOWN=174
KEY_VOLUMEUP=176

All is now well with the keyboard shortcuts.

Hope this helps anyone with the same problem.

=======================================================================

if you want to increase the maximum volume on your Ubuntu system, you can increase the same values... 
I first tried the values 180/200/202 and noticed that the maximum volume was much better...
so I tried the values 250/300/302 and the maximum volume increased some more...  
I always thought that the volume was too low on my Ubuntu installation [IBM Thinkpad T61p] but didn't know how to adjust it...

---

### Post by 3Miro on 2009-03-11
At some point when I was trying to fix an issue with skype, I had changed the setting in system -> prefs -> sound. The volume up/down option now worked with the front mic and not my music playback. Further more, when I was trying to close the lid without first hibernating or suspending the system, I got horrible squeaky sound, some interference from the microphone.

Fixing the sound setting fixed all my problems, I hope it helps other people as well.

---

### Post by heavyduty on 2009-07-29
> **Guille Damke said:**
> Andrewdied,
I think you still have the volume issue. I reread your first post. If you still get the gnome-popup when hitting volume up/down and mute, it means that the keys are mapped correctly, so don't change them or their constants. 
The problem, as some people said before, is in the channel you are changing, I had this problem once.

Go to System>Preferences>Sound, look where it says "Default Mixer Tracks". In "Devices" choose the one that has "alsamixer", in my case: "HDA Intel (Alsa mixer)".
Then, select "Master" from the list that is right below. The instructions for selecting tracks are at the bottom of that window, but you usually want to control "master" with the keyboard volume keys.

It fixed my problem. Much obliged!

---

