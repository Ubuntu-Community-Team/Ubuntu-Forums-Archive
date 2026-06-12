---
title: "ubuntu studio/supercollider hardware q"
date: 2008-12-16
forum: Ubuntu Studio
---

### Post by jtclicker on 2008-12-16
I've been evaluating studio + supercollider on my desktop machine and like it enough to buy a laptop to commit to this as my main composing tool. I need some advice on hardware though.

Is anyone using this combo on a recent laptop? I'm looking for a 13/15 inch machine  where everything works under ubuntu studio 64. needs to be 2.5 duo, with firewire and an esata port (or firewire and expansion card port).

I also need recomendations for a firewire i/o device that has at least two mic ins and 4 audio outs.

Any ideas anyone???

---

### Post by babarosa on 2008-12-16
"...I also need recomendations for a firewire i/o device that has at least two mic ins and 4 audio outs."

If you want to buy a firewire-interface I recommend you visit "www.ffado.org". Take only into consideration an interface which is listed as "supported"! 
Supported interfaces by ffado in general work fine.

Regards, Michael

---

### Post by jtclicker on 2008-12-16
Thanks michael - at least seems to be enough to build a system, which is more than I hoped for. I've got my eye on a small thinkpad t400 - if I can ensure that works with linux I'll be very happy!

---

### Post by babarosa on 2008-12-16
jtclicker,

start here: [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400)

I entered the keywords in google and there is a lot of information about compatible hardware. Additionally "laptop testing team" for ubuntu compatible hardware list.

If you want to build an audio system stick to Ubuntu version 8.04.1! At the moment v8.10 doesn't offer a proper working rt-kernel which is a must for audio applications (for example try ubuntu-studio v8.04).

---

### Post by jtclicker on 2008-12-16
I'm running spuercollider on 8.10 on my desktopand haven't seen a problem yet -  I'm not using an i/o device, but I'm making pataches and recording

---

### Post by Stochastic on 2008-12-16
> **babarosa said:**
> At the moment v8.10 doesn't offer a proper working rt-kernel...

8.10 does have a working rt kernel it just lacks multicore processor support (only one core will work properly) and has a shutdown bug.  Things should mostly work fine for older computers running 8.10

---

### Post by jtclicker on 2008-12-16
I am running an older (non duo) desktop box, hence I've not noticed any problems. I like the blog stochastic!

---

