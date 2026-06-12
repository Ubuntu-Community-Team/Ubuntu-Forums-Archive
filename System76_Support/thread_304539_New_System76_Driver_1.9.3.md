---
title: "New System76 Driver 1.9.3"
date: 2006-11-21
forum: System76 Support
---

### Post by crichell on 2006-11-21
Hello Everyone - later tonight or tomorrow morning a new System76 Driver is being released.  This is a complete re-write of the driver in Python and features some new functionality.

New hardware support - Gazelle Value Card Reader

Camera Drivers for the Gazelle Performance and Serval Performance are ''still'' coming soon.

New functionality - I'm pretty excited about this one.  You can now use a standard Ubuntu installation disc and the new System76 driver to fully restore your system to factory defaults - all current System76 models are supported and both 6.06 Dapper Drake and 6.10 Edgy Eft are supported.

See the following wiki article for details:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

You only have to run the driver installer if one of the devices on the above wiki page are not working.

---

### Post by rfruth on 2006-11-22
This sounds too good to be true, do you ship a supplemental driver CD with each computer or do ya'll use a customized version of Ubuntu, is it up to each user to download the driver ?  As you know I've got my eye on a Ratel desktop (AMD 64) but you use the i386 version on it ?  Thats okay with me, just curious btw the 10 percent off is tempting :-k

---

### Post by crichell on 2006-11-22
A standard Ubuntu cd and our driver restores the system to factory defaults.  Of course the system you receive is already fully configured.  There's a link with instructions on the above wiki page.

---

### Post by ubarry on 2006-11-24
Something's amiss. I have a serval with nvidia graphics, and the driver updater appears to hang. I tried three times.

The last time, I let it run for 20 minutes. On clicking apply, the progress bar moves about one-quarter the way, and then stops. After 10 minutes there was no change. 

ps tells me that gtkfrontend.py is running, but there's no hint that any of the other scripts did run. I never saw the message 'You must reboot for changes to take effect.' 

While waiting, I had opened and moved other windows. By the time 20 minutes had gone by, the driver-installer window was mostly grayed out. I killed gtkfrontend.py and everything seems fine. 

Barry

---

### Post by crichell on 2006-11-24
barry - can you run the driver from a terminal and paste the last few lines.  On a Serval you should see the Reboot screen almost immediately after clicking the Apply button.

from terminal
> system76-driver

---

### Post by ubarry on 2006-11-28
Nope. Running from the terminal, raises the 'installing driver' window, on hitting apply, the progress bar shoots three-fourths across and stops.

Here are the message(s) from the terminal:


$ sudo system76-driver
Password:
Invalid string keyword: system-uuid
Valid string keywords are:
  bios-vendor
  bios-version
  bios-release-date
  system-manufacturer
  system-product-name
  system-version
  system-serial-number
  baseboard-manufacturer
  baseboard-product-name
  baseboard-version
  baseboard-serial-number
  baseboard-asset-tag
  chassis-manufacturer
  chassis-version
  chassis-serial-number
  chassis-asset-tag
  processor-manufacturer
  processor-version
Xlib: unexpected async reply (sequence 0x582)!

---

### Post by crichell on 2006-11-29
run the following command:

```
sudo dmidecode > ~/Desktop/serval_dmidecode.txt
```

There will be a new text file named serverl_dmidecode.txt on your desktop.  Send it over to us at support (at) system76.com

Thanks

---

### Post by asmiller-ke6seh on 2007-12-02
Any news on this, yet?

> **crichell said:**
> Posted a year and a week ago

Camera Drivers for the Gazelle Performance and Serval Performance are ''still'' coming soon.

And, from the original System76 Support Forums:

[QUOTE=ke6seh] posted on September 10, 2007:

Okay (trying a second time) two questions:

1) What is the priority on getting the camera and fingerprint reader functional on Serval Performance

2) Any idea in what quarter or semester (e.g. First Quarter 2008 or First Hal of 2008) we may see this functionality released?
[/QUOTE]

[QUOTE= thomasaaron]Responded, the same day

1. Pretty high, but still a notch or two below some serious acpi bugs. 2. We're shooting for late October / early November (i.e. after Gutsy is released). We've heard there may be some native support there that we can work with.

[/QUOTE]

---

