---
title: "Sound wonky on Galago UltraPro"
date: 2014-01-28
forum: System76 Support
---

### Post by 4CP8X4x on 2014-01-28
Hi there! I understand that Ubuntu is the only officially supported distro but I was hoping for a push in the right direction. I installed Arch a little while ago and I really love it. Everything is faster and/or works better than Ubuntu and I've learned alot about linux. However I have this issue with the sound.

When I login the audio pops slightly
When no application is using audio and I open an app that does, audio pops slightly
When I close the last app that is currently using audio, audio pops slightly
When no app is using audio, sometimes a high pitched whine starts playing which is EXTREMELY annoying and/or can cause a headache if unnoticed (due to the high pitch I sometimes don't notice till my head hurts)

Im using Arch 64bit with Gnome Shell, Pulseaudio, TLP power management (I left TLP default), and the AUR version of the System76 driver.

I would like at the very least like to know what exactly is done by the driver to fix my internal microphone.

Thanks

SOLVED EDIT: TLP was the problem. It turns the audio chip and  controller off after a timeout of 1 second by default. The minute power  savings from which is not worth the audio issues to me.

TLP stores all configuration in /etc/default/tlp

Change:  SOUND_POWER_SAVE=1
to                   SOUND_POWER_SAVE=0

0 disables timeout

I also set SOUND_POWER_SAVE_CONTROLLER=Y
to                       SOUND_POWER_SAVE_CONTROLLER=N

Which disables power saving on the audio controller.

---

### Post by linrunner on 2014-01-29
Hi,

you may want to read the [TLP FAQ]("http://linrunner.de/en/tlp/docs/tlp-faq.html#audio").

---

### Post by 4CP8X4x on 2014-01-29
Ironic that I just found that page, came over here to edit post and read your post. Thanks for helping : )

---

