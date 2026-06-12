---
title: "[Ubuntu Studio]PC as a guitar amplifier"
date: 2015-05-22
forum: Ubuntu Studio
---

### Post by flex567 on 2015-05-22
I have an electric guitar and I would like to use my PC(Ubuntu studio) as an amplifier. How can I do that. I already connected my guitar with the computer through line-in socket??

---

### Post by HermanAB on 2015-05-22
Howdy,

A guitar pickup is very low level.  Use the microphone connection instead.

The connector may be a 3 or 4 way so you got to google for details of whatever you got.

---

### Post by flex567 on 2015-05-22
I plugged the guitar into mic socket. What should I do next because I still don't hear my guitar sound from the speakers?

---

### Post by Frogs Hair on 2015-05-22
Try opening the sound settings and check the input/output, as written if the jack isn't the correct type you won't hear anything. I work with an external microphone instead of direct input mainly because I couldn't easily find the connectors to convert the 1/4 guitar jack to the proper input for the microphone socket. Signal type, analog or digital is a factor also.  

 You might want to check out Rackarrack for effects once get the sound working, this program is not installed by default on my standard Ubuntu, but is in the software center.

---

### Post by flex567 on 2015-05-22
>  I work with an external microphone instead of direct input mainly  because I couldn't easily find the connectors to convert the 1/4 guitar  jack to the proper input for the microphone socket. 
I think you need this cable [http://www.amazon.com/Hosa-Cable-CMS110-inch-Adapter/dp/B000068O36](http://www.amazon.com/Hosa-Cable-CMS110-inch-Adapter/dp/B000068O36)

> 
Try opening the sound settings and check the input/output, as written if  the jack isn't the correct type you won't hear anything. 
I don't know how to do this.

---

### Post by Frogs Hair on 2015-05-22
In Ubuntu, sound settings can be accessed from the sound indicator on the panel and in XFCE you may have to look in the applications menu. The linked jack is stereo on the 1/4 end (2 black bands) and wouldn't work .

---

### Post by HermanAB on 2015-05-23
...and as I said, the little connector may have FOUR terminals.  You got to look up the data sheet of whatever you got, to determine how to connect it.

---

### Post by flex567 on 2015-05-23
> In Ubuntu, sound settings can be accessed from the sound indicator on  the panel and in XFCE you may have to look in the applications menu.

In Ubuntu studio in Settings there is Audio production which has 2 icons LADI control centre and Ladi Log file viewer

> ...and as I said, the little connector may have FOUR terminals
What little connector? do you mean 3.5 mm connector? 
my sound card has 3 sockets one for the speaker and one line in and one mic

> The linked jack is stereo on the 1/4 end (2 black bands) and wouldn't work .
In Windows for me the cable '1/4 to 3.5 mm' works. I can hear the sound from the guitar in the speakers.

---

### Post by MartyBuntu on 2015-05-23
> **flex567 said:**
> In Windows for me the cable '1/4 to 3.5 mm' works. I can hear the sound from the guitar in the speakers.

...and, that's a great way to toast your onboard/sound card...

The correct answer, is to use a pre-amp, plugged into your LINE-IN.

---

### Post by flex567 on 2015-05-23
> [COLOR=#000000]The correct answer, is to use a pre-amp, plugged into your LINE-IN.[/COLOR]
Where can I get this pre-amp ? 

> [COLOR=#000000]...and, that's a great way to toast your onboard/sound card...[/COLOR] I didn't hear that anyone destroyed a sound-card this way yet.

---

### Post by Frogs Hair on 2015-05-23
> The linked jack is stereo on the 1/4 end (2 black bands) and wouldn't work .

> **flex567 said:**
> In Windows for me the cable '1/4 to 3.5 mm' works. I can hear the sound from the guitar in the speakers.

If the spacing works out correctly on the guitar end you will get a mono output signal from the guitar.

Edit : Flex567, run a search for "Guitar Link" it's a USB based link for guitar and speakers.

---

### Post by flex567 on 2015-05-23
> [COLOR=#000000]Edit : Flex567, run a search for "Guitar Link" it's a USB based link for guitar and speakers.[/COLOR]
I bought my 1/4 to 3.5mm in a guitar shop and thus far didn't have any problems with it.

> [COLOR=#000000]If the spacing works out correctly on the guitar end you will get a mono output signal from the guitar.[/COLOR]

what spacing?

---

### Post by madden.playss on 2015-05-23
Check sound settings, try to configure things. Also, does standard MIC works on MIC port? (On Ubuntu)

---

### Post by flex567 on 2015-05-23
> [COLOR=#000000]Also, does standard MIC works on MIC port? (On Ubuntu)[/COLOR] I don't have a standard microphone.

---

### Post by Frogs Hair on 2015-05-23
```
what spacing? 				 			  			   		 			 			 			 				 					
``` As I wrote, on a stereo jack like the one you linked there are two black spacers if the contact is in the correct position a mono signal will be sent from the guitar.

---

### Post by flex567 on 2015-05-23
> [COLOR=#000000]As I wrote, on a stereo jack like the one you linked there are two black spacers if the contact is in the correct position a mono signal will be sent from the guitar.[/COLOR]
Why would i need mono signal and what is the correct position?

---

### Post by cariboo on 2015-05-23
Moved to Ubuntu Studio, where it should have been in the first place.

---

### Post by jejeman on 2015-05-24
Guitar > Pre-amp (with HI-Z) > Line in = best sound (also the safest)

You don't hear any sound because monitoring inputs is disabled by default.
Open
```
alsamixer
```Then unmute Playback sliders for your input. You unmute with "M" key, with arrow keys you turn up the signal.

---

### Post by MartyBuntu on 2015-05-24
> **flex567 said:**
> Where can I get this pre-amp ? 



I bought mine on eBay...$30 SHIPPED.

[IMG]http://i19.servimg.com/u/f19/15/23/17/98/pre-am10.jpg[/IMG]
[IMG]http://i19.servimg.com/u/f19/15/23/17/98/pre-am11.jpg[/IMG]

---

### Post by Frogs Hair on 2015-05-24
> **flex567 said:**
> Why would i need mono signal and what is the correct position?

A guitar sends an analog mono signal so a stereo jack serves no purpose and might not work at all.see below for the difference.

Note the spacers on the end, the mono plug having one.

---

### Post by flex567 on 2015-05-24
> [COLOR=#000000]A guitar sends an analog mono signal so a stereo jack serves no purpose and might not work at all.see below for the difference.[/COLOR]
I have stereo jack on both ends then. 1/4 has 2 stripes and 3.5mm jack is stereo also.  

is there a way to use Ubuntu as an amplifier with just "1/4 to 3.5mm" cable plugged in MIC socket? How can I do that, I still don't know?

---

### Post by flex567 on 2015-05-24
Is there any tutorial about it?

---

### Post by jejeman on 2015-05-24
If cable you got "works in" windows, it will "work in" Ubuntu.
Just unmute Playback for input, as I said.

---

### Post by flex567 on 2015-05-25
it seems that alsamixer is not installed in regular ubuntu

---

### Post by jejeman on 2015-05-26
That is strange,  Alsamixer is always installed. If not, install: alsa-utils.

---

### Post by flex567 on 2015-05-26
It seems that "Utilities for configuring and using ALSA" are installed, there is a green checkmark  nexto to this software on the installation page. 

When I enter in terminal
```
alsamixer
```

I get 
```
cannot open mixer: No such file or directory
```

---

### Post by flex567 on 2015-05-26
I have "pulse avdio volume control" installed maybe that is the problem?

---

### Post by jejeman on 2015-05-26
No, pulse should not be a problem to use alsamixer. I see you use 15.04, don't know if something changed in that version.

Do you have sound card?
Are kernel modules for the sound card loaded?
Are you in "audio" group?

Not being able to load mixer is indicating issue with your sound settings.

---

### Post by flex567 on 2015-05-26
```
[COLOR=#000000]Do you have sound card?[/COLOR]
```

Yes 

```
[COLOR=#000000]Are kernel modules for the sound card loaded?[/COLOR]
[COLOR=#000000]Are you in "audio" group?[/COLOR]
```
How do I know that?

---

### Post by jejeman on 2015-05-27
Which groups you are in is checked by
```
groups
```
Which modules are loaded is listed by
```
lsmod
```The ones starting with "snd_" are for the sound card.

---

### Post by flex567 on 2015-05-27
```
seba@seba-H81-D3:~$ groups
seba adm cdrom sudo dip plugdev lpadmin sambashare

```
```
seba@seba-H81-D3:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1 
uas                    24576  0 
usb_storage            69632  2 uas
i915_bpo             1101824  3 
intel_rapl             20480  0 
arc4                   16384  2 
iosf_mbi               16384  1 intel_rapl
uvcvideo               90112  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
snd_usb_audio         180224  1 
snd_hda_codec_realtek    86016  1 
ath9k                 147456  0 
coretemp               16384  0 
intel_ips              20480  1 i915_bpo
v4l2_common            16384  1 videobuf2_core
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
ath9k_common           32768  1 ath9k
media                  24576  2 uvcvideo,videodev
snd_usbmidi_lib        32768  1 snd_usb_audio
ath9k_hw              458752  2 ath9k_common,ath9k
snd_hda_intel          32768  3 
kvm_intel             151552  0 
snd_hda_controller     32768  1 snd_hda_intel
joydev                 20480  0 
snd_hda_codec         143360  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
i915                 1052672  2 
kvm                   483328  1 kvm_intel
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
ghash_clmulni_intel    16384  0 
aesni_intel           172032  0 
snd_pcm               106496  4 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
aes_x86_64             20480  1 aesni_intel
drm_kms_helper        122880  2 i915,i915_bpo
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
drm                   344064  5 i915,i915_bpo,drm_kms_helper
mac80211              724992  1 ath9k
lrw                    16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
gf128mul               16384  1 lrw
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              16384  0 
soundcore              16384  2 snd,snd_hda_codec
mei_me                 20480  0 
mei                    90112  1 mei_me
i2c_algo_bit           16384  2 i915,i915_bpo
shpchp                 40960  0 
video                  20480  2 i915,i915_bpo
8250_fintek            16384  0 
soc_button_array       16384  0 
mac_hid                16384  0 
lpc_ich                24576  0 
tpm_infineon           20480  0 
parport_pc             32768  1 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
psmouse               118784  0 
ahci                   36864  2 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169



```

There are more with snd_  prefix.

---

### Post by jejeman on 2015-05-27
Yeah, there always are.
Modules seems fine.
You are not in audio group. That is strange. Add yourself in it
```
sudo addgroup seba audio
```Re-login, to take the effect.
Try now alsamixer.

---

### Post by flex567 on 2015-05-27
```
cannot open mixer: No such file or directory
``` again

---

### Post by jejeman on 2015-05-28
Give
```
ls -l /dev/mixer
```
Check
```
groups
```

---

### Post by flex567 on 2015-05-28
```
seba@seba-H81-D3:~$ ls -l /dev/mixer
ls: cannot access /dev/mixer: No such file or directory


```

```
seba@seba-H81-D3:~$ groups
seba adm cdrom sudo audio dip plugdev lpadmin sambashare



```

---

### Post by flex567 on 2015-05-28
should I maybe install GNOME alsamixer or alsamixerGUI?

---

### Post by flex567 on 2015-05-31
I installed Ubutnu studio again and now alsamixer command works I get this window: 
[img]http://i.imgur.com/Ae0bz3d.png[/img]
so what should I do next?

---

### Post by jejeman on 2015-06-03
It is good that you reinstalled, since instalation was wrong in the first place...

Alsamixer opened HDMI card, which you can't utilize as guitar amplifier. You need to use card with analog inputs and outputs.
Give
```
aplay -l
```
for us to see what cards do you have

---

### Post by flex567 on 2015-06-03
```
**** List of PLAYBACK Hardware Devices ****card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

---

### Post by jejeman on 2015-06-03
In Alsamixer press F6 to choose the analog card. It will show controls for it. There is the one you need to unmute (line in or Mic).
Also, analog card should be mapped as card0, not HDMI. Do you have sound output from analog connections?

---

### Post by flex567 on 2015-06-03
[img]http://i.imgur.com/Rj5VhS2.png[/img]
What should I choose now?

---

### Post by MartyBuntu on 2015-06-03
> **jejeman said:**
> In Alsamixer press F6 to choose the analog card. It will show controls for it. There is the one you need to unmute (line in or Mic).
Also, analog card should be mapped as card0, not HDMI. Do you have sound output from analog connections?

You know what? Your advice to the OP is good. No, actually your advice to the OP is *excellent*, but...

...I have a sneaking suspicion that OP is doing something very *basically* wrong...like a muted element in pulseaudio, or a misplugged cable.


I'd really like a description from the OP about the hardware they're using (computer and instrument), how it's hooked up and so forth.
Some pics of the actual hook-up to the computer would help as well as a screenshot or two of Volume preferences, pulseaudio settings and mixer levels.

I think we're over complicating something that might be as simple as "I forgot to put a check-mark in the box"...

---

### Post by flex567 on 2015-06-03
> [COLOR=#000000]Do you have sound output from analog connections?[/COLOR]
what? 
I have a webcam. 

> [COLOR=#000000]I'd really like a description from the OP about the hardware they're using (computer and instrument), how it's hooked up and so forth.[/COLOR]
What is OP?

---

### Post by jejeman on 2015-06-03
OP is original poster, that means You the thread starter.

There are analog and digital connections or connectors. HDMI, SPDIF are digital, Stereo 3.5mm phone is analog.
So, since HDMI is mapped as card0 it indicates that it is the default sound card, and that all sound goes thru it.
That is why I asked do you have sound output from analog connectors?

Analog card is card1, you should choose that in alasmixer. See how they are marked 0, 1, 2. 0-HDMI 1-Analog (PCH) 2-USB.

---

### Post by flex567 on 2015-06-03
> [COLOR=#000000]That is why I asked do you have sound output from analog connectors?[/COLOR]
I don't know what is sound output from [COLOR=#000000]analog connectors.

[/COLOR][IMG]http://i.imgur.com/BDAIBAf.png[/IMG]
What should i unmute now?
My guitar is plugged into Mic plugin.

---

### Post by jejeman on 2015-06-03
These [http://cdn.computerhope.com/back-of-sound-card.jpg](http://cdn.computerhope.com/back-of-sound-card.jpg) are analog connectors. The blue, pink, green 3.5mm phone jacks.

Screen shot you gave of alsamixer doesn't show all available sliders, so I can't tell you. It looks like you have "line in", if you connected guitar to it (the blue jack port) you should unmute and turn up that. If you connected to Mic unmute that, etc.

---

### Post by flex567 on 2015-06-03
> [COLOR=#000000]That is why I asked do you have sound output from analog connectors[/COLOR]
I have speakers connected to these analog connectors and my guitar. Nothing is connected into Line-in plugin. 

This is the other part:
[IMG]http://i.imgur.com/2o64eH2.png[/IMG]

---

### Post by jejeman on 2015-06-04
There are two Mics - Front and Rear which one you use? You set that one. Just unmute with "M" key, and turn it up with arrow keys.
I have the same onboard sound card. Last sliders are for Mic Rear.

---

### Post by flex567 on 2015-06-04
these are now my final settings. But I still cannot hear a guitar through my speakers ?
[img]http://i.imgur.com/wc3V4WE.png[/img]

---

### Post by gygn-johngoff on 2015-06-04
Both your front mic channel and your rear mic channel are muted. Put your cursor over the box with the two M's in it under where it says front mic. Then hit the "m" key on your keyboard. Do the same for the rear channel just in case. Let us know if that works.

---

### Post by flex567 on 2015-06-04
> [COLOR=#000000]Both your front mic channel and your rear mic channel are muted. Put your cursor over the box with the two M's in it under where it says front mic. Then hit the "m" key on your keyboard. Do the same for the rear channel just in case. Let us know if that works.[/COLOR]
I changed the the settings to this but still no sound from the guitar through the speakers. 
[img]http://i.imgur.com/Gn1DBB8.png[/img]

---

### Post by jejeman on 2015-06-04
You set them correctly. So, I don't know why it is not working.
If the cables, guitar are working, than you should hear sound. Try some microphone if you have, it should work.

As I said, I have the same sound card, and I just plug in Mic (front) unmute, turn up, and I hear sound.
Only difference between my system and yours is that my card is mapped as card0, but it should not make a difference.
You can use this code to map your card as card0

```
pcm.!default {
    type hw
    card PCH
}

ctl.!default {
    type hw
    card PCH
}
```This code goes to ~/.asoundrc file. You need to make the file, save it and reboot (probably just re-login)

---

### Post by flex567 on 2015-06-04
maybe it the problem is that I have regular Ubuntu now and you have studio?

---

### Post by jejeman on 2015-06-04
No, It should not make a difference which GNU/Linux distribution you use, as long as it uses ALSA.

---

