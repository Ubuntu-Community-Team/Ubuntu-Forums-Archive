---
title: "Firewire Chipset for the Gazelle Pro"
date: 2012-01-26
forum: System76 Support
---

### Post by kayosiii on 2012-01-26
Does anybody know which this is?
Has anybody tried this laptop for pro audio?

Could somebody post the output of lspci here?

---

### Post by jschall1 on 2012-01-26
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)

---

### Post by kayosiii on 2012-01-26
ok looks like that chipset might be problematic -- sigh 
finding a laptop with a good firewire chipset is such a chore.

Do any of the system76 laptops have a express card slot?

---

### Post by kayosiii on 2012-01-26
If anybody from System76 reads this....

There are a number of people in the Linux Audio community are looking for a laptop that will work well with pro-audio firewire soundcards. Texas Instruments Firewire is probably best, agere and Via are acceptable, ricoh and jmicron are problematic.

Quite a number of people own these soundcards and although usb3 based soundcards will probably start to replace these models it is going to be a conciderable amount of time before there is Linux support for usb3 pro soundcards.

---

### Post by isantop on 2012-01-26
I'll forward your comments on for future products. I will say, however, that there probably won't be much focus on firewire going forward due to the large industry interest in Thunderbolt and USB 3.

---

### Post by kayosiii on 2012-01-27
ok but keep in mind the following...

I am not aware of any pro-audio company doing thunderbolt or USB3 interfaces...

Almost no USB2 interfaces work under Linux and none with comparable features/performance to what the firewire interfaces do. Nor is this likely to change in the next few years (nobody is doing usb2 drivers for linux).

Firewire is capable of much faster latencies (this is what pro audio folks care about) than USB2 is and I have my doubts that USB3 will do much better in this regards thunderbolt could be interesting however.

Pro-Audio interfaces have a long shelf life... I bought my first interface about 5 years ago and I can't see myself buying another in the next 5 years unless I have to. Devices are typically reliable and do the job.

Clevo has created models with Texas instruments firewire. If not it might be possible to use a mini pci based interface for this. Texas instruments is the gold standard as far as firewire goes Agere and via work decently these days. Even for desktop systems this will be a selling point.

You will find people looking for such systems in the following places...

[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)
[http://linuxmusicians.com/](http://linuxmusicians.com/)
[http://lists.linuxaudio.org/listinfo/](http://lists.linuxaudio.org/listinfo/)
[http://www.ardour.org/](http://www.ardour.org/)

possibly
[http://bitwig.com/bitwig_studio.php](http://bitwig.com/bitwig_studio.php)
[http://www.renoise.com/board/](http://www.renoise.com/board/)
[http://www.energy-xt.com/index.php?id=0300](http://www.energy-xt.com/index.php?id=0300)

Focusrite probably has the support for linux of any vendor selling firewire based sound cards.

---

### Post by chriscross93 on 2012-01-31
Just FYI,

I have a System76 GazP6 that is used as a DAW in live environments.  I primarily use Native Instrumnts USB 2.0 interfaces, they work (and sound) great!

Hopefully this helps?...

---

### Post by kayosiii on 2012-02-01
> **chriscross93 said:**
> Just FYI,

I have a System76 GazP6 that is used as a DAW in live environments.  I primarily use Native Instrumnts USB 2.0 interfaces, they work (and sound) great!

Hopefully this helps?...

Is there any chance you could borrow a firewire based card and test it? 

What kind of latency are you getting with the USB card, which model is it?

---

### Post by kayosiii on 2012-02-01
also good to see that there are some descent usb2 based linux cards out there....

also which chipset does the expresscard slot - does it and the firewire share interupts with other devices, if so which devices?

Also which firewire chipsets for the serval pro and the bonobo?

---

