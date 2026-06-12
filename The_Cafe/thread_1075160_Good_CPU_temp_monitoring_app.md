---
title: "Good CPU temp monitoring app"
date: 2009-02-20
forum: The Cafe
---

### Post by wolfen69 on 2009-02-20
i've decided to overclock my new phenom quad core 9950. what's a good prog for monitoring temps? btw, it's freakin awesome.

---

### Post by Polygon on 2009-02-20
lm-sensors

follow this guide to set it up: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

and then install sensors-applet to get a nice gnome applet for it and you can also install hddtemp if you want sensors-applet to show the temps for your hard drives. Once you have everything set up, you ahve to right click > preferences on sensors applet and get rid of the bogus entries, cause i know for me i have like 4 entries for 'cpu' and only one of them is correct

anyway, experiment with it =)

---

### Post by binbash on 2009-02-20
lm-sensors + conky

---

### Post by rajeev1204 on 2009-02-20
[QUOTE=Polygon;6767610]lm-sensors

follow this guide to set it up: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Thats a very old lm-sensors how to.I didnt have to follow all that.Just installed lm sensors and ran sensor detect which seems to load all modules.Probably needs a restart.

But i cant get CPU to show correct temperature.Always stuck at 40 degrees C.Its a known bug.

---

### Post by wolfen69 on 2009-02-20
thank you for your responses. however, i am not filled with confidence about these methods. i had a great temp applet on my taskbar a while ago, but don't remember the name or how i got it. anyone else?

---

### Post by Polygon on 2009-02-20
> **rajeev1204 said:**
> [QUOTE=Polygon;6767610]lm-sensors

follow this guide to set it up: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Thats a very old lm-sensors how to.I didnt have to follow all that.Just installed lm sensors and ran sensor detect which seems to load all modules.Probably needs a restart.

But i cant get CPU to show correct temperature.Always stuck at 40 degrees C.Its a known bug.

the program shows what the sensors on your motherboard report. on my old computer, i had like 5 entries for CPU, 2 of then were like -1 degrees and the other was a constant 30 degrees, while the real one was at like 50 degrees.

---

### Post by wolfen69 on 2009-02-20
when i run sudo ./mkdev.sh, it says command not found.

---

### Post by wolfen69 on 2009-02-20
also, what command can i run to see what frequency i'm running at?

---

### Post by Polygon on 2009-02-20
frequency? as cpu frequency? thats a seperate program, im not sure of a cli one that will do that

and you have to cd to the directory that the script is in.

---

### Post by Twitch6000 on 2009-02-20
> **binbash said:**
> lm-sensors + conky

+1

---

### Post by DMcA on 2009-02-20
there's a native gnome-panel temperature sensor applet in the repositories. I forget the name I'm afraid but once installed you can just "add to panel". I think it just uses "acpi -t", so you could run "watch acpi -t " in a terminal too. Similarly, there's a panel applet for frequency monitoring (which also let's you adjust the frequency if your CPU supports it) but I thought that was installed by default.

---

### Post by wolfen69 on 2009-02-20
> **Polygon said:**
> 
and you have to cd to the directory that the script is in.

i did, but says command not found.

---

### Post by Polygon on 2009-02-21
did you "chmod +x mkdev.sh" first?

---

