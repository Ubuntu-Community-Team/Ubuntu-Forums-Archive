---
title: "midi not working"
date: 2009-06-26
forum: Ubuntu Studio
---

### Post by Magick93 on 2009-06-26
Hi all

I am running Ubuntu 9.04 with an X-fi sound card and OSS4. The audio is fine. But I cannot get midi to work.

Any ideas where to start?

When I try to start JACK Audio Connection I get the following:
21:34:51.722 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:53:15.912 JACK is starting...
21:53:15.913 /usr/bin/jackd -R -doss -r44100 -p1024 -n3 -w16
21:53:15.953 JACK was started with PID=18719.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211324736, from thread -1211324736] (1: Operation not permitted)
cannot create engine
21:53:15.982 JACK was stopped successfully.
21:53:15.983 Post-shutdown script...
21:53:15.984 killall jackd
jackd: no process killed
21:53:16.397 Post-shutdown script terminated with exit status=256.
21:53:18.027 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by barisurum on 2009-06-26
Is your limits.conf set properly? If not:

Open the file with:

```
sudo gedit /etc/security/limits.conf
```

and add these lines to the end:

```
@audio - rtprio 99
@audio - nice -10
@audio - memlock unlimited
```

And you should be a member of the audio group. Check at System/Administration/Users and Groups. Restart the computer to see the result.

---

### Post by Magick93 on 2009-06-26
Thanks for the reply.

I'm not sure if it is set properly or not - not sure what to look for. 

But I added your suggestion, did a restart - but still no joy.

---

### Post by barisurum on 2009-06-26
If jack didn't start after the necessary changes include the messages output so we may track the problem

---

### Post by Magick93 on 2009-06-26
Here is the message output from JACK:

00:15:41.939 Patchbay deactivated.
00:15:42.153 Statistics reset.
00:15:42.165 JACK is starting...
00:15:42.165 /usr/bin/jackd -R -doss -r44100 -p1024 -n3 -w16
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1212655936, from thread -1212655936] (1: Operation not permitted)
cannot create engine
00:15:42.391 JACK was started with PID=9070.
00:15:42.426 JACK was stopped successfully.
00:15:42.427 Post-shutdown script...
00:15:42.427 killall jackd
jackd: no process killed
00:15:42.853 Post-shutdown script terminated with exit status=256.
00:15:44.397 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by barisurum on 2009-06-26
hmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmm
are you sure you select the oss driver? and select the oss device as output and input in the jack setup window? also try to change priority, sample rate, frames - periods buffer settings and continously try to start jack. If this fails then I have no further suggestions. You should search if this card or OSS4 works with jack or not.

---

### Post by raboofje on 2009-06-26
> **Magick93 said:**
> cannot use real-time scheduling (FIFO at priority 10) [for thread -1212655936, from thread -1212655936] (1: Operation not permitted)

If i'm not mistaken this suggests there's still something wrong with your rtprio settings.

Changes to /etc/security/limits.conf require you to log out and back in again, did you do that yet?

To get a better feedback, could you paste the output of [http://code.google.com/p/realtimeconfigquickscan/](http://code.google.com/p/realtimeconfigquickscan/) ? (it will probably ask you to install the rtprio commandline tool, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#priorities](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#priorities)

---

### Post by markbuntu on 2009-06-30
(Operation not permitted). That can mean you are not a member of the group
audio. Check in users and groups and make yourself and root members. Create the group if it is not already there.

Cannot use real time scheduling can also mean you are not using the rt kernel.

---

### Post by raboofje on 2009-07-01
> **markbuntu said:**
> (Operation not permitted). That can mean you are not a member of the group audio. Check in users and groups and make yourself and root members.

Why would you want to put root in that group?

> Cannot use real time scheduling can also mean you are not using the rt kernel.

To nitpick: In this case, an 'Operation not permitted' error was the reason for the 'Cannot use real time scheduling' message. I don't think this is related to whether you're using an -rt kernel or not: you get this error when you enable 'realtime' and request a 'priority' (-Px, looks like it defaults to 10) larger than your maximum rtprio in /etc/security/limits.conf.

Indeed this is typically solved by specifying a large maximum rtprio in /etc/security/limits.conf for the audio group and putting the user in that group (and logging out/in - [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) ).

---

### Post by Magick93 on 2009-07-01
I'm not at my home computer at the moment, so I cannot confirm, but I am fairly certain I am a member of the Audio group.

However I think the problem is that midi is not enabled in OSS.

So I either need to enable this or find a way to get my soundcard (X-Fi) to work with ALSA, which apparently does support Midi.

---

