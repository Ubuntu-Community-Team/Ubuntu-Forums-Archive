---
title: "Extreme CPU usage by Rosegarden"
date: 2010-02-26
forum: Ubuntu Studio
---

### Post by darsu on 2010-02-26
Hi,

I have Rosegarden 10.04 here. It seems that the program uses a horrid amount of CPU resources to *redraw its main window* during sequence playback.

If I set a sequence playing and move to another desktop, Rosegarden's CPU usage is typically around 10%. If I stay on the desktop where Rosegarden is, the usage is no less than 50% and Xorg comes in to eat another 20-25%.

Has anyone else noticed this? Is there a fix?

---

### Post by halfpower on 2010-10-11
When I start an empty project with Rosegarden and hit play, the CPU usage goes up to 65-70%.

---

### Post by mgouin on 2010-11-21
Same thing here.  High CPU when playback if current desktop displays rosegarden.  Goes back to normal level when switching desktop.

Has anyone found a fix?

I tried both "safe" and "fast" graphics option with no apparent changes.

thanks.

---

### Post by Pablo_F on 2010-11-22
Hi, 

What values of frames/period, periods/buffer and SR are you running jack with? Don't try to decrease latency more than necessary!

If you are using Rosegarden only as a sequencer, I strongly recommend you use a high latency in the jack settings and if you don't need capture ports, "playback only" can help. 

Cheers! Pablo

---

### Post by mgouin on 2010-11-22
Hi Pablo, thanks for the reply.  For the moment, I took Jack out of the equation.  I run Rosegarden alone.   Even with an empty project (no notes in any tracks), when I hit play, the CPU jumps to 100% (as indicated by the system monitor indicator applet).  Further analysis (using "top" terminal command) reveals Rosegarden: 83%, Xorg: 7%.  This is definitely not normal...  Even when Rosegarden is idle, it eats about 8% cpu.

Thanks,
Mathieu

---

### Post by Pablo_F on 2010-11-22
> I took Jack out of the equation. I run Rosegarden alone

Is this possible at all?

When you launch Rosegarden without having launched qjackctl before, I am almost sure that rosegarden starts jackd. Check with (for example):
[B]
ps -eo cmd |grep jackd[/B] 

jackd is started with the parameters and options that you have in your ~/.jackdrc file. It is better if you put saner parameters in qjackctl and then start rosegarden.

Cheers! Pablo

---

### Post by mgouin on 2010-11-23
Thanks for the info.  Jackd is in fact started...  I learn everyday :)

Here are the jackd parameters (as given by the ps command):
/usr/bin/jackd -T -ndefault -r -dalsa -dhw:0 -r44100 -p512 -n2 -S -Xseq

Based on your experience, is there anything that you find suspicious in these settings?

Thanks,
Mathieu

---

### Post by mgouin on 2010-11-23
I forgot to emphasize that the high CPU usage is only present if rosegarden is visible.  For example, if rosegarden is minimized, or the desktop is changed to another one, the CPU drops to normal level.  Do you think this is related to jackd?  I would suspect more an issue related to graphics rendering?

Thanks,
Mathieu

---

### Post by Pablo_F on 2010-11-25
> Do you think this is related to jackd? I would suspect more an issue related to graphics rendering?

Maybe (I don't know) Rosegarden could do better but the issue is related to all your hardware-software system configuration and jack is selfish.

My 2 cents: 

1. Give your user rtprio scheduling and memlock unlimited privileges 
2. Start jack through qjackctl in realtime mode (no need for a linux-rt kernel, just point 1)
3. Increase frames/period to 1024 or 2048, turn off midi driver. 

For 1. if you are in lucid, run:

sudo dpkg-configure -p high jackd

(or is it dpkg-reconfigure? sorry I am in a hurry)

If in maverick:

sudo dpkg-configure -p high jackd2

(or jackd1 if you switched to jackd1)

In others, edit /etc/security/limits.conf . See jackaudio.org faqs or limuxmusicians wiki.

Cheers! Pablo

---

### Post by mgouin on 2010-11-26
Hi Pablo, 

Thanks again for your time!

I reconfigured jackd and re-login with:  dpkg-reconfigure -p high jackd

This created /etc/security/limits.d/audio.conf
with:

```

@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```However, when I start jackd with jackctl (2048 frames/period and in real-time), I get this output:

```

 [COLOR=#999999]11:16:39.692 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:16:40.145 Statistics reset.[/COLOR]
 [COLOR=#66cc99]11:16:40.267 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]11:16:41.057 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:16:47.919 JACK is starting...[/COLOR]
 [COLOR=#990099]11:16:47.921 /usr/bin/jackd -P10 -dalsa -dhw:0 -r44100 -p2048 -n2 -Xseq[/COLOR]
 [COLOR=#999999]11:16:48.049 JACK was started with PID=3049.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]11:16:48.136 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]11:16:48.138 Post-shutdown script...[/COLOR]
 [COLOR=#990099]11:16:48.139 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]11:16:48.555 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]11:16:50.230 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```
Based on these messages, I added the lines manually in limits.conf.  But there seems to be a problem with dpkg-reconfigure -p high jackd.

I don't know what you mean by "turning off the midi driver"?  Is this done in jackctl or rosegarden?  I found an option in jackctl settings: "Enable ALSA Sequencer Support".  Is this the setting you were referencing?  I tried with it enabled and disabled but I noted no significant change.

The result is that the CPU still jumps when rosegarden start to play.  I still test with an empty project.  But this time, Xorg 70%, Rosegarden 20%.

Compared to jack in non-real time: Rosegarden: 83%, Xorg: 7%.  

This is really confusing me... 

By the way, I have a P4 1.7GHz, 768MB RAM, NVidia GeFore 4 440Go 32MB.  It's an old Dell laptop (Inspiron 8200).  Maybe my machine is just too old.  But as a comparison, I can run Ardour just fine with jack (CPU stays in the low usage).

Thanks,
Mathieu

---

### Post by Pablo_F on 2010-11-26
Hi, 

@audio   -  rtprio     99
@audio   -  memlock    unlimited

means "the users who belong to the audio group have these privileges". Sorry I forgot to tell you that your user has to be a member of the audio group. 

Do a:

**sudo adduser your_user_name audio**

and reboot. 

There is no difference if these lines are in /etc/security/limits.conf or in /etc/security/limits.d/audio.conf but I would use the later which is written automatically by the dpkg-reconfigure command, as you already realised.

Note that some people has had problems with this even if they already belonged to the audio group, because of some versions of certain login managers that failed to load the pam module. I don't think that this will be your case, but anyway, after rebooting, double check with this command:
[B]
ulimit -r -l[/B]

No wonder that ardour behaves fine with jack. Both programs are designed by the same person, Paul Davies. 

I am not 100% sure but I think that things will improve with jackd in realtime mode. Nevertheless, each system is different. I suggest you try qtractor anyway.

Cheers! Pablo

---

### Post by mgouin on 2010-11-29
Hi,

I tested with my login name instead of @audio and jack did not complain about real-time issue.  I was not getting any XRuns, but rosegarden was still eating CPU.

Maybe it's something with my system.  But I'm curious, if you try exactly what I did, does your CPU goes high, or it stays normal?

I'll have a look at qtractor.  Is is the most similar application to rosegarden?  Do you have any other suggestion I might try?

Thanks,
Mathieu

---

### Post by Pablo_F on 2010-11-29
> if you try exactly what I did, does your CPU goes high, or it stays normal?

Yes, it goes unusually high. The other day I tried and it went high, then I decreased the frames/period value and it got a lot better. Now, it is high as long as I have the editor open, just as you reported, even with 1024 frames/period. I am running version 11.02 which is a development version, not released yet. I will compile the latest stable, 10.10 and see what happens... I will report upstream and here.

There is muse and qtractor. I don't know other similar apps.

Cheers! Pablo

---

### Post by mgouin on 2010-11-29
Hi Pablo, I really appreciate your response.  Thanks.  At least, I see that I'm not alone ;)

Thanks also for the pointers for other apps, but tI'd really like to use rosegarden, because in terms of features, it is perfect!

If there's any other thing I could try to help you in debugging this issue, I'll be glad to help.

Thanks,
Mathieu

---

### Post by chaanakya_chiraag on 2010-11-29
I have seen this with the latest version of Rosegarden, version 10.04.  Have you tried 10.02 instead?  That one works perfectly for me :)

---

### Post by mgouin on 2010-11-30
I forgot to say that I have also Rosegarden 10.02 "Thorn" installed.

---

### Post by chaanakya_chiraag on 2010-11-30
Hmmm...that's bizarre...it certainly took up quite a bit of RAM, but it has never eaten up my CPU...maybe it's because I have 8 CPU cores ;)

---

### Post by mgouin on 2010-11-30
That's unfair :)

As I said earlier in this thread, I have a P4M 1.7GHz, 768MB RAM, NVidia GeFore 4 440Go 32MB.  It's an old Dell laptop (Inspiron 8200).  Do you think it's just too old for rosegarden?

---

### Post by chaanakya_chiraag on 2010-12-01
I feel like that should be enough...how old is the machine?

---

### Post by mgouin on 2010-12-02
Euh... I bought it in 2002... It's dating a bit, but it works perfectly with Ubuntu 10.04.  I find it event a bit quicker than XP (dual boot).

Thanks,
Mathieu

---

### Post by luctor on 2010-12-04
There are some option for the graphics in rosegarden itself. I think it's Safe Graphics and some other. (not on my linux box right now ..)

---

### Post by mgouin on 2010-12-04
Yes, I tried all options without much difference in CPU.  Thanks anyway.

---

