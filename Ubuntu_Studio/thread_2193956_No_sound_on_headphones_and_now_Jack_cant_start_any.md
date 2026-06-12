---
title: "No sound on headphones and now Jack cant start anymore either"
date: 2013-12-15
forum: Ubuntu Studio
---

### Post by onerose on 2013-12-15
I've been fighting the lost sound in my headphones for a week. I tried various forum solutions to no avail to return the sound into my headphones (unmuting alsamixer, editing alsa configurations and adding options, installing pavucontrol, killing pulseaudio, uninstalling pulseaudio, reinstalling, updating, upgrading...), and after I followed the official directions from Canonical, now Jack wont start either (after I JUST got it to work and it took me days... aaaahhh!!! ](*,)). Please help, I dont want to have to reinstall the whole system. The sound mutes when I plug headphones in, speakers work, but headphones do not. I cant do anything in studio. Here is more detail that might give you the clue whats the problem.

Edit: I reinstalled jack again and I am able to start it. Now Ardour is not working again. However, nothing helps the headphones.
Edit 2: Nope, Jack wont start. Messages give this:

 Sun Dec 15 22:01:40 2013: Starting jack server...
 Sun Dec 15 22:01:40 2013: JACK server starting in non-realtime mode
 Sun Dec 15 22:01:40 2013: Device reservation request with priority 2147483647 denied for "Audio0": org.freedesktop.DBus.Error.UnknownMethod (Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 )
 Sun Dec 15 22:01:40 2013: ERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 Sun Dec 15 22:01:40 2013: ERROR: Audio device hw:0,0 cannot be acquired...
 Sun Dec 15 22:01:40 2013: ERROR: Cannot initialize driver
 Sun Dec 15 22:01:40 2013: ERROR: JackServer::Open failed with -1
 Sun Dec 15 22:01:40 2013: ERROR: Failed to open server
 Sun Dec 15 22:01:42 2013: Saving settings to "/home/CHARNAME/.config/jack/conf.xml" ...

 [COLOR=#ff0000]22:01:53.731 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started




ALSA information:

[http://www.alsa-project.org/db/?f=9441ba9f71c9e4d3b4cdd611830c8c2bf5fe238e](http://www.alsa-project.org/db/?f=9441ba9f71c9e4d3b4cdd611830c8c2bf5fe238e)

---

### Post by jejeman on 2013-12-15
Which soundcard do you use?
Give
```
aplay -l
```
Where do you plug in the headphones?

I would disable (jack) dbus in Qjackctl.

---

### Post by onerose on 2013-12-15
Sure, it is a Realtek soundcard.

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I plug them normally into the headphones port (if it is called so :)). I just tried one more option for asus in alsa configuration, I will try to disable dbus too and see how it goes (it worked normally with dbus before, it stopped working again when I reinstalled lmms, and lmms is the culprit that I have no headphone sound as well. I am trying to use ubuntu for studio but I cant manage to make the sound work - ubuntustudio distro was even worse I had no sound at all and couldnt fix it - I mention this because people usually start recommending ubuntustudio but it just wont work on my computer).

EDIT: Still the same, jack stops as soon as I start it and headphones do not work.

---

### Post by onerose on 2013-12-15
I tried to completely remove pulseaudio and set ALSA as default, still no sound from headphones. At least Jack started running, yay, but... Ardour is freezing and crashing, terrible sound which used to be good. In LMMS the sound is terrible too, scratchy and crackling (same as before). I dont know at this point whether to return pulseaudio?????? Im desperate. Why does LMMS keep switching to DummyOutput with no sound? I cant switch it to anything else it ignores my changes.

The real question: does anyone here have jack, lmms, ardour and working sound on the same computer and what are your settings??? It is like that they cannot coexist. I am switching lmms to windows to see if jack and ardour can function together.

---

