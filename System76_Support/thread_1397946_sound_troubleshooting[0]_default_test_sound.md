---
title: "sound troubleshooting[0]: default test sound?"
date: 2010-02-03
forum: System76 Support
---

### Post by tlroche on 2010-02-03
What's an easy, ultra-reliable, no-dependency way to play a test sound in vanilla/GNOME ubuntu karmic/9.10? Why I ask:

Once upon a time (while an undergrad) I worked IT support on a mostly-windows campus. This was back when PC sound was new, so we did a lotta audio debugging, for which my usual procedure was like

[LIST=1]
[*]be sure to take a known-good pair of headphones (usually already on my head).
[*]goto Control Panel>Sounds and Audio Devices>Volume and check for mute and volume. Unmute and increase volume if necessary.
[*]goto Control Panel>Sounds and Audio Devices>Sounds, select a "program event" (usually Asterisk), ensure it mapped to a sound file, and hit the adjacent button to play that sound. 
[/LIST]

If I could not get one of those known-good sounds to play, either with the user's speakers or my headphones, I started looking at the driver; otherwise I looked downstream (speakers, etc).

I'm wondering, what's the Ubuntu/GNOME equivalent should-always-be-playable sound for debugging? I tried (in karmic) System>Preferences>Sound>Sound Effects, but I can't see how to play any of those.

---

### Post by jdb on 2010-02-03
> **tlroche said:**
> What's an easy, ultra-reliable, no-dependency way to play a test sound in vanilla/GNOME ubuntu karmic/9.10? Why I ask:

Once upon a time (while an undergrad) I worked IT support on a mostly-windows campus. This was back when PC sound was new, so we did a lotta audio debugging, for which my usual procedure was like

[LIST=1]
[*]be sure to take a known-good pair of headphones (usually already on my head).
[*]goto Control Panel>Sounds and Audio Devices>Volume and check for mute and volume. Unmute and increase volume if necessary.
[*]goto Control Panel>Sounds and Audio Devices>Sounds, select a "program event" (usually Asterisk), ensure it mapped to a sound file, and hit the adjacent button to play that sound. 
[/LIST]

If I could not get one of those known-good sounds to play, either with the user's speakers or my headphones, I started looking at the driver; otherwise I looked downstream (speakers, etc).

I'm wondering, what's the Ubuntu/GNOME equivalent should-always-be-playable sound for debugging? I tried (in karmic) System>Preferences>Sound>Sound Effects, but I can't see how to play any of those.

aplay is available on most linux systems and is installed as part of the alsa-utils package on Ubuntu.

Just type
```
aplay any_sound.wav
```
at the command line.

If you don't have a wave file handy Front_Center.wav is a file that is also part of the alsa-utils package.

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```


jdb

---

### Post by tlroche on 2010-02-03
> **tlroche said:**
> What's an easy, ultra-reliable, no-dependency way to play a test sound in vanilla/GNOME ubuntu karmic/9.10?

> **jdb said:**
> If you don't have a wave file handy Front_Center.wav is a file that is also part of the alsa-utils package.
```
aplay /usr/share/sounds/alsa/Front_Center.wav
```


Thanks! I tried this on my GF's starling, on which sound is working, and got an interesting result: the first time I ran the line above from the terminal, nothing happened! So I did

```
ls -al /usr/share/sounds/alsa/Front_*.wav
```

and then tried

```
aplay /usr/share/sounds/alsa/Front_Left.wav
```

which played. I then repeated 

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

which played, and

```
aplay /usr/share/sounds/alsa/Front_Right.wav
```

which did not play, the first time, but ...

```
aplay /usr/share/sounds/alsa/Front_Right.wav
```

... did play the second time. So at least on this box, these sounds will play, but not always on the first try--dunno why.

---

### Post by jdb on 2010-02-04
> **tlroche said:**
> Thanks! I tried this on my GF's starling, on which sound is working, and got an interesting result: the first time I ran the line above from the terminal, nothing happened! So I did

```
ls -al /usr/share/sounds/alsa/Front_*.wav
```

and then tried

```
aplay /usr/share/sounds/alsa/Front_Left.wav
```

which played. I then repeated 

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

which played, and

```
aplay /usr/share/sounds/alsa/Front_Right.wav
```

which did not play, the first time, but ...

```
aplay /usr/share/sounds/alsa/Front_Right.wav
```

... did play the second time. So at least on this box, these sounds will play, but not always on the first try--dunno why.

Look in this file:

```
/etc/modprobe.d/alsa-base.conf
```

See if the last line is:

```
options snd-hda-intel power_save=10 power_save_controller=N
```

To save power it turns the audio controller off when it is not in use.
Sometimes it is slow to turn back on.
You can comment out that line like this:
```
#options snd-hda-intel power_save=10 power_save_controller=N
```

jdb

---

### Post by thomasaaron on 2010-02-04
tlroche, go to System > Administration > Hardware Drivers and disable the driver called "Modem Software." Then reboot. Did that fix your sound.

You used to be able to go to System > Preferences > Sound and click a test button. But the devs, for some bewildering reason, decided to do away with that.

---

### Post by jdb on 2010-02-04
> **tlroche said:**
> Thanks! I tried this on my GF's starling, on which sound is working, and got an interesting result: the first time I ran the line above from the terminal, nothing happened! So I did

```
ls -al /usr/share/sounds/alsa/Front_*.wav
```



This was kind of fun :)

```
find /usr/share -name "*.wav" -exec aplay {} \;
```


jdb

---

### Post by Flyers2391 on 2010-02-04
You can also go to System > Administration > System Testing and do the audio test

---

### Post by tlroche on 2010-02-04
> **Flyers2391 said:**
> You can also go to System > Administration > System Testing and do the audio test

Good idea! I didn't know about that. Unfortunately the audio tests require one to Next through several mic tests before one gets to the audio-output tests, which seems odd.

---

