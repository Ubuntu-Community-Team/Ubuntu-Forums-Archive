---
title: "Stupid Skype / Pulseaudio Fix"
date: 2008-05-11
forum: Tutorials
---

### Post by KillerKiwi on 2008-05-11
Ok this is tested on hardy with standard pulse audio setup, its a bit clunky but I prefer it over dmix hacks.

Create a script 

gedit ~/bin/pause_pulse

```

#!/bin/sh
# temporarily pause pulseaudio so I can use Skype or whatever
pasuspender -- /usr/bin/zenity --info --text "Click OK to resume Pulseaudio"

```

Make it executable 
chmod +x ~/bin/pause_pulse

Ok now setup skype

[LIST]
[*] Fire up skype goto options
[*] Goto notifications tab
[*] Click the advanced view button
[*] Select Incoming ring call
[*] check the "execute script" checkbox
[*] paste in ~/bin/pause_pulse (this might require the full path)
[*] click apply
[*] Select Outgoing ring call
[*] check the "execute script" checkbox
[*] paste in ~/bin/pause_pulse (this might require the full path)
[*] click apply
[/LIST]

That's it.. when a call starts you that will trigger pasuspender.. just click the button to start pulse sound again

It not perfect but I can at least use skype again...

EDIT: Also useful is to make a panel icon that runs the script.. gives you a bit more control

---

### Post by psyke83 on 2008-05-12
Hi there,

Your solution works, but there are disadvantages. PulseAudio will be blocked from using the sound card while your script is active (unless your card supports hardware mixing, perhaps).

It seems Debian have recently fixed some bugs in the "pulse_pcm" driver for ALSA, meaning that Skype can now work correctly with PulseAudio (providing your system is configured correctly). The latest version of Skype is also available in OSS form, meaning that the "padsp" wrapper is an option; both of these solutions work better than using "pasuspender", as Skype will no longer hog the sound card, even during a call.

See my HOWTO (Step A, C and General Tips is probably what you need to follow) here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by simplyw00x on 2008-05-12
I'm on Fedora 9 and this is absolutely brilliant! It might be worth pointing out that you'll probably have to change the devices in Skype's audio settings from 'default' to use this script though. And psyke83, wonderful, but I would assume rawhide's packages are newer than Debian's, and it's still not working for me. Also, the padsp/skype OSS solution results in unusably-stuttering sound.

---

### Post by KillerKiwi on 2008-05-12
> **psyke83 said:**
> Hi there,

Your solution works, but there are disadvantages. PulseAudio will be blocked from using the sound card while your script is active (unless your card supports hardware mixing, perhaps).

It seems Debian have recently fixed some bugs in the "pulse_pcm" driver for ALSA, meaning that Skype can now work correctly with PulseAudio (providing your system is configured correctly). The latest version of Skype is also available in OSS form, meaning that the "padsp" wrapper is an option; both of these solutions work better than using "pasuspender", as Skype will no longer hog the sound card, even during a call.

See my HOWTO (Step A, C and General Tips is probably what you need to follow) here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I know it stops other sounds... but that is actually what I want when I'm on the phone ;) I'm hoping pulse will have a way of doing this semi-automatic in the future.. no idea how you would UI it though

Good to see a fix is on its way

I tried the OSS version, the sound quality was terrible, lots of pops and crackles

---

### Post by mikelito on 2008-05-14
I had unbearably cracky sound with OSS version. Just wanted to suggest a slight improvement to the workaround: if one uses

pasuspender -- /usr/bin/zenity --notification --text "Resume Pulseaudio" 

zenity produces a less intrusive notification area icon, which reenables pulseaudio when clicked. one can also give a --window-icon=XXX.png option to select the icon to be used.

I think the workaround is OK, until the skype developers decide to make it pulseaudio-compatible, or I get pissed off and start using Ekiga ;-)

thanks for the idea.

---

### Post by psyke83 on 2008-05-15
> **simplyw00x said:**
> I'm on Fedora 9 and this is absolutely brilliant! It might be worth pointing out that you'll probably have to change the devices in Skype's audio settings from 'default' to use this script though. And psyke83, wonderful, but I would assume rawhide's packages are newer than Debian's, and it's still not working for me. Also, the padsp/skype OSS solution results in unusably-stuttering sound.

I have Fedora 9 installed as well, and it doesn't work because the required configuration is not set by default. See this bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453) (yes, it applies to Fedora as much as Ubuntu).

---

### Post by athianos on 2008-07-25
I love you. Truly.

Worked a treat!

---

### Post by nidelius on 2008-09-10
I have tried with a lot of different ways to get it working but banshee seems to lock up the driver and skype tells me the audiodriver is uavailable..

the terminal gives me the following output:
```

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

---

### Post by psyke83 on 2008-09-10
> **nidelius said:**
> I have tried with a lot of different ways to get it working but banshee seems to lock up the driver and skype tells me the audiodriver is uavailable..

the terminal gives me the following output:
```

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

This guide uses a poor workaround - it suspends the PulseAudio server while Skype is running. That means that either Skype or PulseAudio applications can play audio, but not both.

Look at this instead (with emphasis on the note for Skype in Appendix B): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by lucho64 on 2010-09-11
Easiest fix: just apt-get remove pulseaudio. You are not going to miss it.

---

### Post by stoian on 2011-04-03
I had no microphone signal from my web camera, until I went into System > Preferences > Sound. In that dialog, switch to input tab and "Choose a device for sound input": I set mine to my webcam (VF0610 Live! Cam socialize HD Analog Mono").

Solved, now, eh?

---

### Post by joelpedersen on 2011-04-17
I had this problem as well...  very scratchy sound out of skype, along with sort of an annoying echo.  

UPDATED...  Last fix entered was not permanent as the problem came back...  However, I have been getting good results by entering this line under:

Skype -> options -> Notifications -> Skype Login -> Advanced View -> Execute the Following Script (***not*** Execute the Following Script on any event):    pulseaudio --cleanup-shm

Please let me know if this works for anyone else or does not...

---

### Post by pikarl on 2011-08-10
I had this Skype problem for more than a year now without finding a solution. Finally, this tweak helped very much. Thanks!

---

### Post by ortermagic on 2012-07-28
> **joelpedersen said:**
> I had this problem as well...  very scratchy sound out of skype, along with sort of an annoying echo.  

UPDATED...  Last fix entered was not permanent as the problem came back...  However, I have been getting good results by entering this line under:

Skype -> options -> Notifications -> Skype Login -> Advanced View -> Execute the Following Script (***not*** Execute the Following Script on any event):    pulseaudio --cleanup-shm

Please let me know if this works for anyone else or does not...


Thanks for that tip Joel...I have been getting a lot of  sound trouble related to sound quality and skype  myself, I was on the brink of removing pulse audio when I found your fix. Thank you.

---

