---
title: "xruns and cpu"
date: 2013-06-16
forum: Ubuntu Studio
---

### Post by roughi on 2013-06-16
hello there
i play guitar thru a firewire behringer fca202 interface, basically with qjackctl and rakarrack. I just take the rakarrack effects which don't produce xruns. But even then, e.g. when switching a window, when recording with QjackRcd or especially when listening to a youtube sound, xruns happen. I think it is because of high cpu. I tried with sample rate 48000 instead of 96000 and more frames/period, but at some point latency is too big to play. 
i checked the cpu setting: 
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
->performance

My system: ubuntu 12.10, Kernel Linux 3.5.0-26-lowlatency
VIA C7-M Processor 1600MHz, 1.7 GB RAM

is there a way, to make jack less sensitive to cpu usage? or is there another setting to check?
thank you for help!

---

### Post by Maxei on 2013-06-17
In my laptop, to avoid xruns I have installed the cpufrequtils to set the cpu of both cores to the highest set, which is 'performance'. Like you did, it helped in my case. Maybe some tweaking is also needed to make them default instead of doing it manually each time (like editing a settings file).
I also have tried with some success, to change the 'nice' value in the gnome-system-monitor, up to -20, for the highest priority; you can try if changing that for both kjack controller and also your application. Hope this helps.

---

### Post by roughi on 2013-06-17
thx, but didn't help so far. I checked my system settings with help of [http://wiki.linuxaudio.org/wiki/system_configuration](http://wiki.linuxaudio.org/wiki/system_configuration) and i guess there's something not okay with my kernel. i will check tomorrow.

---

