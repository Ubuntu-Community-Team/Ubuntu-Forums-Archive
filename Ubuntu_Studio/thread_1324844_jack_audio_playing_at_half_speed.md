---
title: "jack audio playing at half speed?"
date: 2009-11-12
forum: Ubuntu Studio
---

### Post by NoxNoctis7 on 2009-11-12
Thanks to the help of some here on this forum i've got jack working but its only running audio at half speed, so everything sounds very low pitched and a little distorted.

I can't seem to set jack to anything but 48000. Any ideas on how to fix this issue, or where i can read up on how this works so i can solve the problem myself?

Thanks in advance for any information.

---

### Post by sgx on 2009-11-13
> **NoxNoctis7 said:**
> Thanks to the help of some here on this forum i've got jack working but its only running audio at half speed, so everything sounds very low pitched and a little distorted.

I can't seem to set jack to anything but 48000. Any ideas on how to fix this issue, or where i can read up on how this works so i can solve the problem myself?

Thanks in advance for any information.
I had that experience a few years back, and checked all the alsa related
files that could be text edited, one of them had an entry of 22,500 instead of 44100, probably a dropping from some game or video app I installed.
When I changed it, things were fine again.
Cheers

---

### Post by NoxNoctis7 on 2009-11-13
thanks a lot for the reply. I'm pretty new to linux so I don't even know where to start but i'll poke around and see what i can find. thanks again

---

### Post by NoxNoctis7 on 2009-11-13
i looked around with what limited skills i have and all i could find was 
/usr/share/alsa.conf

in that file there's a thingy that says
defaults.pcm.dmix.rate 48000

i dunno even know if thats the line i need to edit, but if it is, that sounds right to me?

I dont have a .asoundrc file or a /etc/asound.conf file. am i missing something somewhere?

thanks again for any help
P.S. is there jack support forum that this question might be better placed in?

---

### Post by kayosiii on 2009-11-13
Is this just ardour or any jack program.

If you happen to have recorded audio at 48k you change jacks sample rate - Ardour will not resample for you automatically your recorded audio will just play back either faster or slower.

You will either need to stick to a consistant sample rate throughout the project or resample your recorded files. You can find instructions on doing so in the forums on the ardour website.
[www.ardour.org](www.ardour.org)

---

### Post by NoxNoctis7 on 2009-11-13
sorry for the sketchy details.

I experience this problem with ardour, LMMS and rosegarden, which are the only jack apps i've been able to use successfully

this happens with both recorded music and a lot of the softsynths

in rosegarden, my midi recordings play back at half speed as well, which is strange

---

