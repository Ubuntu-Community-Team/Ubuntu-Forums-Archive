---
title: "only records noises from line-in and other audio errors.."
date: 2009-02-08
forum: Ubuntu Studio
---

### Post by iseeclouds on 2009-02-08
ok, i finally have Renoise working in ubuntu studio. but today i noticed some other annoying things... i already tried several 'solutions' (like this for example [http://ubuntuforums.org/showthread.php?t=789578&highlight=audacity](http://ubuntuforums.org/showthread.php?t=789578&highlight=audacity)) but nothing works. or maybe i'm trying the wrong things? here are my problems:

- when i record something from the line-in/mic input i only get small cracks but no sound. (i thought it was audacity's fould but get the same thing in ardour).
- can't use more than one audio-program at a time. can't even play audio while renoise is open or have 2 renoise files open at the same time.
-when i plug in my headphones, the internal speakers from my laptop keep working.


hope anyone can help me.

---

### Post by sgx on 2009-02-09
Very precise details of your computer hardware, OS, and installed software will be needed! Help will follow...
Cheers

---

### Post by rlameiro on 2009-02-09
Yes, please give more details. Just one more question, are you using JACK?

---

### Post by iseeclouds on 2009-02-09
> **sgx said:**
> Very precise details of your computer hardware, OS, and installed software will be needed! Help will follow...
Cheers
sorry for my ultra-n00bness. but where do i find this?

i have ubuntu studio installed over ubuntu 8.04

hardware: Intel Centrino Processor technology with Intel Core 2 Duo Processor T5800, NVIDIA GeForce 9600M GS DirectX® 10 with
256 MB GDDR3 memory en digital HDMI audio/video output.

i run Renoise through ALSA ('cause jack makes the sound in renoise all glitchy and noisy). i think it also uses the rt-kernel. i used to work with audacity (on Vista) but whatever setting i try i only get really bad sounds. Ardour does the same. i just want to have a simple recording program that i can run on the same time as renoise. i'm not using jack, tried it but it only made things worse or maybe i put the settings wrong.

---

### Post by sgx on 2009-02-09
> **iseeclouds said:**
> sorry for my ultra-n00bness. but where do i find this?

i have ubuntu studio installed over ubuntu 8.04

hardware: Intel Centrino Processor technology with Intel Core 2 Duo Processor T5800, NVIDIA GeForce 9600M GS DirectX® 10 with
256 MB GDDR3 memory en digital HDMI audio/video output.

i run Renoise through ALSA ('cause jack makes the sound in renoise all glitchy and noisy). i think it also uses the rt-kernel. i used to work with audacity (on Vista) but whatever setting i try i only get really bad sounds. Ardour does the same. i just want to have a simple recording program that i can run on the same time as renoise. i'm not using jack, tried it but it only made things worse or maybe i put the settings wrong.
Try starting jackd like this, from a command line:
jackd -dalsa -r44100

Then start qjackctl from another command line. Just type the word at the prompt.
Now start zynaddsubfx, again, just type the name at a command prompt.

adjust windows as needed, and look at the 3 tabs in qjackctl gui, the Audio tab should have zyn on the left, and 'system', or something related, on both left and right.
Click on zyn, highlighting it, then click on system on the opposite side, highlighting it, and now at the bottom lower left, click the Connect  button, a line should appear between the zyn and system to indicate the connection.

Now click the Alsa tab, and connect zyn (on the right this time) to your sound-chip/card, which should be listed on the left, again, a line appears between the two, indicating a connection.
Now, in the zyn interface, upper right, just below the PANIC button, is a
VK button, press it to display a midi keyboard, now play the zyn synth
with the qwerty-keyboard when your mouse is over the zyn keyboard, or by mouseclicks. 

This should work out of the box, but use synaptic to install zynaddsubfx if it is not yet there, its a world-class synthesizer!
If no sound source is shown on the left side of the Alsa panel in qjackctl, then Ubuntu needs you to configure your sound system using the tools in the system menus.
Cheers
Note that other topics show Ubuntu Studio 8.10 to be seriously flawed. If you have 8.10 apps installed over any version of 8.04, there could well be some bad chemistry. A clean install of 8.04, using synaptic for adding audio apps as needed, or a clean install of 8.04 Studio, would both be more stable than a hybrid of 8.10 and 8.04.

---

### Post by iseeclouds on 2009-02-10
> **sgx said:**
> If no sound source is shown on the left side of the Alsa panel in qjackctl, then Ubuntu needs you to configure your sound system using the tools in the system menus.
how do you do this? only thing in that side is "14/mid through". tried to change settings in system/preferences/sound but that doesn't work. still get cracking sound in renoise and i also can't listen music when jack is running.

> **sgx said:**
> A clean install of 8.04, using synaptic for adding audio apps as needed, or a clean install of 8.04 Studio, would both be more stable than a hybrid of 8.10 and 8.04.
used synaptic to install packages of ubuntu studio 8.04 on ubuntu 8.04.2. i hope that's stable, hadn't experienced any problems with that.

---

### Post by iseeclouds on 2009-02-10
ok, i can finally run Renoise decently through Jackd. i can also play something in Ardour while Renoise is open. i can also record in Ardour. i can only use the mic-input for recording, but it's sensible for overdrive. is there a way i could use the line-in instead?
The Jack icon turns red when i play something for the first time and stays red. what does this mean? how do i stop this from happening?
i still have the problem that my internal laptop-speakers don't mute when i plug in headphones. any solutions?

---

### Post by sgx on 2009-02-13
> **iseeclouds said:**
> ok, i can finally run Renoise decently through Jackd. i can also play something in Ardour while Renoise is open. i can also record in Ardour. i can only use the mic-input for recording, but it's sensible for overdrive. is there a way i could use the line-in instead?
The Jack icon turns red when i play something for the first time and stays red. what does this mean? how do i stop this from happening?
i still have the problem that my internal laptop-speakers don't mute when i plug in headphones. any solutions?

Hi, check  your ubuntu menus for hardware configuration/detection options,
your soundcards 'system' capture connections should display on the left qjackctl audio panel, 'system' playback, on the right. Click the + sign by the word 'system' to see the expanded view. Ardour should show up in qjackctl, I'm re-installing it now, and will edit this. Try and get it working without renoise first? Renoise is a pretty new project, so integration with longstanding apps is in the infancy. Great to see you are conquering as you go!:)
In the meantime. a huge Ardour tutorial I  found lurks here:
[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

---

