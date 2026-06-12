---
title: "Sound Card Drivers with Virtual Box"
date: 2011-01-01
forum: Ubuntu Studio
---

### Post by TobiasRipper on 2011-01-01
I have the firefly 808 external audio interface which can be connected through USB or Firewire. When I was working on Windows, I would just install the firefly drivers from the CD and windows would automatically see the device. Well now, I moved on to Ubuntu Linux. I have not installed the audio drivers on linux because there is no Linux drivers for this interface.

I'm thinking... will the audio work if I install Windows through Virtual Box and then install the windows audio drivers for the interface?

---

### Post by celldweller1591 on 2011-01-02
If you do what you suggested above will install audio inside virtual box for windows only. You will not be able to use those with Ubuntu anyway.

---

### Post by peterfernandes238 on 2011-01-03
I would just install the firefly drivers from the CD and windows would automatically see the device.
--------
Peter Fernandes

---

### Post by AutoStatic on 2011-01-03
[http://ffado.org/?q=node/553](http://ffado.org/?q=node/553)
So apparently it works. But [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm"). So you have to use JACK and make [some adjustments]("https://help.ubuntu.com/community/FireWire") to your Ubuntu installation.
But could you install the **ffado-tools** package and post the outcome of the **ffado-diag** command with the FireFly connected?

Best,

Jeremy

---

