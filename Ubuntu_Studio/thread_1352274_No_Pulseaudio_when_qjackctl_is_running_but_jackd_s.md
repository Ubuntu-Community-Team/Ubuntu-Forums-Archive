---
title: "No Pulseaudio when qjackctl is running but jackd stopped"
date: 2009-12-11
forum: Ubuntu Studio
---

### Post by neufena on 2009-12-11
Hi,

Got a very strange problem.  Pulseaudio works fine and I can play Mp3s etc when qjackctl isn't running.  I've also set up a jack pulseaudio sink so it works when jackd is running too.  BUT when qjackctl is running but the jack server is stopped I get no audio.  No error messages but nothing will play either, any ideas?

---

### Post by AutoStatic on 2009-12-11
Yes. As soon as you start up /usr/bin/qjackctl PulseAudio gets suspended, even if jackd is not running. You can try for yourself with the following command: **pasuspender -- /usr/bin/qjackctl.bin**
This suspends PulseAudio and starts up Qjackctl just like /usr/bin/qjackctl does, see for yourself: **less /usr/bin/qjackctl**

---

### Post by bandgeek on 2009-12-29
I have the same problem and am wondering how do you make it so this doesn't happen?

---

### Post by AutoStatic on 2009-12-30
Kill QjackCtl. QjackCtl is run with the **pasuspender** command, see my previous post. So if you want to use Pulse again you have to either kill QjackCtl or start JACK with the corresponding PulseAudio modules. Or don't use QjackCtl but just run JACK directly from the commandline.

---

### Post by trulan on 2009-12-30
Or get qjackctl from a ppa, for instance, frasten's.  Then pasuspender never gets called by qjackctl.  You're opening the door for new and exciting bugs by using ppa's, so use at your own risk.  But that would do what you are asking.

---

### Post by AutoStatic on 2009-12-30
If you run /usr/bin/qjackctl.bin directly pasuspender won't be called too. You could write a startup and stop script then to kill and restart PulseAudio.

---

### Post by bandgeek on 2009-12-30
I'm just not going to bother. All these small hacks are not the the best way to do things.

Why isn't jack in main?

---

### Post by AutoStatic on 2009-12-30
[https://bugs.launchpad.net/ubuntustudio/+bug/407841](https://bugs.launchpad.net/ubuntustudio/+bug/407841)
[https://bugs.launchpad.net/ubuntu/+source/libffado/+bug/416778](https://bugs.launchpad.net/ubuntu/+source/libffado/+bug/416778)

---

### Post by ireneshusband on 2010-01-19
What I have done is simply to go to the JACK Control item in the KDE menu editor (the procedure in Gnome is not much different) and change the command from "/usr/bin/qjackctl" to "/usr/bin/qjackctl.bin". In fact I may create a second item with the orignal command so that I can have a choice of behaviours depending on whether I am planning to run jack on the internal sound card that I normally use for VOIP etc (when I'm out and about), or on the external audio interface I use at home.

---

### Post by Stochastic on 2010-01-21
> **bandgeek said:**
> I'm just not going to bother. All these small hacks are not the the best way to do things.

Why isn't jack in main?
> **AutoStatic said:**
> [https://bugs.launchpad.net/ubuntustudio/+bug/407841](https://bugs.launchpad.net/ubuntustudio/+bug/407841)
[https://bugs.launchpad.net/ubuntu/+source/libffado/+bug/416778](https://bugs.launchpad.net/ubuntu/+source/libffado/+bug/416778)

And now 
[https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/510481](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/510481)

^
|
Watch that to see if it gets done before Lucid's Feature Freeze.

---

