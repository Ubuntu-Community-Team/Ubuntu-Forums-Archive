---
title: "half of the time sound is muted when logging in"
date: 2022-03-16
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-03-16
Hello,

this happens a long time now, yet I post it in case someone else has been experiencing the same issue. Either logging in or switching, the sound, not always but most of the time, is muted. Initially I thought that it might be temporal, yet with the latest alsa updates it didn't go away. 

I do not know why sometimes it happens and sometimes not.

Regards!

---

### Post by #&amp;thj^% on 2022-03-16
On a different system I test I have used this:
```
alsactl nrestore
```
if that helps or even works ubuntu, you could then add to autostart.
```
alsactl nrestore
alsactl: state_lock:129: file /var/lib/alsa/asound.state lock error: Permission denied
alsactl: load_state:1689: Cannot open /var/lib/alsa/asound.state for reading: Permission denied
Found hardware: "HDA-Intel" "Nvidia GPU 94 HDMI/DP" "HDA:10de0094,10de10fa,00100100" "0x10de" "0x10fa"
Hardware is initialized using a generic method
Found hardware: "HDA-Intel" "Realtek ALC257" "HDA:10ec0257,17aa387d,00100001" "0x17aa" "0x381b"
Hardware is initialized using a generic method
Found hardware: "USB-Audio" "USB Mixer" "USB17e9:4307" "" ""
Hardware is initialized using a generic method

```
Just throwing an idea in.
EDIT: Went through some old notes and found that this is what I used in 21.10:
```
amixer -D pulse set Master 1+ toggle

```
What it dose is It specifies pulse audio to ensure unmute, unmutes everything. or mutes
How i came to that was finding this:
```
amixer scontents
```
EG:
```
amixer scontents
**Simple mixer control 'Master',0**
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 61602 [94%] [on]
  Front Right: Playback 61602 [94%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 64304 [98%] [off]
  Front Right: Capture 64304 [98%] [off]

```
The script I used as a workaround:
```


#!/bin/bash

CURRENT_STATE=`amixer get Master | egrep 'Playback.*?\[o' | egrep -o '\[o.+\]'`

if [[ $CURRENT_STATE == '[on]' ]]; then
    amixer set Master mute
else
    amixer set Master unmute
    amixer set Front unmute
    amixer set Headphone unmute
fi

```

---

### Post by Claus7 on 2022-03-16
Hello,

I tried the first command you posted. Things seem to be fine: I logged out and back in twice and did not observe any mute. Also, I checked the sound and is working fine. If problem persists, after the final release of jammy, I will try to apply the rest of your post. 

Thank you,
Regards!

---

### Post by speartip on 2022-03-28
This is a problem I've had in 20.04 & 22.04. Strangely it doesn't affect Mint Cinnamon. Anyway 1fallen's 1st command seems to do the trick.

---

### Post by Claus7 on 2022-08-19
Hello,

this issue was bothering me from time to time, even after the release of 22.04.1. I wanted to avoid adding a startup application, even though I suppose that what I did is close to that. First of all I would like to mention that not only most of the times when logging in, sound was muted, but also when typing:
```
alsamixer
```
the configurations were changing as well.

Trying to comment the line of the file /etc/pulse/default.pa:
load-module module-device-restore
by putting a # in front of that line and hitting save didn't change anything.

What I did, and it seems that is working for some time now, is the following (taken from here: [https://askubuntu.com/questions/131857/alsamixer-howto-disable-auto-mute-mode):](https://askubuntu.com/questions/131857/alsamixer-howto-disable-auto-mute-mode):)
I went as root to the file
sudo vim /etc/rc.local

and just before the exit line I added the string:
> /usr/bin/amixer -c 0 sset "Auto-Mute Mode" Disabled
I then saved and logged out and back in in order to see the change taking effect.
Time will tell how much this will survive. (spoke too soon, it didn't keep much the changes...)

Regards!

---

### Post by speartip on 2022-08-21
Thanks for that Claus7. I'll give it a try.

---

### Post by Claus7 on 2022-08-21
Hello,

> **speartip said:**
> Thanks for that Claus7. I'll give it a try.

hope it helps, yet if you noticed it didn't last long. Now I have removed it from my system. What I noticed right away, though, when I added it, is that the login screen no longer showed the sound icon muted. 

One more thing I should add is that creating a new user, I never observed the muted situation logging in to that user, yet I tested it only a couple of times.
edit: Last time I opened alsamixer, I made sure to have 00 underneath master instead of MM and all the rest apart from headphones. This didn't seem to affect my sound devices, yet it seems that it makes a difference. Fingers crossed for how long this will work.

Regards!

---

