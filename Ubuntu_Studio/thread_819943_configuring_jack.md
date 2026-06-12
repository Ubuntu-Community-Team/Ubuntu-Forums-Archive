---
title: "configuring jack"
date: 2008-06-05
forum: Ubuntu Studio
---

### Post by le_vainqueur on 2008-06-05
I just did a fresh install of Ubuntu Studio to make sure that there were no problems as I start to set up my computer to record audio.  I am following this guide to get jack up and running:
> [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

Question 1: I am not sure what my audio device is.  My soundcard is simply the chipset built into [my mother board]("http://www.intel.com/products/motherboard/D946GZIS/"). My options in jack control are:
> hw:0 HDA Intel
hw:0,0 STAC92xx Analog
default
Regardless of which I choose, I seem to have the same result, so...on to question 2...

Question 2: Xruns...I read the documentation, and increased the Frames/Period as outlined in the guide, but I still get xruns when I start jack server.  Here is the output in the message box
> 20:09:56.006 Patchbay deactivated.
20:09:56.175 Statistics reset.
20:09:56.234 ALSA connection graph change.
20:09:56.391 ALSA connection change.
20:10:02.517 Startup script...
20:10:02.517 artsshell -q terminate
20:10:02.939 Startup script terminated with exit status=256.
20:10:02.939 JACK is starting...
20:10:02.940 /usr/bin/jackd -R -dalsa -dhw:0,0 -r44100 -p1024 -n2 -m
20:10:02.948 JACK was started with PID=13132.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
20:10:05.006 Server configuration saved to "/home/brandon/.jackdrc".
20:10:05.008 Statistics reset.
20:10:05.013 Client activated.
20:10:05.018 JACK connection change.
20:10:05.020 JACK connection graph change.
cannot lock down memory for RT thread (Cannot allocate memory)
**** alsa_pcm: xrun of at least 0.011 msecs
20:10:42.866 XRUN callback (1).



Thanks for the help,

LV

---

### Post by Stochastic on 2008-06-05
> **le_vainqueur said:**
> Question 1: I am not sure what my audio device is.  My soundcard is simply the chipset built into [my mother board]("http://www.intel.com/products/motherboard/D946GZIS/"). My options in jack control are:

Regardless of which I choose, I seem to have the same result

Yup, basically hw:0 points to hw:0,0 by default (some cards have hw:0,1 and hw:0,2).

> Question 2: Xruns...I read the documentation, and increased the Frames/Period as outlined in the guide, but I still get xruns when I start jack server.

Do you get xruns all the time, or just when jack starts?

---

### Post by thorgal on 2008-06-06
intel HDA ? try setting the "periods/buffer" to 3 in the qjackctl control window.

There's also a kernel module option you may want to try at loading time for the intel-hda, which is something like "position_fix=1". If it sounds chinese to you, ask someone who can tweak your kernel module options (somewhere in /etc/modprobe.d/alsa-base or something like that).

---

### Post by rab4567 on 2008-06-06
Hey I finally got jack to work with audacity but  I'm getting back ground buzzy noise and this is what I'm getting in the terminal
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
no more csLADSPA plugins


**** alsa_pcm: xrun of at least 0.044 msecs



**** alsa_pcm: xrun of at least 0.041 msecs

Any way to fix this, I'm so close.

---

### Post by rab4567 on 2008-06-06
I'm noticing some stuttering and xruns from 0.028 to 0.068 msecs.

---

### Post by kramthegram on 2008-06-06
Here is one problem:
> JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory

to fix this you need to edit your /etc/security/limits.conf file
$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
$ sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

you also need to make sure that the group audio exists and that you are a member of that group, this will give you high priority ability, along with an aggressive nice setting and the ability to memlock(fixes the error you were getting)


also, if you are running the real-time kernel(which you should be for audio production) you need to edit your kernel boot line in /boot/grub/menu.lst

it should look something like this...

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-rt root=UUID=d01c8f74-2cb0-4f2e-940e-8428084b03f3 ro quiet splash **nohz=off**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

the nohz=off parameter turns of tickles operation, which is causing a problem in the realtime kernel currently, this will drastically reduce xruns if this was you problem, hope this helps

---

### Post by le_vainqueur on 2008-06-09
Thanks for the tips everyone, here are my results:

> Do you get xruns all the time, or just when jack starts?
All the time.  They come a lot more often once I start up Audacity, though.

> you also need to make sure that the group audio exists and that you are a member of that group
Add a user group named "audio" and make sure I'm in it?  Are there special settings I should be employing.

> to fix this you need to edit your /etc/security/limits.conf file
That fixed the memory error, Thanks!

> you need to edit your kernel boot line in /boot/grub/menu.lst
By default, the Ubuntu Studio Grub menu looks like this:
> title		Ubuntu 8.04, kernel 2.6.24-18-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=1d21bee4-9f1d-4e1b-b7a0-9180cc1f2717 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet
Is this the appropriate modification?
> title		Ubuntu 8.04, kernel 2.6.24-18-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=1d21bee4-9f1d-4e1b-b7a0-9180cc1f2717 ro quiet splash nohz=off
initrd		/boot/initrd.img-2.6.24-18-rt
quiet
If so, it doesn't seem to have fixed my xruns error.

> intel HDA ? try setting the "periods/buffer" to 3 in the qjackctl control window
I get this error when changing to 3:
> 18:39:07.673 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info

I made the above changes, and no longer have the memory error, but there are still xruns.  Audacity is still unable to record any audio. Here is my new message window:

> 
18:52:45.058 Patchbay deactivated.
18:52:45.161 Statistics reset.
18:52:45.200 ALSA connection graph change.
18:52:45.373 ALSA connection change.
18:52:47.909 Startup script...
18:52:47.910 artsshell -q terminate
18:52:48.331 Startup script terminated with exit status=256.
18:52:48.331 JACK is starting...
18:52:48.332 /usr/bin/jackd -R -dalsa -dhw:0,0 -r44100 -p1024 -n2 -m
18:52:48.340 JACK was started with PID=6227.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
18:52:50.382 Server configuration saved to "/home/brandon/.jackdrc".
18:52:50.383 Statistics reset.
18:52:50.410 Client activated.
18:52:50.413 JACK connection change.
18:52:50.416 JACK connection graph change.



Also,

> ...If it sounds chinese to you...
That part is most definitely Chinese...is it something an amateur could do?

Any more ideas?  I sure do need them.

---

### Post by le_vainqueur on 2008-06-16
*bump*

---

### Post by userfriendly on 2008-06-17
> **le_vainqueur said:**
> *bump*
...and another *bump* from me. I'm having troubles with the Jack, too.

My system:

- RME HDSP Multiface
- Via chipset (with onboard audio)
- Ati HD2600XT (apparently also with audio)
- Ubuntu Studio 8.04, kernel 2.6.24-19-rt

My problems:

- can't get Jack to work properly.
- audio devices seem to arbitrarily switch their indices with each reboot (sometimes the HDSP is hw:3, sometimes it's hw:2 - I suspect best would be getting it to be hw:0 and stay hw:0)

What I did so far:

[LIST]
[*]did a fresh install of Ubuntu Studio 8.04
- Host error LED of HDSP box remained lit
- I remembered that it needs its firmware, googled a bit and...
[*] installed alsa-firmware-loader
[*] ran hdsploader
- it complained about not finding firmware for HDSP
[*] found me a multiface_firmware_rev11.bin and placed it in the expected folder
[*] ran hdsploader again
- that seemed to work, gave me HDSP as hw:3
[*] started jack control and followed these instructions: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)
- kept getting complaints about Jack not being able to allocate memory
[*] edited the limits.conf like mentioned above
- that did it, so I went and started Ardour, marveled at the strangeness of the interface (I'm used to Cakewalk Sonar), when suddenly:
[/LIST]
> ALSA: poll time out, polled for 2176047 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken...

at this point I'm tempted to go back to Windows XP again. It's just that I don't really want to. I'm using Ubuntu for virtually every other thing, and I hate to boot into Windows every time I want to make some music. So... I suppose I'll keep tinkering with it, and I'd appreciate any help you guys can offer.

---

### Post by userfriendly on 2008-06-17
now i added "nohz=off" to my boot options, rebooted the machine - and lo and behold, ardour plays back my audio file =) well, so far. *knocks on wood*

hmmmmmm. i really hope i don't have to bug you guys anymore. heh. in any case, many thanks again to you, this forum is really the greatest. ever.

now off to learn ardour. yay. hopefully the hdsp remembers to stay hw:3 <_<

---

### Post by userfriendly on 2008-06-17
oh well... =(

when i edited a text file to keep some notes, gnome froze on me. i rebooted the machine. started jack. and moved my mouse pointer over a .wav file on my desktop. it played back nicely, but jack died again:

> ALSA: poll time out, polled for 2175953 usecs
DRIVER NT: could not run driver cycle
22:21:13.859 Shutdown notification.
22:21:13.865 JACK is stopping...
22:21:13.868 JACK is being forced...
jack main caught signal 12
no message buffer overruns
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler
22:21:14.069 JACK was stopped successfully.
22:21:14.069 Post-shutdown script...
22:21:14.070 killall jackd
jackd: Kein Prozess beendet
22:21:14.514 Post-shutdown script terminated with exit status=256.

apparently there's still something wrong with it. *sigh*

and now i can't restart it:

> 22:26:20.904 Patchbay deactivated.
22:26:21.058 Statistics reset.
22:26:21.097 Startup script...
22:26:21.097 artsshell -q terminate
22:26:21.136 ALSA connection graph change.
22:26:21.522 Startup script terminated with exit status=256.
22:26:21.522 JACK is starting...
22:26:21.523 /usr/bin/jackd -R -m -dalsa -r44100 -p64 -n2 -D -Chw:3 -Phw:3 -m
22:26:21.525 JACK was started with PID=6114.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:3|hw:3|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:3
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
22:26:21.726 ALSA connection change.
ALSA: poll time out, polled for 2176053 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
22:26:23.725 JACK was stopped successfully.
22:26:23.725 Post-shutdown script...
22:26:23.726 killall jackd
22:26:23.737 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
jackd: Kein Prozess beendet
22:26:29.446 Post-shutdown script terminated with exit status=256.

---

### Post by userfriendly on 2008-06-17
alright. i have officially not a clue what i'm doing. but i think the trouble is related to my having multiple audio devices in my system. jack remained suicidal and going to system->preferences->audio and clicking on "test" (i have it set to "detect automagically) resulted in an error message about the system not being able to use the soundcard. which one ever... so i went and disabled the onboard sound in the bios.

started again. same result. meh. then i looked again for a solution for this specific problem (multiple cards), and came across this: [http://ubuntuforums.org/showthread.php?t=27186](http://ubuntuforums.org/showthread.php?t=27186) - i followed the instructions, still having no clue. but magically, it worked.

now, as far as i can tell (which isn't very far, to be honest), i have the problem that udev assigns the indices to the devices depending on how it feels like when the machine starts. sometimes the hdsp is hw:2, sometimes it's hw:1 - every time it changes i have to change the settings in jack control. after doing that, it works. more or less. getting some xruns, but not many.

i still don't have sound in adobe flash, though. but the "test" in system->preferences->audio yields the obnoxious beep, i can play back files with totem and ardour plays my tracks. still not perfect, but i'm getting there. eventually. probably some time next year. <_<

so... is there a way to make udev stop switching the cards around? alternatively, how do i kill off the hdmi audio of my graphics card? i googled until my fingers were bleeding but i haven't found a solution to that yet.

also, "snd_mpu401" - is that the midi portion of the hsdp? or is it something else? because it wants to be a hw:n, too, and udev loves to juggle and all too gratefully accepts it.

---

### Post by thorgal on 2008-06-17
for the index order, you need to specify it in /etc/modprobe.d/alsa-base :

```

options <your sounds module> index=n

```

where <your sound module> is snd-whatever and n is one of 0, 1, 2, etc.

For flash videos (youtube, etc), I use oss2jack, a jack client that creates a "fake" /dev/dsp. All apps using OSS io calls will be fooled by this, it is very cool :)

oss2jack requires a few things :

- disable the alsa oss emulation layer
- compile fusd which will give you a kernel module called kfusd to be loaded at boot time
- having a udev rules for fusd so that the audio group have write permission on fusd dev nodes (/dev/fusd/control and /dev/fusd/status)
- compile oss2jack.

Once you have all of this compiled and set up correctly, just fire up oss2jack after jackd is running. You can do so from a terminal or from the app launcher (Alt+F2 in KDE, I don't know in gnome).

but I see in your previous post that you want to run things at 64 frames at period 2. It is a challenging jack setting ... why don't you increase to 128 or 256 ? the increased latency won't be felt or very little and you will have improved jack stability, especially if you run oss2jack which is not the fastest client ever.

---

### Post by userfriendly on 2008-06-17
> **thorgal said:**
> for the index order, you need to specify it in /etc/modprobe.d/alsa-base :

```

options <your sounds module> index=n

```

where <your sound module> is snd-whatever and n is one of 0, 1, 2, etc.
tried that, but... now the hdsp disappeared from /proc/asound/modules completely. :o i put it at the end of the file, was that maybe not-so-correct?

> **thorgal said:**
> For flash videos (youtube, etc), I use oss2jack, a jack client that creates a "fake" /dev/dsp. All apps using OSS io calls will be fooled by this, it is very cool :)

oss2jack requires a few things :

- disable the alsa oss emulation layer
- compile fusd which will give you a kernel module called kfusd to be loaded at boot time
- having a udev rules for fusd so that the audio group have write permission on fusd dev nodes (/dev/fusd/control and /dev/fusd/status)
- compile oss2jack.

Once you have all of this compiled and set up correctly, just fire up oss2jack after jackd is running. You can do so from a terminal or from the app launcher (Alt+F2 in KDE, I don't know in gnome).
thanks. :) will try that as soon as i have jack and stuff set up in a reliable way.

> **thorgal said:**
> but I see in your previous post that you want to run things at 64 frames at period 2. It is a challenging jack setting ... why don't you increase to 128 or 256 ? the increased latency won't be felt or very little and you will have improved jack stability, especially if you run oss2jack which is not the fastest client ever.
will try that, too. i notice that after a while, jack dies off again. maybe that solves this particular annoyance.

---

### Post by thorgal on 2008-06-17
copy / paste here what you wrote in the alsa module file without any modification. The right spaces are important in this matter. I know someone who had a problem because of a misplaced space (he wrote index = 1, and not index=1 which is the correct form).

what version of jackd are you using ? I am following discussions on the jackaudio mailing list. The latest svn source code has many bug fixes, especially bugs that make jackd crash or zombify apps.

Actually, in my studio, I always go for the latest svn code (at least for ardour 2.4 and jack) because the developers are fixing tons of bugs. They want to release jack 1.0 and ardour 2.5 so it is a good time to catch on bug fixes :)

---

### Post by userfriendly on 2008-06-17
> options snd-hdsp index=0

i'm using the jack version that came with ubuntu studio 8.04, which is 0.3.2 - will check out the latest code next.

seriously, thanks for your help. it has to work, and i'll get there eventually. :)

---

### Post by thorgal on 2008-06-17
you're welcome :) I have been through this myself about a year ago ... it does pay off when it finally decides to play nice!

about the jackd version, you confuse qjackctl and jackd. qjackctl is just a graphical frontend to jackd. The latest official jackd release is more like 0.109.2 or something like that. Have a look at [www.jackaudio.org](www.jackaudio.org) for more info.

---

### Post by userfriendly on 2008-06-17
> **thorgal said:**
> about the jackd version, you confuse qjackctl and jackd.
oops. yeah. the thought crossed my feeble mind. :D anyway, the version in the svn repository is very probably newer than the one that came with the os.

will continue tomorrow, it's 2am over here now. thanks & good night for now. :)

---

### Post by userfriendly on 2008-06-18
alright, situation report. haven't compiled jack anew yet, been playing around with several pieces of software, mostly players. vlc and totem - i get lets of xruns when playing back *.mkv files in vlc, and every 5 to 20 minutes jack drops dead, sometimes taking gnome with it. have to reboot to get it working again. playing back *.wav, *.mp3 and *.wma files in totem, however, seems to work fine without xruns or other stuff, at least for the past hour that i'm trying it.

been thinking about possible reasons for the troubles - might it be an interrupt problem? or is that a thing of the past? haven't had these kinds of problems under windows for years... pretty much since windows xp, i think.

here's the output of hdsploader, btw:
> hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : HDA ATI HDMI at 0xff4ec000 irq 21
Card 1 : RME Hammerfall DSP at 0xff6e0000, irq 22
Upload firmware for card hw:1
Firmware uploaded for card hw:1
Card 2 : MPU-401 UART at 0x330, irq 5
this time putting the hdsp as hw:1 again.

since i'm not using hdmi, i'd love to disable that audio device of my graphics card. not sure if that would really help, but at least it removes one more thing eating up stuff. also, i still have no clue what that mpu-401 thing is supposed to be. might it be something on my mainboard? it doesn't have a gameport or anything. just a soundcard that i already disabled. or is it the MIDI portion of the hdsp, and is treated as a separate device?

things i will try tonight:
[LIST]
[*]checking out latest svn code of jack and compiling it.
[*]trying to convince udev to let the hdsp keep the hw:0 designation.
[*]playing around with jack setup (buffers, timeout etc.) in order to achieve xrun-free playback of *.mkv files in vlc.
[/LIST]

if all else fails, i'll probably go with another fresh ubuntu studio install, this time using latest svn code for jack from the get-go, documenting every single step i take.

ETA... re: interrupts... i'm seeing from the output of hdsploader that the hdmi audio has a lower irq than the hdsp, meaning a higher priority if i remember that kind of thing correctly. so i'm guessing that this is the case for the actual graphics portion of the ati card as well. which, looking at how playing back *.mkv video files behaves compared to playing back only audio files, leads me to believe it might indeed be related.

---

### Post by userfriendly on 2008-06-18
so... i'm skipping the attempts to repair this and start anew. and sorry for hijacking this thread, i went and created my own: [http://ubuntuforums.org/showthread.php?t=833212](http://ubuntuforums.org/showthread.php?t=833212)

---

