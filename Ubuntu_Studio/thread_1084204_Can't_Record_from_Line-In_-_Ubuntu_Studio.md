---
title: "Can't Record from Line-In - Ubuntu Studio"
date: 2009-03-01
forum: Ubuntu Studio
---

### Post by Dougger on 2009-03-01
I have a feeling that this has been covered elsewhere - but I'm Googled and forum-search'd out at this point.  I've come across things that almost, but not quite, get at my problem; including Markbuntu 10,000 page thingy.

As the title indicates, I can't seem to record from the line-in.  Playback works like a champ, and I can mute the the line-in from the volume control record tab, and it indeed mutes (tapping microphone while cycling mute).  The mic is going through a preamp, so it's a line-level signal.

Can't get muting from any of the PulseAudio sources.

Can't get SoundRecord to record.

As far as gear, let's see if I can give the pertinent stuff:
Pentium D processor, 2.66GHz
1.0 GB RAM
Gigabyte MOBO, M/N GA-8I945GZME-RH (onboard sound disabled in BIOS)
Turtle Beach Santa Cruz PCI sound card (CS 46XX chipset)

OS is Ubuntu Studio, 8.10

I'm attaching screen shots of the gnome-volume-control, Sound Preferences, and PulseAudio volume.

Halp!

---

### Post by markbuntu on 2009-03-03
Change the sound capture to pulseaudio and then make sure the default device in the PA volume control is the CS46 whatever by right clicking on it etc. Sound recorder generally uses the PA default to record from.

---

### Post by Dougger on 2009-03-03
Ok, in Sound Preferences I have all entries set to PA, except for "Default Mixer Tracks," which is set for the Cirrus Logic OSS mixer.

On the Input tab of the PA volume control, I had it display all available inputs.  I set each one in turn to default, and for each one pulled up the PA Volume Meter for recording - no signal displayed.  Also, couldn't mute the input from from any of the available PA inputs.

The only place that lets me mute the input is the Record tab of the OSS mixer.  The ALSA mixer lets me mute the input from the Playback tab, but neither Capture 1 nor Capture 2 do anything on the Record tab.

The three available inputs shown in the PA volume control are:
1- Monitor Source of ALSA PCM on front:0 (CS46xx) via DMA
2- ALSA PCM on front:0 (CS46xx) via DMA
3- Monitor Source of Simultaneous Output to ALSA PCM on front:0 (CS46xx) via DMA

It lools like, from the PA Device Chooser, you can specify a source from other than the default...no drop-down choice though, have to type it explicitly, I guess.

Any other thoughts?

---

### Post by markbuntu on 2009-03-04
You might find more controls with the gnome-alsa-mixer, it is in the repos.

---

### Post by Dougger on 2009-03-04
98% Solved!  Thanks for that last tip - I'm now able to at least record from the line-in.

However, when I start the gnome-alsa-mixer, I get an error.  When I display the details, there are a multitude of lines that look like this:
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/Cirrus_Logic_CS4297A_rev_4,Cirrus_Logic_CS4294_rev_5": `,' is an invalid character in key/directory names

But, the sliders still come up.  I find that I have to have both ADC and Capture marked for record to get anything.

Also (could be related), it seems that in both Ardour and Audacity, I'm getting the stereo mix along with the line-in signal.  Same result from pulling up the PA record monitor, and playing mp3's - it picks up the mp3 playback along with the line-in.  Can't seem to get the right combination of options to get it to look at only line-in.

There are a couple of results coming up when I search the error - haven't found anything exactly relevant yet.  I'll try again after a refuel.

---

### Post by Dougger on 2009-03-04
Success!  Installed a different version of alsamixer - there's no "about" menu, but the title says "Gamix".  Allows you to select mix or line for capture.

Thanks again for pointing me in the right direction, MB!

---

