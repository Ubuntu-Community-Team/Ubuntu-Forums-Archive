---
title: "Echo Mia MIDI on Ubuntu Studio 10.04 doesn't work"
date: 2010-09-30
forum: Ubuntu Studio
---

### Post by aredcat66 on 2010-09-30
Hi All.

Yesterday night I've installed Ubuntu Studio 10.04 on my PC.  
I'm new to this OS so I need to make my own experience.

It seems it was all ok but the soundcard (Echo Mia MIDI) doesn't work

I remember I had the same problem 2 years ago trying to install a previous version of Ubuntu Studio. I've searched on the internet and I've found an article [here ]("http://www.alsa-project.org/main/index.php/Matrix:Module-mia"). I've tryed to follow the steps but, as I've said, I'm new to linux world so I probably made some error and my system didn't work. I was sad but I returned to the previous OS (win xp) because I need to work with audio and had no much time to spend on tuning my PC.
This time I would like to begin my trip in LINUX world but I think I need some step by step help to resolve my problem with the soundcard (that works in WINXP).

I hope someone can give me some tips.

Thank you in advance
aredcat66

---

### Post by mango42 on 2010-09-30
I'm a perennial beginner so take what I say with a pinch of salt.

Have you started Jack server (via QJackCtl)? If so, does it show any MIDI devices in its 'Connect' window?

Have you set 'alsa' as your driver in its 'setup' dialogue? In the same setup (down in bottom left corner) have you set MIDI to 'seq'?

Do you have the module '**a2jmidid**' set to start up via Jack (options page, enable 2nd field down and just type a2jmidid)

AFAIK, in Karmic & Lucid studios, it *should* work straight out of the box - that article you worked with is 3 years old - not sure whether all those steps haven't been incorporated automagically since then.

FWIW & good luck. Hopefully one of the *real *programmers here will come to your aid if these basic suggestions don't work.

---

### Post by AutoStatic on 2010-09-30
Hello aredcat66,

The card should work and no need to compile anything because 10.04 comes with the Mia driver by default:

```
modinfo snd-mia
filename:       /lib/modules/2.6.32-25-generic/kernel/sound/pci/echoaudio/snd-mia.ko
description:    Echoaudio Mia soundcards driver
license:        GPL v2
author:         Giuliano Pochini <pochini@shiny.it>
firmware:       ea/mia_dsp.fw
firmware:       ea/loader_dsp.fw
srcversion:     BAD7096F9C57C9CE7B83DC7
alias:          pci:v00001057d00003410sv0000ECC0sd00000081bc*sc*i*
alias:          pci:v00001057d00003410sv0000ECC0sd00000080bc*sc*i*
depends:        snd-pcm,snd,snd-page-alloc,snd-rawmidi
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 
parm:           index:Index value for Mia soundcard. (array of int)
parm:           id:ID string for Mia soundcard. (array of charp)
parm:           enable:Enable Mia soundcard. (array of bool)
```

Could you post the result of the terminal command **aplay -l** ?

---

### Post by lykeion on 2010-09-30
Hi there
I used to have a Echo Mia card long time ago. Sorry to disappoint you but I don't have a step-by-step guide for you, and I remember I had to fiddle a lot to get it to work in Ubuntu. Things might have become easier since then. I haven't kept up with the latest UbuntuStudio and today I use another card and mainly do my music production in Windows. 

I did some googling for you and came up with these links (some of them are for Layla3G card but it shouldn't matter). I would try the tips in order and only resort to complicated things like compiling ALSA as a last resort.

This is a very good sound troubleshooting guide. I often recommend it to others:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

EDIT
I see you've already got answers from people more up to date with Ubuntu Studio than me. So I've removed some old links I found.

---

### Post by aredcat66 on 2010-09-30
Thank you all folks !

> **AutoStatic said:**
> Hello aredcat66,

The card should work and no need to compile anything because 10.04 comes with the Mia driver by default:

l command **aplay -l** ?

Here is the result of the command :

[FONT=Courier New]aplay -l 
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: nForce2 [NVidia nForce2], dispositivo 0: Intel ICH [NVidia nForce2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: nForce2 [NVidia nForce2], dispositivo 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Mia [Mia], dispositivo 0: PCM [Mia]
  Sottoperiferiche: 7/8
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
  Sottoperiferica #2: subdevice #2
  Sottoperiferica #3: subdevice #3
  Sottoperiferica #4: subdevice #4
  Sottoperiferica #5: subdevice #5
  Sottoperiferica #6: subdevice #6
  Sottoperiferica #7: subdevice #7[/FONT]

is there something I can do ?

---

### Post by AutoStatic on 2010-09-30
It's properly recognized. You probably would want to take a look at JACK and QjackCtl: [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

In your case you can use **hw:Mia** as your card's designation in the Interface field of the QjackCtl Settings window.

---

### Post by aredcat66 on 2010-09-30
> **AutoStatic said:**
> It's properly recognized. You probably would want to take a look at JACK and QjackCtl: [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

In your case you can use **hw:Mia** as your card's designation in the Interface field of the QjackCtl Settings window.
I've tryed to start Jack with different parameters but it seems something doesn't work :

p, li { white-space: pre-wrap; } [COLOR=#999999]00:30:17.611 Logging started --- ven ott 1 00:30:17 2010 ---[/COLOR]
 [COLOR=#999999]00:30:17.669 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]00:30:17.771 Statistics reset.[/COLOR]
 [COLOR=#66cc99]00:30:18.006 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]00:30:18.908 ALSA connection change.[/COLOR]
 [COLOR=#999999]00:31:31.482 Startup script...[/COLOR]
 [COLOR=#990099]00:31:31.483 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]00:31:31.887 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]00:31:31.889 JACK is starting...[/COLOR]
 [COLOR=#990099]00:31:31.890 jackd-realtime -v -dalsa -r44100 -p64 -n3 -D -Chw:0 -Phw:0,0 -o1 -Xraw -zs[/COLOR]
 [COLOR=#ff0000]00:31:31.905 Could not start JACK. Sorry.[/COLOR]
 [COLOR=#999999]00:31:35.339 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]00:31:35.341 Post-shutdown script...[/COLOR]
 [COLOR=#990099]00:31:35.342 killall jackd[/COLOR]
 jackd: nessun processo trovato
 [COLOR=#999999]00:31:35.763 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#999999]00:31:56.518 Startup script...[/COLOR]
 [COLOR=#990099]00:31:56.519 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]00:31:56.923 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]00:31:56.924 JACK is starting...[/COLOR]
 [COLOR=#990099]00:31:56.925 jackstart -v -dalsa -r44100 -p64 -n3 -D -Chw:0 -Phw:0,0 -o1 -Xraw -zs[/COLOR]
 [COLOR=#ff0000]00:31:56.939 Could not start JACK. Sorry.[/COLOR]
 [COLOR=#999999]00:32:00.094 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]00:32:00.096 Post-shutdown script...[/COLOR]
 [COLOR=#990099]00:32:00.097 killall jackd[/COLOR]
 jackd: nessun processo trovato
 [COLOR=#999999]00:32:00.509 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#999999]00:32:34.580 Startup script...[/COLOR]
 [COLOR=#990099]00:32:34.581 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]00:32:34.985 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]00:32:34.986 JACK is starting...[/COLOR]
 [COLOR=#990099]00:32:34.987 /usr/bin/jackd -v -dalsa -r44100 -p64 -n3 -D -Chw:0 -Phw:0,0 -o1 -Xraw -zs[/COLOR]
 [COLOR=#999999]00:32:35.002 JACK was started with PID=2856.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1546278
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 no message buffer overruns
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 getting driver descriptor from /usr/lib/jack/jack_net.so
 JACK compiled with System V SHM support.
 server `default' registered
 [COLOR=#999933]00:32:35.133 Server configuration saved to "/home/redcat00/.jackdrc".[/COLOR]
 [COLOR=#999999]00:32:35.134 Statistics reset.[/COLOR]
 [COLOR=#999999]00:32:35.286 Client activated.[/COLOR]
 [COLOR=#cc9966]00:32:35.295 JACK connection graph change.[/COLOR]
 loading driver ..
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 new client: alsa_pcm, id = 1 type 1 @ 0x9409fd0 fd = -1
 apparent rate = 44100
 creating alsa driver ... hw:0,0|hw:0|64|3|44100|0|1|nomon|swmeter|-|32bit
 control device hw:0
 server thread back from poll
 new client: qjackctl, id = 2 type 2 @ 0xb773f000 fd = 16
 start poll on 4 fd's
 server thread back from poll
 new client qjackctl using 17 for events
 start poll on 4 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 0
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 17 for qjackctl starts at 7994381094
 back from client event poll after 16 usecs
 client qjackctl: wait_fd=24, execution_order=1 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 4 fd's
 configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 3 periods

---

### Post by AutoStatic on 2010-10-01
That's because you are now using **hw:0** as the soundcard while the Mia is **hw:Mia** (or **hw:2**). And set the number of output channels to default, setting it to 1 won't work.
You can enter card names manually in the Interfaces field of the QjackCtl Settings window. If you enter **hw:Mia** it should work. See the attached screenshot, you could try using it as an example.

---

### Post by aredcat66 on 2010-10-03
> **AutoStatic said:**
> That's because you are now using **hw:0** as the soundcard while the Mia is **hw:Mia** (or **hw:2**). And set the number of output channels to default, setting it to 1 won't work.
You can enter card names manually in the Interfaces field of the QjackCtl Settings window. If you enter **hw:Mia** it should work. See the attached screenshot, you could try using it as an example.

Thank you very mutch.
This time before to start the OS, I've changed the settings in the bios. I' ve disabled the on board sound card in the MB.
I' ve tried again with the setting you have shown to me but still Echo Mia MIDI  doesn't  work 
Perhaps there is a lot of difference between Echo Mia and Echo mia MIDI ?
I don't understand if it depends on the soundcard or on the "drivers"  or again on the compatibility of all my HW (MB, SOUNDCARD, other device ).
I can try to activate the on board Sound Card and see if it works under ubuntu ? Don't know I'll be more lucky. This will not solve my problem but perhaps may be useful to understand if the problem is due to Mia soundcard or other.
:

p, li { white-space: pre-wrap; } [COLOR=#999999]15:38:08.744 Logging started --- dom ott 3 15:38:08 2010 ---[/COLOR]
 [COLOR=#999999]15:38:08.814 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:38:08.852 Statistics reset.[/COLOR]
 [COLOR=#66cc99]15:38:09.098 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]15:38:09.399 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:40:43.067 Startup script...[/COLOR]
 [COLOR=#990099]15:40:43.068 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:40:43.471 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:40:43.473 JACK is starting...[/COLOR]
 [COLOR=#990099]15:40:43.474 /usr/bin/jackd -P69 -t2000 -dalsa -dhw:Mia -r44100 -p64 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]15:40:43.504 JACK was started with PID=2672.[/COLOR]
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1546278
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:Mia|hw:Mia|64|2|44100|0|0|nomon|swmeter|-|32bit
 [COLOR=#999933]15:40:45.797 Server configuration saved to "/home/redcat00/.jackdrc".[/COLOR]
 [COLOR=#999999]15:40:45.799 Statistics reset.[/COLOR]
 [COLOR=#999999]15:40:46.217 Client activated.[/COLOR]
 [COLOR=#cc9966]15:40:46.224 JACK connection graph change.[/COLOR]
 configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#996633]15:40:47.221 Buffer size change (64).[/COLOR]
 [COLOR=#cc9966]15:40:47.231 JACK connection graph change.[/COLOR]
 [COLOR=#cc66cc]15:40:47.237 XRUN callback (1).[/COLOR]
 [COLOR=#9999cc]15:40:47.245 JACK connection change.[/COLOR]
 [COLOR=#cc66cc]15:41:13.618 XRUN callback (2).[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 11.640 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 12.976 msecs[/COLOR]
 [COLOR=#cc99cc]15:41:14.427 XRUN callback (1 skipped).[/COLOR]
 [COLOR=#cc66cc]15:41:22.588 XRUN callback (4).[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 13.105 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 12.430 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 12.327 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 12.774 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 13.045 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 1.219 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 12.288 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 1.805 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 12.718 msecs[/COLOR]
 [COLOR=#999999]**** alsa_pcm: xrun of at least 0.116 msecs[/COLOR]
 [COLOR=#cc99cc]15:41:24.452 XRUN callback (9 skipped).[/COLOR]
 [COLOR=#cc66cc]15:46:04.117 XRUN callback (14).[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 3.098 msecs[/COLOR]

---

### Post by AutoStatic on 2010-10-03
It works! But you get major xruns which means JACK can't handle the incoming data/sound fast enough. You could try raising the number of Frames to 128 or 256 to see if that works better. And do you know if your CPU supports frequency scaling? If so, try adding the CPU frequency Scaling applet (one for each core) to your gnome-panel and set it to performance.

---

### Post by aredcat66 on 2010-10-05
> **AutoStatic said:**
> It works! But you get major xruns which means JACK can't handle the incoming data/sound fast enough. You could try raising the number of Frames to 128 or 256 to see if that works better. And do you know if your CPU supports frequency scaling? If so, try adding the CPU frequency Scaling applet (one for each core) to your gnome-panel and set it to performance.


I 've tryed to increase the value in the Frame/Period field and, after I've added the  &#8220;CPU Frequency Scaling Monitor&#8221; to the top bar I've verified that the CPU is set to "Performance".
Still I' don't hear anything in the headphones (while using xp it works, so I think it not depends on the HW).

Perhaps my hw is too old ? It's performance doesn't meet the minimum requirements for this distribution ? Or perhaps I'm drowning in a glass of 'water", I've to set some parameter in some system file and I need to read carefully  the documentation :).

It seems that also for basic features to work,  I need to study and understand better the OS

I admit my ignorance :confused:
However thank's for the time spent answering this questions.

P.S.
A strange thing happens. When I Switch off the Jack Audio Connection Kit the MIA Meters start to work (the bars iare flashing)  while when I start Jack the Meters stop work. The same with the player and the meters of Audacity. 


 p, li { white-space: pre-wrap; } [COLOR=#999999]22:45:11.185 Logging started --- mar ott 5 22:45:11 2010 ---[/COLOR]
 [COLOR=#999999]22:45:11.244 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:45:11.538 Statistics reset.[/COLOR]
 [COLOR=#66cc99]22:45:11.568 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]22:45:11.859 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:50:15.644 Startup script...[/COLOR]
 [COLOR=#990099]22:50:15.646 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:50:16.050 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:50:16.051 JACK is starting...[/COLOR]
 [COLOR=#990099]22:50:16.052 /usr/bin/jackd -P69 -t2000 -dalsa -dhw:Mia -r44100 -p256 -n3[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1546278
 no message buffer overruns
 [COLOR=#999999]22:50:16.128 JACK was started with PID=3102.[/COLOR]
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:Mia|hw:Mia|256|3|44100|0|0|nomon|swmeter|-|32bit
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 [COLOR=#999933]22:50:18.240 Server configuration saved to "/home/redcat00/.jackdrc".[/COLOR]
 [COLOR=#999999]22:50:18.241 Statistics reset.[/COLOR]
 [COLOR=#999999]22:50:18.291 Client activated.[/COLOR]
 [COLOR=#9999cc]22:50:18.293 JACK connection change.[/COLOR]
 [COLOR=#cc9966]22:50:18.312 JACK connection graph change.[/COLOR]

---

