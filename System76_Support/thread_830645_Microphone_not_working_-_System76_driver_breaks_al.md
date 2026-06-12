---
title: "Microphone not working - System76 driver breaks alsa-source"
date: 2008-06-16
forum: System76 Support
---

### Post by vjones777 on 2008-06-16
A while ago my external microphone stopped working on my laptop.  When I first received the laptop the external mic wouldn't work - it was fixed by reinstalling the system76 driver.  Hoping the same would work again, but instead, after rebooting, the package manager showed an error - alsa-source (Installed and latest versions shown as 1.0.15rc3-ldd1).  At the time the system76 driver was 2.2.0.
So, I marked alsa-source for complete removal - rebooted without errors.  I updated all packages, including syst76 driver and rebooted again for the fun of it.  Then re-ran the syst76 driver and rebooted.  Then I get the alsa-source error again.

Volume control shows 'HDA Intel (Alsa mixer)'.  The playback tab shows Master and PCM but the only Capture device is 'capture'.  If I use volume control - File- change device to go to 'Generic 14f1 ID 5054 (OSS Mixer)', the playback tab shows 'Volume' and 'In-gain', but no capture tab is displayed.

I'm testing the mic with Sound-recorder 2.14.2 - record from input 'capture'.

Any ideas?

laptop Gazv2
Celeron M CPU 410@1
Driver is shown as v2.2.1 in system76 driver installer- about
	(yet, looking the changelog in /opt/system76/system76-driver/src, it shows 2.2.2.)
Ubuntu 6.06LTS (yes, I know its not the latest LTS)
Gnome 2.14.3
incidenly, the repository shows alsa-source of 1.0.10-4Ubuntu4)

---

### Post by thomasaaron on 2008-06-16
Double-click your speaker icon. In the resulting window, go to Edit > Preferences and make sure all of the checkboxes are selected. That should give you more sliders.

---

### Post by vjones777 on 2008-06-16
Afraid not.  All of the selections there are already selected.

---

### Post by thomasaaron on 2008-06-17
I apologize, but after re-reading your first post, I'm pretty confused.

Do you still get an error? And what exactly does it say?
What version of ALSA are you now on?
Have you tried reverting to a previous version of the System76 driver?

---

### Post by vjones777 on 2008-06-19
Sorry, I re-read that and yes, it wasn't clear.
There are really two issues:
1) The driver breaks alsa-source.  
2) The mic's not working.

1. That's described ok in the original post - every time I install the driver it breaks alsa-source.

2. I didn't specify that after I verified the driver breaking Alsa, I cleaned up again by using Synaptic package manager to completely remove then reinstall Alsa-source.  Sorry for not stating that.

Some other things I've checked are:

The 'capture' volume level is set to max.  Gnome Alsa mixer also shows the same thing - only Master, PCM and capture sliders for Generic 14f1 ID 5045, no mic slider.  Same for alsamixer and alsamixergui.

Sound-recorder is still not picking up anything.  I've also tried gnusound with the same result.

alsa-source is 1.0.10-4Ubuntu4 - I've attached a screenshot for all the other alsa components.
The system76 driver installer- about shows v2.2.1

I think the problem is theres no 'mic' device shown, which I'm pretty sure I used to have when it was working.

---

### Post by vjones777 on 2008-06-28
BUMP.

I'm still having this problem.  Any suggestions on things to try?  Do you need me to check anything, sent logfiles etc.?

---

### Post by thomasaaron on 2008-06-30
This may have been caused by a problem in the sound module of the 2.2.1 System76 driver. Please remove alsa-source and run the following commands:

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.2.0.deb](http://planet76.com/repositories/system76-driver-2.2.0.deb)
sudo dpkg -i system76-driver-2.2.0.deb

Then go to System > Administration > System 76 Driver
Click the install tab and the install button.

Reboot your computer.

---

### Post by vjones777 on 2008-07-01
OK, just tried that.  After rebooting the volume control still only shows 3 devices (Master, PCM and capture) if 'HDA Intel (Alsa mixer)' is selected.  If the 'Generic 14f1 ID 5045 (OSS mixer)' is selected, I just get two items on the playback tab - Volume and In-gain - there's no capture tab.

The sytem76 driver seemed to be changed as its now reported as 2.2.0.

Synaptic shows alsa-source as broken - installed=latest=1.0.15rc3-ldd1
:(

---

### Post by thomasaaron on 2008-07-01
I'm just not sure.

I'll image a GazV2 with Dapper and run the driver to see what happens.
(Hope I can still remember how Dapper works! [-o<

---

### Post by vjones777 on 2008-07-03
Just for the heck of it, I tried rolling back the driver to 2.0.5 - I followed all of the steps in your previous post again, except I used version 2.0.5. instead.
This time it worked !!   :D

I havn't tried to (and don't intend to) reinstall alsa-source - hopefully no other dependency will require it.

Thanks for all your help.

Vic.

Incidently, the volume control now shows 3 output devices under HDA Intel (Alsa mixer) - Headphone, PCM and speaker.  It still shows just the one 'Capture' under the Capture tab.
(If I change the device under volume control to 'Conexant ID 5045' it shows 2 playback devices: PCM-2 & In-gain.  No capture device shown.  Surprisingly, Sound recorder still works even if I have the Conexant selected).

---

