---
title: "Problem with Mic"
date: 2009-03-18
forum: Ubuntu Studio
---

### Post by Yanz on 2009-03-18
I have a built in Microphone.. It doesn't want to work with Ubuntu.. Any one know why?

---

### Post by markbuntu on 2009-03-18
There's a few thousand reasons why and they all have to do with your hardware so, if you wouldn't mind telling us what particular machine you are using we might be able to help you.

---

### Post by lvleph on 2009-03-18
Open a terminal (Accessories>>Terminal) and type lspci and then past the output here.

---

### Post by Reeman on 2009-03-18
> **Yanz said:**
> I have a built in Microphone.. It doesn't want to work with Ubuntu.. Any one know why?
Try to see if there is a reference to the mic in alsamixer it could be that the device is not being seen. If you shut down the pulse audio server then more devices just might show up in alsamixer. 

Try shutting down the pulse server then run alsamixer -c 0 in a terminal... if your audio card is completely supported then all the functions will show up.

If you open mixer preferences the with the mixer gui you might be able to add more mixer devices to the pulse default gnome mixer instead of the just level control. 

If this is not the case and alsa delivers the device correctly then the XP%@^*&! pulse audio server is the culprit.

Sometimes I wish Ubuntu would just dump the stupid pulse audio crap...and let things work the way they should.

---

### Post by Flag on 2009-03-19
Sometimes I wish Ubuntu would just dump the stupid pulse audio crap...and let things work the way they should.

+1

---

### Post by Flag on 2009-03-19
Don't know yr. OS. It helped me to add a line to /modprobe.d/alsa-base, like (depends on yr hardware) options snd-hda-intel model=xxxx, this would give you options to choose from. ( speaker icon -> prefs )

---

### Post by Reeman on 2009-03-19
> **Flag said:**
> Sometimes I wish Ubuntu would just dump the stupid pulse audio crap...and let things work the way they should.

+1

Same crap with windows vista the windows default audio server plays heeellll with anything written for an asio standard device interface. You can forgive Microsoft though their intentions are clear...make it so you have to use their audio interface if you want to do any multimedia. That way you have to just put up with audio that cannot handle RT compliant software.

The Ubuntu use of pulse is very similar...it hogs /dev/dsp and unless you known that it is just a server layer on top of alsa then you are tricked into thinking that it is necessary for audio software to work. My suggestion is to develop a simple switch interface that shuts the thing off completely and kills the sound deamon. Preferably permanently at boot if the user chooses.

---

### Post by linux_tech on 2009-03-21
```
killall pulseaudio
``` to stop pulseaudio
```
pulseaudio
``` to start pulseaudio

---

