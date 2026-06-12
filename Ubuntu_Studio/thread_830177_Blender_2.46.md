---
title: "Blender 2.46"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by eks on 2008-06-15
Hellos!

I'm in need of some features on the new version of Blender (2.46), but the Ubuntu repository has only the old one (2.45). Is there any estimation of when the repo will be updated?

And what if I don't want to wait, how do I upgrade the 2.45 controlled by synaptic to a 2.46 installed manually?

Or should I uninstall the 2.45 first and install the new one then?


Thanks!
eks

---

### Post by cotcot on 2008-06-15
Get 2.46 [[COLOR="Red"]here[/COLOR]]("http://www.blender.org/download/get-blender/"). Extract the file, go in it and just click the blender executable. Nothing to install. Leave the 2.45 version just is you have it from the repos. 2.45 can live aside 2.46.

I do not know if you know how to correct the sound :
The solution is to add the variable [COLOR="Red"]SDL_AUDIODRIVER=alsa[/COLOR] in /etc/environment
# sudo nano /etc/environment
SDL_AUDIODRIVER=alsa
restart the computer and launch blender

---

### Post by cotcot on 2008-06-15
Deleted (was a double post sorry)

---

