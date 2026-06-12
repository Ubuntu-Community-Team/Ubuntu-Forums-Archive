---
title: "Pangolin v2 (Value) with Gutsy"
date: 2007-10-12
forum: System76 Support
---

### Post by Rowan187 on 2007-10-12
So far things have been well... pretty good, minor graphical glitches here and there. I just wanted to mention to the staff that with the Pangv2 (im pretty sure thats what version i have. its the Pangolin Value from back in April), when the Driver 2.0.9 is installed, sound and wireless and everything works, but the graphics card doesn't seem to be working correctly. Some games and some compiz fusion effects flicker and the mouse won't appear in some of the games.

I checked in the Synaptic Package Manager and it seems 915resolution isn't even installed this time, which I recall the System76 Driver installing it the other times.

Sorry if my wording is weird today, been up for two days with no sleep for different reasons. I'll clear anything up if anyone can't understand. Sorry about that

Thanks for your time
-Rowan

---

### Post by thomasaaron on 2007-10-15
Thanks for letting us know. 

They System 76 driver likely will clear that up. Right now, it does nothing with Gutsy.

We're testing this week.

Best,
Tom

---

### Post by Rowan187 on 2007-10-16
> **thomasaaron said:**
> Thanks for letting us know. 

They System 76 driver likely will clear that up. Right now, it does nothing with Gutsy.

We're testing this week.

Best,
Tom

ah thank you, after recent updates from Ubuntu its gotten better but the graphics are still a little choppy. Thanks for checking it out, So far I've seen nothing but greatness from System76 and their support. I knew it was the right choice over Dell :)

---

### Post by gbutler69 on 2007-10-16
I just received my "Pangolin Value". This is the second System76 laptop I've purchased in less than a year. My first was a "Gazelle Performance".

After I received it, I did the upgrade to "7.10 Gutsy Gibbon". Out of the box, the graphics were "Bandy" (before the upgrade), but, compiz worked (enable graphics effects, wobbly windows/cube).

Currently, after the upgrade, the banding in the graphics is gone, but, my sound doesn't appear to work. Also, I cannot get the desktop effects to work. When I try, it says "Unable to enable Desktop Effects" (after a short pause).

I'm a little unsure at this point if it installed the drivers correctly. I tried installing the "System76" drivers (from the option under System - Administration), but, it says something to the effect of "...all drivers are provided by Ubuntu...".

I'm a little disappointed in this laptop as compared to the previous one I purchased a little over 6 months ago. It came with 6.10 and upgraded to 7.04 without a hitch. I've been running Beryl with all the effects on that one.

I'd really like to have my sound and video working better. I really miss the desktop effects. I've come to find them a great aide to my productivity.

Is there a resolution for these issues?

Thanks...

---

### Post by thomasaaron on 2007-10-16
It's a little pre-mature to be disenchanted with the laptop, considering Gutsy hasn't even been released yet. You've kinda jumped the gun a little!  :lolflag:

The System 76 driver is still supporting Feisty. It won't do anything under Gutsy yet. We are smack in the middle of gutsy testing right now.

I just tested sound on a PanV3. It will work just fine.

See if this fixes it:

1. sudo gedit /etc/modprobe.d/alsa-base
2. add this line to the VERY end of the file, then click the save button.
options snd-hda-intel model=toshiba
3. reboot your computer

---

### Post by gbutler69 on 2007-10-16
After following your instructions to edit the '..../alsa-base' file and rebooting, the sound still does not work.

I'm trying from both "Preferences - Sound - TEST" and "Preferences - Multimedia Systems Selector - TEST". Neither produces any sound on the built-in speakers or when I hook up headphones.

Any other things I could try?

lsmod | grep intel

gives the following output

gbutler@ubuntu:~$ lsmod | grep intel
snd_hda_intel         263712  1 
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
gbutler@ubuntu:~$

---

### Post by thomasaaron on 2007-10-16
OK. There are a couple of realtek patches that have to be incorporated into alsa.
I guess they didn't make it into Gutsy.

It's all in the sound.py file if you want to give it a go.

Look at the wget command for the panv3/gazv5. It downloads sys76-alsa.... That is the Alsa version you want. Patches are included therein.  Then just compile it based on the commands in that section.

(Note: I believe it will also work with Alsa 1.0.15 (the latest stable: alsa-project.org). That version definitely has the patches included.

The driver that supports Gutsy should be out on Thursday if you want to go that route.

Best,
Tom

---

