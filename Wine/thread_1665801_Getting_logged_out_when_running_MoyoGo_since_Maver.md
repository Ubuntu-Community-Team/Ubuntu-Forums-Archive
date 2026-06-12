---
title: "Getting logged out when running MoyoGo since Maverick update"
date: 2011-01-12
forum: Wine
---

### Post by emerald000 on 2011-01-12
I have been running MoyoGo ([http://www.moyogo.com/](http://www.moyogo.com/)) with wine on 9.10 without any problem. I recently updated to 10.10 with the update manager. Now, whenever I try to run it, I get back to the login screen some seconds after the splash screen of MoyoGo appears.

I am running wine 1.3.11, but I tried a couple of earlier versions with the same results. I can also run other programs under wine without any problem.

Here's the terminal output, showing what seems like a Xserver problem:

```
fixme:shell:FileIconInit (true)
fixme:mixer:ALSA_MixerInit No master control found on ThinkPad Console Audio Control, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x218f50,0x21d0a0): stub
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 87165 requests (87163 known processed) with 0 events remaining.

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 1005 requests (970 known processed) with 0 events remaining.
```

This is most likely a problem not related to wine, but I couldn't get an answer to my thread in the General Help forum. So I am trying my luck here.

And thank you in advance for your help!

---

### Post by emerald000 on 2011-01-16
Help?

---

### Post by cogadh on 2011-01-16
That does not appear to be a Wine issue at all, but rather a case of Wine exposing some unrelated issue. Considering it seems to be an Xserver error, the first question would be, what do you have for graphics hardware?

---

### Post by emerald000 on 2011-01-17
I have a Radeon HD 3650, with native drivers.

---

### Post by emerald000 on 2011-02-02
So?

---

