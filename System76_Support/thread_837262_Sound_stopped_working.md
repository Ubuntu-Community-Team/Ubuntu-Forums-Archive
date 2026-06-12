---
title: "Sound stopped working"
date: 2008-06-22
forum: System76 Support
---

### Post by EmilyRose on 2008-06-22
My sound has mysteriously stopped working - first noted trying to watch youtube videos, but it doesn't work in anything now (tried sound prefernces tests and don't hear a thing). My speakers are turned all the way up, and I checked all the volume controls are turned all the way up, too.

---

### Post by walkeraj on 2008-06-22
Right click on the speaker icon and go to "open volume control".  This should display the gui equivalent of "alsamixer".  Does anything look amiss?

---

### Post by Pethegreat on 2008-06-22
I had a similar problem. It happens every 4th boot. I boot 3 times with full sound. I boot the 4th time, no sound. 

I have a Pangolin Value that I purached in march 2008. I currently am running 8.04(upgraded from 7.10) with all updates.

---

### Post by pauper on 2008-06-23
I could be completely off track, but a few days back there was a kernel update. Try to restore your system configuration via:

System-Administration-System76 Driver-Restore System-Restore

---

### Post by EmilyRose on 2008-06-23
Hmm, this is wierd, sometimes when I reset it fixes it, sometimes not. The first time I load youtube, I *usually* have sound, but then after I try to do another video it won't work... so I have one shot to pick the video I want to watch, then if I want to watch another, I have to reset...

---

### Post by thomasaaron on 2008-06-23
Just tested that here, and I'm not getting those symptoms.
Are you using Hardy, Firefox, and flashplugin-nonfree?

---

### Post by fiartruck0125 on 2008-06-23
My sound stopped working too.

  There used to be about 6 sliders in the volume control now its down to just "pcm" and "master" both of which are up all the way and unmuted with no sound. (I checked Edit->Preferences thats all the controls available)

  I tried OSS but there there's only *one* slider and it still doesn't work.

  I did just do an update, but not a kernel update or anything related to sound, I don't think.

--Thomas Dunlap

---

### Post by thomasaaron on 2008-06-23
firetruck,

Run your System76 driver (System > Administration > System76 Driver).
Then reboot your computer.

---

### Post by thinkmassive on 2008-07-29
I had a similar issue where my sound just suddenly stopped working when I paused a quicktime movie.  I tried restarting X, which somehow made Xfce unable to manage my desktop anymore.  Then I rebooted and that allowed my desktop to work again but the sound was still off.

All volume controls were on, and the media players indicated that clips were playing.  Finally I pressed one of the volume buttons on my ThinkPad and it started working again.  
[img]http://ph.ubuntuforums.com/images/smilies/smiley-faces-75.gif[/img]
Haha, laugh all you want...  I didn't touch the mute button, but somehow it got enabled.  Just a thought.

---

### Post by thomasaaron on 2008-07-29
fiartruck,

If you double-click your speaker icon and (in the resulting window) go to edit > preferences and select all of the checkboxes, you should then have more sliders.

---

### Post by adam.smith on 2008-08-04
> **corerunner said:**
> I had a similar issue where my sound just suddenly stopped working when I paused a quicktime movie.  I tried restarting X, which somehow made Xfce unable to manage my desktop anymore.  Then I rebooted and that allowed my desktop to work again but the sound was still off.

All volume controls were on, and the media players indicated that clips were playing.  Finally I pressed one of the volume buttons on my ThinkPad and it started working again.  
[img]http://ph.ubuntuforums.com/images/smilies/smiley-faces-75.gif[/img]
Haha, laugh all you want...  I didn't touch the mute button, but somehow it got enabled.  Just a thought.
I'm not laughing - after spending 2h debugging my system, reinstalling alsa etc. etc. I just found your post and it saved my day. Exact same issue, also on a thinkpad - might actually be a bug.

---

### Post by mark q on 2008-08-06
Yes, as another Thinkpad user I too have had this issue. It may have originated with an application, in my case this was while using Audacious. However, I feel it may stem from a conflict between the keyboard sound control and that of the desktop control. The sound was effectively muted without the speaker icon or other displays showing it to be the case. Even now muting with the keyboard does not effect the status of the speaker icon, the sound however does mute. This was discovered after a reinstallation of the alsa drivers. Just another quirk or something deeper?

---

### Post by timz84 on 2008-08-25
I had the same problem, using firefox and then no sound in videos or mp3s. This seemed to work for me: I did "sudo /etc/init.d/alsa-utils restart" and then closed and restarted firefox, sound works now.

---

### Post by dzisler on 2008-08-30
I have just updated as of Aug 29 and now have no sound for youtube sites but have sound when playing back CD's or any stored music file. I have no opening or exit sounds and all the minimize (-) or maximize (+) or close icons that should appear in the open windows on the upper right corner are gone.

---

### Post by thomasaaron on 2008-09-01
Try running these commands:

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

---

### Post by Armaron on 2008-09-15
Got the same issue. I use amaroK in the Gnome environment and after I paused the music and wanted it to continue playing, it just gave no sound.

I restarted my alsa-utils, I restarted amaroK, all the volume controls of my sound are turned up and System > Preferences > Sounds is all set on autodetect.

---

### Post by thomasaaron on 2008-09-15
Amaron,

Which System76 model do you have? Did you run the System76 driver and reboot?

Emily's problem has been solved. It was a program for running a modem that conflicted with ALSA.

---

### Post by Armaron on 2008-09-15
> **thomasaaron said:**
> Amaron,

Which System76 model do you have? Did you run the System76 driver and reboot?

Emily's problem has been solved. It was a program for running a modem that conflicted with ALSA.

I don't know what a System76 model is or where I could check the driver.

---

### Post by benjo316 on 2008-09-15
> **Armaron said:**
> I don't know what a System76 model is or where I could check the driver.[http://system76.com/](http://system76.com/)

^
|
"System76 Support"

Are you using a system76 Laptop or Desktop?

---

### Post by thomasaaron on 2008-09-16
This forum is for the support of System76 computers. Did you purchase your computer from System76?

If you did, you can go to System > Administration > System76 Driver and see your model number. In fact, while you are there, click on the Install Tab and Install Button to fix your sound, and then reboot your computer for the drivers to take effect.

If you do not have a System76 computer, we might still be able to point you in the right direction, but we don't have non-System76 computer models in our shop to test with.

---

### Post by phyzome on 2008-09-18
> **thomasaaron said:**
> Run your System76 driver (System > Administration > System76 Driver).
Then reboot your computer.

Even simpler: Spit over your left shoulder, turn clockwise three times, and reboot. It works for me... because rebooting solves the problem (temporarily) by itself. :-/

What is needed is a solid test-case that will cause the "muting". Then this sequence can be followed:
[LIST=1]
[*]Execute proposed solution
[*]Reboot
[*]Run test-case
[*]Check if "muting" has occurred
[/LIST]

(This is not to say installing the System76 driver should not be the first step. I'm just noting that it might appear to "fix" the problem for some people temporarily, even though it's not the actual solution.)

---

### Post by phyzome on 2008-09-18
I've tried the following suggestions (in roughly this order):

[LIST]
[*]Check alsamixer settings
[*]Check Preferences -> Sound settings (Autodetect x 3 and PulseAudio)
[*]killall pulseaudio
[*]sudo /etc/init.d/alsa-utils restart
[*]Uninstall and reinstall flashplugin-nonfree
[*]Install System76 driver
[*]Reboot
[/LIST]

To test these as a group, I have done the following:
[LIST]
[*]Play a YouTube video
[*]Play music in Rhythmbox
[*]Some combination of these in sequence
[*]Some combination of these in parallel
[/LIST]

The test case I have worked out that will cause the muting (at least on my panp4i):
[LIST]
[*]Suspend and close laptop
[*]Open laptop (un-suspends)
[/LIST]

I believe that rebooting after a suspend clears the problem.

I do not think that any of the suggestions I have tried so far have worked as well as a reboot.

---

### Post by thomasaaron on 2008-09-19
Pyhzome,

This thread had been hijacked pretty badly. The original problem, posted by Emily has long been solved. It was a modem program she installed that caused ALSA to fail. So uninstalling the program fixed her computer.

The problem you are describing sounds to me like it might be this...
[https://bugs.launchpad.net/system76/+bug/264516](https://bugs.launchpad.net/system76/+bug/264516)

---

### Post by smaddox on 2010-06-12
> **fiartruck0125 said:**
> My sound stopped working too.

  There used to be about 6 sliders in the volume control now its down to just "pcm" and "master" both of which are up all the way and unmuted with no sound. (I checked Edit->Preferences thats all the controls available)

  I tried OSS but there there's only *one* slider and it still doesn't work.

  I did just do an update, but not a kernel update or anything related to sound, I don't think.

--Thomas Dunlap

Thanks for the tip. This worked for me. Sound stopped working randomly, but just cycling the mute button on my logitech keyboard got the sound working again. Note that before cycling the mute button, none of the indicators showed muted.

---

