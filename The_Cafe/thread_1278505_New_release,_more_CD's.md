---
title: "New release, more CD's"
date: 2009-09-29
forum: The Cafe
---

### Post by renkinjutsu on 2009-09-29
Ubuntu provides a minimalistic way of installing.. (almost like Arch) in that it provides a bare system with the mini.iso image.

But it's such a shame to have to burn a 9MB iso image onto a CD..
Just a thought, but why doesn't Canonical provide img usb images instead? That way, the same USB can be reused everytime..

The usb boot disk creator doesn't work with mini iso's .. neither does unetbootin

---

### Post by LowSky on 2009-09-29
there is more than one way to get an iso made into an img. But please remember that minimal installs are geared toward thoose with older hardware, and older hardware migth not have USB but it most certainly have a CD-Rom drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by speedwell68 on 2009-09-29
Use this...

[http://ppa.launchpad.net/ogra/ubuntu/pool/main/u/usb-imagewriter/usb-imagewriter_0.1.3-0ubuntu1~intrepid~ppa1_all.deb](http://ppa.launchpad.net/ogra/ubuntu/pool/main/u/usb-imagewriter/usb-imagewriter_0.1.3-0ubuntu1~intrepid~ppa1_all.deb)

---

### Post by renkinjutsu on 2009-09-29
Doesn't that just do what `dd` does?
Even if the iso were to be written onto the USB stick, tons of alterations would have to be made to make it bootable, right?

why not make img USB images in the first place? They're as commonplace as CD's right?

---

### Post by Sean Moran on 2009-09-29
It might take a little experimentation to see if it does what you require, but Clonezilla can put an .iso onto a USB stick.  

I am nowhere near an expert on this as I've only used it for a couple of days to clone a working partition, (which it does even to the point of cloning the UUID if you like) and with an .iso image, and I am under the impression that my legacy BIOS doesn't boot from USB without the help of a manually added listing on the GRUB menu, so please don't take this advice as gospel.  

I just hope you can save a few packs of CDs if it works the way you want it.

---o0o---

Ironically enough, Clonezilla downloaded as a 107Mb .iso image and the first thing I did once it had downloaded was to burn it onto yet another blank CD, but that CD might come in handy to avoid some of the need to burn more.  It might be worth looking at as an option is all.

---

### Post by SunnyRabbiera on 2009-09-29
> **renkinjutsu said:**
> Doesn't that just do what `dd` does?
Even if the iso were to be written onto the USB stick, tons of alterations would have to be made to make it bootable, right?

why not make img USB images in the first place? They're as commonplace as CD's right?

With modern computers yes but with some older computers not so.
Most BIOS's are able to pick up CD drives, but not all of them pick up USB drives.

---

