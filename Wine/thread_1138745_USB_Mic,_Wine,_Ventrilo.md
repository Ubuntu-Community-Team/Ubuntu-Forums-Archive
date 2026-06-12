---
title: "USB Mic, Wine, Ventrilo"
date: 2009-04-26
forum: Wine
---

### Post by Yoshis88 on 2009-04-26
Okay!  This is quite easily the last thing that is keeping me from totally abandoning the Microsoft bucket.  I feel good, learnt a lot.   Anyway, I've got a problem.  I know, it's another Wine/Ventrilo thread.  Sorry if it's a bit lengthy :P

I have Jaunty and I'm trying to configure Ventrilo for use with Wine.  I took the latest wine version (1.1.20~winehq0~ubuntu~9.04-0ubuntu1) and didn't use the one from the latest Ubuntu repositories, because if I did, I couldn't install WoW (Accept button greyed on EULA).  WoW works out of the box.  +10 points for Wine.

I have a couple-years-old Logitech webcam.  Video capture works out of the box with cheese.  More relevantly, if I choose it as the microphone by going
System > Preferences > Sound > Sound Capture > USB Device 0x46d:0x8d7 USB Audio (ALSA)
Then! Gnome sound recorder works out of the box.  +10 points for Ubuntu

Now for Ventrilo.  I install (latest version, 3.0.5 at the time of this writing) through Wine.  I can run, configure, and connect to the Vent server just fine.  I can hear everyone just fine, even while WoW is playing.  Push-to-talk "works" out of the box in that when I press left control, I hear confirmation sound that I'm recording, and my little speaker turns green to everyone on the Vent server.  Except they can't hear me. -1 point for Ventrilo.  Linux client in development, psh.  +10 to Spux when they finish their client.

Anyway, so here's the sleuthing I did.  I read "aoss" might help.  Installed it, tried it, nothing.  The interesting part comes to the winecfg Audio tab.
ALSA was the only checked audio driver by default!  There is also the OSS, JACK, NAS, and EsounD drivers.
[LIST]
[*]Under the ALSA Driver, both Wave Out and Wave In are 'default', with the Mixer Devices as 'ATI IXP'
[*]Under the OSS Driver, Wave Out has 'Realtek ALC658D', both the Wave In and the Mixer Devices have 'Realtek ALC658D' and 'USB Mixer'!
[/LIST]
Additionally, if I manually put a jack-style microphone in the front plug of my computer, Ventrilo picks it up!  So, the analog style microphone must be 'ATI IXP' and the Logitech webcam must be 'USB Mixer'!

And that's where I'm stuck.  I don't know how to tell Wine to make 'USB Mixer' an ALSA device, or check the OSS box and play some game with "aoss" to make it work, or something.  I feel really close.  Pointers would be appreciated.  The computer currently dual-boots to a Windows XP partition, I'm not afraid of the command line at all and am ready to post any outputs you might want and install any packages that might help.

---

