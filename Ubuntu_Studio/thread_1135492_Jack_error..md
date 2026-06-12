---
title: "Jack error."
date: 2009-04-24
forum: Ubuntu Studio
---

### Post by LostMagix on 2009-04-24
Hello, my name is Chris.


I am running Ubuntu 9.04


Over that last few days, I have been trying to get jack working properly with no luck.  I decided to start from scratch so I reinstalled all the programs relating to jack. This is the first time I have ever had jack not work out of the box so Im lost.

In 8.10 jack worked fine, I don't know what happened.

here are a few outputs:

```
:~$ /usr/bin/qjackctl
Suspending PulseAudio
Xlib:  extension "RANDR" missing on display ":0.0".
```

Here is the error i get when starting jack controller:

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info

```
10:05:07.265 Patchbay deactivated.
10:05:07.268 Statistics reset.
10:05:07.310 ALSA connection graph change.
10:05:07.507 ALSA connection change.
10:05:25.270 Startup script...
10:05:25.270 artsshell -q terminate
sh: artsshell: not found
10:05:25.672 Startup script terminated with exit status=32512.
10:05:25.672 JACK is starting...
10:05:25.672 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
10:05:25.677 JACK was started with PID=4707.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211550016, from thread -1211550016] (1: Operation not permitted)
cannot create engine
10:05:25.960 JACK was stopped successfully.
10:05:25.960 Post-shutdown script...
10:05:25.961 killall jackd
jackd: no process killed
10:05:26.373 Post-shutdown script terminated with exit status=256.
10:05:27.718 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```



I know next to nothing about Jack,

---

### Post by LostMagix on 2009-04-24
I got a friend coming over latter and he really wants to try out the sound mixing stuff in Linux, I would like to get this fixed soon if I can.

---

### Post by LostMagix on 2009-04-24
Ok, I got jack to start after messing with the setting for a while, ending up un-checking "realtime".




creox still isnt working

gtkguitune stoped working

---

### Post by thorgal on 2009-04-25
LostMagix,

How did you update to 9.04 ? it is obvious from the output of jack that your realtime privileges have gone. Which kernel are you using by the way ?

About creox, I never used it but it seems to me that it is an old app that has not been updated for ages. On the other hand, jack has evolved a lot in a couple of years. The version you're using now is 0.116.1, which may have a different API than at the time creox was developed.

You know there are many ways to apply realtime effects on your input signal. What is it you're doing exactly ?

---

### Post by LostMagix on 2009-04-25
> **thorgal said:**
> LostMagix,

How did you update to 9.04 ? it is obvious from the output of jack that your realtime privileges have gone. Which kernel are you using by the way ?

I did a fresh install of the 9.04 beta, kernel 2.6.28-11.

> **thorgal said:**
> 
About creox, I never used it but it seems to me that it is an old app that has not been updated for ages. On the other hand, jack has evolved a lot in a couple of years. The version you're using now is 0.116.1, which may have a different API than at the time creox was developed.


You know there are many ways to apply realtime effects on your input signal. What is it you're doing exactly ?


Right now, I just want apply different effects to my friends and mine acoustic and electric guitars.

---

### Post by thorgal on 2009-04-25
is it this kernel that jaunty came up with ? ... I had little experience with 2.6.28 but it seemed more problematic than 2.6.29. I have been running 2.6.29.1-rt8 for some time now and it is the best RT kernel I've ever used in almost 2 years (built up my DAW in August-Sept 2007).

You could probably google about /etc/security/limits.conf and audio group but I would presume that installing Ubuntu Studio would take care of that. So is it Ubuntu Studio or plain Ubuntu that you installed ? 

About RT audio effects, there are a-plenty:
- guitarix
- rackarrak
- jack-rack with all the LADSPA suite
- ardour as a plugin host, simply add LADSPA or LV2 stuff on the master bus pre- or post fader, or declare more busses, no need to have tracks if you don't want to record anything. I think ppl underestimate ardour's capability as a simple effect box. Ardour by itself won't take much system resources, especially if you don't record or play back track data (disk-streaming). And the advantage is that you can do all sorts of crazy routing between busses.

---

### Post by LostMagix on 2009-05-07
Im sorry it took so long to get back.


I am indeed running 2.6.28-generic with Ubuntu 9.04, i did try installing U.S. on a different partition with the newer kernel but it didn't help.


I also tried those other programs you put up but they are doing the same thing.

---

### Post by LostMagix on 2009-05-07
This might be a clue, not sure what to make of it.

```
:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
Terminating processes: 3380 13264lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

```

---

### Post by LostMagix on 2009-05-07
Running both jack and creox as a super user it works so there are some permissions messed up somewhere.

---

### Post by mrowth on 2009-05-08
> **LostMagix said:**
> Running both jack and creox as a super user it works so there are some permissions messed up somewhere.

Do you or don't you have this in your /etc/security/limits.conf file?

```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -19
```

(This is from the JACK website. I don't know if those are the ideal settings for Ubuntu.)

It will allow members of the group "audio" to run stuff with realtime privileges. (Your user should be a member of that group.) You may have to reboot for it to take effect.

...Er... and/or try installing the "linux-rt" package, though the rt kernel that's currently available is not stable for me.

---

### Post by Nyrup on 2009-05-08
I've got the exact same problem.
Now I've tried to start jackctrl from the terminal with sudo and it starts with no
problems. However I need to do the same with Rosegarden and my system hangs.
I have checked /etc/security/limits.conf
Everything in there is commented out with #
I have added this:

@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -19

But it didn't  help.

Kind regard,
Nyrup

---

### Post by thorgal on 2009-05-08
Hej Nyrup,

You must log out and log in again after changing something in this system file.

You also want to make sure you belong to the audio group.

In a terminal, type
```

id

```

check that 'audio' is part of the groups listed in the output.

If not, check that you do have an audio group:

```

cat /etc/group | grep audio

```
if nothing pops up, you have no audio group.
if that's the case (only if that's the case), you can just use your own group (username is also being used as primary group name in ubuntu, as far as I know).

So in this case, you replace @audio by @your-user-name in /etc/security/limits.conf

But not having an audio group would be pretty strange in a debian based system. If you do have an audio group and don't belong to it (strange but anything can happen), just add yourself to it:

```

sudo adduser your-user-name audio

```

log out and log in again.

Hilse fra Danmark :)

---

### Post by Nyrup on 2009-05-09
Hi
Thanks a lot!
Mange tak!:)

It works! - Thats great!
I would never have got it to work if it weren't for you guys.
Actually I tried an install of Ubuntu 9.04 on my stationary Pentium 4 based
PC with the exact same problem.
It seems that I am not member of the Audio group on the system even though
the Audio group do exist.
Also it is necessary to make the change to /etc/security/limits.conf 

Thanks again.
Nyrup.
PS. Det var vist at gå over åen efter vand. - Verden er lille.8-)

---

### Post by LostMagix on 2009-05-11
> **thorgal said:**
> Hej Nyrup,

You must log out and log in again after changing something in this system file.

You also want to make sure you belong to the audio group.

In a terminal, type
```

id

```

check that 'audio' is part of the groups listed in the output.

If not, check that you do have an audio group:

```

cat /etc/group | grep audio

```
if nothing pops up, you have no audio group.
if that's the case (only if that's the case), you can just use your own group (username is also being used as primary group name in ubuntu, as far as I know).

So in this case, you replace @audio by @your-user-name in /etc/security/limits.conf

But not having an audio group would be pretty strange in a debian based system. If you do have an audio group and don't belong to it (strange but anything can happen), just add yourself to it:

```

sudo adduser your-user-name audio

```

log out and log in again.

Hilse fra Danmark :)

This also worked for me, thanks you very much!!



Thread = solved

Time to jam out!!

---

