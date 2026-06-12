---
title: "Sound stops working in Virtual Box Sometimes"
date: 2009-06-29
forum: Virtualisation
---

### Post by hufferd on 2009-06-29
I have been using virtual box (running windows 7) to play a game that I downloaded over the weekend..  The game it self works fine....  But every so often the sounds stop completely  for no reason.  The only way to get the sound back in Virtual Box is to completely short it down (a restart will not work) and then bring the virtual machine back up. Whats interesting is when the sound will not work in VB it is still working on the host with no issues.  Most of the time right before the sound stops working it gets choppy

Any ideas? 
Thanks

---

### Post by hufferd on 2009-07-01
):P +1

I found this on another thread here... wondering if this is my issue anyone have any ideas... will try this fix and see if it works 

> 
****** VBOX fix in Winxp ******** (this was from Vbox forum site)

With pulseaudio on Ubuntu 9.04, the daemon dies because of CPU overload. It's a bug in the dependency libraries of PulseAudio. You can avoid this by editing

/etc/pulse/daemon.conf

and put this in it, or edit the already existing line to match.

Code:
no-cpu-limit = yes


Now PulseAudio won't get killed because of CPU overload and you have sound in the Guest, but it does add additional CPU load, because until the VM is closed, PA will run on 100% on one core all the time. The VM will shut down normally so you don't have to kill it and once the VM is closed, the CPU usage will go down.
For more information on this issue, check [https://bugs.launchpad.net/ubuntu/+sour](https://bugs.launchpad.net/ubuntu/+sour) ... bug/373450 which also has a fix, somewhat.

There is an alternative to all this. You can set up PulseAudio on the Guest too. There is a version for Windows. Check their website, [www.pulseaudio.org](www.pulseaudio.org). You can set the VM to use NULL Audio, with the AC'97, install PA and set it to hook itself to the Host PA server. You may need to change a few settings on the Host to accept remote connections.
All audio should then go to the Host.

******************* 

---

