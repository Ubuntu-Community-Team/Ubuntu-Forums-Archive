---
title: "volume level low"
date: 2016-04-02
forum: Ubuntu Studio
---

### Post by tony.de.lobelle@gmail.com on 2016-04-02
Installed latest ubuntu studio...01APR16...:D

everything works fine, but the volume level is way lower than it is in 14.04...

wher can I manipulate these setting?

I am using alsa and audacious for music playback...
also USB DAC(concero HD)

kind regards,

Tony

---

### Post by yoshii on 2016-04-02
Check QasMixer settings as well as PulseAudio Volume Control.  
The hardware's internal volume might be set low.  QasMixer I think can access this and change it.

---

### Post by tony.de.lobelle@gmail.com on 2016-04-03
Found it...

QasHctl has a HW volume setting wich was set to low...

[https://drive.google.com/file/d/0B5bWHD56pprZR25tX1paaExuNEk/view?usp=sharing]("https://drive.google.com/file/d/0B5bWHD56pprZR25tX1paaExuNEk/view?usp=sharing")

did not have to change this in previous versions...
maybe standard setting could be set a little higher?

---

