---
title: "Hardware Monitoring"
date: 2017-12-28
forum: Ubuntu, Linux and OS Chat
---

### Post by newtsoup on 2017-12-28
Hi there,

Can anyone recommend a GUI program that will let me monitor CPU and GPU temperatures in real time?

I'm planning to overclock my system and need something like C.....

Turns out its 

~$ sudo apt-get install lm-sensors hddtemp
~$ sudo apt-get install psensor

run
~$ sudo sensors-detect

choosing the default option, listed in caps, each time

you can then do

~$ sensors

at the console or run psensor from the menu to bring up a graphical interface that will show you CPU, System, GPU and Hard Disk temps in real time.


I just thought I'd post what I found for anyone else looking for the same thing to read.

---

### Post by Quarkrad on 2017-12-28
Anyone interested in this area should also search for **Conky** on ubuntu - adds value to the above.

---

### Post by Yellow Pasque on 2017-12-28
I'm confused. Is there a question here or is this like a how-to thread that should be marked as [SOLVED]?

---

### Post by newtsoup on 2017-12-28
I've marked it as solved, It started as a question but turned into a "how-to"

---

### Post by 1clue on 2017-12-28
gkrellm works pretty well.

---

### Post by coffeecat on 2017-12-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

And thread title edited to remove the reference to howto.

@newtsoup, please see our guidelines concerning tutorials and howtos: [https://ubuntuforums.org/showthread.php?t=2143602](https://ubuntuforums.org/showthread.php?t=2143602)

Since this seems to have turned into a discussion, I've moved it to the appropriate discussion subforum.

---

