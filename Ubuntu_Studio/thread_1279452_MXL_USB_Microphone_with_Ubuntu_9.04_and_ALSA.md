---
title: "MXL USB Microphone with Ubuntu 9.04 and ALSA"
date: 2009-09-30
forum: Ubuntu Studio
---

### Post by nawtion on 2009-09-30
Hello,
 I'm running Ubuntu 9.04 on a gateway (S-7320M - [http://www.gateway.com/product_spec.php?product_recid=529666064](http://www.gateway.com/product_spec.php?product_recid=529666064)), and I'm having some trouble configuring my USB Microphone (MXL USB.006). I would like to be able to use it with Audacity/skype/etc. I have ALSA installed, but as I am relatively new to linux, I have little idea wihat that is doing for me.  Should I be installing a sound server, or is there a driver that I need to install?

Thanks!

---

### Post by stolenbaby on 2009-09-30
Someone named mr. thraz seems to be using that mic- perhaps he could tell you what driver is needed?

saw his setup on this thread:
[http://ohioloco.ubuntuforums.org/showthread.php?p=7902611](http://ohioloco.ubuntuforums.org/showthread.php?p=7902611)

With all that equipment, I'm sure he's using Jack, but he might be of some help.  Best of luck!

---

### Post by nawtion on 2009-10-01
Thanks
 
I checked out that post.  I guess my follow up question is what is the difference between ALSA and JACK.  Are they different programs, or do they do the same thing?  I've searched the interwebs, but thus far have had little luck figuring out what exactly they do.  I've had Ubuntu Studio installed before, but I switched to Jaunty because it was more multi purpose for me.

---

### Post by solarbird on 2009-10-02
They're different and you likely need both. You always need ALSA. ALSA is the set of standard libraries and the driver specs for how to control soundcards and access their features in a standard way. It also includes some utilities to do things like set volume levels, recording levels, things like that, if you don't have anything else doing that for you.

JACK, by contrast, is a virtual plugboard. It lets you connect different sound components together. These components can be ALSA-supported hardware (like soundcards, accessed through their ALSA drivers) or software (like, say, Ardour) or both. JACK lets you connect different pieces of sound software directly to each other as well, like, say, routing the output from one piece of software (say, a media player) to the inputs of another (say, again, Ardour). So you could use it to run a signal from a hardware input through a piece of software that does one set of processing to another piece of software that does more processing to Ardour for recording purposes.

Does that make sense? I've probably left some stuff out but that's the main idea as I understand it. (I find JACK very confusing in practical use but awfully cool in theory.)

Here this might help too: [http://alsa.opensrc.org/index.php/ALSA](http://alsa.opensrc.org/index.php/ALSA)

---

### Post by raboofje on 2009-10-02
Also, [http://wiki.linuxaudio.org/wiki/audio_layers_overview](http://wiki.linuxaudio.org/wiki/audio_layers_overview)

---

### Post by nawtion on 2009-10-03
Thanks, I'll be sure to read that.

---

### Post by nawtion on 2009-10-08
Ok, I read those websites, but I'm still confused.  I have JACK installed now, but now I have no sound.  Will JACK work well with laptops that don't have a sound card?  I had Pulse Audio installed, and, after a little trial and error, was able to use my microphone with Audacity.  But after switching to jack I  couldn't seem to find my microphone.

---

### Post by solarbird on 2009-10-09
Okay, first: you have a soundcard. Actually, since the USB microphone is technically an input-only soundcard, you have two, at least when the microphone is hooked up. The other one is on the motherboard; according to Gateway, it's a SigmaTel STAC9200. (See [here]("http://support.gateway.com/s/Mobile/2007/Orion/1014335R/1014335Rsp2.shtml") for details.) 

PulseAudio is a server that works with ALSA-compatible drivers but is not a Jack replacement. Unless there's a specific reason not to, you can and for ease of use probably should have both PulseAudio and Jack on the machine. (I find that PulseAudio makes it easier to assign system noises, for example, and things like the default system output device.) Did you remove PulseAudio?

What does JACK say in the output log when it starts up? Can you paste that in here?

---

### Post by nawtion on 2009-10-12
Ok, I plugged in the microphone, and ran qjackctl...here's the message
 p, li { white-space: pre-wrap; }  [COLOR=#999999]12:39:02.139 Startup script...[/COLOR]
 [COLOR=#990099]12:39:02.140 artsshell -q terminate[/COLOR]
 [COLOR=#FF0000]sh: artsshell: not found[/COLOR]
 [COLOR=#999999]12:39:02.545 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:39:02.545 JACK is starting...[/COLOR]
 [COLOR=#990099]12:39:02.545 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#FF0000]no message buffer overruns[/COLOR]
 [COLOR=#FF0000]jackd 0.116.1[/COLOR]
 [COLOR=#FF0000]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#FF0000]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#FF0000]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#FF0000]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#FF0000]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#FF0000]cannot use real-time scheduling (FIFO at priority 10) [for thread -1208375616, from thread -1208375616] (1: Operation not permitted)[/COLOR]
 [COLOR=#FF0000]cannot create engine[/COLOR]
 [COLOR=#999999]12:39:02.568 JACK was started with PID=4156.[/COLOR]
 [COLOR=#999999]12:39:02.582 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:39:02.583 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:39:02.583 killall jackd[/COLOR]
 [COLOR=#FF0000]jackd: no process found[/COLOR]
 [COLOR=#999999]12:39:02.991 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]12:39:04.711 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I still have pulse audio installed.  Thanks for looking at this!

---

### Post by solarbird on 2009-10-14
Okay, Jack is starting but then shutting right back down. So Jack is not actually running. This is because it's trying to run in realtime mode, but doesn't have permission. This is *usually* caused by one of these things: either you don't have the realtime kernel installed, your user isn't a member of the "audio" user group and therefore doesn't have realtime privileges, or the audio user group doesn't have realtime privileges.

However, it might be easier to try to _not_ run Jack in realtime and see whether that works for you. In the Jack control settings panel, on the left, there will be a checkbox for realtime. Uncheck it and see whether Jack starts and keeps running. If you can't tell whether it keeps running, paste the new output into a reply like you did last time.

If Jack does run, and everything works and you don't get buffer xruns, then you could call yourself finished! Yay!

However, if you really need realtime kernel, check to see whether you're in the audio group. Open a terminal window and type:

id

If "audio" is one of the groups that are listed in the output, then you are a member of that group. Hopefully you are. If you are, and if you're booting off a -rt kernel (the kernel name should have "-rt" at the end of it) then look at the file /etc/security/limits.conf and see whether it has lines like these in it:

@audio - rtprio 90
@audio - nice -19
@audio - memlock unlimited

If it doesn't have those lines, add them and reboot.

---

### Post by surfed on 2009-10-15
Trying to get Jack to work so you can use your mic is total overkill. Trash Jack.
try in a console
alsamixer -c1
(-c1 is your second card assuming your first is onbord audio and your second usb mic)
then with tab change to capture tab, space toggles capture on/off, up/down changes volume
your mic will not play back directly, so you need to check with skype test call. make sure you configure skype to use the correct recording device, it should be USB Device xxxxx:xxxxx, USB Audio Default Device or similar. Allow skype to change mixer levels too.

---

