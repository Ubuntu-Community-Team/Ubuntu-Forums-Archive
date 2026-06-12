---
title: "Audacity hangs when I try to fade out"
date: 2010-02-26
forum: Ubuntu Studio
---

### Post by potiphera on 2010-02-26
I've been using Audacity on Ubuntu Studio Karmic, and it hangs about 90% of the time I try to use the fadeout effect.  I'm thinking it's [this bug]("https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/361534"), although I didn't get any messages in kern.log about it.  I also didn't get any error messages when running it from the terminal.

In the bug report, someone suggests installing Audacity 1.3.10 instead.  How do I replace 1.3.9 with 1.3.10?

Also, Audacity won't work with JACK.  If I select JACK as the host in the Devices section of Edit>Preferences, JACK doesn't show Audacity in the Connections interface like it would other programs.  How do I fix that?

Thanks!

---

### Post by tgalati4 on 2010-02-26
You might have to download it and build it yourself.  It's not difficult.  Search the forums for "make configure audacity".

Audacity works with ALSA and OSS.  I don't think it's JACK compatible.

---

### Post by sgx on 2010-02-26
With Audacity, open qjackctrl, start jackd, then start and pause Audacity. Now the Audacity portaudio connection should appear in qjacktl, so connect as desired, and unpause to record. 

As for the fx in audacity, make sure you have plenty of disk space, 2 gig should be ok, start Audacity after a cold boot, import a song, and try
the the fade. It should work. 
There is a setting allowing you to import a separate  version of the audio file, rather than working on the original. This is good luck.

Sometimes Audacity stops responding, with many menu items greyed out. If you double click in the waveform, press play and quickly press stop, this often restores menus, and export the file, and reboot and re-import, again
diskspace can be a factor.

Cheers

---

### Post by potiphera on 2010-02-27
> **tgalati4 said:**
> You might have to download it and build it yourself.  It's not difficult.  Search the forums for "make configure audacity".I just compiled and installed it, but I left out some of the options for stuff I wanted, like FLAC support.  How do I uninstall so I can compile and install again?

---

### Post by potiphera on 2010-02-27
> **tgalati4 said:**
> Audacity works with ALSA and OSS.  I don't think it's JACK compatible.It appeared to be when I used it in Hardy.

And in response to sgx, none of that advice has worked for me, although I had the hang with grayed-out menu items.  As for the JACK advice, it didn't get Audacity to show up in JACK, but after trying it I see ALSA and OSS as available devices instead of ALSA and JACK.  Odd.

---

### Post by AutoStatic on 2010-02-27
Audacity is JACK compatible in Karmic, see the attached screenshot. First start JACK with the help of QjackCtl, then start Audacity. Add the Device Toolbar (View - Toolbar - Device Toolbar) and select 'JACK Audio Connection Kit: system' for both recording and playback. In Preferences (Edit - Preferences) set the Default Samplerate at the same rate JACK is using. And set Devices - Interface - Host on 'Jack Audio Connection Kit' too.

---

### Post by potiphera on 2010-02-27
Thanks, AutoStatic, that worked!

Can anyone tell me how to uninstall the version of Audacity I built from source so I can do it again properly?  I only know how to do this stuff with apt, but I guess that doesn't work for something I compiled myself.

---

### Post by potiphera on 2010-02-28
Oh, never mind, I figured out that it was sudo make uninstall.

Also, I realized that I don't need to compile -- I installed the most recent daily build using [these instructions]("http://www.ubuntugeek.com/how-to-install-audacity-daily-build-from-ubuntu-ppa.html").  It works fine so far.

---

### Post by sgx on 2010-02-28
> **potiphera said:**
> Thanks, AutoStatic, that worked!

Can anyone tell me how to uninstall the version of Audacity I built from source so I can do it again properly?  I only know how to do this stuff with apt, but I guess that doesn't work for something I compiled myself.

This is the first hit of google search terms uninstall compiled audacity

[http://ubuntuforums.org/archive/index.php/t-812445.html](http://ubuntuforums.org/archive/index.php/t-812445.html)

Cheers

---

