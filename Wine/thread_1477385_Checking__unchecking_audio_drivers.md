---
title: "Checking / unchecking audio drivers"
date: 2010-05-08
forum: Wine
---

### Post by phuxed on 2010-05-08
I want to play Beat Hazard, and it's definitely possible, you just have to change the audio from ALSA to OSS

Problem is I can't uncheck ALSA or check OSS in the audio config

It's not crashing.. It just won't let me do anything.

Seems like this is one of the only games where I have to use OSS so it isn't a huge deal to me but I would still like to know why I can't uncheck anything

[IMG]http://img101.imageshack.us/img101/2582/screenshotwineconfigura.png[/IMG]

I'm using the newest development version on wine1.2, 1.1.43.

---

### Post by cogadh on 2010-05-08
Do you have OSS support installed? I believe you need at least both the alsa-oss and oss-compat packages installed.

---

### Post by phuxed on 2010-05-10
Sorry, couldn't reply right away

Yes, of course. I have full support for OSS and JACK installed.

I also have full PulseAudio support as well, which confuses me a bit because PulseAudio isn't even on the list at all

---

### Post by cogadh on 2010-05-10
That's because [Wine doesn't support Pulse]("http://wiki.winehq.org/FAQ#head-5d0b06ede012970adb6b0c2b08c7b144a58ce331").

You could try manually editing your /home/<username>/.wine/user.reg to add the extra audio drivers. Open the user.reg file with your text editor of choice and look for a section like this:
```
[Software\\Wine\\Drivers] 1273171381
"Audio"="alsa"
```
simply change the second line to look like this:
```
"Audio"="alsa,oss"
```
and you should have both ALSA and OSS audio drivers available at once.

---

### Post by phuxed on 2010-05-10
> **cogadh said:**
> That's because [Wine doesn't support Pulse]("http://wiki.winehq.org/FAQ#head-5d0b06ede012970adb6b0c2b08c7b144a58ce331").

You could try manually editing your /home/<username>/.wine/user.reg to add the extra audio drivers. Open the user.reg file with your text editor of choice and look for a section like this:
```
[Software\\Wine\\Drivers] 1273171381
"Audio"="alsa"
```
simply change the second line to look like this:
```
"Audio"="alsa,oss"
```
and you should have both ALSA and OSS audio drivers available at once.

That seems to have both fixed the problem and also lets me check the boxes again

Thanks. I have no idea how it locked up or why it fixed itself, but it worked!

---

