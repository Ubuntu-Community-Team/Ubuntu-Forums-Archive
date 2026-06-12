---
title: "Sound Manager gone"
date: 2013-06-22
forum: Ubuntu Studio
---

### Post by tnob on 2013-06-22
Greetings all

I'm running Ubuntu DreamStudio 12.04 LTS on an IBM Intel (R) Core (TM) i 6-3470 CPU @ 320 GHz 3.20 GHz desktop (RAM 4Gb). And my problem has to do with Sound Settings. 

Initially, the Sound Manager (loudspeaker icon in top tool bar) did not show any activity. Input and Output windows,  under Sound Settings, are completely dead: no recognition whatsoever of Microphone/Speakers/Headset. Alsamixer is enabled and in perfect working order, though, as far as I can see.

A friend advised to try

sudo apt-get remove pulseaudio && sudo apt-get autoremove &&  sudo apt-get install pulseaudio

This was duly followed up (see below). Reading not entirely complete, I'm afraid, due to an error whilst copying and pasting.

```
Reading package lists... Done

Building dependency tree

Reading state information... Done

The following packages were automatically installed and are no longer required:

libmpeg3cine libguicast1 libtorque2 blender-codecs-ffmpeg0.10 libopenmpi1.3

libopenimageio1.0 libquicktimecine libboost-thread1.46.1 gnome-alsamixer

localechooser-data sfftw2 libnuma1 libibverbs1 libgsoap1 libltcsmpte1

blender-openshadinglanguage-data

Use 'apt-get autoremove' to remove them.

The following packages will be REMOVED

dreamstudio-audio-control dreamstudio-audio-effects

dreamstudio-audio-essentials dreamstudio-audio-recording

dreamstudio-audio-utilities dreamstudio-complete dreamstudio-dj-tools

dreamstudio-instruments dreamstudio-unity-desktop indicator-sound

libcanberra-pulse pulseaudio pulseaudio-module-jack pulseaudio-module-x11

0 upgraded, 0 newly installed, 14 to remove and 0 not upgraded.

After this operation, 4,570 kB disk space will be freed.

Do you want to continue [Y/n]? y

(Reading database ... 300546 files and directories currently installed.)

Removing dreamstudio-complete ...

Removing dreamstudio-audio-utilities ...

Removing dreamstudio-instruments ...

Removing dreamstudio-dj-tools ...

Removing dreamstudio-audio-recording ...

Removing dreamstudio-audio-effects ...

Removing dreamstudio-audio-essentials ...

Removing dreamstudio-audio-control ...

Removing dreamstudio-unity-desktop ...

Removing indicator-sound ...

Removing libcanberra-pulse ...

Removing pulseaudio-module-x11 ...

Removing pulseaudio-module-jack ...

Removing pulseaudio ...

Processing triggers for libglib2.0-0 ...

Processing triggers for ureadahead ...

Processing triggers for man-db ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Reading package lists... Done

Building dependency tree

Reading state information... Done

The following packages will be REMOVED

blender-codecs-ffmpeg0.10 blender-openshadinglanguage-data gnome-alsamixer

libboost-thread1.46.1 libgsoap1 libguicast1 libibverbs1 libltcsmpte1

libmpeg3cine libnuma1 libopenimageio1.0 libopenmpi1.3 libquicktimecine

libtorque2 localechooser-data sfftw2

0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.

After this operation, 27.1 MB disk space will be freed.

Do you want to continue [Y/n]? y

(Reading database ... 300339 files and directories currently installed.)

Removing blender-codecs-ffmpeg0.10 ...

Removing blender-openshadinglanguage-data ...

Removing gnome-alsamixer ...

Removing libboost-thread1.46.1 ...

Removing libgsoap1 ...

Removing libguicast1 ...

Removing sfftw2 ...

Removing libopenmpi1.3 ...

Removing libibverbs1 ...

Removing libltcsmpte1 ...

Removing libquicktimecine ...

Removing libmpeg3cine ...

Removing libnuma1 ...

Removing libopenimageio1.0 ...

Removing libtorque2 &#8230;
```

 - by the end of which my Sound Manager had completely vanished.
 Subsequently, I repeated

sudo apt-get install pulseaudio

This yielded the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

Alsamixer was checked on as well - and still enabled, so no changes there. After restarting , however, no trace of Voice Manager, as before.

Due to a hearing impediment, it's essential that Sound Settings is working properly. But I don't have a clue as to where to go from here.

tnob

---

### Post by jejeman on 2013-06-22
Give
```
dpkg -l | grep -i pulsea
```
```
apaly -l
```

**advice
Put terminal output in CODE tags.

---

### Post by tnob on 2013-06-22
Thanks Jejeman,

I'm going to try that. 

But before I do, could you please expand a little on what CODE tags are? I'm not that experienced yet with Terminal.

tnob

---

### Post by jejeman on 2013-06-22
CODE tags are for formating the forum post. It is "#" icon. 
It has nothing to do with terminal.

You should edit your first post and put terminal output in [CODE] tags, not in[SIZE=1][/ SIZE] as you did.

---

### Post by tnob on 2013-06-22
Found out where CODE tags are to be gotten from, in the meanwhile, but haven't worked out yet how to insert those into a thread. So please forgive me for not giving you the Terminal output properly encased just yet.

This is what I received:

ii  gstreamer0.10-pulseaudio               0.10.31-1ubuntu1.2                      GStreamer plugin for PulseAudio
ii  libpulse-mainloop-glib0                1:1.1-0ubuntu15.3                       PulseAudio client libraries (glib support)
ii  libpulse0                              1:1.1-0ubuntu15.3                       PulseAudio client libraries
ii  libpulsedsp                            1:1.1-0ubuntu15.3                       PulseAudio OSS pre-load library
ii  pavucontrol                            0.99.2-1build1                          PulseAudio Volume Control
ii  pulseaudio                             1:1.1-0ubuntu15.3                       PulseAudio sound server
ii  pulseaudio-equalizer                   2.7.0.2-2~webupd8~oneiric3              PulseAudio Equalizer - LADSPA plugin graphical user interface
ii  pulseaudio-module-x11                  1:1.1-0ubuntu15.3                       X11 module for PulseAudio sound server
ii  pulseaudio-utils                       1:1.1-0ubuntu15.3                       Command line tools for the PulseAudio sound server
ii  vlc-plugin-pulse                       2.0.5-0ubuntu0.12.04.1+opus1.2          PulseAudio plugin for VLC

And subsequently:

No command 'apaly' found, did you mean:
 Command 'aplay' from package 'alsa-utils' (main)
apaly: command not found
peter@peter-toshiba:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

What now?

tnob

---

### Post by jejeman on 2013-06-22
Give
```
dpkg -l | grep -i indicator-
```
Is the sound working?

---

### Post by tnob on 2013-06-22
> **jejeman said:**
> Give
```
dpkg -l | grep -i indicator-
```
Is the sound working?

Yep. Sound is working.

It was, anyway, last time I tried (a couple of hours ago). All on the same level, though: no way now of adjusting the desktop's sound volume.

tnob

---

### Post by tnob on 2013-06-22
By the way,  this is what I'm getting from dpkg -l | grep -i indicator-

ii  indicator-application                  0.5.0-0ubuntu1                          Application Indicators
ii  indicator-appmenu                      0.3.97-0ubuntu1                         Indicator for application menus.
ii  indicator-cpufreq                      0.1.4-0ubuntu2                          CPU frequency scaling indicator
ii  indicator-datetime                     0.3.94-0ubuntu2                         Simple clock
ii  indicator-messages                     0.6.0-0ubuntu2                          indicator that collects messages that need a response
ii  indicator-power                        2.0-0ubuntu1                            Indicator showing power state.
ii  indicator-printers                     0.1.6-0ubuntu1                          indicator showing active print jobs
ii  indicator-session                      0.3.96-0ubuntu1                         indicator showing session management, status and user switching
ii  indicator-status-provider-mc5          0.6.0-0ubuntu2                          indicator-messages status provider for telepathy mission-control-5
ii  libindicator-messages-status-provider1 0.6.0-0ubuntu2

tnob

---

### Post by jejeman on 2013-06-22
You need indicator-sound.
Install it
```
sudo apt-get install indicator-sound
```

---

### Post by tnob on 2013-06-23
Greetings all,

Last advice received, as to restoring Sound Manager in Ubuntu DreamStudio 12.04 LTS (originally posted on Saturday 22. June 2013) was to try

sudo apt-get install indicator-sound

Terminal output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  indicator-sound
0 upgraded, 1 newly installed, 0 to remove and 31 not upgraded.
Need to get 106 kB of archives.
After this operation, 367 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main indicator-sound i386 0.8.5.0-0ubuntu2.1 [106 kB]
Fetched 106 kB in 0s (568 kB/s)     
Selecting previously unselected package indicator-sound.
(Reading database ... 303905 files and directories currently installed.)
Unpacking indicator-sound (from .../indicator-sound_0.8.5.0-0ubuntu2.1_i386.deb) ...
Processing triggers for libglib2.0-0 ...
 Setting up indicator-sound (0.8.5.0-0ubuntu2.1) ...

Obviously another command is expected, for setting up/installing indicator sound. Please guide me...!

As to putting Terminal output in a box: I found the tags box, in the meanwhile, but keep getting error messages saying that content is limited to only 18 characters.

Thanks,

tnob

---

### Post by jejeman on 2013-06-23
Why did you open another topic for the same problem?
What is wrong with old thread?

Just re-login and indicator should show up.
Of course, pulseaudio needs to be running.

---

### Post by howefield on 2013-06-23
Duplicate threads merged.

---

### Post by tnob on 2013-07-03
[FONT=arial]To Jejeman:

some time had already gone between start of thread and my last quick reply, so I thought this the simplest way to pick up at where we had left off. Nothing more to it.

Your suggestions sorted out my laptop, by the way - but my desktop not yet. Thanks very much for your help.


tnob [/FONT]

---

### Post by alfonsofernandezyf on 2014-01-21
Hi everyone,

I have the same problem, I'm running ubuntu 13.10 on an Acer Aspire V7-581 and I installed the music production packages from Ubuntu Studio.

Everithing worked great until I connected the HDMI cable from my computer, I was able to select the output inernal speakers/HDMI, I dont remember if turned the computer off or just closed the lid, but next time i logged in, the sound indicator was gone. Sound works, but there is no way of controlling neither the volume nor can I select the output. 

I noticed that when i log out of my user there is a sond indicator on the login screen and if I llog as a guest the indicatro, as well as the audio controls work perfectly.

I alreade purged reinstalled Pulse-audio, I force reloaded alsa-base, but nothing brings the controls back.

I hope you can help me.


Thanks.

---

### Post by jejeman on 2014-01-22
Indicator just starts
```
pavucontrol
```So, there you can change audio settings.

During the 5-6 years using Ubuntu Studio (GNU/Linux) I never saw that reinstall of the software resolved any problem.

---

### Post by cub on 2014-01-22
> **tnob said:**
> Greetings all

I'm running Ubuntu DreamStudio 12.04 LTS on an IBM Intel (R) Core (TM) i 6-3470 CPU @ 320 GHz 3.20 GHz desktop (RAM 4Gb). And my problem has to do with Sound Settings. 


Please note that "Ubuntu DreamStudio" is not "Ubuntu Studio" ...

They also have a support forum: [http://www.celeum.com/forums/forum/dreamstudio/](http://www.celeum.com/forums/forum/dreamstudio/)

---

