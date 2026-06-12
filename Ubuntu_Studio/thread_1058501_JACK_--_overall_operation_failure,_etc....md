---
title: "JACK -- overall operation failure, etc..."
date: 2009-02-02
forum: Ubuntu Studio
---

### Post by le_vainqueur on 2009-02-02
I just did a fresh install of Ubuntu Studio 8.04 and got my Tascam US-122 working using the guide on the ALSA web site.  I plugged my guitar in and started Audacity using the command "pasuspender -- audacity" and everything was able to record well.

I also want to be able to use my Tascam for MIDI. My understanding of things leads me to believe that getting JACK up and running is the first step in reaching that goal.  I'm new to both MIDI and JACK, so please bare with me.  I was looking [here]("https://help.ubuntu.com/community/HowToJACKConfiguration") for information on how to set things up, but when I start Jack I get the following output message:

> 22:11:18.396 Patchbay deactivated.
22:11:18.482 Statistics reset.
22:11:18.556 ALSA connection graph change.
22:11:18.695 ALSA connection change.
22:11:42.179 Startup script...
22:11:42.180 artsshell -q terminate
22:11:42.601 Startup script terminated with exit status=256.
22:11:42.601 JACK is starting...
22:11:42.602 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Cplughw:0 -Pplughw:0
22:11:42.604 JACK was started with PID=6465.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... plughw:0|plughw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
22:11:42.633 JACK was stopped successfully.
22:11:42.634 Post-shutdown script...
22:11:42.634 killall jackd
jackd: no process killed
22:11:43.042 Post-shutdown script terminated with exit status=256.
22:11:44.612 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

It seems logical to me that my USB Tascam is "plughw:0", so that's what I chose as both input and output, but I tried all of the various options at one point or another.  I don't understand why hw:0 is still showing up in this message however.  I disabled my motherboards sound device in BIOS and it no longer shows up in the preferences dialog box.

Other than that, none of the message makes sense.  I'm still not quite clear on how ALSA vs. PulseAudio plays into all of this.  I know I need to kill pulse before starting Audacity...does that need to happen before starting JACK as well?

What am I missing?


Thanks,

LV

---

### Post by le_vainqueur on 2009-02-03
Hey all, still trying to get this thing working.  I found [this]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") website in my efforts. When following their steps, however, I am unable to change #1.  The "interface" drop down is grayed out.  When I try starting the jac, I receive the same error as before.

Anyone have advice or resources they could point me to?

---

### Post by thorgal on 2009-02-04
salut le_vainqueur:

you have to understand what this command 
```

/usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Cplughw:0 -Pplughw:0

```
is really doing because that's what gets executed when you start jack through Qjackctl.

First, you should not use the plughw:, use the direct hardware hw:

Second, starting jack like this will not make it handle MIDI. In fact, if you just want to use your tascam for MIDI, you don't need jack. However, the latest jack is quite advanced in its MIDI capabilities, so you can enable it with the option -X seq. This option is available in the qjackctl setup window (it is called MIDI driver or something like that).But be aware that few apps are using native jack MIDI. The fact that qjackctl displays a MIDI tab called ALSA is confusing most people. It is a convenience that has nothing to do with jack. It shows the _ALSA_ MIDI layer, not native jack MIDI layer.

Moreover, if you use the same device, you don't need to specify -C and -P. Just use -d alsa -dhw:0 (if your tascam is indeed hw:0). To be sure, can you post the output of:

```

cat /proc/asound/cards

```

thanks.

Before fiddling around with qjackctl, you could just open a terminal and launch jackd manually with the right options. 

Another very useful tip:
if you want to know why your soundcard is busy and jack cannot grab it when you try to start it, use a utility called fuser:

```

fuser /dev/snd/pcmC0D0p

```

assuming that you are interested in soundcard hw:0. The final p is for playback. For capture, it is pcmC0D0c

What fuser does is report the process ID of the process using your sound card. It will look like:
```

1234m 5678m

```

this is just an example. To kill these processes (in order to free your sound card), just do
```

sudo kill -9 1234 5678

```

Of course, you should replace these numbers by what fuser is reporting. 
If these processes happen to be related to pulseaudio, you will thereby kill pulseaudio, That's maybe not what you want ;)

so before killing them, check what these processes are:
```

ps xa | grep 1234
ps xa | grep 5678

```

I hope you understand what I am saying here. Just speak up if you don't.

---

### Post by le_vainqueur on 2009-02-05
Thanks for the reply.  I'm still trying to figure out all of my capabilities/options and what is best for me.  

I input the command "cat /proc/asound/cards" and got the following:

>  1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/004)


I don't see how this relates to the hw:0 issue.

---

### Post by thorgal on 2009-02-06
le_vainqueur:

according to /proc/asound/cards, your tascam card is at hw:1   ;)

---

### Post by le_vainqueur on 2009-02-09
Thanks for the translation thorgal. I guess I should have been able to figure that one out.

Anyway, jack appears to be up an running smoothly now.  I had one more slight problem, but found it well documented here: [http://ubuntuforums.org/showthread.php?t=955600](http://ubuntuforums.org/showthread.php?t=955600)

Thanks for the help!

---

