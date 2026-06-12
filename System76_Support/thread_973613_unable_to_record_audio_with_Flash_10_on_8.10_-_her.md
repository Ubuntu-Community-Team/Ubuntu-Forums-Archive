---
title: "unable to record audio with Flash 10 on 8.10 - here is why / the fix"
date: 2008-11-06
forum: System76 Support
---

### Post by ctsdownloads on 2008-11-06
I hate calling this a fix as clearly, [no one from Canonical]("https://bugs.launchpad.net/ubuntu/+bug/290121") is lifting a finger to fix this. 

But if you have a microphone, USB or otherwise and you have tried everything to get it working after upgrading to Ubuntu 8.10, this is why. Alsa along with its interaction with Pulseaudio is not jiving.

Try this - 

killall -w pulseaudio

Now try using ustream with a mic/cam that worked previously with 8.04 - success.

If you are like me, after spending days trying to figure out why your asoundconf settings were being ignored for audio recording, this clears things up really quick. 


If you are like me and use a dedicated PC for stuff like ustream, toss this into your sessions to send Pulseaudio back to where it belongs:

sh -c "sleep 10 && killall pulseaudio"

I like Pulseaudio for my boxes that have nothing to do with microphones, but not so much with my webcam/mic setup.

---

