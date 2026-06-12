---
title: "How to disable system sounds completly"
date: 2019-03-15
forum: Ubuntu Development Version
---

### Post by moma on 2019-03-15
Hello,

I do a occasional recordings (from mic and audio) on my Ubuntu 19.04 system.
One thing that bugs me is this.

During recordings I often adjust the volume setting by scrolling mouse on the system-tray (volume icon) .
Those small mouse scrolls (or clicks) are also recorded, even so faintly, the clicks are hearable during playback.

I have set the "System sounds" setting to zero in system-settings dialog. But it does not help. 
How to disable system sounds entirely?
I cannot recall this was an issue in earlier Ubuntu and GNOME-systems.

This maybe partly a Gstreamer issue, that adjusting the volume level during recording simply affects the recording pipeline.

I am recording with:
[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)
 
My system is:
$ lsb_release -a
Distributor ID:	  Ubuntu
Description:       Ubuntu Disco Dingo (development branch)
Release:	19.04 disco

Obrigado,
 Moma  
 Portugal

---

### Post by #&amp;thj^% on 2019-03-15
Hello moma see if this still works, I haven't had to use it for couple years now.
```
dconf write /org/gnome/desktop/sound/event-sounds false
```

---

### Post by moma on 2019-03-15
Hello,

Thank you very much.
I actually think it works. 
Of course sudden changes in volume-level affect also the recording.
But I think the small faint scroll-clicks are gone.

I remember last year that system-settings had ON/OFF button for event-sounds.
Has is disappeared for ever?  

Though your command does same thing.

Muito obrigado,
Moma
Portugal

---

### Post by #&amp;thj^% on 2019-03-15
> **moma said:**
> Hello,

Thank you very much.
I actually think it works. 
Of course sudden changes in volume-level affect also the recording.
But I think the small faint scroll-clicks are gone.

I remember last year that system-settings had ON/OFF button for event-sounds.
Has is disappeared for ever?  

Though your command does same thing.

Muito obrigado,
Moma
Portugal

Well I'm no longer a Gnome user, but I think you'll find the same with "Gnome-Tweak"Tool. ;)

---

