---
title: "jackd server won't run"
date: 2009-10-01
forum: Ubuntu Studio
---

### Post by sketchi_back on 2009-10-01
I have been trying to get jack server to run for months now and no matter what I try I don't seem to get anywhere. I have installed the JACK Audio Connection Kit package and when I try to start the jack server I get the following printed in the messages window.

15:07:40.427 Patchbay deactivated.
15:07:40.435 Statistics reset.
15:07:40.557 ALSA connection graph change.
15:07:40.972 ALSA connection change.
15:07:44.336 Startup script...
15:07:44.337 artsshell -q terminate
sh: artsshell: not found
15:07:44.742 Startup script terminated with exit status=32512.
15:07:44.745 JACK is starting...
15:07:44.746 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n3
15:07:44.757 JACK was started with PID=3758.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1212691712, from thread -1212691712] (1: Operation not permitted)
cannot create engine
15:07:45.644 JACK was stopped successfully.
15:07:45.645 Post-shutdown script...
15:07:45.647 killall jackd
jackd: no process killed
15:07:46.112 Post-shutdown script terminated with exit status=256.
15:07:46.983 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I would really appreciate any help that I can get at this point!

Thanks

---

### Post by thorgal on 2009-10-01
realtime priority not allowed, that's your problem. 

Read about /etc/security/limits.conf and audio group in these forums and you'll see the light at the end of the tunnel :)

---

### Post by VertexPusher on 2009-10-02
> **sketchi_back said:**
> cannot use real-time scheduling (FIFO at priority 10) [for thread -1212691712, from thread -1212691712] (1: Operation not permitted)
Install the package "linux-rt" or disable real-time scheduling in Jack.

---

### Post by raboofje on 2009-10-02
> **VertexPusher said:**
> Install the package "linux-rt" or disable real-time scheduling in Jack.

Not entirely: this error goes away when you give the user running jack the permission to run applications at higher 'rtprio' priorities, regardless of whether you're running the -rt kernel. 

See [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting) for details. In short, the recommended solution is to allow the 'audio' group to use rtprio priorities, and add your user to this group.

---

### Post by VertexPusher on 2009-10-02
Is this new in Jaunty? I remember when I used Jack on Hardy, all I needed for RT mode was the RT kernel. No other configuration changes were required. No changes in limits.conf, no group membership changes. The priority in QJackCtl was set at "(default)". My onboard soundcard latency was 4ms out of the box, with no XRUNs. Did I miss something?

---

### Post by raboofje on 2009-10-02
> **VertexPusher said:**
> Is this new in Jaunty? I remember when I used Jack on Hardy, all I needed for RT mode was the RT kernel. No other configuration changes were required. No changes in limits.conf, no group membership changes. The priority in QJackCtl was set at "(default)". My onboard soundcard latency was 4ms out of the box, with no XRUNs. Did I miss something?

Iirc the only thing that changed in this regard is that jackd now defaults to 'realtime' instead of 'non-realtime'...

---

### Post by trulan on 2009-10-02
You have always needed groups membership and a line in limits.conf to use realtime in Jack (which is actually allowing you to set the processor priority given to Jack, it is a seperate issue from whether your kernel is real time or generic).  But, as was stated, real time is off by default in Jack in Hardy and on by default in Jack in Jaunty.  Plus, Jaunty does not include the 'Audio' group by default.  To top it off, Ubuntu Studio controls in Jaunty sometimes goofs up and doesn't always set all of the permissions like it is supposed to.  So, setting these permissions can be a pain, but it's just a small pain.

---

### Post by VertexPusher on 2009-10-05
Is raising Jack's priority above default recommended or even required? In Hardy, I just installed the RT kernel, then enabled RT in QJackCtl. I didn't raise Jack's priority because there was no need to do so. I've known people who failed to decrease latency below 12ms with Windows Vista and pro-audio hardware, so 4ms with RealTek onboard sound is pretty good. No need to go further and jeopardize system stability.

The reason why there's a limits.conf in the first place is because realtime priority increases the risk of lock-ups. If you look around, you'll see lots of complaints about Jaunty locking up in RT mode. Maybe that's because people mess with RT priority when they shouldn't.

Installing the RT kernel should be enough. If there are still XRUNs, the system may just be too slow to handle the load.

---

### Post by Papa_Smurf on 2009-10-23
I installed ubuntustudio, including the ubuntustudio-defaults, and my jack has realtime set as the default. I did have to check Use Audio in the preferences. The very first error message about artsshell not found means that th OP does not have audio permissions, and thus nothing will work right if at all. To give yourself permissions, go to System->Administration->Users and Groups. Select and Unlock your user name. In your Properties, in the User Privileges tab, check "Use audio devices". Save your changes and re-boot (I select the RT kernel from Grub). Now Jack runs for me.:popcorn:

---

### Post by AutoStatic on 2009-10-23
Papa_Smurf, check [http://ubuntuforums.org/showpost.php?p=8151733&postcount=6](http://ubuntuforums.org/showpost.php?p=8151733&postcount=6)
And thorgal was already spot on. You need to set permissions in /etc/security/limits.conf and make sure you're a member of the audio group before you can use jackd in realtime mode.

---

