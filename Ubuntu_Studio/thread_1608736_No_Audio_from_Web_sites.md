---
title: "No Audio from Web sites"
date: 2010-10-29
forum: Ubuntu Studio
---

### Post by windeguy on 2010-10-29
I am not hearing any audio from web sites. I am using gstreamer with JACK and do not have a problem playing MP3s, videos with sound, midi files, VST instruments using VSTHost, or Reaper under WINE. 

I upgraded to the latest version of Adobe Flash player in Firefox but still do not get any sound when playing a video from YouTube, CNN, etc. The video is playing OK, just without any audio. 

I have checked the ALSA Mixer and nothing is muted.

Any suggestions?

---

### Post by Pablo_F on 2010-10-29
Hi, 

You need jack support for the flash player or another workaround like alsa-jack or pulse-jack plugins. If you use the first option (a jackified flash player) you won't have sound from flash unless jack is running beforehand. I myself use this option as I am always running jack but YMMV. 

For the first option, see:

[http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323](http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323) 

For other options, this thread can help:

[http://ubuntuforums.org/showthread.php?p=7304344](http://ubuntuforums.org/showthread.php?p=7304344)

Cheers! Pablo

---

### Post by windeguy on 2010-10-29
> **Pablo_F said:**
> Hi, 

You need jack support for the flash player or another workaround like alsa-jack or pulse-jack plugins. If you use the first option (a jackified flash player) you won't have sound from flash unless jack is running beforehand. I myself use this option as I am always running jack but YMMV. 

For the first option, see:

[http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323](http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323) 

For other options, this thread can help:

[http://ubuntuforums.org/showthread.php?p=7304344](http://ubuntuforums.org/showthread.php?p=7304344)

Cheers! Pablo

Thank you for the response Pablo.  I too would prefer option one and have jack running all of the time. 

I went to the link you indicated and found this set of installation instructions


To install:

[B]git clone git://repo.or.cz/libflashsupport-jack.git
cd to the libflashsupport directory
sh bootstrap.sh
make
sudo make install[/B]


I first had to install git since it was not on my system.  I was then able to execute the commands up to "make" , but when I typed "make" I got the following response and was at a dead end since I am not very Linux aware:

mike@mike-laptop:/libflashsupport-jack$ make
make: *** No targets specified and no makefile found.  Stop.
mike@mike-laptop:/libflashsupport-jack$ make^C
mike@mike-laptop:/libflashsupport-jack$ ^C
mike@mike-laptop:/libflashsupport-jack$ 

Ah, I figured out I needed to install the other programs you had listed at that link and I could then run commands and they seemed to execute. 

I now have audio when running Flash in Firefox.  Thanks again.

---

