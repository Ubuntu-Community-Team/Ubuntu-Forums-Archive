---
title: "VLC crashes attempting to play video after starting a VM with Virtualbox"
date: 2009-09-19
forum: Virtualisation
---

### Post by diablo75 on 2009-09-19
I am running the latest version of Virtualbox, non-OSE as well as the latest version of VLC.  VLC works great, unless I attempt to use it to play a video while or after using Virtualbox.

To get a little more info about this I ran VLC from the terminal and watched it for errors when attempting to play a video.  Below is the output.  The red text is what was displayed after I started playing the video (so you can see where the non-error output ends and the error begins more clearly).

```
VLC media player 1.0.1 Goldeneye
[0x929f140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[COLOR="Red"][0x96faf48] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
Segmentation fault[/COLOR]
```

The only way I can fix this is to log off and log back in.

---

### Post by stlsaint on 2009-09-22
what os are you using for vm and for troubleshooting try using a different media player. Looks like compatiblity issues/settings for virtual graphics.

---

### Post by retardo555 on 2009-09-23
Same problem..
If anybody has hints, I'm available for any test

---

### Post by diablo75 on 2009-10-26
I was wondering if anybody has found a bug report about this or if any updates are out there as far as a potential solution goes...

---

