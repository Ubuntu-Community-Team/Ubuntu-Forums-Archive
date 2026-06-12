---
title: "Using a projector"
date: 2012-11-12
forum: System76 Support
---

### Post by volkerbradley on 2012-11-12
I have a 64-bit Serval Pro with Ubuntu Precise and NVidia driver version 310.14.
I'm trying to connect my computer to an Epson PowerLite 85+ projector.  Unfortunately, the projector only has VGA cable and the laptop only has DVI out.
I connected a DVI to VGA convertor and then connected the VGA cable to the convertor.
As soon as I connect the VGA cable, the laptop screen goes blank (black). Therefore I can't detect the displays and configure them in the NVIDIA Server Settings program.   As soon as the laptop screen goes blank the projector displays the following message:
"Source; Computer 1 (Auto)
 Not supported
 H: 67.79hHz   V: 120.00 Hz"

Do you know how  to configure NVIDIA so that I could use this projector with my computer?
Thanks.

---

### Post by isantop on 2012-11-12
> **volkerbradley said:**
> I have a 64-bit Serval Pro with Ubuntu Precise and NVidia driver version 310.14.
I'm trying to connect my computer to an Epson PowerLite 85+ projector.  Unfortunately, the projector only has VGA cable and the laptop only has DVI out.
I connected a DVI to VGA convertor and then connected the VGA cable to the convertor.
As soon as I connect the VGA cable, the laptop screen goes blank (black). Therefore I can't detect the displays and configure them in the NVIDIA Server Settings program.   As soon as the laptop screen goes blank the projector displays the following message:
"Source; Computer 1 (Auto)
 Not supported
 H: 67.79hHz   V: 120.00 Hz"

Do you know how  to configure NVIDIA so that I could use this projector with my computer?
Thanks.

Can you test with the 304 version of the Nvidia driver? The 310 version is experimental, and we don't recommend using it right now.

---

### Post by volkerbradley on 2012-11-12
I installed the 304 version of the NVIDIA driver.  I then connected the DVI to VGA convertor and then made a VGA connection to a monitor rather than to the projector.  Immediately after connecting the dvi to vga conector and then a vga cable to the monitor, both the computer and the monitor screens went blank.
Interestingly, this monitor has a DVI input as well.  When I connect to the monitor with the DVI cable, I can configure NVIDIA to send the signal to the monitor.  Works perfectly with DVI.
Any other suggestions?

---

### Post by isantop on 2012-11-13
> **volkerbradley said:**
> I installed the 304 version of the NVIDIA driver.  I then connected the DVI to VGA convertor and then made a VGA connection to a monitor rather than to the projector.  Immediately after connecting the dvi to vga conector and then a vga cable to the monitor, both the computer and the monitor screens went blank.
Interestingly, this monitor has a DVI input as well.  When I connect to the monitor with the DVI cable, I can configure NVIDIA to send the signal to the monitor.  Works perfectly with DVI.
Any other suggestions?

You might consider a different adapter, as they can sometimes make a difference in the compatibility. Otherwise, converting a DVI signal to a VGA signal is really just hit or miss, and doesn't always work.

---

### Post by volkerbradley on 2012-11-14
I bought a new adapter.  It made no difference.  Still was met with blank screens.  Would be interested in seeing any post where someone mas successful using a DVI to VGA adapter.  I could not find one.

---

