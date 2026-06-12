---
title: "Ardour won't play or record"
date: 2010-03-03
forum: Ubuntu Studio
---

### Post by djm227 on 2010-03-03
This is driving me absolutely crazy.  I really want to drop cubase in order to move production completely to Ubuntu...but Ardour is giving me major problems.

I open it, but that's about all I can do.  I tried importing an audio file, and then playing it, but it does nothing.  The stop button is always highlighted, no matter what.  The start and end markers are in the right spots.  I'm at a loss......I don't know if it has anything to do with Jack or not, but to be honest I barely know what Jack is...so me fixing it without some help would be difficult.

Any help would be greatly appreciated, let me know if there's anymore info you need.

Thanks.

---

### Post by cchhrriiss121212 on 2010-03-04
Before using Ardour you will need to set up jack first. Jack is just a sound server that connects all your audio programs together and processes it all at a low latency.
If you have jack installed, go to Applications>Sound>Qjackctl. Press the start button and post any errors if it does not run.

Have you looked into ubuntu studio? It is much easier to get started as it comes with the realtime kernel (you will need this) and a lot of good programs. You can download as a separate distro image, or there is a ubuntu studio package in synaptic which you can install on top of plain ubuntu.

---

### Post by djm227 on 2010-03-04
This is what jack said when I clicked "start"

> 19:18:20.604 Patchbay deactivated.
19:18:20.667 Statistics reset.
19:18:20.692 ALSA connection graph change.
19:18:20.981 ALSA connection change.
19:18:29.877 Startup script...
19:18:29.878 artsshell -q terminate
sh: artsshell: not found
19:18:30.280 Startup script terminated with exit status=32512.
19:18:30.281 JACK is starting...
19:18:30.282 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
19:18:30.314 JACK was started with PID=7337.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216444736, from thread -1216444736] (1: Operation not permitted)
cannot create engine
19:18:30.578 JACK was stopped successfully.
19:18:30.578 Post-shutdown script...
19:18:30.579 killall jackd
jackd: no process found
19:18:30.999 Post-shutdown script terminated with exit status=256.
19:18:32.321 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I have been looking into Ubuntu Studio lately, and am interested in getting it.  Would getting Ubuntu Studio solve problems such as these?  Would I get the exact same feature if I installed it over my current Ubuntu installation instead of from scratch?

Thanks again for the help, i appreciate it.

---

### Post by Capoeira on 2010-03-04
> **djm227 said:**
> This is what jack said when I clicked "start"



are you tying to run jack in real-time-mode without having a realtime-kernel?
if you have realtime-kernel than or you didn't chnged your limits.conf or you are not in audio group

---

### Post by djm227 on 2010-03-04
If I turn off real time mode it does run, but Ardour still doesn't work.  This is what Jack says when I run it without real time:

> 20:23:39.137 Patchbay deactivated.
20:23:39.231 Statistics reset.
20:23:39.289 ALSA connection graph change.
20:23:39.620 ALSA connection change.
20:23:46.819 Startup script...
20:23:46.820 artsshell -q terminate
sh: artsshell: not found
20:23:47.241 Startup script terminated with exit status=32512.
20:23:47.242 JACK is starting...
20:23:47.244 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
20:23:47.291 JACK was started with PID=8492.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
20:23:49.309 Server configuration saved to "/home/dan/.jackdrc".
20:23:49.310 Statistics reset.
20:23:49.312 Client activated.
20:23:49.315 JACK connection change.
20:23:49.320 JACK connection graph change.
20:23:49.357 XRUN callback (1).
20:23:51.319 XRUN callback (24 skipped).
20:23:53.325 XRUN callback (25 skipped).
20:23:55.330 XRUN callback (24 skipped).
20:23:57.332 XRUN callback (24 skipped).
20:23:59.335 XRUN callback (24 skipped).
20:24:01.338 XRUN callback (24 skipped).
20:24:03.341 XRUN callback (24 skipped).
20:24:05.344 XRUN callback (24 skipped).

---

### Post by hxcobd on 2010-03-05
This is going to be a RIDICULOUS oversimplification, but it sounds like you're pretty new to this, so here's laymans' terms:

The first error log you posted, when JACK wouldn't Start at all, is generally the result of having a non-working setup with your particular hardware. From my experience, it generally means one of a few things:

- Your bitrate is set too high
- Your buffer is set too low
- You have the wrong audio interface selected
- You have RT enabled on a non-RT kernel

So messing with the settings, in your case, seemed to solve this.

The SECOND error log you posted, when JACK started but displayed a ton of XRUN errors, generally means audio is skipping like crazy or otherwise just won't play back smoothly. This generally means one of a few things:

- Your buffer setting is wrong
- Your CPU scaling may need to be changed
- Any other number of not-quite-perfect JACK settings
- Possible underpowered hardware, especially if on RT kernel

JACK is a finicky beast. It can take days or weeks to get a grasp on how it works, and then to get it set up properly. But when it does work, it performs VERY well. It's worth the time and effort.

Also, I'd like to add that Ubuntu Studio probably isn't worth the time and effort, as all fairly recent Ubuntu kernels have Realtime support and "completing" the steps for RT JACK is just a matter of editing a few config files. Takes minimal time.

---

### Post by hxcobd on 2010-03-05
I should add that getting XRUNS doesn't necessarily mean audio won't be usable. In a prime setup, though, you'll get minimum XRUNs or errors of any sort.

Also, I see you're using an ALSA period of 2. The standard setting for this is 3, unless you're using built-in Intel sound. I'd leave it on 3 if possible.

---

### Post by cchhrriiss121212 on 2010-03-05
This is a very useful document:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

If you want to do a lot of recording you may want to get a dedicated soundcard to get good latency with no xruns. There is linux support for external devices via usb and firewire, and many internal pci cards. The alsa website will show you what is fully supported.

---

### Post by djm227 on 2010-03-05
Thanks for the help guys, just a few more questions and hopefully I won't have to bother you anymore.

Are there any guides to setting up Jack that I could take a look at?  It seems like a real useful program, but it also seems like a bitch to configure.  Is getting it to work even possible on my system with my current hardware configuration?

I am using an Intel built in sound card.  BUT I usually use an interface for recording...I just need to figure out how to get mine to work with Ubuntu, which is another issue all together.

Lastly, is this Jack problem the thing that is messing up Ardour, or are they two separate problems?  I would think that even if Ardour wasn't getting audio from Jack, it would still play/record (without sound of course).

Thanks again for the help, I appreciate it.

---

### Post by cchhrriiss121212 on 2010-03-06
> **djm227 said:**
>  Is getting it to work even possible on my system with my current hardware configuration?


Yes, it will work better using the rt-kernel, so download that and set it as your default kernel using startup manager. You have already seen jack running, just with loads of xruns, you can eliminate these by increasing the frame rate.

Quick jack setup example:
frames: 4096
sample rate: 44100
periods: 2 (3 for an interface)
driver: alsa
interface: default (hw:1 for an interface)
check realtime and soft mode boxes

What interface do you record with? Type it in to google + "linux" or "alsa" to see whether it is supported. Jack will run much better with a supported interface as opposed to integrated sound, so I would use it all the time with jack.

Forget about Ardour until you get jack setup, once you get jack going Ardour will run fine.

---

### Post by djm227 on 2010-03-07
Sorry for not replying sooner, I was away from my computer for the weekend,

I installed and booted to the rt-kernal, and also ran the real time support commands listed [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation").  I set up jack just like you said, but unfortuneately it still isn't connecting.  Here's what it said:

> 23:00:39.285 Patchbay deactivated.
23:00:39.313 Statistics reset.
23:00:39.478 ALSA connection graph change.
23:00:39.912 ALSA connection change.
23:01:34.519 Startup script...
23:01:34.520 artsshell -q terminate
sh: artsshell: not found
23:01:34.923 Startup script terminated with exit status=32512.
23:01:34.924 JACK is starting...
23:01:34.925 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p4096 -n2 -s
23:01:34.958 JACK was started with PID=3422.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216129344, from thread -1216129344] (1: Operation not permitted)
cannot create engine
23:01:35.283 JACK was stopped successfully.
23:01:35.283 Post-shutdown script...
23:01:35.284 killall jackd
jackd: no process found
23:01:35.782 Post-shutdown script terminated with exit status=256.
23:01:37.200 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I'm trying to learn how to do this stuff on my own, so I read through that...but none of it makes much sense to me.

---

### Post by cchhrriiss121212 on 2010-03-08
OK you just need to add a few lines to your /etc/security/limits.conf file. Have a look at the Studio preparation link I posted earlier. If it runs you can try decreasing the frame rate for lower latency.

---

### Post by hxcobd on 2010-03-09
Following up on what chris said:

To install a realtime kernel on ubuntu you can simply do a 
"sudo apt-get install linux-rt"

or open Synaptic and search for "realtime" or "rt" and install whichever kernel comes up



Then, in the limits.conf, add the following:
username - rtprio 99
username - memlock unlimited
username - nice &#8722;10

or add your username to a group called audio and use:
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice &#8722;10

You'll have to be logged as root to edit the limits.conf file. Make sure you reboot after installing the RT kernel and editing limits.conf.

---

### Post by trulan on 2010-03-09
The relevant error message in your output is here:
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216129344, from thread -1216129344] (1: Operation not permitted)
```Jack is trying to set its priority and the system will not allow that.  If you do
```
sudo gedit /etc/security/limits.conf
```You can add the @audio lines suggested, log out and log back in, and that problem will be taken care of.

Alternately, you could uncheck the 'realtime' option in qjackctl.  This will probably decrease performace a bit, but it will avoid the error.

Any Ubuntu, even Ubuntu Studio, ships with Jack broken like this.  It will not work out of the box, everybody has to fix this issue if they want to actually use it.

---

