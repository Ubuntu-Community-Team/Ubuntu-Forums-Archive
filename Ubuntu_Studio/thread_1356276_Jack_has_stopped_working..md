---
title: "Jack has stopped working."
date: 2009-12-15
forum: Ubuntu Studio
---

### Post by EggplantOfFire on 2009-12-15
I upgraded to Karmic recently and got Jack to work through my US-122 USB audio interface. Had some issue with getting mp3s and streaming audio to continue to work right but I got that to work fine, again going through the US-122. In the meantime I had taken a break from recording guitar parts for about a week and then went back to it. When I loaded the Jack qtjackctl it came up with a message saying:

> 22:04:43.383 Patchbay deactivated.
22:04:43.387 Statistics reset.
22:04:43.445 ALSA connection graph change.
22:04:43.640 ALSA connection change.


And when I hit "start" it fails saying:

> Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

with the message window saying:
> 22:12:15.607 Startup script...
22:12:15.608 artsshell -q terminate
sh: artsshell: not found
22:12:16.010 Startup script terminated with exit status=32512.
22:12:16.010 JACK is starting...
22:12:16.011 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n3
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1215949120, from thread -1215949120] (1: Operation not permitted)
cannot create engine
22:12:16.055 JACK was started with PID=2997.
22:12:16.108 JACK was stopped successfully.
22:12:16.109 Post-shutdown script...
22:12:16.110 killall jackd
jackd: no process found
22:12:16.523 Post-shutdown script terminated with exit status=256.
22:12:18.194 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I don't really know a whole lot about all this. I just know it worked at first and I know the US-122 works with this computer as I had it set up in Hardy and it worked fine. 

Every other music or media player works only when Jack is not up, which is not really a problem. I may have done something when I was trying to get regular audio to work after reading one of the "Comprehensive Sound Problems..." guides though I can't find it now and can't remember what I did. Any and all help is appreciated. Thanks.

---

### Post by AutoStatic on 2009-12-16
Hello EggplantOfFire,

```
cannot use real-time scheduling (FIFO at priority 10) [for thread -1215949120, from thread -1215949120] (1: Operation not permitted)
```

[http://ubuntuforums.org/search.php?searchid=68221353](http://ubuntuforums.org/search.php?searchid=68221353)

Which returns several solved threads like this one: [http://ubuntuforums.org/showthread.php?t=1307149&highlight=cannot+use+real-time+scheduling](http://ubuntuforums.org/showthread.php?t=1307149&highlight=cannot+use+real-time+scheduling)

---

### Post by sgx on 2009-12-16
EggPlantOfFire :lolflag: can only wonder what your girlfriends nik might be...hope you get the tascam back working, it makes good people go crazy when things change for no good reason!

---

### Post by EggplantOfFire on 2009-12-16
> **AutoStatic said:**
> Hello EggplantOfFire,

```
cannot use real-time scheduling (FIFO at priority 10) [for thread -1215949120, from thread -1215949120] (1: Operation not permitted)
```

[http://ubuntuforums.org/search.php?searchid=68221353](http://ubuntuforums.org/search.php?searchid=68221353)

Which returns several solved threads like this one: [http://ubuntuforums.org/showthread.php?t=1307149&highlight=cannot+use+real-time+scheduling](http://ubuntuforums.org/showthread.php?t=1307149&highlight=cannot+use+real-time+scheduling)

Thank you. I didn't even see that part about real time scheduling. And even if I did I wouldn't have known what to do. 
BTW, it seems a restart is needed after all that. Thanks again.

Edit: Also found this page somehow, [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") that has instructions under "Real-Time Support" and has code to use for getting the real time scheduling to work.

---

### Post by EggplantOfFire on 2009-12-16
> **sgx said:**
> EggPlantOfFire :lolflag: can only wonder what your girlfriends nik might be...

HA! If only!

---

### Post by AutoStatic on 2009-12-16
> **EggplantOfFire said:**
> Thank you. I didn't even see that part about real time scheduling.jackd spits out quite some information so you quickly oversee it, that's true.

> **EggplantOfFire said:**
> And even if I did I wouldn't have known what to do. 
BTW, it seems a restart is needed after all that. Thanks again.You're welcome, good thing that it works now :)

---

