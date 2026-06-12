---
title: "safe to uninstall ardour?"
date: 2013-01-18
forum: Ubuntu Studio
---

### Post by mnieber on 2013-01-18
I'd like to remove ardour from my ubuntu studio (to keep my computer clean and not have too many programs).

The software center tells me that to remove it, the packages "ubuntustudio-generation" and "ubuntustudio-recording" must also
be removed.

Is this safe, or will it break the system?

---

### Post by Frogs Hair on 2013-01-18
Do you use the related packages recording software ? If you don't use the programs and don't get any warnings I would say it's alright to remove. You can reinstall if there are problems.

Ardour is available in Ubuntu(Unity) but I don't know if it is integrated into the desktop the same way as Ubuntu Studio(XFCE). U-Studio recording and the other package appearer independently in the synaptic package manager.

---

### Post by cfhowlett on 2013-01-19
Break the sytem?  No.  Remove a major piece of usable engineering?  Yes.

---

### Post by jejeman on 2013-01-19
> **mnieber said:**
> I'd like to remove ardour from my ubuntu studio (to keep my computer clean and not have too many programs).

The software center tells me that to remove it, the packages "ubuntustudio-generation" and "ubuntustudio-recording" must also
be removed.

Is this safe, or will it break the system?Here is the extrat from my dpkg log:
```
2012-07-10 00:10:01 remove ubuntustudio-recording 0.100 <none>
2012-07-10 00:10:02 remove ubuntustudio-generation 0.100 <none>
2012-07-10 00:10:03 remove pulseaudio-module-jack 1:1.1-0ubuntu15.1 <none>
2012-09-03 19:28:53 remove ubuntustudio-video 0.100 <none>
2012-09-03 19:28:54 remove openshot 1.4.0-1ubuntu1 <none>
2012-09-09 22:14:12 remove ubuntustudio-graphics 0.100 <none>
2012-09-09 22:14:12 remove gimp-ufraw 0.18-1.1build1 <none>
2012-09-09 22:14:13 remove gimp-resynthesizer 0.16-1.1 <none>
2012-09-09 22:14:13 remove gimp-plugin-registry 3.5.4-1 <none>
2012-09-09 22:14:14 remove gimp-gmic 1.5.0.8+dfsg-1 <none>
2012-09-09 22:14:15 remove gimp-gap 2.6.0+dfsg-2 <none>
2012-09-09 22:14:15 remove gimp 2.6.12-1ubuntu1 <none>


```So, as you can see, it is safe to remove those **meta** packages.

---

### Post by Frogs Hair on 2013-01-19
I would leave well enough alone, Arduor is obviously well integrated with the U Studio  desktop and you may end up with an unstable mess.

---

### Post by ttoine on 2013-01-21
This will not break the system.

Just, it will break two meta packages in wich Ardour is a dependency:
"ubuntustudio-generation" and "ubuntustudio-recording"

If you don't do audio recording at all, you can safely uninstall Ardour. The system will still be able to install updates, etc.

---

### Post by jejeman on 2013-01-22
Just to make all clear.
As you can see in my dpkg log, because I wanted to remove "pulseaudio-module-jack" the meta packages "ubuntustudio-recording ubuntustudio-generation" had to go too. These meta packages do not remove all the packages they install. It only removes just them. So all the packages remain. For example, ubuntustudio-recording depends on:
```
a2jmidid
    Daemon for exposing legacy ALSA MIDI in JACK MIDI systems 

alsa-tools
    Console based ALSA utilities for specific hardware 

alsa-tools-gui
    GUI based ALSA utilities for specific hardware 

ardour
    digital audio workstation (graphical gtk2 interface)
    also a virtual package provided by ardour-i686 

audacity
    fast, cross-platform audio editor 

cdrdao
    records CDs in Disk-At-Once (DAO) mode 

ffado-dbus-server
    FFADO D-Bus server 

ffado-mixer-qt4
    FFADO D-Bus mixer applets (QT4) 

ffado-tools
    FFADO debugging and firmware tools 

gladish
    graphical interface for LADI Session Handler 

guitarix
    Rock guitar amplifier for Jack 

hydrogen
    advanced drum machine/step sequencer 

hydrogen-drumkits
    drumkits for Hydrogen 

jack-rack
    LADSPA effects "rack" for JACK 

jackd
    JACK Audio Connection Kit (default server package) 

jamin
    Audio mastering from a mixed down multitrack source with JACK 

libavcodec-extra-53
    Libav codec library 

libavdevice-extra-53
    Libav device handling library 

libavfilter-extra-2
    Libav filter library 

libavformat-extra-53
    Libav video postprocessing library 

libavutil-extra-51
    Libav utility library 

libpostproc-extra-52
    Libav video postprocessing library 

libswscale-extra-2
    Libav video software scaling library 

meterbridge
    A collection of Audio meters for the JACK audio server 

mudita24
    ALSA GUI control tool for Envy24 (ice1712) soundcards 

patchage
    modular patch bay for Jack audio and Alsa Midi 

pulseaudio-module-jack
    jackd modules for PulseAudio sound server 

qjackctl
    User interface for controlling the JACK sound server 

rakarrack
    Simple and easy guitar effects processor for GNU/Linux 

zynjacku
    JACK based host for LV2 synths and LV2 plugins 
```As you can see, these dependecies are only effective upon install, not upon removal. I still have all those packages exept "pulseaudio-module-jack". I can still make music without any problems related to packages. Now, if I want to remove Ardour it only removes just it.
So, "system" will not "break" if you remove these meta packages that I have removed (ubuntustudio-recording, ubuntustudio-generation, ubuntustudio-video, ubuntustudio-graphics). I can still record audio, generate audio, do video editing and graphics. (Regarding to my dpkg log) I use Kdenlive for video editing and GIMP 2.8.2 for image manipulation.

I hope this will make clear all the confusion that these meta packages can bring.

---

