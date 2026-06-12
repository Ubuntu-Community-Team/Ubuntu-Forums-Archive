---
title: "Can't start JACK"
date: 2009-05-28
forum: Ubuntu Studio
---

### Post by highfructose on 2009-05-28
I'm fairly new to Ubuntu, and I'm completely new to Ubuntu Studio. I just installed the latest version of Ubuntu Studio. I'm trying to use Ardour and/or Creox, but I get errors whenever I try to open these programs. It seems like the problems are related to JACK.

When I go to JACK and try to start it, I get the following error message.


> 
 Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.


The messages box reads:


> 


[COLOR=#999999]12:22:31.325 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:22:31.473 Statistics reset.[/COLOR]
 [COLOR=#66cc99]12:22:31.631 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]12:22:32.050 Startup script...[/COLOR]
 [COLOR=#990099]12:22:32.051 artsshell -q terminate[/COLOR]
 [COLOR=#cccc99]12:22:32.181 ALSA connection change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:22:32.455 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:22:32.457 JACK is starting...[/COLOR]
 [COLOR=#990099]12:22:32.458 /usr/bin/jackd -R -dalsa -dhw:1,0 -r44100 -p64 -n2 -m[/COLOR]
 [COLOR=#999999]12:22:32.523 JACK was started with PID=5278.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1211885888, from thread -1211885888] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]12:22:32.586 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:22:32.587 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:22:32.588 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]12:22:33.002 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]12:22:34.667 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
What can I do to get JACK, Creox, and Ardour all working? Let me know if my specs are needed. Keep in mind that I'm a bit of a beginner to Ubuntu. Thanks in advance.

---

### Post by highfructose on 2009-05-28
bump

---

### Post by goodmanbrown on 2009-05-28
I'm getting the same error after upgrading to Jaunty.  I just discovered it last night and so far have made no progress figuring it out.

jackd starts *not* in realtime mode, which on my system is useless because of near-constant x-runs.  If I try to start it in realtime mode, I get the same message you get.

If you discover a fix, please post it!  I'll do the same.

---

### Post by highfructose on 2009-05-28
Mine has the same error message whether or not I have Realtime checked. I've experimented a bit with the parameters, but no luck at all so far.

---

### Post by highfructose on 2009-05-28
Ok, I've got JACK to start by forcing 16-bit and turning off Realtime. I think I will, like you, need to have Realtime on, however, to work with Creox. Not sure how to get that done.

---

### Post by kayosiii on 2009-05-29
Either use the Ubuntu studio control panel... 


or manual edit /etc/security/limits.conf....
And check that the audio group has the rights to run with realtime privileges. (Information on how to this has been posted in this forum about a zillion times already -- search for /etc/security/limits.conf)
It is possible that an upgrade will break this even if you had it set before (ubuntu is not as serious about multimedia production as I would like them to be)....

Creox seems to get cranky at some sample rates 44100 is probably safest.

---

### Post by raboofje on 2009-05-29
> **kayosiii said:**
> Either use the Ubuntu studio control panel... 

or manual edit /etc/security/limits.conf....
And check that the audio group has the rights to run with realtime privileges. (Information on how to this has been posted in this forum about a zillion times already -- search for /etc/security/limits.conf)

If something has to be explained a zillion times in the forums, the docs should be improved or made easier to find - let's start with the latter:

[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)

---

### Post by dawiba on 2009-05-29
highfructose - just a thought, since you're new to ubuntustudio.

Are you booting into the rt kernel when you start up? If your install was actually an upgrade from regular Ubuntu, you'll still be booting into the regular kernel by default.

This could cause your problem with Jack if you have the 'realtime' box ticked. Jack should work fine with the 'realtime' box ticked, if you have booted up into the realtime kernel.

Apologies if I'm stating the obvious and you've covered this already.

---

### Post by highfructose on 2009-05-29
Dawiba:

I went here

[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support\]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support")

And followed the instructions concerning the realtime kernel. When I type the command to install the realtime kernel, I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-rt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


When I follow the instructions under "Real-Time Support", the commands listed do nothing when I type them into terminal.

---

### Post by dawiba on 2009-05-29
That's the route I took to upgrade to studio. It also means that you have the real time kernel installed.

You won't necessarily see anything happen after following those instructions, 

sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -19 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'

but it will have changed the appropriate file on your computer.

What happens for me, is when I boot up and GRUB comes up, I press 'esc' and choose which kernel to boot. When I want to do music, I'll choose the real time kernel. Otherwise, Ubuntu defaults to the regular kernel.

If you've booted using the real time kernel, you should now be able to tick the 'realtime' box in Jack and use Ardour and Creox and so on.

What soundcard/interface are you trying to use?

---

### Post by highfructose on 2009-05-29
Thanks for the explanation, dawiba. Got it to work in Realtime.

I appreciate your patience everybody. Still some minor kinks with some Studio applications to work out, but I think it's stuff I can handle.

---

### Post by Endolith on 2009-05-30
> **kayosiii said:**
> 
And check that the audio group has the rights to run with realtime privileges. (Information on how to this has been posted in this forum about a zillion times already -- search for /etc/security/limits.conf)

Why isn't this configured by default?

---

### Post by dawiba on 2009-05-30
> **Endolith said:**
> Why isn't this configured by default?

I would agree for a standard/fresh UbuntuStudio installation, but not perhaps for someone who has chosen just to install certain packages on top of regular Ubuntu.

UbuntuStudio defaults to the rt kernel when you switch on, so Jack should work pretty much straight away once you've told it what soundcard you're using and set sample rate etc. Someone tell me if I'm wrong, but I believe the audio group is set up as well in UbuntuStudio. Of course, if you want to use Firewire that all changes

As a matter of interest, I did the full upgrade to UbuntuStudio to try it and my first impression is that there is just too stuff jammed in there. It might be better to offer the programs most used by most people with the option to upgrade to a 'full' version later if they wish. This, with some of the setup (audio group etc) already done or simplified, might be a more sane starting point for those new to Linux and UbuntuStudio (which is how I still think of myself)

---

### Post by raboofje on 2009-05-30
> **dawiba said:**
> I would agree for a standard/fresh UbuntuStudio installation, but not perhaps for someone who has chosen just to install certain packages on top of regular Ubuntu.

Enabling realtime/nice/memlock limits for the 'audio' group could well be an ubuntu-wide default imho, so I opened a [launchpad item](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/381937) for this bit.

---

