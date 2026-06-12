---
title: "Ubuntu Studio/Virtual box (sound not working)"
date: 2008-01-30
forum: Virtualisation
---

### Post by RadiationHazard on 2008-01-30
Ok, so i just go ubuntu studios becuase i'm wanting to make music and do video editing and all that but when i go to take the sound inside ubuntu studios off mute it doesn't work? and i'm running the ubuntu studios 7.10 and i'm running ubuntu gusty gibbon 7.10 as my actual operating system. so i don't really see why the sounds not work?

---

### Post by airbornemist6 on 2008-01-30
Try reinstalling Alsa. If all else fails you maybe be forced to install from source. In which case, you can look at this thread. It's meant to install stuff on a laptop, however, his guide for upgrading alsa is pretty much a good guide to install with. Please note, if you do have to follow that thread, your soundcard is most likely not the same, so do not assume yours is hda-intel, it's probably not.

EDIT:
Whoops I just realized, I forgot to include the thread I was talking  about xD

[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

---

### Post by theZoid on 2008-02-01
> **RadiationHazard said:**
> Ok, so i just go ubuntu studios becuase i'm wanting to make music and do video editing and all that but when i go to take the sound inside urdbuntu studios off mute it doesn't work? and i'm running the ubuntu studios 7.10 and i'm running ubuntu gusty gibbon 7.10 as my actual operating system. so i don't really see why the sounds not work?

What does this have to do with VirtualBox?  Are you saying the sound won't work in VirtualBox guest OS?  That needs to be set to OSS driver in settings.  Are you saying sound won't work in Ubuntu Studio when the Virtual Machine is running?  That would be because the VM has control of the card I think similar to how it takes control of USB devices, etc....but someone may correct me on that.  You really should clarify your question.

---

