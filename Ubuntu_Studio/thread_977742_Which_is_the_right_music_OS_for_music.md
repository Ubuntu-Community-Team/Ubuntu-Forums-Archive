---
title: "Which is the right music OS for music"
date: 2008-11-10
forum: Ubuntu Studio
---

### Post by Nu music project on 2008-11-10
Ok,the artist formally known as Bolex100 restarts his world with a new name. A respondent had suggested making the thread titles more descriptive.  I figure with this name you'll know my ultimate goal.

My aim is to take my laptop to small venues and use it as a drum machine or sequencer.  Ideally I want to link the sequencer and drum machine together.  lastly ( and more importantly) I want to be able to start up and run with the minimum of fuss, because I can't jump on stage at 5 minutes warning a be "configuring".
By the way, its a Dell inspiron 1525. Current O/S is Ubuntu 8.1


So question #1.  Should I install Ubuntu-studio? What extra does it give me?   Do i need that?  can I just run vanilla.  What is the downside?

---

### Post by kayosiii on 2008-11-10
Well Ubuntu studio installs a bunch of extra software - which you can install individually as well - installing ubuntustudio-audio is like saying give a whole bunch of the better sound programs.

The other thing is it usually (not for 8.10) installs the realtime kernel for you - you can do this anyways... 

It also installs some tools to configure your computer better for doing sound.

You can get all the benifits of running ubuntu studio by installing the ubuntustudio packages from regular ubuntu.

As far as drum machines go - my first stop would be to check out Hydrogen. Not sure what I would pick as a sequencer

---

### Post by Nu music project on 2008-11-13
Can I upgrade to ubuntustudio or do I have to rebuild my O/S from scratch?

---

### Post by snowpine on 2008-11-13
+1 to what kayosiii said. You don't need to reinstall; all of the Ubuntu Studio applications are available to a "vanilla" Ubuntu system.

Try this: Open the synaptic package manager (gksu synaptic) and search for ubuntustudio. You'll see they are separated (audio, video, etc) so you can just install ubuntustudio-audio if you want.

Part of the ubuntustudio-audio package is linux-rt, the real time kernel, which has low latency for audio production. You can select between the generic and real time kernels from Grub. 

Hydrogen is a nice drum machine; I have no experience with the sampling side of things.

Good luck!

---

### Post by markbuntu on 2008-11-14
You can get started with this:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

There are more links about setting up jack and stuff like that here (near the end):

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

