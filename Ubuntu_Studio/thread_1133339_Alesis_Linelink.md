---
title: "Alesis Linelink"
date: 2009-04-22
forum: Ubuntu Studio
---

### Post by bmac1911 on 2009-04-22
I bought an alesis linelink;  1/4" (x2, L/R) cable to USB for sending audio signal to a computer. Additionally I got myself a laptop, dumped Windows Vista and installed Ubuntu Studio. Unfortunately, the cable is supposed to be plug and play for PC and MAC -- and I assumed (n00b) it would be for ubuntu studio. The cable works fine on my desktop PC, allowing me to record my drum machine, for example, into my DAW software...so, I'm trying to figure out how to get it to work on my ubuntuified laptop...any ideas?

For the record, this cable is a 'new release'; this L/R 1/4" version has only been out a couple of weeks I think - but I don't know if that has anything to do with it. I usually refrain from forums because whatever I need is usually found with a bit of looking around (and I don't have the chops to really help anyone else out - unless they're dumber than I am) - but I'm utterly stumped on this one.

---

### Post by cariboo on 2009-04-23
Could you open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

and post the output in your next post?

---

### Post by bmac1911 on 2009-04-23
sure, here it is...

--------
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 064e:a103 Suyin Corp. 
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
--------

---

### Post by bmac1911 on 2009-05-01
Nevermind.

After a few updates, I got it to work.

If any other new folks get this issue; don't forget to use JACK to define the input to the LineLink Cable. It won't be in the drop down menu for the Input selection in the Settings - you'll have to use the expanding arrow to the right of the box and "Linelink" will be sitting right there :)

Okay - so it's not plug and play, like in Windows. I almost gave up and went back to Vista - but I persevered and got it to work - and glad I did. Ubuntu and it's sister Studio, are just a better running platform. Thanks to these forums and some other online resources.

Now all I have to figure out is the latency...grrr.

---

### Post by gorg0th on 2009-07-20
If you do find a work around for the latency I'd love to hear it.  I am also using one of the alesis 'link' series, the guitarlink, and while everything seems to work, the latency makes this unusable for any sort of real time uses...Anyone know if I can update the USB more frequently?

~g

---

