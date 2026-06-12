---
title: "[SOLVED] Getting Sound to Work: VMWare, Ubuntu host, XP guest"
date: 2008-06-09
forum: Virtualisation
---

### Post by wayfarer51 on 2008-06-09
I'm running VMWare Server 1.0.6 on a Hardy machine, Ubuntu host, WinXP guest.  I'm unable to play a sound file of any kind in XP.  Control Panel > Sounds and Audio Devices reports that I have no audio device.  I just assume that the XP guest can't recognize the soundcard I use in Ubuntu all the time.

Is there any way I could get XP to recognize and use the soundcard I have?  

Thanks for your help.

Neill

---

### Post by fjgaude on 2008-06-10
Well, do you have in VM/Settings/Sound Adpater showing? If not, power off the VM and see if you can Add it, menu at the bottom of the list with the big plus sign.

---

### Post by wayfarer51 on 2008-06-10
That did it.  Worked like a charm!  

I felt like I was wandering in the midst of too many settings and preferences.  Thanks for showing me the way out.

Neill

---

### Post by fjgaude on 2008-06-10
We all know what you mean... lots to observe and to learn, day-by-day.

---

