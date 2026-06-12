---
title: "Can't get Firepod firewire interface working in Ubuntu"
date: 2009-03-10
forum: Ubuntu Studio
---

### Post by sumpm1 on 2009-03-10
Hey guys. I just got a Presonus Firepod interface and want to get it working in Ubuntu. I have Jack and Qjackctl installed. I run Jack Control, and select Freebob from the list of drivers. I get the following mewssages from Jack:

```
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
13:51:42.599 JACK was stopped successfully.
13:51:42.600 Post-shutdown script...
13:51:42.600 killall jackd
13:51:42.600 JACK has crashed.
13:51:42.620 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

I am not even sure that my firewire card is recognized in Ubuntu, how can I do that? And where do I need to start to get the Firepod working with Jack?

Thanks

---

### Post by Stochastic on 2009-03-10
Looks like you have a permissions error (this is actually the default firewire setup in Ubuntu).  To fix this do ```
sudo apt-get install ubuntustudio-controls
``` then go to System->Administration->Ubuntu Studio Controls
You'll want to check off the middle box (labeled raw1394) - and if you have the realtime kernel installed you probably will also want to check the other options.  Click apply then click close.  That should take care of things (a reboot shouldn't be needed but can be a good next step if any problems arise).  Let us know if you get it working.

---

### Post by sumpm1 on 2009-03-10
Hey Stochastic. I just have regular Ubuntu 8.10 installed, not UbuntuStudio. I installed that program, but it does not start when I run it. Since I have a ton of software installed, and I like my current Ubuntu setup, I was trying to avoid having to install UbuntuStudio and the realtime kernel. I do not need super low latency for recording, I personally do not monitor while I record. BUT, I did hear that you can just install the packages that come with UbuntuStudio.

---

### Post by Stochastic on 2009-03-10
The 8.10 realtime kernel is borked, so avoid installing that.

UbuntuStudio really is just a collection of meta-packages (plus that configuration manager I recommended you install, and some theme packages), so adding them to your current setup will not be any different than installing a bunch of separate programs.  To see which meta packages there are do ```
apt-cache search ubuntustudio
```

As for the Firewire issue, could you run this from a terminal and post the output: ```
gksu ubuntustudio-controls
```  I'd like to know why it's not running on your machine.

To do the firewire configuration manually, open a terminal, do ```
sudo nano /etc/udev/rules.d/40-permissions.rules
```
find the line that reads ```
KERNEL=="raw1394",                      GROUP="disk"
``` and change it to ```
KERNEL=="raw1394",                      GROUP="video"
``` save and exit.  Then you'll need to reload the raw1394 module, I forget the command right now, but a reboot will take care of it.

---

### Post by sumpm1 on 2009-03-11
Update: I was able to get the Firepod working with Jack and Freebob. I set the group to GROUP="audio" similar to your instructions, but found elsewhere. If I turn off the Firepod after Jack starts, then turn it back on and start Jack, the blue light comes on and I am able to RECORD ONLY.

That's right, I got it working if I set "Capture Only" from the Jack setup, I recorded a couple of tracks in Reaper with WineAsio. If I try "Duplex" or "Playback Only," I get xruns popping up every second or two, hmmm. I tried bumping up the samples/buffers in Jack to no avail.

BTW, I booted up XP, downloaded the Firepod XP drivers, and was recording in Reaper; just to make sure all of my hardware worked, and it did.






For the permissions with raw1394, I set the group to GROUP="audio" as instructed on the Presonus forum in the following link. I also created an "audio" group and added myself and root to it.
 


[http://forums.presonus.com/showthread.php?t=5306&highlight=raw1394](http://forums.presonus.com/showthread.php?t=5306&highlight=raw1394)

---

### Post by kayosiii on 2009-03-11
unfortunately freebob is a bit borked in Intrepid... see if you can't get freebob from hardy and install that instead...
Alternatively you could build the new drivers ffado but that is a lot of work on Intrepid (a lot easier on Jaunty though).

---

### Post by sumpm1 on 2009-03-12
Well, I believe libfreebob or whatever package Freebob is in, got installed with Jack. So would I purge-remove Jack from my computer, and then get the Hardy debian installer?

I am sort of new (6 months) to Linux and Ubuntu, and was always afraid of "compiling" or "building" packages and things. Tell me, is "compiling" or "building" a package just refer to ./configure, make, and install? Because I have had to build things that way with minimal success before.

@kayosiii: Also, won't having Ffado installed allow me to have a software mixer for the Firepod, or at least mute the inputs?

Thanks.

---

### Post by ussndmac on 2009-03-12
First let me say you should be able to get the it running with the suggestions that have been made so far. But, as mentioned 8.10 -rt kernel is not there yet, though I understand it is close.

In addition, there are a couple of issues with Ardour, Jack and Freebob from the repositories. In short they are old revs. In addition Jack compiled with non-standard symlinks to libs. This makes it lesss than trivial to just down the sources and build.

But the FP should work without that.

All that said, I have the following working well:

Ubuntu Studio 8.04 (thus -rt)

and from this PPA:

[https://launchpad.net/~khashayar/+archive/ppa](https://launchpad.net/~khashayar/+archive/ppa)

Backported latest:

Ardour
Jack
FFADO

I have this working for both dual Firepods and dual Audiofire12's.

Regards,
Mac

---

