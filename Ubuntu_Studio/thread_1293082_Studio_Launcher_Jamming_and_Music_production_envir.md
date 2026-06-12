---
title: "Studio Launcher: Jamming and Music production environment on-demand in seconds"
date: 2009-10-16
forum: Ubuntu Studio
---

### Post by motin on 2009-10-16
*Short version:*
A first release of Studio launcher is available at [https://launchpad.net/~motin/+archive/ppa](https://launchpad.net/~motin/+archive/ppa)

Latest version is (for direct download): [https://launchpad.net/~motin/+archive/ppa/+files/studiolauncher_0.1_all.deb](https://launchpad.net/~motin/+archive/ppa/+files/studiolauncher_0.1_all.deb)

*Long version:*
Back in 8.04, I set up [some scripts]("http://ubuntuforums.org/showthread.php?t=923860") to help out with the complex configuration and initation of JACK based music software in Ubuntu.

With Karmic's Quickly, updates to the scripts (so that they actually work on Karmic) and some newly aquired PPA packaging know-how, the project is resurrected in the form of "Studio Launcher": [https://launchpad.net/studiolauncher](https://launchpad.net/studiolauncher)

It is not finished in any way (and it obviously shows that this is my first attempt to do anything even partly in python) but already helps with a great deal:
- Installation and usage of linuxsampler (which is not in repos nor easy to install using the official packages)
- Configuration of JACK and PulseAudio so that ordinary applications still have sound features while running JACK
- Usage of VSTi instruments (through wine and dssi-vst)

Currently, it requires manual changes to the scripts to work in your environment, the Settings dialog is not yet implemented...

Try out the latest version from my PPA: [https://launchpad.net/~motin/+archive/ppa](https://launchpad.net/~motin/+archive/ppa)

Be sure to read the readmes...

Earlier post (for Hardy):
[HOWTO: Set up a Jamming and Music production environment on-demand in seconds]("http://ubuntuforums.org/showthread.php?t=923860")

> Ever since I started using Linux, I have wanted to use free applications for Jamming and producing music. This is "very possible" and over the years I have found how to combine many free tools to transform my laptop into a jamming box that has joined me at several performances. 

But... setting up all applications every time takes quite some time, (not accounting the research needed to get them running in the first place...). We are using Linux, right? So why not automate the process?

Cutting to the chase, I have finally written a helping script that configures my home jamming and music production environment most automagically. Actually, I haven't come to far in music production in this script (todo...), but at the current stage, at least it makes my MIDI keyboard useful, and should help quite some others to that as well I hope...

All in all, hope this helps you get up and jamming!

EDIT: This software requires previous JACK and realtime kernel setup. If you are new to Music in Linux, i strongly recommend [http://wiki.linuxmusicians.com/](http://wiki.linuxmusicians.com/) as a great starting point to learn what is possible.

---

### Post by motin on 2009-10-20
Replying here on posts from the old thread:

> **bolex100 said:**
> I must say that i like the idea of this, but I'm more interested in the USE of the packages than the installation.  (although fitting together is important!)
Perhaps you could enlighten use about what you actually do with them.

At the moment it allows me to use a MIDI keyboard to play various software synthesizers using the 16 different channels. I'll definitely update the project page later including the various use-cases... Thanks for the feedback! :)

> **AutoStatic said:**
> Looks good, but I've checked some of the scripts and apparently this does not set up a real-time low-latency environment which seems a bit pointless to me. But correct me if I'm wrong :) And personally I disable PulseAudio completely when working with audio on my system.

As stated in the readmes, this helps in setting up the various music-softwares together but requires preivous experience of jack and an already working real-time environment for best performance. However, there is already a lot of documentation on that part and it's pretty straight-forward to set-up: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

About PulseAudio - I like to use Amarok and Youtube while jamming. That way I can play along with any music I feel like for the moment. And since it's possible to use them at the same time, but _very_ difficult to set-up in Ubuntu for the novice (since jack is not included in main), I hope this comes in useful. 

Cheers

---

### Post by AutoStatic on 2009-10-21
> **motin said:**
> 
As stated in the readmes, this helps in setting up the various music-softwares together but requires preivous experience of jack and an already working real-time environment for best performance. However, there is already a lot of documentation on that part and it's pretty straight-forward to set-up: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)Ah, I checked the scripts but did not read the readme's #-o

> **motin said:**
> About PulseAudio - I like to use Amarok and Youtube while jamming. That way I can play along with any music I feel like for the moment. And since it's possible to use them at the same time, but _very_ difficult to set-up in Ubuntu for the novice (since jack is not included in main), I hope this comes in useful.Good point. I use Audacious which has a JACK plugin. I barely check YouTube so that possibility didn't cross my mind.

---

### Post by markbuntu on 2009-10-22
That is interesting. I will give it a try when I get karmic studio up and running.

udev suspends pulse when jack starts, how did you get around that?

I am asking because there was some recent questions about that on the pulse mailing list and lennart was sceptical that it could be done properly.

---

### Post by motin on 2009-10-23
> **markbuntu said:**
> That is interesting. I will give it a try when I get karmic studio up and running.

udev suspends pulse when jack starts, how did you get around that?

I am asking because there was some recent questions about that on the pulse mailing list and lennart was sceptical that it could be done properly.

By running qjackctl.bin directly instead of the wrapper script qjackctl (which suspends pulse when jack starts). Hope it helps :)

---

### Post by motin on 2009-10-23
> **AutoStatic said:**
> Good point. I use Audacious which has a JACK plugin. I barely check YouTube so that possibility didn't cross my mind.

Also, it's possible to use Skype properly now when it supports PulseAudio. :)

I am working on a PPA to help out with the installation of the PulseAudio JACK sink: [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main](https://launchpad.net/~motin/+archive/until-jack-is-included-in-main)

Still a work in progress, I'll get back when it's working better.

---

### Post by AutoStatic on 2009-10-23
> **motin said:**
> I am working on a PPA to help out with the installation of the PulseAudio JACK sink: [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main](https://launchpad.net/~motin/+archive/until-jack-is-included-in-main)

Still a work in progress, I'll get back when it's working better.That's good news motin! I'm now using Khashayar's PPA for those modules, not very ideal but at least those modules are compiled against the same version of PA that Jaunty uses.

---

### Post by AutoStatic on 2009-10-23
> **motin said:**
> By running qjackctl.bin directly instead of the wrapper script qjackctl (which suspends pulse when jack starts). Hope it helps :)It sure does, never thought of that before... * adapts startup scripts *

---

### Post by motin on 2009-10-23
> **motin said:**
> I am working on a PPA to help out with the installation of the PulseAudio JACK sink: [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main](https://launchpad.net/~motin/+archive/until-jack-is-included-in-main)

Still a work in progress, I'll get back when it's working better.

Now it includes I believe the most important libraries. Studio Launcher setup now uses this PPA.

New version of launcher (~public5) - changelog:
"Usage of new JACK-enabling PPA for an easier and more complete installation. Minor changes in documentation"

---

### Post by motin on 2009-11-01
Major updates. Scripts revised, more applications included in setup, patchbay persistance used for connection of audio ports, documentation updated. First release...

V 0.1 Available in the PPA :)

---

### Post by medienstudent on 2009-12-22
Hey Motin,
your project sounds really nice. So I implemented your PPA. I haven't install ubuntu studio; but I downloaded most apps used there. Jack is working fine and also ardour. 

I couldn't find any readmes for help to install. Where are they?

Until now, it doesn't work to run any pulseaudioprogram with jack, even some versions of audio-packages were updated.

Now I made a look through 'withjack'-packages in Synaptic version-search and installed some new, which I suspect, they are needed. I m gonna restart the computer-tension...
still not working. May you help me to get your phantastic idea to work.

---

### Post by mwasem on 2010-01-22
I'm running this right now with an external Edirol sound card, using ffado and jack.  It's amazing, you can connect any app to jack trough the pulseaudio server.  The Jack control must be started using the command:

```
$ qjackctl.bin
```

as was said above, instead of the standard command.  Once you start the jack daemon, connect it to pulse by typing in another terminal:

```
$ pulse-jack
```

That's all it took.  If this doesn't work, double check that you have all the relevant packages in this ppa, specially pulseaudio compiled with jack support and the connector, pulse-jack.

---

### Post by jorgealfonso on 2010-04-03
Hi everybody!

Since I started the project of making music on Ubuntu, I am having serisous issues with pulseaudio making jack applications crash. Pretty discouraging... but this could be the solution I have been looking for :)

Post corrected:After being lost for some days, I just noticed (by chance) the Studiolauncher icon installed on the "Sound and Video" menu. I'm trying it right now.

---

