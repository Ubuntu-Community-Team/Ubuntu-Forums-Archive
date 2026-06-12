---
title: "Audio Problems in Ubuntu 9.10"
date: 2009-10-31
forum: Wine
---

### Post by Joseph Schwenker on 2009-10-31
Hey everyone!  I have been encountering audio problems since installing Ubuntu 9.10.  In Ubuntu 9.04, I was able to run a lot of software with very little glitches under Wine.  The biggest being Osmos, which ran wonderfully, being based on OpenGL, and having perfectly compatible sound.  So, I installed the latest version of Wine, 1.01, and loaded Osmos.  Well, the sound didn't work at all.  I was lucky to even get the test sound playing in the audio tab of winecfg!  Roller Coaster Tycoon also worked perfectly in the last Ubuntu; now it won't work with sound at all!  God!  This is starting to seem like Windows.  Maybe Karmic is indeed the Vista of Ubuntu?  Please help!

---

### Post by alex.rayu on 2009-10-31
Audio problems with Gnome have long become a feature. Inability of Gnome team to heed the clients' complains about PulseAudio are only comparable to their stubbornness of pushing it on.

---

### Post by denali on 2009-10-31
> **Joseph Schwenker said:**
> Hey everyone!  I have been encountering audio problems since installing Ubuntu 9.10.  In Ubuntu 9.04, I was able to run a lot of software with very little glitches under Wine.  The biggest being Osmos, which ran wonderfully, being based on OpenGL, and having perfectly compatible sound.  So, I installed the latest version of Wine, 1.01, and loaded Osmos.  Well, the sound didn't work at all.  I was lucky to even get the test sound playing in the audio tab of winecfg!  Roller Coaster Tycoon also worked perfectly in the last Ubuntu; now it won't work with sound at all!  God!  This is starting to seem like Windows.  Maybe Karmic is indeed the Vista of Ubuntu?  Please help!

I'm having the same problem in WoW.  I'm using version 1.1.32 of Wine from git.  When I play, the sound stutters.  I've turned all the sound quality and buffer sliders down and it doesn't change anything.

---

### Post by alex.rayu on 2009-10-31
Try selecting the ALSA driver for use in Wine config. If no result, try this:
sudo apt-get remove pulseaudio

This will remove the gleachy sound server that is not supported by Wine.

---

### Post by ell02 on 2009-10-31
[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

This helped my sound stutter in a different online game.Needed to enable simultaneous ouput.

---

### Post by Joseph Schwenker on 2009-10-31
> **alex.rayu said:**
> Try selecting the ALSA driver for use in Wine config. If no result, try this:
sudo apt-get remove pulseaudio

This will remove the gleachy sound server that is not supported by Wine.

I already had the ALSA driver selected.  I just uninstalled pulseaudio, and now the "Test Sound" button on the audio tab replies with the message, "Audio test failed!".  What can I do now?

---

### Post by Joseph Schwenker on 2009-10-31
OK, now the audio is randomly working again.  However, my sound quality in Osmos is not very good.  How can I improve the sound quality?
Edit: Well, the sound now WORKS in Roller Coaster Tycoon 1 and Osmos, but has pretty bad quality.

---

### Post by alex.rayu on 2009-10-31
How nice! 300 linux distros, changed kernel every few months, and can't even get sound to work right.

---

### Post by Joseph Schwenker on 2009-11-01
> **alex.rayu said:**
> How nice! 300 linux distros, changed kernel every few months, and can't even get sound to work right.

So you know of no other way to get the sound working?  Oh, and Happy Halloween!

---

### Post by oyvinst on 2009-11-01
For best Wine audio performance with Pulseaudio, I've found that Wine OSS output works pretty well. But one needs to run things with the 'padsp' command. 

1) Run:
```
$ padsp winecfg
```

Select OSS audio output in the audio properties tab.

2) Then always run any wine-app with the "padsp" command: ```
$ padsp wine MyApp.exe ..
```

This preloads/injects a Pulseaudio-interceptor library (libpulsedsp.so) into Wine and redirects all OSS audio-output natively to the Pulseaudio daemon. For info on padsp, see its manual page.

Works even with "Full hardware acceleration" specified in the Wine audio configuration.

Or, if you don't want Pulseaudio getting in your way at all, you can always suspend Pulseaudio before running e.g. games under Wine. See "man pasuspender". This gives Wine direct access to audio devices, and probably works best if Wine is configured with ALSA output.

---

### Post by Joseph Schwenker on 2009-11-01
> **oyvinst said:**
> For best Wine audio performance with Pulseaudio, I've found that Wine OSS output works pretty well. But one needs to run things with the 'padsp' command. 

1) Run:
```
$ padsp winecfg
```

Select OSS audio output in the audio properties tab.

2) Then always run any wine-app with the "padsp" command: ```
$ padsp wine MyApp.exe ..
```

This preloads/injects a Pulseaudio-interceptor library (libpulsedsp.so) into Wine and redirects all OSS audio-output natively to the Pulseaudio daemon. For info on padsp, see its manual page.

Works even with "Full hardware acceleration" specified in the Wine audio configuration.

Or, if you don't want Pulseaudio getting in your way at all, you can always suspend Pulseaudio before running e.g. games under Wine. See "man pasuspender". This gives Wine direct access to audio devices, and probably works best if Wine is configured with ALSA output.

Oh, excellent!  Thanks a lot!  This solved pretty much all of my problems!  Thank you!

---

### Post by dogooder on 2009-11-05
> **oyvinst said:**
> For best Wine audio performance with Pulseaudio, ... 
This worked for me too. Thanks.

---

