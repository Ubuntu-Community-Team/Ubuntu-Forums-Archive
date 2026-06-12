---
title: "No sound after Karmic update/reboot on Wild Dog"
date: 2010-01-18
forum: System76 Support
---

### Post by jpv on 2010-01-18
Just got a Wild Dog (System76 driver says wilp6).  Stock S76 Karmic 64-bit install, everything worked fine.  (Note, not an upgrade to Karmic, stock Karmic from the factory, which worked.)

I recently did updates and rebooted, so now:
Linux 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

No sound after reboot.  'sudo /sbin/alsa force-reload' makes a bleep from the speakers but is no help otherwise.

$ aplay -l
aplay: device_list:223: no soundcards found...

$ lspci -v
[...]
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Intel Corporation Device 5001
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
[...]

$ lsmod | grep snd
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_hda_intel          31880  0 
snd_hda_codec_idt      72976  1 
snd_hda_codec          87584  2 snd_hda_intel,snd_hda_codec_idt
snd_hwdep               9352  1 snd_hda_codec
snd_pcm                93160  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
snd_timer              26992  2 snd_seq,snd_pcm
snd                    77096  12 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec_idt,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               9088  1 snd

$ dmesg
[...]
[   11.897822] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   11.921824] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   11.921864] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   11.921906] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.921945] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.921983] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.922021] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.922059] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[...]


System > Preferences > Sound:
Hardware is empty
Output is dummy

There is no modem to disable in System > Admin > Hardware Drivers.


Any clues?

---

### Post by jpv on 2010-01-18
I should mention I also tried rebooting into the previous kernel, but that didn't help.

Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

---

### Post by riseringseeker on 2010-01-18
> **jpv said:**
> Just got a Wild Dog (System76 driver says wilp6).  Stock S76 Karmic 64-bit install, everything worked fine.  (Note, not an upgrade to Karmic, stock Karmic from the factory, which worked.)

I recently did updates and rebooted, so now:
Linux 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

No sound after reboot.  'sudo /sbin/alsa force-reload' makes a bleep from the speakers but is no help otherwise.

$ aplay -l
aplay: device_list:223: no soundcards found...

$ lspci -v
[...]
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Intel Corporation Device 5001
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
[...]

$ lsmod | grep snd
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_hda_intel          31880  0 
snd_hda_codec_idt      72976  1 
snd_hda_codec          87584  2 snd_hda_intel,snd_hda_codec_idt
snd_hwdep               9352  1 snd_hda_codec
snd_pcm                93160  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
snd_timer              26992  2 snd_seq,snd_pcm
snd                    77096  12 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec_idt,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               9088  1 snd

$ dmesg
[...]
[   11.897822] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   11.921824] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   11.921864] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   11.921906] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.921945] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.921983] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.922021] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.922059] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[...]


System > Preferences > Sound:
Hardware is empty
Output is dummy

There is no modem to disable in System > Admin > Hardware Drivers.


Any clues?

I had trouble after a clean install of 9.10 on my Wild Dog (wilp5) with the sound, it would play through the USB headset, but not the speakers (after I unmuted them - seems that was the default). You do not mention what you're trying to get the sound out on - speakers, headset, both?  

I had to change which jack I had plugged my speakers into among other things.  The "color coordinated" (black) jack worked fine with Jaunty but with the Karmic install, now I have to have it in the green one - go figure.

I installed PulseAudio Device Chooser

```
sudo apt-get install padevchooser
```

Once you have that installed, it (and volume manager) will show in the Sound & Audio tab.  Click on PA Volume Manager (or click device chooser, then click on the resulting icon in the top panel and choose volume control), and see if anything there is of any help.

The "Playback tab" will only show system sounds until something is playing, and then only for as long as it's playing.

Poke around with that and let me know what you see.  If you wish, I'll send some screenshots of how things are here.

---

### Post by jpv on 2010-01-18
> **riseringseeker said:**
> I had trouble after a clean install of 9.10 on my Wild Dog (wilp5) with the sound, it would play through the USB headset, but not the speakers (after I unmuted them - seems that was the default). You do not mention what you're trying to get the sound out on - speakers, headset, both?  

I had to change which jack I had plugged my speakers into among other things.  The "color coordinated" (black) jack worked fine with Jaunty but with the Karmic install, now I have to have it in the green one - go figure.

I'm trying to use regular old external speakers, and have always used the green jack, though when I look at the output label I see what you mean.  I did sort-of mention that in passing: "'sudo /sbin/alsa force-reload' makes a bleep from the speakers but is no help otherwise."

AFAICT everything is unmuted; I've checked every volume control I can find.  And as noted it worked until I rebooted.  (I installed a metric crapton of stuff on 2010-01-13, soon after I pulled the unit out of the box.  All the current updates to the stock System76 install, plus all the apps I usually use.  At the end I hit "restart" but it looks like I also ran into the bug where "restart" only restarts X, not the PC.  (That's going to mess up a lot of people who won't end up using what they think they are, and who will have delayed problems, just like this one.)  I still had the "restart needed" icon, so I did a 'sudo reboot' yesterday and that's when the sound went away.

```
# wc -l /var/log/aptitude                        
1197 /var/log/aptitude

# head -3 /var/log/aptitude 
Aptitude 0.4.11.11: log report
Wed, Jan 13 2010 01:09:29 -0500

# egrep -i 'snd|audio|sound|pulse|alsa|padev' /var/log/aptitude 
[HOLD, DEPENDENCIES] lib32asound2
[HOLD] gstreamer0.10-alsa
[HOLD] libasound2
[UPGRADE] gstreamer0.10-alsa 0.10.25-2ubuntu1 -> 0.10.25-2ubuntu1.2
[UPGRADE] lib32asound2 1.0.20-3ubuntu6 -> 1.0.20-3ubuntu6.1
[UPGRADE] libasound2 1.0.20-3ubuntu6 -> 1.0.20-3ubuntu6.1
[INSTALL, DEPENDENCIES] childsplay-alphabet-sounds-bg
[INSTALL] gcompris-sound-en
[INSTALL, DEPENDENCIES] vlc-plugin-pulse
[INSTALL, DEPENDENCIES] libcdaudio1
[INSTALL, DEPENDENCIES] libsoundtouch1c2
[REMOVE, DEPENDENCIES] libsdl1.2debian-alsa
[INSTALL] libsdl1.2debian-pulseaudio
[INSTALL, DEPENDENCIES] pulseaudio-module-zeroconf
[INSTALL] padevchooser
```


> **riseringseeker said:**
> I installed PulseAudio Device Chooser

```
sudo apt-get install padevchooser
```

Once you have that installed, it (and volume manager) will show in the Sound & Audio tab.  Click on PA Volume Manager (or click device chooser, then click on the resulting icon in the top panel and choose volume control), and see if anything there is of any help.

The "Playback tab" will only show system sounds until something is playing, and then only for as long as it's playing.

Poke around with that and let me know what you see.  If you wish, I'll send some screenshots of how things are here.

I've installed that (no reboot) but there is no change.  As noted above sound prefs still show no hardware or input device, output is still dummy, and I do NOT see any new options.  Also, the "tool tip" on the taskbar volume control (still) says "Output 100%, 0.00 db, Dummy output" and that can't be good.

```
# aptitude install padevchooser
The following NEW packages will be installed:
  padevchooser paman{a} paprefs{a} pavucontrol{a} pavumeter{a} 
  pulseaudio-module-zeroconf{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 12 not upgraded.
Need to get 399kB of archives. After unpacking 2,683kB will be used.
```

---

### Post by jpv on 2010-01-18
Nuke dup post

---

### Post by jpv on 2010-01-18
AAAAAAARRRRGGGGGGHHHHHHHHH!!!!!!!!!!!!!

After some more goofing around, this was really starting to look like a permissions issue, because things kinda worked as root, but not as my user.  For example, my user had:
```
$ aplay -vl
aplay: device_list:223: no soundcards found...

$ cat /proc/asoun/cards                           
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe3220000 irq 22

```

But root got useful output from 'aplay'.

It turns out that I had to add my user to "audio" in /etc/group (maybe related to an AppArmor tweak?).  I also did some other things that may or may not have helped...

So if anyone else runs into this, try these steps in this order

1) Add your user to "audio" in /etc/group, so it looks like this: audio:x:29:pulse,{your_user_here}

Use 'sudo nano /etc/group' at the command line.  Then reboot for the change to take effect.  If that doesn't fix it, try:

2) sudo nano /etc/modprobe.d/alsa-base.conf
and comment out the last line and make it look like this:
```

# BAD options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto

```

Again, reboot.  If that still doesn't work:

3) Try purging and re-installing (don't use aptitude or it'll remove Ubuntu-Desktop, which is a Bad Thing):
```
$ sudo apt-get remove --purge alsa-base pulseaudio pavucontrol paman pavumeter
$ sudo aptitude install alsa-base pulseaudio
```

That last is admittedly voodoo, but lots of non-S76 Ubuntu forum posts recommended it, so...

---

### Post by ryseshan on 2010-01-20
Hai Friends,

I also faced same problem with no sound in 9.10. I got solved from the file downloaded it fixed my sound problem. I am hereby giving u the link for the site so that u can download the file and fix ur sound problem in 9.10

[http://www.h3manth.com/content/sound...ntu-910-fix-it](http://www.h3manth.com/content/sound...ntu-910-fix-it)

---

### Post by ryseshan on 2010-01-20
[QUOTE=ryseshan;8694359]Hai Friends,

I also faced same problem with no sound in 9.10. I got solved from the file downloaded it fixed my sound problem. I am hereby giving u the link for the site so that u can download the file and fix ur sound problem in 9.10

[http://www.h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it](http://www.h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it)

---

### Post by jpv on 2010-01-20
> **ryseshan said:**
> Hai Friends,

I also faced same problem with no sound in 9.10. I got solved from the file downloaded it fixed my sound problem. I am hereby giving u the link for the site so that u can download the file and fix ur sound problem in 9.10

[http://www.h3manth.com/content/sound...ntu-910-fix-it](http://www.h3manth.com/content/sound...ntu-910-fix-it)

That's for a completely different sound card, and probably a different problem than what I ran into (and solved).  It's also "Copyright (c) 1999-2002  SuSE GmbH" which makes me really wonder if it would be useful on 2009 Ubuntu.  After a very quick eyeball of the script I don't think I'd run it on a current Ubuntu machine...

But thanks for the thought.

---

### Post by riseringseeker on 2010-01-20
> **jpv said:**
> AAAAAAARRRRGGGGGGHHHHHHHHH!!!!!!!!!!!!!

After some more goofing around, this was really starting to look like a permissions issue, because things kinda worked as root, but not as my user.  For example, my user had:
```
$ aplay -vl
aplay: device_list:223: no soundcards found...

$ cat /proc/asoun/cards                           
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe3220000 irq 22

```


My Wild Dog shows the same, (the "cat" command should be "cat /proc/asound/cards" though) but also lists USB devices I have plugged in.

> 
But root got useful output from 'aplay'.

"aplay" is owned by root, so that is as it should be.
[/quote]
> 
It turns out that I had to add my user to "audio" in /etc/group (maybe related to an AppArmor tweak?).  I also did some other things that may or may not have helped...

Odd, I don't even have an "audio" group on my machine, so obviously I am not on it. 
> 

So if anyone else runs into this, try these steps in this order

1) Add your user to "audio" in /etc/group, so it looks like this: audio:x:29:pulse,{your_user_here}

Use 'sudo nano /etc/group' at the command line.  Then reboot for the change to take effect.  If that doesn't fix it, try:

2) sudo nano /etc/modprobe.d/alsa-base.conf
and comment out the last line and make it look like this:
```

# BAD options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto

```

I don't/didn't have that line in that file, may have been the problem right there!
> 

Again, reboot.  If that still doesn't work:

3) Try purging and re-installing (don't use aptitude or it'll remove Ubuntu-Desktop, which is a Bad Thing):
```
$ sudo apt-get remove --purge alsa-base pulseaudio pavucontrol paman pavumeter
$ sudo aptitude install alsa-base pulseaudio
```

That last is admittedly voodoo, but lots of non-S76 Ubuntu forum posts recommended it, so...

I think that this was what fixed it (since you list it, I'm assuming you tried this as well).  I'm further guessing that somehow the audio stuff got borked by the update for some reason only known to the Ubuntu gods.

I am surprised that Tom has not weighed in, but as long as it's fixed...

---

### Post by arvana on 2010-02-05
Thanks jpv, your solutions in Post #6 fixed my sound.  I need to do all three.

---

### Post by krippa on 2010-02-09
I may be the only one stupid enough not to notice it had changed but for me the solution was to select the analog devices in the mixer/sound preferences. Really annoying that this simply changed after an update. All of a sudden my HDMI audio output was chosen and no device was chosen for input..

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

