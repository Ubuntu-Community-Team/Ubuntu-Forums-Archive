---
title: "MIDI broken in ubuntu studio"
date: 2013-11-30
forum: Ubuntu Studio
---

### Post by alainhenry on 2013-11-30
This is what happened since last time I played a midi file succesfully on my ubuntu studio 12.04.3 system:
installed ubuntu-restricted-extras (not MIDI-related but who knows...)
installed linuxband (that's what I wanted to to)
   to achieve this I had to install
   - libdbus-1-dev (1.4.18-1ubuntu1.4)
   - libjack-jackd2-dev (1.9.8~dfsg.1-1ubuntu2)
   - libgtk2.0-dev (2.24.10-0ubuntu6)    which installed 57 dependancies
Having done this I compiled linuxband. Install went smoothly. It started, but could not play a sound. 
And suddenly, I could not play a midi sound either...
I removed all linuxband related files mentionned above (not the restricted-extras). Still, MIDI does not play.
pmidi -l    lists midi ports 14:0 and 128:0 to 3
I have timidity running as a daemon for MIDI. I reinstalled it, just to make sure.
But no MIDI sound anymore.  

[Edit] If I launch a new instance of timidity as MIDI server, I get access to ports 129:0 to 3, and they work. Still, I would like to have the first instance working.

I need some idea to fix this. Thanks

---

### Post by gdesilva on 2013-12-10
Perhaps you may have done this already....but I would run Qjackctl and check whether the connections are in place.

---

### Post by royleith on 2014-02-01
@ gdesilva

I have exactly the same problem with US11.10. Timidity worked at the beginning, although I never had it working with jack running. Task Manager shows one process: timidity -Os -iAD

> $ pmidi -p128:0 bad_moon_rising.mid

causes client 131 to appear in Patchage and connected to Timidity Port 0, but the track does not play. There is no actual port shown in the client.

> $ timidity -Os -iAD
$ Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 131:0 131:1 131:2 131:3
^C
$ pmidi -p131:0 bad_moon_rising.mid
Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes

causes a second process of 'timidity -Os -iAD' to appear in Task Manager and Client 132 to appear in Patchage  with a Port 0 unconnected to anything.

The track plays correctly and the timidity output appears in the following entries in Sound Settings (Left click on the system tray loudspeaker),

Playback: ALSA plug-in [timidity]:ALSA Playback on                           jack sink (PulseAudio JACK Sink)
Output Devices: jack sink (PulseAudio jack sink).

The Timidity instance is correctly launched during boot and the ports appear in jack Connections (as timidity port 128:0-3), but the system tie to the Pulse Audio sink is not made. Any new instances of Timidity work correctly both with jack running, and with jack stopped:

Playback: ALSA plug-in [timidity]:ALSA Playback on                            Built-in Audio Analogue Stereo
Output Devices: Built-in Audio Analogue Stereo                         Port: Headphones    <this is the green 3.5mm socket>

Gmidimonitor and Virtual MIDI Keyboard show the keyboard generating MIDI messages in Gmidimonitor, but the connection to Timidity does not play them. Connecting to an external MIDI module works correctly.

Something alainhenry and I have done has disturbed the startup configuration of Timidity although we have not installed the same software.

---

### Post by royleith on 2014-02-01
A Workaround:

I found that setting up a new user did not solve the timidity problem for the new user. I tried sudo service timidity restart which stopped the service and restarted it. Timidity still had the same problems.

However,

> $ sudo service timidity stop
[sudo] password for roy: 
 * Stopping TiMidity++ ALSA midi emulation...                            [ OK ] 
$ timidity -Os -iAD
$ Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3
^C
$ Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 32768, period size 8192 bytes
^C
$ 

gets everything working in jack. With jack stopped, the sound settings revert to the correct config, but timidity stops working. 

issuing another 'service timidity stop' brings the report that 'No timidity found running; none killed.
 Also a 'timidity  -Os -iAD' sets up a port 131 and the original timidity task is still running together with the new one.

It would seem that the services startup config is at fault. I will have a look at that, next.

---

### Post by su:bhatta on 2014-02-01
I am using Linuxband for sometime now, and never faced any problem.
After compiling Linuxband you have to connect it to some sound generator, like Qsynth or ZynjackU( Using any synth) through Jack connections or Patchage.

Linuxband itself is just a GUI for MMA and makes the mma file ( you should have MMA installed for Linuxband to operate, I am guessing you have done this as mentioned in Linuxband Documentation page) the sound of the midi file created by linuxband has to be generated through some synth.
Hope this helps in some issues. As, for Timidity I cannot help, but if you face any problems regarding Linuxband, I can help you. :P

---

