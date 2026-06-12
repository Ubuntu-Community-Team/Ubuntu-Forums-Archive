---
title: "JACK error"
date: 2009-10-30
forum: Ubuntu Studio
---

### Post by Vigh on 2009-10-30
When I hit the start button on Jack I get the following output, is this because ALSA isnt set up correctly?


cannot use real-time scheduling (FIFO at priority 10) [for thread -1210030416, from thread -1210030416] (1: Operation not permitted)
cannot create engine
11:37:05.572 JACK was stopped successfully.
11:37:05.572 Post-shutdown script...
11:37:05.572 killall jackd
jackd: no process killed
11:37:05.977 Post-shutdown script terminated with exit status=256.
11:37:07.674 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by bawig1 on 2009-10-30
I am having similar problems. I installed Rosegarden to use with a Roland SH32 and I cannot get Jack to work. I am using a  MIDI to USB cable, will that work with Jack? I have never tried to used a sequencer with Linux before so I am kinda new to this.
I found a thread here;

[http://ubuntuforums.org/showthread.php?t=806730&highlight=rosegarden](http://ubuntuforums.org/showthread.php?t=806730&highlight=rosegarden)[URL="http://ubuntuforums.org/showthread.php?t=806730&highlight=rosegarden"]
[/URL]
but I am not sure if it is correct.

 Here is the output I get when I try to start Jack.

```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]14:34:32.849 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:34:32.867 Statistics reset.[/COLOR]
 [COLOR=#66cc99]14:34:32.988 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]14:34:33.329 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:34:44.248 Startup script...[/COLOR]
 [COLOR=#990099]14:34:44.250 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:34:44.653 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:34:44.654 JACK is starting...[/COLOR]
 [COLOR=#990099]14:34:44.655 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]14:34:44.661 JACK was started with PID=12757.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1212655936, from thread -1212655936] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]14:34:45.026 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]14:34:45.027 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:34:45.028 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]14:34:45.497 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]14:34:46.764 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


```- Brett

---

### Post by trulan on 2009-10-31
Both of you need to either:
Uncheck the 'real time' box in Jack **or:**

Set your system to allow real time scheduling for audio processes.  You'll need to add a few lines to /etc/security/limits.conf (I think Ubuntu Studio Controls will handle this for you if you want a nice GUI). 
You'll also need to add yourself to the 'audio' group (go into system/Users and Groups, unlock it to make changes, select your username, select 'properties', select 'User Priviledges' and check the box 'Use Audio Devices'.)
Edit: those are the instructions for Karmic.  In Jaunty you need to create the 'audio' group and make yourself a member.

---

### Post by bawig1 on 2009-10-31
hey,

the link I posted in my reply works... here is the output when I start jack;

```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]15:03:32.450 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:03:32.634 Statistics reset.[/COLOR]
 [COLOR=#66CC99]15:03:32.669 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]15:03:32.882 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:03:37.748 Startup script...[/COLOR]
 [COLOR=#990099]15:03:37.749 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:03:38.152 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:03:38.153 JACK is starting...[/COLOR]
 [COLOR=#990099]15:03:38.154 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]15:03:38.238 JACK was started with PID=14725.[/COLOR]
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
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]15:03:40.315 Server configuration saved to "/home/brett/.jackdrc".[/COLOR]
 [COLOR=#999999]15:03:40.317 Statistics reset.[/COLOR]
 [COLOR=#999999]15:03:41.054 Client activated.[/COLOR]
 [COLOR=#9999CC]15:03:41.056 JACK connection change.[/COLOR]
 [COLOR=#CC9966]15:03:41.096 JACK connection graph change.[/COLOR]


```

---

### Post by Vigh on 2009-10-31
followed the instructions still getting the same error message i am running 8.04 hardy would this have anything to do with it

---

### Post by Vigh on 2009-10-31
turned off realtime for now, seems to be working, would like to get the realtime kernel working though, MAN THERE ARE SO MANY AWESOME SOUNDS ON LINUX! ITS SWEET! AND THEY ARE FREE! :D ME A HAPPY MAN!

---

### Post by trulan on 2009-10-31
In Hardy the audio group is already there, you just need to add your username to it.  I don't know the command off the top of my head but there's a simple line to run from a terminal.  You can also do it through the Users and Groups gui, I think by clicking 'manage groups' or something like that.

---

### Post by afrodeity on 2009-12-16
> **trulan said:**
> Both of you need to either:
Uncheck the 'real time' box in Jack **or:**

Set your system to allow real time scheduling for audio processes.  You'll need to add a few lines to /etc/security/limits.conf (I think Ubuntu Studio Controls will handle this for you if you want a nice GUI). 
You'll also need to add yourself to the 'audio' group (go into system/Users and Groups, unlock it to make changes, select your username, select 'properties', select 'User Priviledges' and check the box 'Use Audio Devices'.)
Edit: those are the instructions for Karmic.  In Jaunty you need to create the 'audio' group and make yourself a member.

What would those lines be in /etc/security/limits.conf?

---

### Post by trulan on 2009-12-16
```
@audio - rtprio 99
@audio - nice -10
@audio - memlock unlimited

```You can set memlock to 50% of your system memory, or any other value you choose (set it using number in kilobytes, 512000 would be 50% of 1Gb).  Or you can set it to unlimited, as shown above.  Jack will work without nice being set, but it needs the rtprio line and the memlock line to be able to run with real time priority.  Also, as stated above, your username needs to be a member of the audio group.

---

### Post by afrodeity on 2009-12-17
Thanks. Tell me, would @audio need to be set under

 <domain>      <type>  <item>         <value>

????

---

### Post by AutoStatic on 2009-12-17
Just copy and paste the lines trulan posted at the end of your /etc/security/limits.conf

---

