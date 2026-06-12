---
title: "[Starling] [9.10 NR] Audio suddenly not working!"
date: 2010-02-02
forum: System76 Support
---

### Post by ligaa9mm on 2010-02-02
Hey all,

A few weeks ago I installed Ubuntu 9.10 Netbook Remix on my Starling (not upgrading). Two days ago I ran a few updates, and at the time, the sound was working. Well halfway through the updates, the computer brought up a black screen with a white cursor in the upper left corner, and the entire system locked up.
I let it sit for several minutes but eventually had to shut it down and reboot. I couldn't finish the updating process until I fixed whatever issue it was in the terminal (it gave me some command to type in). I didn't notice the lack of sound at the time.

Today I start up my netbook and I noticed that the sound icon was missing from the panel at the top. So I went into System > Sound, and it sits there saying "waiting for device" endlessly. I tried opening System Monitor, and I got the same Black Screen of Death and was forced to reboot.

So where did my sound go? :( I did some forum hunting and all the issues other people were having applied to 8.10, 9.04, or upgrades from 9.04 to 9.10. The solutions tended to be "reinstall the OS", which I'd rather not have to do if I can avoid it. (I just got the wireless card working!)

Here's a bit of information I saw other users posting for similar issues:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

And my lsmod results:
```
Module                  Size  Used by
aes_i586                8124  2 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
iptable_filter          3100  0 
snd_hda_intel          26920  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
ip_tables              11692  1 iptable_filter
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
x_tables               16544  1 ip_tables
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
r8187b                171024  2 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

```

Any help would be greatly appreciated!

---

### Post by black_ice=cream on 2010-02-02
it's weird... when I updated recently, the screen went black with the mouse in the upper left hand corner, (just as yours) but when I rebooted mine the **mouse** didn't work... something about that update... But I'm really not sure about your audio issue. Here's something to try but I'm pretty sure it won't work. Okay, reboot your computer and hit 'Esc' when GRUB is loading. Boot into recovery mode and choose the option that says 'netroot' on the left column. Then, once the CL has loaded and you've entered you password, type: 'apt-get install hal --reinstall'. Then type 'reboot' and boot into Ubuntu and see if your audio works. Again: I'm **not sure this will work**. Just a thought... let me know what happens.

---

### Post by thomasaaron on 2010-02-03
black_ice=cream's suggestion is a good one, but I'd like to add two notes...
1. If you're running 9.10, you may have to press the shift key to get to the kernel menu.

2. You will need a WIRED internet connection BEFORE going into recovery mode / netroot. 

3. Once you boot into recovery mode and netroot, I'd run a few additional commands just to be thorough. Here's what I'd run...

dpkg --configure -a
apt-get remove winbind
apt-get install winbind
apt-get --reinstall install hal
apt-get install grub-pc   #This one will give you a few questions. Choose all default settings.
apt-get update
apt-get dist-upgrade
reboot -h now

If some of them throw errors, it's OK. Just keep going.

---

### Post by macabrem on 2010-02-03
> **ligaa9mm said:**
>  I tried opening System Monitor, and I got the same Black Screen of Death and was forced to reboot.


Sorry to threadjack, I don't have much input on your overall problem.

I had a question about this "Black Screen of Death."  I got that screen the other day while opening System Monitor.  I'm running 9.10 Netbook Remix on my Starling, with no updates, and I've only had this happen once.  Does anybody else have this issue?  I thought it was odd that we both had it happen while opening System Monitor.

---

### Post by thomasaaron on 2010-02-03
Yes.

There is a bug with the wireless driver that will cause a kernel panic if you run iwconfig or open System Monitor. It doesn't seem to affect wireless performance otherwise. We're looking into it, but are focusing more on getting the driver into Lucid (which will probably fix those problems).

---

### Post by ligaa9mm on 2010-02-12
Alright, sorry it took me so long to get back to this. I finally tried what you suggested. It didn't give any errors that I could see. However, when I booted back into Ubuntu normally, I noticed something strange.
The Ubuntu startup sound didn't play, or the login sound. But when I went to a youtube video, I had sound again. It even worked for my headphones. There's still no volume icon up by the clock (maybe it's just hidden?), and Sound in the System menu still just sits there saying "Waiting for sound system to respond".
Just on a whim, I ran the System Test program for audio. I couldn't  hear the speech it played for the first test. I could hear what I said into a headset's microphone played back over the headphones. Then I tested the internal microphone, and audio played back over the internal speakers.
Finally, it got to the part where it detected my sound device. It showed...

0 [Intel      ]: HDA-Intel - HDA Intel
HDA Intel at 0x94340000 irq 16

When testing this device, I did hear a sound over the internal speakers.

Soooo... I feel kind of silly. But I think it's just an issue with the volume icon missing from the panel. I noticed that I had to put my ear right up to the speakers in order to hear anything. I'll see if I can figure out how to get the icon back and then I'll report in again here.


_**Edit:**_

Alright, I unlocked the panel and dragged the nubbie thing over. This gave me access to "Add to Panel", but no where in any of the options did it have a Sound applet that I could add. Still at a loss, still trolling forums...
Also, my Synaptic package manager has gotten... problematic. It tends to freeze constantly.

---

### Post by thomasaaron on 2010-02-15
Do you see the battery icon? If not, your "Notification Area" icon is missing. I *believe* that housed the speaker icon. The "Notification Area" icon is available via "Add to Panel."

---

