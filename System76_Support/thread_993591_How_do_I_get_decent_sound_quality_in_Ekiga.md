---
title: "How do I get decent sound quality in Ekiga?"
date: 2008-11-25
forum: System76 Support
---

### Post by gruntlips_ on 2008-11-25
Hi, I would like to use ekiga but so far I have found the sound quality of the echo test call to be abysmal for three reasons - (1) the playback is from the mic is really faint, almost inaudible (2) there is a lot of background crackling noise and (3) if I turn up the mic so it is not as faint the crackling noise swamps out everything.  

I configured my sound settings using a post on the system76 board for front mic. I have fiddled with these settings endlessly but I can't seem to improve the sound quality of the call.  

I don't have any problems with sound in other apps such as banshee or vlc.
  
In the ekiga sound settings it is using the alsa plugin and output and input audio devices are default.  If i switch these last two to ALSA, I get this error "An error occured while trying to play audio to the soundcard for the audio reception. Please check that your soundcard is not busy and that your driver supports full-duplex.The audio reception has been disabled."

I am running 8.10 on a serval (serp4) and using ekiga 2.0.12.

Thanks for the help!

- ccc

---

### Post by doyouhas on 2008-11-25
This problem is not limited to Ekiga, I had the exact same problem with Skype under Linux. I just use Windows when I know I´m going to use Skype. Not an expert with the sound configuration in Ubuntu, but there is a good bet you need to configure Pulse Audio.

---

### Post by thomasaaron on 2008-11-26
First, the internal mic on the SerP4 doesn't produce the highest quality sound under Ubuntu. You might want to try an external mic.

Second, if you're using 8.04, you should be using ALSA. If you're using 8.10, you should set all of the dropdowns to pulse audio in System > Preferences Sound.

---

### Post by gruntlips_ on 2008-11-26
Thanks, I switched all my sound settings to pulse audio as you suggested.  I tried Ekiga again but did not detect an improvement in sound quality.  Also, in Ekiga there is no pulse setting under audio setup.  The audio plugin is only ALSA and the output and input devices are either default or ALSA.

What do i select in sound preferences for default track mixer?
Besides, changing all options under sound setting to pulse are there any other things to tweak?

Thanks.

-ccc

---

### Post by thomasaaron on 2008-11-27
As I mentioned, you would be better off to use an external mic.

You can set the default track to master, front, or pcm. Whatever you set it to is what your speaker icon (upper right) and function key volume controls will manipulate.

---

