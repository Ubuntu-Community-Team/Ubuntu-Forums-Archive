---
title: "I'm wondering about the earliest stage of the boot process"
date: 2020-02-15
forum: The Cafe
---

### Post by raphaell2 on 2020-02-15
My computer was put together from individual bits and pieces by the small independent computer shop where I bought it, so it doesn't really have a brand name in the conventional sense. As far as I can tell, the computer case was supplied by Exone, a German company that specializes in computers for business environments (not to be confused with the American company of the same name that sells 3D printers), and the motherboard is by Gigabyte. 

Now, what I'm wondering about is this: when I turn it on, the very first thing I see is a screen with the word "Exone" on top. Shouldn't it be "Gigabyte"? After all, the earliest stage of the bootup process is controlled by the BIOS (yes, I still have a BIOS, not a UEFI), and that, in turn, is somewhere on the motherboard. What does the *computer case* have to do with booting the computer? And what would the first screen I see after turning the computer on show if I would replace the motherboard at some time in the future? I'm confused, to be honest.

---

### Post by EuclideanCoffee on 2020-02-15
You're right. But I think your Exone case may be special, or they have provided you the Exone BIOS software instead of a generic software third party provider for Gigabyte.

I don't use Exone, but it appears they have a digital aspect to their cases. In a picture on their website, you see a case with a digital screen. The digital screen part will need to have a boot process. So it is possible that your case provider actually provides the BIOS. The BIOS is normally stored on your board. Though Gigabyte provides boards, I've worked with them enough to know that they do not provide their own BIOS in some of the models, specifically the older models I worked on as a system administrator. So it's likely that the Exone case needs a specific BIOS that they provide. The BIOS is software that you install via "flashing the board." This involves installing a firmware package and then that provides the BIOS software.

Therefore you could potentially install many different BIOS variations.

If you could send us pictures, maybe someone could further elaborate, as a lot of my thinking is speculative at this point. :)

---

### Post by TheFu on 2020-02-15
Many BIOSes the last 15+ yrs have a way to insert an OEM image to be shown during boot. In the beginning the image had to be a specific format, specific resolution and specific color limitations. These days, the BIOS can often handle BMP, GIF, PNG, and specific JPEG versions.

Hopefully, the vendor that sold the computer provided all the manuals for the MB, GPU, PSU, drives and anything else. Look inside those for specific questions.  Knowing the gigabyte MB model and revision until you are done with this computer will be very helpful.

---

### Post by raphaell2 on 2020-02-16
Thank you!


> **ruze said:**
> 
If you could send us pictures, maybe someone could further elaborate, as a lot of my thinking is speculative at this point. :)

Sure, here's the first thing I see on my screen after turning my computer on:

[https://drive.google.com/file/d/1ZIQqL9AyyoRbvo778I_Ygt6zKud-5UVJ/view?usp=sharing](https://drive.google.com/file/d/1ZIQqL9AyyoRbvo778I_Ygt6zKud-5UVJ/view?usp=sharing)

("IT für Unternehmen" is German for "IT for businesses/corporations".)


> **TheFu said:**
> Many BIOSes the last 15+ yrs have a way to insert an OEM image to be shown during boot. In the beginning the image had to be a specific format, specific resolution and specific color limitations. These days, the BIOS can often handle BMP, GIF, PNG, and specific JPEG versions.


Thank you, interesting to know. 

> Knowing the gigabyte MB model and revision until you are done with this computer will be very helpful.

It's an H61M-S2PV. I'm not sure about the revision, though.

---

### Post by TheFu on 2020-02-16
[https://www.gigabyte.com/us/Motherboard/GA-H61M-S2PV-rev-10#ov](https://www.gigabyte.com/us/Motherboard/GA-H61M-S2PV-rev-10#ov) shows there are 4 revisions. I would spend the time to figure out which revision was mind, grab the PDF manual so it was here and limit the chances of future mistakes/misunderstandings today.  The revision is usually part of the vendor Name stamp near the center of the motherboard.  For me, using a smartphone to take a flash photo is usually the easiest way to get to see it, rotate and zoom in. Usually takes about 10 attempts to get a good enough, focused, photo. ;)

Then get reading the section about  boot images and OEM stuff.

---

### Post by raphaell2 on 2020-02-16
I couldn't find a revision number anywhere on the motherboard - could that mean that it's the earliest revision, from when they didn't know for sure that there would be other revisions in the future?

---

### Post by ajgreeny on 2020-02-16
Assuming you can get into the BIOS settings with the DEL key as shown in the image you attached, you may be able to figure out which BIOS system is underneath the Exone BIOS which may help figure out many other BIOS details for you.

---

### Post by TheFu on 2020-02-16
> **raphaell2 said:**
> I couldn't find a revision number anywhere on the motherboard - could that mean that it's the earliest revision, from when they didn't know for sure that there would be other revisions in the future?

The link above has a "compare" capability.  Add each revision to the compare list and see what's different.  For example, v2.0 has an 1 x Atheros 8151 LAN chip (10/100/1000 Mbit) NIC.  If yours has that, you are done.  If it doesn't, then you've excluded the v2.0 version.

**sudo lshw** might have the revision too.

---

### Post by him610 on 2020-02-17
No need to physically inspect the motherboard. Using *inxi -F* or only *inxi -M* will display MFG, model, UEFI; vers, date, and serial (if root)
This is what mine looks like,
```

$ inxi -M
Machine:   Type: Desktop Mobo: ASRock model: B450M/ac serial: <root required> 
           UEFI: American Megatrends v: P1.50 date: 10/14/2019 

```

---

### Post by raphaell2 on 2020-02-18
> **him610 said:**
> No need to physically inspect the motherboard. Using *inxi -F* or only *inxi -M* will display MFG, model, UEFI; vers, date, and serial (if root)
This is what mine looks like,
```

$ inxi -M
Machine:   Type: Desktop Mobo: ASRock model: B450M/ac serial: <root required> 
           UEFI: American Megatrends v: P1.50 date: 10/14/2019 

```

My result for inxi -M is

```

Machine:
  Type: Desktop System: extra product: N/A v: N/A serial: <root required> 
  Mobo: Gigabyte model: H61M-S2PV v: x.x serial: <root required> 
  BIOS: American Megatrends v: FH EP date: 06/13/2013 

```

I get "x.x" as the Motherboard version with every hardware detection tool I've tried, under both Linux and Windows. I'll see if I get somewhere with the Compare function on the Gigabyte website, though. But at least the BIOS mystery has been solved.

---

### Post by TheFu on 2020-02-18
My inxi -M's for booted systems are:
```
Machine:   System: Bochs product: Bochs
Machine:   System: TAR product: T5XE CFX-SLI version: 6.0
Machine:   Mobo: Gigabyte model: H81M-HD3 v: x.x
Machine:   Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx
Machine:   System: ASUSTeK (portable) product: X510UAR v: 1.0
Machine:   No /sys/class/dmi; using dmidecode: no smbios data available. Old system?
```

The last one is a raspberry pi v3.  No bios on those.
The first one is just a sample from a VM. Most systems here run inside VMs.

---

