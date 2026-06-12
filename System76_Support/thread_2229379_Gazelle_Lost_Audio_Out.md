---
title: "Gazelle Lost Audio Out"
date: 2014-06-12
forum: System76 Support
---

### Post by KivalliqKid on 2014-06-12
Ok, so this afternoon, my wife was using our laptop. Then our two year old came an touched the trackpad, swiping across it... Then somehow, the audio was gone. It was not muted, volume was turned all the way up, and system settings said the internal speakers were selected.

I tried: sudo alsa force-reload

That did not work. So I tried: sudo apt-get remove --purge alsa-base pulseaudio
and then installing it again (tried this earlier when I lost audio when using HDMI, and it worked), but this did not work either. In fact I lost a lot of system settings, and had to install ubuntu-desktop to get them back.

Still no audio out...

What am I to do to fix the suddently dissapearing audio?

Thank you for your time and answers.

---

### Post by KivalliqKid on 2014-06-12
Well apparently the speakers are blown :( :(
Plugged in some headphones and they worked perfectly fine. Well that sucks.

---

