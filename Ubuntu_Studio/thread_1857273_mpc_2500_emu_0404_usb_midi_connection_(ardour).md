---
title: "mpc 2500 emu 0404 usb midi connection (ardour)"
date: 2011-10-10
forum: Ubuntu Studio
---

### Post by anemi on 2011-10-10
hello ubuntu forums. i have upgraded from ubuntu 10.10 to ubuntu studio manually (sudo apt-get, not from cd/dvd). i use a emu 0404 usb audio interface, that works fine from once i plugged in, but i havent ever explored its midi capabilities.

so, im connecting my mpc 2500 to emu 0404 usb (midi out to in), and i want when i hit play on the mpc, ardour start playing too, so i can sync a project and multitrack export my beats, channel by channel, and all channels play correctly from start. how is this possible?.

---

### Post by dawiba on 2011-10-10
With Ardour open, hold down Ctrl and then click the middle mouse button over the control you want to assign, say the 'Play' button in Ardour's Transport. You'll get a small window popup which says 'operate controller now'. At this point, operate whichever controller you want to use on your mpc to control Ardour's 'Play' function and that should be it assigned.

Just repeat the process for each different control that you want to assign

---

### Post by anemi on 2011-10-11
i do this but nothing pops up..

from jack, i went to connect->alsa and connected emu usb midi 1 to 129:ardour 0:control.
now when i hit play on the mpc, the ardour does start playing (not from the start point), but also recording in two channels at the same time and monitoring!! crazyness:p:p

---

### Post by dawiba on 2011-10-11
In Ardour, go to Options -> Control Surfaces and select Generic Midi. I usually also select 'Remote ID assigned by User'. Then try holding down Ctrl and middle clicking again to assign your controls.

---

### Post by anemi on 2011-10-19
thank you very much, i made everything you said, the window popped up but nothing happened, am i supposed to have jack open as well? and if yes, with what settings?

---

### Post by sgx on 2011-10-19
> **anemi said:**
> thank you very much, i made everything you said, the window popped up but nothing happened, am i supposed to have jack open as well? and if yes, with what settings?
Ardour should start jackd automatically. Check the connections in qjackctl. Use 3 for the qjackctl periods/buffer setting.

[http://www.youtube.com/watch?v=kS2xEp0mDt8](http://www.youtube.com/watch?v=kS2xEp0mDt8)  ardour-midi video
 
I would use the ardour binary alpha releases, perhaps less stable,
but having the more modern capabilities, particularly
where midi is involved. qtractor would also be worth testing,
and reaper in a wine/wineasio setup, may offer the most
complete compatibility. 

Midi from devices having both usb, and 5 pin connectors sometimes have
specific modes or cabling that need to be observed, so double-check
for tips in the manual. Installing a2jmidid might help, providing a jack midi port in the qjackctl midi tab.

a2jmidid -j default   starts the jack midi port

When using it. I also connect
the midi ports to the midi-through ports (if any) in the alsa tab.

A link to the Ardour Alpha binary is here:

[http://ardour.org/node](http://ardour.org/node)  expand the archive, and run the installer, no synaptic needed.

[http://www.reaper.fm/](http://www.reaper.fm/)   Wine and wineasio are needed, well worth
the effort, to use modern gear in linux.

Akai sure makes some fine hardware. I'm saving up for their wind controller :)

---

