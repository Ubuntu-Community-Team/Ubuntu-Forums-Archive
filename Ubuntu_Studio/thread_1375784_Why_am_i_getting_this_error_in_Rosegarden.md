---
title: "Why am i getting this error in Rosegarden?"
date: 2010-01-08
forum: Ubuntu Studio
---

### Post by Macfunky on 2010-01-08
As per attachment. I tried typing what was suggested into a terminal but no joy. Also that site just brings me to sourceforge's homepage. Anyone able to help me out?

---

### Post by thorgal on 2010-01-08
in a terminal, type this

```

ls /lib/modules/`uname -r`/kernel/sound/core/*timer*

```

what does it return ?

then

```

grep CONFIG_HZ /boot/config-`uname -r`

```

what does it return ?

---

### Post by Macfunky on 2010-01-08
Here is the output -

meme@JitterBug:~$ ls /lib/modules/`uname -r`/kernel/sound/core/*timer*
/lib/modules/2.6.28-17-generic/kernel/sound/core/snd-timer.ko
meme@JitterBug:~$ grep CONFIG_HZ /boot/config-`uname -r`
# CONFIG_HZ_1000 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ=250
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
meme@JitterBug:~$

---

### Post by thorgal on 2010-01-08
thanks. From your output, I can see two things:

- your kernel is more configured for server operation rather than desktop (250Hz sys timer freq instead of 1000Hz). Not a strict thing though, but increasing the kernel timer freq would help a bit.

- your ALSA kernel layer does not benefit from a high resolution timer.

There are ways to add this support but this is not easy if you never compiled anything.

1- if your h/w supports it, you could benefit from HPET ([http://en.wikipedia.org/wiki/High_Precision_Event_Timer](http://en.wikipedia.org/wiki/High_Precision_Event_Timer))

2- the modern kernel has some code to benefit from hpet (so-called High Resolution timer code)

3- ALSA has now (as of 1.0.20 I think) a module that can use the HR timer kernel code (snd-hrtimer). 

A proaudio-centric distro should try to provide these, along with a 1000Hz sys timer kernel.

---

### Post by barisurum on 2010-01-09
Macfunky: Are you using the rt kernel provided with ubuntustudio-audio package? Also I'm not sure but the ibex's rt kernel may be set to 250hz operation which is low resolution. Then upgrading to 9.10 ubuntu studio may solve the problem.

---

