---
title: "playing/recording my guitar via guitarport in any program"
date: 2009-07-07
forum: Ubuntu Studio
---

### Post by JohnsShadow on 2009-07-07
hey guys i recently upgraded to 9.04 and im having a noob moment 

i have a device called guitarport made by line6
[http://line6.com/guitarport/](http://line6.com/guitarport/)

i used this guide to get the device reconized by gnome
[http://ubuntuforums.org/showthread.php?t=1163608](http://ubuntuforums.org/showthread.php?t=1163608)

it worked when i got to : system<prefrences<sound, i can set the audio capture as line6 guitar port with choices of ( alsa / oss ) i went with alsa because the rest of my system dose

im trying to simply play my guitar (with some distortions) and recording would be nice but i would be happy with a live feed :guitar:

i have downloaded several programs but cant get them to work NOTE: using gnome 2.26.0

creox c    (synaptic) 0.2.2rc (kde app) works but i have no idea how to even configure it

Jack Rack  (repository) crashes instantly (i also grabed jack control &jack EQ) was looking for jack server to make rosegarden happy but couldnt find it

rosegarden (repository) 1.7.2 (kde app)
i get some weird errors with rosegarden 

```
Failed to connect to JACK audio server.
Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.
```

```
System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See http://rosegarden.wiki.sourceforge.net/Low+latency+kernels for notes about this.
```

```
Helper programs not found
Rosegarden could not find one or more helper programs which it needs to provide some features. The following features will not be available:
Export and import of Rosegarden Project files
To fix this, you should install the following additional programs:
kdialog - for project file support
```

---

### Post by kayosiii on 2009-07-07
Most interesting audio production software on Ubuntu requires jack to be running. The easiest way to run and set up jack is to use the jack control tool. There are a lot of performance tweaks that can be made to get Jack to run really well I will leave it up to you to search these forums to find your answers to all of that.

---

### Post by JohnsShadow on 2009-07-08
so turn on jack connection kit ok done

```
Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.
```

```
23:52:40.172 Patchbay deactivated.
23:52:40.184 Statistics reset.
23:52:40.229 ALSA connection graph change.
23:52:40.462 ALSA connection change.
23:52:40.464 ALSA connection graph change.
23:53:28.011 ALSA connection change.
23:53:28.052 ALSA connection graph change.
23:53:33.468 ALSA connection change.
23:53:35.748 ALSA connection change.
23:53:38.691 ALSA connection change.
00:01:58.152 Startup script...
00:01:58.153 artsshell -q terminate
sh: artsshell: not found
00:01:58.555 Startup script terminated with exit status=32512.
00:01:58.556 JACK is starting...
00:01:58.557 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -P -Xraw
00:01:58.563 JACK was started with PID=5382.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210915136, from thread -1210915136] (1: Operation not permitted)
cannot create engine
00:01:59.012 JACK was stopped successfully.
00:01:59.013 Post-shutdown script...
00:01:59.014 killall jackd
jackd: no process killed
00:01:59.442 Post-shutdown script terminated with exit status=256.
00:02:00.693 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

thats the error i get when i press the start buttion in jact connection kit shall i take a screen shot of my configurations?
i have no idea what im doing configuring this is like speaking an alien language to me

terminated with exit status=256 any idea what exit status 256 is?

i have been playing with settings but still cant get it to start

What happned to ubuntu's pholisophy (it should just work)

---

### Post by dawiba on 2009-07-08
Open Jack Control.

Click on 'Setup'.

Make sure 'alsa' is selected in the drop down menu over to the right hand side (in my attachment it says 'firewire' because that's what I use).

Over on the left, uncheck the 'realtime' box (you can see it's checked in my attachment).

Save and close 'setup' window.

Click on the start button on Jack Control.

Hopefully you'll be good to go ;)

---

### Post by JohnsShadow on 2009-07-08
I love you

when i pressed the start buttion it started with no errors :D

here is a screeny

and now jack rack finally boots up 

now i just gotta get it to play back the stuff i play on guitar....

O_O sooo many menu's

---

### Post by sgx on 2009-07-09
Hi, I use the line-out from a Line6 Spider III amp to connect my guitar to my soundcard line-in, and that is connected to rakarrack multifx app
using qjackctl. Super simple and effective, and sounds better than costly guitar fx programs. I record with Reaper 3.05  or Cantabile 1.2 using wine/wineasio. Cheers

---

### Post by JohnsShadow on 2009-07-09
i found a ppa of rakarrack 3.0 for 32bit

rakarrack
[https://launchpad.net/~rzr-team/+archive/ppa](https://launchpad.net/~rzr-team/+archive/ppa)

couldnt get it to install tho (not shure how i managed that)

and im not shure what happned but the jack server (jack connection kit / qjackctl ) stoped working, i did nothing i swear

i get this error

```
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
```

im confused it was working fine with alsa not even 2 hours ago...

---

### Post by sgx on 2009-07-09
> **JohnsShadow said:**
> i found a ppa of rakarrack 3.0 for 32bit

rakarrack
[https://launchpad.net/~rzr-team/+archive/ppa](https://launchpad.net/~rzr-team/+archive/ppa)

couldnt get it to install tho (not shure how i managed that)

and im not shure what happned but the jack server (jack connection kit / qjackctl ) stoped working, i did nothing i swear

i get this error

```
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
```

im confused it was working fine with alsa not even 2 hours ago...

sometimes a web app, or sound app hogs the pcm device. Did a cold start
change the faulty behaviour, or error message? Is the pulseaudio system installed? That can bring fits of random bad luck! Is aoss installed? That brings good luck!

Try your root user running the alsaconf command to reconfigure alsa.

 I made a .deb file from a rakarrack .rpm file using the alien command

alien rakarrack-xxx.rpm

This will make a .deb version in the same directory.

dpkg -i rakarrack-xxx.deb

will install it. The version I have required no dependancies, if you get some, use synaptic to install them, then run the dpkg -i as above.
Cheers

---

### Post by JohnsShadow on 2009-07-10
i would like to try your ppa of rakarrack

could not find you on launch pad

do you go by another name there

was the ppa i posted yours?

and yes a hard reset has cleared up the trouble with asla

just a question tho what dose the "connection" tab (on qjackctl) do and is there a proper way to configure it?

ive had bad luck finding manpages (still searching)

---

### Post by sgx on 2009-07-11
> **JohnsShadow said:**
> i would like to try your ppa of rakarrack

could not find you on launch pad

do you go by another name there

was the ppa i posted yours?

and yes a hard reset has cleared up the trouble with asla

just a question tho what dose the "connection" tab (on qjackctl) do and is there a proper way to configure it?

ive had bad luck finding manpages (still searching)

This links to a Fedora Linux download for Rakarrack

[http://nettowa-ku.net/2009/03/31/rakarrack-fedora-10-package](http://nettowa-ku.net/2009/03/31/rakarrack-fedora-10-package)

This should work with the alien and dpkg commands, as noted in a previous post. If you start qjackctl, click the connect button, and there will appear tabs for audio, midi, and alsa. If you start rakarrack, you'll see it appear in the alsa and audio tabs,  so
select it, and each input/output you want to connect it with, and then press the connect button. Start zynaddsubfx, and connect it to rakarrack in this way: in the audio tab, click the system + widget on the right half of the panel, it will expand to show your audio input ports. Click the + widgets for rakarrack and zynaddsubfx to see their outputs, you want zynaddsubfx output going to rakarrack input. The, rakarrack output going to system input.

Back on the main qjackctl panel, find the > widgets (far right, halfway down, one for input devices, one for output devices. Click those to see devices your system recognizes. If your guitarport is there, you can stop jackd from the main panel, select your guitarport, restart jackd, and make that fateful strum!

Zyn has many sounds, the menu Instrument --> show instrument bank opens a window, find and click the triangle widget by the 'Refresh bank list' button to see the categories of sounds. Pick one of the guitars, and enjoy rakarrack (which has a button in its upper-left corner labeled 'fx'
which you must click to start the fx.
Creox fx app can be used the same way, also has an off/on button, and the fx in it can be used together, or individually by selecting the ones you want, and using the sliders to adjust settings. Nice tremolo and echo and phaser! A notebook is handy for so many options to remember!

Cheers

---

### Post by JohnsShadow on 2009-07-20
> **sgx said:**
> 
 I made a .deb file from a rakarrack .rpm file using the alien command

alien rakarrack-xxx.rpm

This will make a .deb version in the same directory.

dpkg -i rakarrack-xxx.deb

will install it. The version I have required no dependancies, if you get some, use synaptic to install them, then run the dpkg -i as above.
Cheers

durring the alien creation of rakarrack i got this

```
johnsshadow@JsX-Evil-PC:~/Desktop$ sudo alien rakarrack-0.3.0-2.fc10.i386.rpm
Warning: Skipping conversion of scripts in package rakarrack: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
rakarrack_0.3.0-3_i386.deb generated
johnsshadow@JsX-Evil-PC:~/Desktop$ 
```

sorry it took so long to reply ive been dealing with some ********

---

