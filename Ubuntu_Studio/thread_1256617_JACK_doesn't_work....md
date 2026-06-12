---
title: "JACK doesn't work..."
date: 2009-09-02
forum: Ubuntu Studio
---

### Post by delsydebothom on 2009-09-02
Hey all! I really need to get JACK working, and I think I'm gonna need some help doing so. When I try to start Jack, I get this output in the message window:

> 21:12:36.429 Patchbay deactivated.
21:12:36.824 Statistics reset.
21:12:36.896 Startup script...
21:12:36.896 artsshell -q terminate
21:12:36.902 ALSA connection graph change.
sh: artsshell: not found
21:12:38.167 Startup script terminated with exit status=32512.
21:12:38.168 JACK is starting...
21:12:38.168 /usr/bin/jackd -v -R -dalsa -dhw:0 -r44100 -p1024 -n2
21:12:38.180 JACK was started with PID=6879.
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211033920, from thread -1211033920] (1: Operation not permitted)
cannot create engine
cleaning up shared memory
cleaning up files
unregistering server `default'
21:12:38.546 JACK was stopped successfully.
21:12:38.547 Post-shutdown script...
21:12:38.548 killall jackd
21:12:38.553 ALSA connection change.
jackd: no process killed
21:12:38.961 Post-shutdown script terminated with exit status=256.
21:12:41.825 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Is there anything I can do? Thanks!

---

### Post by Stochastic on 2009-09-03
It looks like you're trying to run Jack in realtime mode without permissions.  This is probably because you don't have the realtime kernel installed.

If you run "uname -r" in a terminal, a realtime kernel will show up with an -rt ending.  If you ARE running a realtime kernel, post back.  For now I'll assume you're not.

There are two ways to remedy this.
1) In qjackctl's settings window uncheck the 'realtime' option.
2) Install the [linux-rt]("apt:linux-rt") package and reboot with that kernel.


The realtime mode allows much lower latency with less xruns (drops in the audio stream).

---

### Post by delsydebothom on 2009-09-03
> **Stochastic said:**
> It looks like you're trying to run Jack in realtime mode without permissions.  This is probably because you don't have the realtime kernel installed.

If you run "uname -r" in a terminal, a realtime kernel will show up with an -rt ending.  If you ARE running a realtime kernel, post back.  For now I'll assume you're not.

There are two ways to remedy this.
1) In qjackctl's settings window uncheck the 'realtime' option.
2) Install the [linux-rt]("apt:linux-rt") package and reboot with that kernel.


The realtime mode allows much lower latency with less xruns (drops in the audio stream).


Hey, thanks! But I *am* running a real-time kernel. However, for some reason, it works when not in realtime mode...I'll have to see if that's good enough, I suppose. Have you any ideas about how to get it working in realtime mode, though? Thanks!

---

### Post by theluddite on 2009-09-03
Ensure you set your realtime permissions.  Did you follow the instructions here?

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

---

### Post by Stochastic on 2009-09-03
> **theluddite said:**
> Ensure you set your realtime permissions.  Did you follow the instructions here?

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

That page has WAAAYYY too many little tweaks that have no bearing on the problem.  The tweaks needed can easily be accomplished by the Ubuntu Studio Controls application.

Here's the howto you should read: [https://help.ubuntu.com/community/UbuntuStudioControls](https://help.ubuntu.com/community/UbuntuStudioControls)

---

### Post by delsydebothom on 2009-09-03
At any rate, I am learning more about Ubuntu Studio with your help. Still no luck with JACK, though...

On the one hand, I don't know how to set memlock to unlimited; the highest it goes it 90%. On the other, I don't really know what to do with "nice".

---

### Post by Stochastic on 2009-09-04
I'd set nice to about -10 (%)

Oh, and it looks like you need to create a group named audio and add your user to that group.  This can all be done in the System->Administration->Users and Groups tool or by command line with the following commands ```
sudo addgroup audio
sudo adduser <username> audio
```
Then reboot to make the new group rules take effect.

---

### Post by delsydebothom on 2009-09-04
> **Stochastic said:**
> I'd set nice to about -10 (%)

Oh, and it looks like you need to create a group named audio and add your user to that group.  This can all be done in the System->Administration->Users and Groups tool or by command line with the following commands ```
sudo addgroup audio
sudo adduser <username> audio
```
Then reboot to make the new group rules take effect.

This bit of information did the trick. Thank you so much!

---

### Post by delsydebothom on 2009-09-04
And now I can't find where the "thank" button is on the forum... O.o

---

### Post by Stochastic on 2009-09-04
They got rid of that button during some upgrades, along with the feature to mark a thread solved.  They were taking too many resources on the servers.  But you still can add a 'solved' tag to the thread.

---

