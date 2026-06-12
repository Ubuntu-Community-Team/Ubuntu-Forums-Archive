---
title: "sound troubleshooting[1]: no sound from PanP5 (probably) after karmic upgrade"
date: 2010-02-04
forum: System76 Support
---

### Post by tlroche on 2010-02-04
I have a PanP5 (model=panp5) that played sound as originally shipped with jaunty. It had touchpad problems, which System76 replaced under warranty. After it came back, I upgraded the PanP5 to karmic using

```
sudo do-release-upgrade
```

then installing the System76 driver. This worked great ... except that, just now when I tried to play sound, I got nothing. Since I don't recall trying to play sound since I upgraded to karmic, I'm assuming that's the problem, but I don't recall trying to play sound since it came back from service, either. Note also that I get no sound either through the box's own speakers, or using known-good headphones attached to the headphone jack on the right (as viewed from the typing position).

In any case, this PanP5 is still vanilla/GNOME ubuntu.

Here's what I've tried, debugging using the [sound-troubleshooting community doc]("https://help.ubuntu.com/community/SoundTroubleshooting").

[LIST=1]
[*]check volume:

```
https://help.ubuntu.com/community/SoundTroubleshooting
> Double click on the "speaker" icon in the upper right hand corner of
> the screen. This will launch the Volume Control application, which
> has various sliders to control the volume.

```

Volume Control is maxed, not muted. Note mouse hover text
```
Output: 100%
0.00 dB
Dummy Output

```

rclick Volume Control panel icon: Mute is unchecked.

rclick Volume Control panel icon>Sound Preferences: Mute is unchecked in both "Output volume" and  "Alert volume", volume is 100% in both.
[*]try known-good sound:

Thanks to jdb, I added this to the doc:

```
https://help.ubuntu.com/community/SoundTroubleshooting
> try to run

> aplay /usr/share/sounds/alsa/Front_Center.wav

> in a terminal. You should hear a voice saying "Front" then "Center".
> If it doesn't play the first time you run that command, try running
> it again (it may not play the first time)

```

I tried running this through, in order,

[LIST=1]
[*]the PanP5's own speakers
[*]known-good headphones in each of the three jacks on the right side (when typing) of the box
[/LIST]

```
tlroche@tlrPanP5:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
tlroche@tlrPanP5:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
tlroche@tlrPanP5:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
tlroche@tlrPanP5:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

but got no sound.

[*]check permissions:

```
https://help.ubuntu.com/community/SoundTroubleshooting
> Check that you are in the appropriate group.

```

I didn't belong to group=audio. Unfortunately, fixing that didn't restore sound:

```
tlroche@tlrPanP5:~$ fgrep -ie 'sound' /etc/group | wc -l
> 0
tlroche@tlrPanP5:~$ fgrep -ie 'audio' /etc/group | wc -l
> 1
tlroche@tlrPanP5:~$ cat /etc/group | fgrep -ie 'audio'
> audio:x:29:pulse
tlroche@tlrPanP5:~$ ls -al /etc/group*
> -rw-r--r-- 1 root root 921 2010-01-31 10:35 /etc/group
> -rw------- 1 root root 927 2010-01-31 10:35 /etc/group-
tlroche@tlrPanP5:~$ sudo cp /etc/group /etc/group_20100203
tlroche@tlrPanP5:~$ sudo chmod a-wx /etc/group_20100203
tlroche@tlrPanP5:~$ sudo adduser tlroche audio
> Adding user `tlroche' to group `audio' ...
> Adding user tlroche to group audio
> Done.
tlroche@tlrPanP5:~$ sudo diff /etc/group /etc/group_20100203
> 22c22
> < audio:x:29:pulse,tlroche
> ---
> > audio:x:29:pulse

```

After that I shutdown/restart, but there was no startup sound or other sound. I also noted that System>Preferences>Sound>Hardware>"Choose a device to configure:" shows nothing.

[*]check for `aplay` devices:

```
https://help.ubuntu.com/community/SoundTroubleshooting
> Is the system recognizing your sound card?

> Open a terminal window, and type

> sudo aplay -l 

> Your output should look something like this:

> **** List of PLAYBACK Hardware Devices ****
> card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
>   Subdevices: 0/1
>   Subdevice #0: subdevice #0

> If you see aplay: device_list:221: no soundcard found..., Ubuntu is not recognizing your sound card for playback. Check that you have the proper modules installed

```

```
tlroche@tlrPanP5:~$ sudo aplay -l | fgrep -ie 'no sound'
tlroche@tlrPanP5:~$ sudo aplay -l
> **** List of PLAYBACK Hardware Devices ****
> card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
>  Subdevices: 1/1
>  Subdevice #0: subdevice #0
> card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
>  Subdevices: 1/1
>  Subdevice #0: subdevice #0
> card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
>  Subdevices: 1/1
>  Subdevice #0: subdevice #0
> card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
>  Subdevices: 0/1
>  Subdevice #0: subdevice #0

```

[*]check sound modules are installed:

```
https://help.ubuntu.com/community/SoundTroubleshooting
> Do you have the sound modules installed?

> Open a terminal window, and type

> find /lib/modules/`uname -r` | grep snd

> You should see a whole list of items come up.

```

```
tlroche@tlrPanP5:~$ find /lib/modules/$(uname -r) | fgrep -ie snd
> /lib/modules/2.6.31-17-generic/kernel/sound/core/snd-hwdep.ko
...
> /lib/modules/2.6.31-17-generic/kernel/sound/synth/emux/snd-emux-synth.ko
tlroche@tlrPanP5:~$ find /lib/modules/$(uname -r) | fgrep -ie snd | wc -l
> 159
tlroche@tlrPanP5:~$ find /lib/modules/$(uname -r) | fgrep -ie 'sound' | wc -l
> 225
tlroche@tlrPanP5:~$ find /lib/modules/$(uname -r) | fgrep -ie 'sound' | fgrep -ie 'alc'
tlroche@tlrPanP5:~$ lspci -v | fgrep -e 'Audio device'
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
tlroche@tlrPanP5:~$ lspci -v | fgrep -A 6 -e 'Audio device'
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
>        Subsystem: CLEVO/KAPOK Computer Device 0806
>        Flags: bus master, fast devsel, latency 0, IRQ 22
>        Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
>        Capabilities: <access denied>
>        Kernel driver in use: HDA Intel
>        Kernel modules: snd-hda-intel

```
[/LIST]

So it looks like everything is there. Before I go to the next item in the [sound-troubleshooting community doc]("https://help.ubuntu.com/community/SoundTroubleshooting") (ALSA checking), I'm wondering, is there something else I should check or do first or instead?

---

### Post by Lee_Machine on 2010-02-04
Sometimes the Gnome sound UI will say that your sound is turned up, and not muted but it really is. In the past this has happened to me after release updates, or ALSA updates.

try this...

In terminal type 

alsamixer


Using the arrow keys make sure everything is turned up, and the M key unmutes them. The infinity symbol means its muted.


Does that work?

---

### Post by thomasaaron on 2010-02-04
Go to System > Administration > Hardware Drivers and disable the driver called "Modem Software" and then reboot. Did that fix it.

---

### Post by tlroche on 2010-02-04
> **thomasaaron said:**
> Go to System > Administration > Hardware Drivers and disable the driver called ["Software modem"] and then reboot. Did that fix it.

Yes! Thanks.

---

