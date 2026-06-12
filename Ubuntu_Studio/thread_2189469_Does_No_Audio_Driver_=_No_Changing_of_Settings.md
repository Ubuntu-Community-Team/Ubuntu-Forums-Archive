---
title: "Does No Audio Driver = No Changing of Settings"
date: 2013-11-22
forum: Ubuntu Studio
---

### Post by bbarton11 on 2013-11-22
I think I've answered my own question on this already but I wanted to throw this out there before I remove Ubuntu Studio from my machine.  

I have an M-Audio Fasttrack Ultra 8R audio device (USB) that I use for music recording.  Apparently there is some kind of driver for it in Linux as I'm able to record with it but the problem I'm having is that I can't change the reverb settings in it.  For example, on my Win7 boot I brought up the GUI for the 8R and saw that there was reverb on the unit.  When I use JACK/Ardour for recording, I'm unable to turn off or change that reverb.  I had to reboot, go into Win7, change the reverb settings to fully off, reboot, and go back into JACK/Ardour. 

That's obviously not very productive for me.  Is there no interface for me on the Linux side so I can do that?

Thanks,
Brian

---

### Post by cub on 2013-11-23
I'm not sure it will help you and you might already seen it, but there seem to be a way to turn the effects off with alsamixer? [http://heikki.ketoharju.info/2013/03/linux-and-fasttrackultra/](http://heikki.ketoharju.info/2013/03/linux-and-fasttrackultra/)

---

