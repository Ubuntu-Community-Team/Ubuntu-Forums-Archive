---
title: "I hate thee Jack Ctrl"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by DestriAero on 2008-06-01
Hey guys - I am here with more questions.

I have jack set up as the following (screenshots attached). I run 8.04 real-time kernel. I have alsa set up and working. In order to launch jack i have to "alsa force-reload" after which it finally connects.

However anything I play back thru jack with alsa, is plagued by xruns, therefore everything i playback is slowed down and is basically noise.

What can I do??? I am running Thinkpad R60 with an HDA Intel card. Please note that ALSA by itself without Jack runs smoothly. Minus the startup sounds that also crackle a bit O.o

---

### Post by markbuntu on 2008-06-01
Try changing the input and output devices to ALSA or to your sound card instead of default. 

Then go to System/Preferences/Sound and change that from automatic to ALSA or to your sound card.

Those things often default to pulseaudio so you need to explicitly tell them what to do.
There is also a little app you can get to change the ALSA default. It is in the repos. It is handy of you are constantly switching around between jack and alsa and pulseaudio and OSS apps and just want to get things back to normal.

You really have to just fool around with these settings to find out what works best.

You can also try changing the Frames/Period down and Periods/Buffer up to get rid of the xruns.

Also, apps do not always shut down jack when they are done with it so you need to do it manually in Jack Ctrl when you are finished with them to get ALSA back. I found this with hydrogen and a few other apps that use jack.

---

### Post by Ed J on 2008-07-16
> **markbuntu said:**
> 

There is also a little app you can get to change the ALSA default. 



What "app" are you talking about?

> **markbuntu said:**
> 

Also, apps do not always shut down jack when they are done with it so you need to do it manually in Jack Ctrl when you are finished with them to get ALSA back. I found this with hydrogen and a few other apps that use jack.

I've experienced some of this funny behavior also.

---

### Post by markbuntu on 2008-07-16
asoundconf-gtk  (choose default alsa sound card)

I find it very helpful. After it is installed, you can find it as System/Preferences/Default Sound Card.

You shoud also check in etc/libao.conf and make sure it has only this line:
default_driver=alsa 

Also, make sure you have the packages

libasound2

and

libasound2-plugins

which is the plugins for jack and oss and pulseaudio

---

### Post by Ed J on 2008-07-17
I like the asooundconf -gtk, just what I needed for multiple sound cards...a day ago. 
 Maybe you can tell me why pulseaudio shows up in the list of cards.  Is pulseaudio emulating a card? 

 Also I'm looking at your post " Multiple Sound Solution (ALSA w Pulseaudio)
 Multiple Sound Solution (ALSA w Pulseaudio)"  Is this the latest and greatest method?  I'm giving it a shot, I'll post results on that thread.

Ed J

---

### Post by markbuntu on 2008-07-19
OK. I will see you there.

---

