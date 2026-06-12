---
title: "What is this? Gallium 0.4 on NVA5"
date: 2012-12-21
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2012-12-21
After today's update Details now says Graphics - Gallium 0.4 on NVA5.

Over the past year or so, Details has had the occasional moment of clarity when it recognised my Nvidia GT220 as a GT210. But those moments quickly passed. Usually it shows Graphics - Unknown.

Now its says Gallium 0.4 on NVA5. I am using Nouveau. And I am curious. Synaptic cannot find anything installed called Gallium.

From a little research it seems that Gallium is the bit in Nouveau that does OpenGl rendering.

From here I see that NVA5 is a code name for Nvidia GT210, GT220 and others.

[http://nouveau.freedesktop.org/wiki/CodeNames]("http://nouveau.freedesktop.org/wiki/CodeNames")

So, from now onwards let it be known that I have a NVA5. So, there!

Regards.

---

### Post by ventrical on 2012-12-21
Coincidently enough, I was troubleshooting a bug in another thread, then decided to install nouveau-firmware (to see if that would solve the problem). having nouveau now installed (and muck quicker mind you) I have the same results that you have presented.

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

---

### Post by grahammechanical on 2012-12-21
Ah! you have got an NVA8. I have only got an NVA5. :(

---

### Post by ventrical on 2012-12-21
> **grahammechanical said:**
> Ah! you have got an NVA8. I have only got an NVA5. :(


Wha!!? Isn't your adaptor a higher version than mine?

---

### Post by grahammechanical on 2012-12-21
This is confusing me even more (no surprise there!)

[http://www.xbitlabs.com/misc/picture/?src=/images/video/gf-210-gt220/gf210_220_specs.png&1=1]("http://www.xbitlabs.com/misc/picture/?src=/images/video/gf-210-gt220/gf210_220_specs.png&1=1")

The column headed GT220 has the GPU code name of GT216. Whereas the column headed GT210 has the GPU code name GT218. And the link to the code names page is taking too long to load. So, I cannot re-check that.

Response? Give UP!

---

### Post by ventrical on 2012-12-21
> **grahammechanical said:**
> This is confusing me even more (no surprise there!)

[http://www.xbitlabs.com/misc/picture/?src=/images/video/gf-210-gt220/gf210_220_specs.png&1=1](http://www.xbitlabs.com/misc/picture/?src=/images/video/gf-210-gt220/gf210_220_specs.png&1=1)

The column headed GT220 has the GPU code name of GT216. Whereas the column headed GT210 has the GPU code name GT218. And the link to the code names page is taking too long to load. So, I cannot re-check that.

Response? Give UP!

 
According to that link your card is faster/newer than mine and should get a higher rating.

Also .. the other link just will not load now for some reason. Perhaps it is an error reported.

---

### Post by ventrical on 2012-12-21
Oy vey!

---

### Post by ventrical on 2012-12-21
> **grahammechanical said:**
> This is confusing me even more (no surprise there!)

[http://www.xbitlabs.com/misc/picture/?src=/images/video/gf-210-gt220/gf210_220_specs.png&1=1](http://www.xbitlabs.com/misc/picture/?src=/images/video/gf-210-gt220/gf210_220_specs.png&1=1)

The column headed GT220 has the GPU code name of GT216. Whereas the column headed GT210 has the GPU code name GT218. And the link to the code names page is taking too long to load. So, I cannot re-check that.

Response? Give UP!

There is defintely a bug in graphics details (and erroneous details on your first link). Our graphics adaptors do not fall under the NV codenames. Please see here:

[http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units](http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units)

 I assume that the first link is outdated and that the 'details' app is drawing from a non-updated database. I stand to be corrected.

---

### Post by ventrical on 2012-12-21
There is definitely some confusion.  I finally got to the weblink you provided and took some screen shots. It says (from that link) that those code names are the nvidia official codenames but, contrarily, the link I sent up puts this claim in dispute - so then I would assume that those codenames would be referenced only to the nouveau-firmware driver.

So , which one is it?

---

### Post by ventrical on 2012-12-21
pics

---

### Post by mc4man on 2012-12-21
mesa-utils is now being default installed so that something would show in Details > Graphics depending on what driver used.

As far as nouveau it's reporting the 'on' as defined here
[http://nouveau.freedesktop.org/wiki/CodeNames](http://nouveau.freedesktop.org/wiki/CodeNames)
notabug

---

### Post by ventrical on 2012-12-21
Thanks for that . I assumed  the 'official' nvidia codes from the link I provided had not been updated  to the link that you provided but I see now that there is a different codenameing convention used.

---

### Post by grahammechanical on 2012-12-21
I have come to the conclusion that the Details page is accurately reporting the codes it is getting from the adapter. Commercial companies release hardware with slightly different specifications and at different price points. What looks like a development progression is more accurately a mixing and matching of components to supply a market.

I am glad that the details page is beginning to fully do its job. This 'graphics unknown' confuses many new users.

Regards.

---

