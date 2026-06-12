---
title: "Monitor swap for bug follow-up / nVidia or nouveau?"
date: 2015-02-10
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-02-10
Some time within the next few days I need to perform quite a bit of follow-up testing to help squash this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602)

It affects Vivid, Utopic, and 14.04.2 (Trusty with the Utopic HWE stack). One of the big hang-ups for me is that's my HTPC (nothing fancy but I have no TV so it's my only source of entertainment aside from a small AM/FM radio) and it's also not in an ergonomic friendly location. So sometime in the next day or two I want to temporarily swap that computer into my testing suite (two PC's sharing peripherals with a KVM switch) and use another PC for streaming. I've already added some additional storage (a second hard drive) to that streaming box so I'll be able to turn it into a multi-boot box easily for testing.

I have a dumb question though :redface:

The biggest change will be going from a 21.5" widescreen monitor running @ 1920x1080 down to an 18.5" monitor running @ 1366x768. The current "stable" OS is Trusty and a recent kernel update breaks nouveau (that bug) but nvidia-current is fine. Naturally I'd like to NOT break the "stable" OS.

So if I were to boot the "stable" OS with the nvidia drivers enabled would the nvidia driver automatically handle the monitor change? Or would it be better to change to the nouveau driver before the swap? I guess the latter would be the safest way to go because I know I can boot nouveau using the "nouveau.config=NvMSI=0" boot parameter.

Any thoughts? Always better to ask a dumb question rather than make a dumb mistake, eh?

---

### Post by grahammechanical on 2015-02-10
It is my understanding that with modern digital monitors and TVs that X gets the resolution and refresh rates from information stored in the TV or monitor. It is called Extended Display Identification Data (EDID).

I do not think that you will have a problem. I have found that a VGA connection will not always allow for the highest resolutions available with modern screens. I recently switched from a digital 20 inch TV/Monitor that I used DVI to connect with to a 24 inch digital TV that did not have a DVI connector. I used VGA until I could purchase a HDMI cable to use. The VGA connection did not allow the higher resolutions possible with the new TV. The video driver and its settings manager could not make an improvement.

Regards.

---

### Post by zika on 2015-02-10
> **grahammechanical said:**
> It is my understanding that with modern digital monitors and TVs that X gets the resolution and refresh rates from information stored in the TV or monitor. It is called Extended Display Identification Data (EDID).

I do not think that you will have a problem. I have found that a VGA connection will not always allow for the highest resolutions available with modern screens. I recently switched from a digital 20 inch TV/Monitor that I used DVI to connect with to a 24 inch digital TV that did not have a DVI connector. I used VGA until I could purchase a HDMI cable to use. The VGA connection did not allow the higher resolutions possible with the new TV. The video driver and its settings manager could not make an improvement.

Regards.[https://sewelldirect.com/articles/VGA-vs-DVI.aspx](https://sewelldirect.com/articles/VGA-vs-DVI.aspx)
[http://www.digitaltrends.com/computing/hdmi-vs-dvi-vs-displayport-vs-vga/](http://www.digitaltrends.com/computing/hdmi-vs-dvi-vs-displayport-vs-vga/)

---

### Post by kansasnoob on 2015-02-10
I know I have a dual-boot usb hard drive with both i386 and amd64 versions of Ubuntu that I use for working on borked puters and I always try to keep it on open source drivers so it works on almost everything I plug it into. I'm not sure what nvidia will do - I've noticed that enabling the nvidia driver produces the equivalent of an xorg.conf but I've never had to edit anything.

I think I'll just try it and see what happens - worst case scenario would probably be the need to purge nvidia-current from CLI and reboot.

---

