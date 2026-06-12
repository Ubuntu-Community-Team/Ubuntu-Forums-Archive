---
title: "USB MIDI interface does not work after upgrading to 8.10"
date: 2008-11-09
forum: Ubuntu Studio
---

### Post by haba7 on 2008-11-09
Some USB MIDI interfaces (at least my [Yamaha UX-16]("http://uk.yamaha.com/en/products/music_production/accessories/usb_midi/ux16/")) stop working, when upgrading Ubuntu Studio from 8.04 to 8.10, 

Before trying to access the device from computer, the led displaying MIDI activity blinks according to data send from a MIDI keyboard.

Trying to record MIDI (eg. with Rosegarden) makes ALSA get stuck so that it can not be restarted. Actually, the whole computer can not be gracefully shut down, because ALSA does not stop. The MIDI activity led stops blinking.

Has anyone else had this kind of problem?

Any ideas for fixing the problem or finding a workaround until the bug is fixed?

---

### Post by haba7 on 2008-11-10
I tried the interface on my Kubuntu 8.10 desktop and it worked fine... so I decided to install the generic kernel also to my Ubuntu Studio 8.10 and the midi interface was fully functional!

So, this is [a bug]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/296195") in a current rt kernel [linux-image-2.6.27-3-rt]("http://packages.ubuntu.com/intrepid/linux-image-2.6.27-3-rt").

---

### Post by haba7 on 2008-11-10
Workaround is to install the realtime kernel and modules from 8.04. Download debs from here (choose the right architecture):

[http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-rt](http://packages.ubuntu.com/hardy/linux-image-2.6.24-19-rt)
[http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-19-rt](http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-19-rt)

Put them into an empty directory, cd there and say

sudo dpkg -i *.deb

Reboot the machine and choose the right kernel from the boot menu.

---

