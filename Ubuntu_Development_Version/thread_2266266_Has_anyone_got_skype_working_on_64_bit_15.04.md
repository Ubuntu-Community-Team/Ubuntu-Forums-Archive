---
title: "Has anyone got skype working on 64 bit 15.04?"
date: 2015-02-21
forum: Ubuntu Development Version
---

### Post by ubername on 2015-02-21
Hi

I have tried installing skype on an up to date version of 64 bit 15.04  via these instructions:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I can't get the sound to work (neither microphone nor speakers) (videocam works).

I tried following this:

[http://www.dedoimedo.com/computers/linux-skype-4-3-no-sound.html](http://www.dedoimedo.com/computers/linux-skype-4-3-no-sound.html)

However when I try and install the 

sudo apt-get install libpulse0:i386


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libpulse0:i386 : Depends: libsndfile1:i386 (>= 1.0.20) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I basically get lost in a set of dependencies. 

Using fix broken packages from synaptic doesn't help.

So I then do: 
 sudo apt-get install libsndfile1:i386


and get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libsndfile1:i386 : Depends: libflac8:i386 (>= 1.3.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

so i then do:

sudo apt-get install libflac8:i386


and get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 indicator-bluetooth : Depends: unity-control-center but it is not going to be installed or
                                gnome-control-center but it is not going to be installed or
                                ubuntu-system-settings but it is not going to be installed
 libcanberra-pulse : Depends: pulseaudio
 libcheese-gtk23 : Depends: libcheese7 (>= 3.4.0) but it is not going to be installed
 libpulse0 : Depends: libsndfile1 (>= 1.0.20) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

At which point I thought I would post here to see if anyone has an answer.

---

### Post by ubername on 2015-02-21
Please feel free to just say you have got it working, without providing nay details or solutions: I just want to check there is something odd with my set-up. I'm off to create a new user now to see if that will work.

---

### Post by Jack_Mathews_Jr. on 2015-02-21
Working fine for me. Just installed and logged in no problems. Upto date 15.04 on HP G7 laptop. Forgot, it is 64 bit 15.04.

---

### Post by jerrylamos on 2015-02-21
All up to date vivid amd64::

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu Vivid Vervet (development branch)"
Linux Lenovo2 3.18.0-13-generic #14-Ubuntu SMP Fri Feb 6 09:55:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Then did:

sudo apt-get install skype:i386

Note whole potful (!) of i386 libraries installed.

Then did:

skype

signed on with our skype account

Called my cell and it worked.

---

### Post by ubername on 2015-02-22
Thanks, did you use the version from the standard repos?

---

### Post by Jack_Mathews_Jr. on 2015-02-22
I am using version 4.3.0.37. I downloaded it from here > [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/) and installed it with software center.

---

### Post by jerrylamos on 2015-02-22
> **ubername said:**
> Thanks, did you use the version from the standard repos?

I assume standard repros since I just used 
sudo apt-get install skype:i386
so whatever the default.  Just as a test since this is vivid 64 install, I tried without the i386 and it wanted to install tons of i386 stuff anyway.  I assumed skype was 32 and not 64.
This is a vivid installed from the .iso a couple days ago with no mods other than my personalization, i.e. firefox flash, chromium + pepperflash, screen setup, apt-get updates, samba, synaptic, zsync, gparted, ufw firewall, privacy settings, etc. mostly done fairly automatically with an exec since for development I wind up doing an install every couple weeks, and 4 test pc's at that.

---

### Post by motang on 2015-02-23
I'm runnung 64bit Ubuntu 15.04, and installed Skype from the Software Center without any issues. Works fine for me.

---

### Post by Scott Deagan on 2015-03-31
You need to make sure you have enabled the "Canonical Partners" repo on Software & Updates:

1. Open "Software & Updates".
2. Click on the "Other Software" tab.
3. Tick the "Canonical Partners" checkbox.
4. From the terminal, run: sudo apt-get update
5. From the terminal, run: sudo apt-get install skype

For those who strive for perfection, there is an additional (but optional) step in Ubuntu:

6. sudo apt-get install gtk2-engines-murrine:i386 gtk2-engines-pixbuf:i386

Step 6 will make sure Skype is themed to match unity.

---

### Post by ubunt72 on 2015-04-12
> **Scott Deagan said:**
> You need to make sure you have enabled the "Canonical Partners" repo on Software & Updates:

1. Open "Software & Updates".
2. Click on the "Other Software" tab.
3. Tick the "Canonical Partners" checkbox.
4. From the terminal, run: sudo apt-get update
5. From the terminal, run: sudo apt-get install skype

For those who strive for perfection, there is an additional (but optional) step in Ubuntu:

6. sudo apt-get install gtk2-engines-murrine:i386 gtk2-engines-pixbuf:i386

Step 6 will make sure Skype is themed to match unity.
I did most of it - this way.   Except for the last part.   I used Synaptic instead of the terminal and I'm using Xubuntu 15.04 (beta 2) so I didn't use the last step.

Not sure how you other guys used Software Center.   The only skype packages I noticed there had to do with themes and empathy etc.   I found the skype package listed in synaptic, though.

OP or anyone wanting to install skype - it's easier using the 'Canonical Partners' method.

---

### Post by The Bright Side on 2015-05-12
Does anybody have trouble with sound input in Skype? On my system, Skype installs properly and properly recognizes Pulse Audio. It even plays back sound.

However, it just won't hear me :-( pavucontrol shows me that sound input is working quite well: the volume bars respond when I speak into the mic.

My sound output is my NVidia GeForce 970 card, HDMI to 5.1 receiver. My input device is the onboard sound card, mic plugged into the rear panel. Running Ubuntu GNOME 15.04, 64 bit.

I installed Skype using the deb, and when problems arose, I re-installed it from the Software center. No dice. Does anybody have any suggestions?

---

### Post by dino99 on 2015-05-12
as pavucontrol shows the sound input, then the 'software' side is ok. Might be related to the jack not plugged as it might be (wrongly plotted), try something else

---

### Post by The Bright Side on 2015-05-12
That's what I would think, too. However, pavucontrol not only correctly reports the mic as plugged in, but also responds when I speak into it. The system definitely "hears" me correctly, only Skype doesn't.

---

### Post by dino99 on 2015-05-12
could be also a bios's sound setting wrongly set to 'ac97' instead of 'hda'

---

### Post by The Bright Side on 2015-05-12
Nice, thanks! I will try that tonight.

---

### Post by cariboo on 2015-05-12
Thread closed, as we are now discussing Wily.

---

