---
title: "Behringer FCA1616"
date: 2014-01-24
forum: Ubuntu Studio
---

### Post by Jaap3 on 2014-01-24
I've recently bought the Behringer FCA1616 audio interface and am having trouble getting it to work. From what I've gathered it's supposed to work on Linux but I'm not having much success.

I've got it hooked up through Firewire. Starting Jack with the Firewire drivers does seem to initialize the device but then qjackctl just freezes. The device itself just crackles every now and then. Hooking it up through USB seems to do nothing, I can't even figure out if it's being detected.

Any advice on how to debug this would be much appreciated!

---

### Post by jejeman on 2014-01-25
For USB do
```
lsusb
aplay -l
```
For firewire do
```
ls /dev/fw*
dmesg | grep -i fw
```I don't know this device, read the manual to see if USB is for audio stream and can both USB and firewire be connected at the same time.

---

### Post by Jaap3 on 2014-01-26
The device has a button that switches between Firewire or USB mode.

Anyway, I've got it to work in USB mode with ALSA and Jack. Not sure what I was doing wrong, but it's behaving as expected now. Thanks for the help!

---

### Post by WunNation on 2014-08-02
I use the FCA1616 on Ubuntu 12.04, and it took me a while to get working well.

Switchable Firewire/USB:
I had success using the device in USB Mode but never tried Firewire mode.
Only one of them works at a time with this device, though, so make sure you have the correct one enabled for your setup.
The selection is toggled, by holding down the 'Digital Select' button on the Front Panel for 3-seconds.
You know it has switched, when the FCA1616 resets, and all the LEDs flash.

Using FCA1616 and Jack:
For me the key to getting this device to run at low latencies (~5 ms) without X-Runs, 
was to set the Sample Rate to 88.2 kHz, and run Jack with Real Time Priority.
The rest of the settings I chose are fairly arbitrary. 

Jack and Real Time Priority: Joining the Audio Group
To use 'Real Time Priority' with jackd, 
- You must add 'audio' to the groups that your user belongs to. I used*[FONT=arial] '[COLOR=#3C3C3C][I]Users Administration Tool'*[/COLOR] [/FONT][/I]to accomplish this.
- You can also add yourself to the audio group using the terminal. This process is detailed here:
[http://www.liberiangeek.net/2012/04/quickly-add-users-to-groups-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/quickly-add-users-to-groups-in-ubuntu-12-04-precise-pangolin/)

Jack and Real Time Priority: Configuring the Audio Group
- You must also add a couple of lines to your audio.conf file to give the audio group access to 'Real Time' scheduling.
 @audio - rtprio 90       # maximum realtime priority  
 @audio - memlock unlimited  # maximum locked-in-memory address space (KB)
This is detailed here: [http://wiki.linuxaudio.org/wiki/system_configuration#limitsconfaudioconf](http://wiki.linuxaudio.org/wiki/system_configuration#limitsconfaudioconf)

My Jack Configuration for this device:
Here is how I run the FCA1616 using jackd from the command line with the aforementioned settings:
jackd -R -P70 -dalsa -dhw:0 -p512 -r88200

To get your hardware number (in my example this was 0: '-dhw:0' ): 
type in terminal 
'aplay -l',
 and use the 'card' number for the FCA1616.

Other Issues:
If you end up with a popping sound every few seconds, review your 'sync' setting on the FCA1616's Front Panel (changed by quickly pushing the 'Digital Select' button).
I've found that the SMUX and COAX options do not cause this problem (while the ADAT option does).

---

