---
title: "GMA X3100 vs nVidia Quadro 140M"
date: 2007-05-17
forum: The Cafe
---

### Post by maniacmusician on 2007-05-17
Some of you may have seen my thread about T61 vs Darter. I'm leaning strongly towards the T61 at this point, but I'm still pondering some of the configuration options. In particular, which GPU to get. I'm just interested in what all of you think.

**Note: ** Keep in mind that these options are for a laptop. Make your decision with all the appropriate factors in mind (battery life, weight, etc).

First up is the GMA X3100. I know that it's a step up from GMA950 (I believe the X3100 is GMA965), but how good is this GPU really? Would it be enough to satisfy you? It's advantages are better battery life, reasonable 3D performance, and a little cheaper. 

Second is the nVidia Quadro NVS 140M. This is just another card from nVidia. Powerful, but it has a negative impact on battery life. It's more expensive, of course.

Basically, I want to know if the X3100 is powerful enough for you. Is the prospect of conserving battery life more enticing than better 3D performance? Vote now!

edit: sorry, typo in poll...ignore the "system graphics" bit. Can a mod or admin fix that for me please?

---

### Post by yatt on 2007-05-17
Assuming you don't plan on doing much gaming, I'd go with the X3100. It'll run Compiz/Beryl just fine, and you shouldn't have to do any driver configuration.

EDIT :I wish I had a thousand bucks, seeing how the T61's are on sale now.

---

### Post by mips on 2007-05-18
Do you game or have heavy 3d needs ?

The X3100 will do the job in most cases.

Beware when reading reviews of the X3100 on the Windows platform. The windows driver is still crippled and does not have full support for the hardware. The Linux driver on the other hand has the hardware support windows lacks.

Some benchmarks:
[http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-X2000.2176.0.html](http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-X2000.2176.0.html)
[http://www.notebookcheck.net/Mobile-Graphics-Cards-Benchmark-List.844.0.html?&or=&search=&sort=3dmark03](http://www.notebookcheck.net/Mobile-Graphics-Cards-Benchmark-List.844.0.html?&or=&search=&sort=3dmark03)
[http://www.notebookreview.com/default.asp?newsID=3708](http://www.notebookreview.com/default.asp?newsID=3708)
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.pcwelt.de%2Ftests%2Fhardware-tests%2Fnotebooks%2F79788%2Findex10.html&langpair=de%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.pcwelt.de%2Ftests%2Fhardware-tests%2Fnotebooks%2F79788%2Findex10.html&langpair=de%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

---

### Post by cdrigby on 2007-08-04
Hello ManiacMusician,

My response is a bit dated, relative to your post. I just decided on a laptop to purchase. I'm slowly setting up a web page for it that will be ready Some Fine Day. I chose a system based on the Intel GM965/GMA X3100 because for my purposes it is indeed, "good enough". It is also supported by Intel with an open source driver (variously GPL and MIT for different parts thereof). The website is here: [http://www.intellinuxgraphics.org/]("http://www.intellinuxgraphics.org/") though I suspect you and others are already familiar with it. FWIW, I consider myself to be a Free/Open Source Software enthusiast, not a zealot, but I'll reward manufacturers that support FOSS whenever possible.

This site reviews and rates a lot of laptop video chipsets: [http://www.notebookcheck.com/]("http://www.notebookcheck.com/"). You might want to take a look there.

I have an Intel motherboard in the desktop system that has the G965 chipset with the X3000 graphics driver. It is more than sufficient for Ubuntu use, and older 3D games such as the first NeverWinter Nights work just fine if you turn off some of the more demanding video options.

I've had the new lappy, an Acer Aspire 4720-301G16 less than 24-hours, though, so I've not had a chance to do more than backup Microsoft's Vista Home Premium prior to gparted'ing myself some space for Ubuntu. Once I think I actually have things under control on this machine, I'll report back to the community with my results and observations.

Kindest Regards,
C David Rigby

---

### Post by cdrigby on 2007-08-10
Just a quick update:

Ubuntu 7.04 Feisty Fawn installs without problems on the Acer Aspire 4720-series laptop mention above, except for the graphics driver. The GMA X3100 is not recognized by the installer, and the vesa driver is substituted. Since the vesa driver apparently does not have an option for 1280x800 resolution, X.org is configured for 1024x768. This results in a distorted display that is "stretched" along the horizontal access.

So, GMA X3100 has promise, but stable support appears to be a bit in the future still. I am going to install the alpha for Gutsy Gibbon and see how that goes, since the next version includes an update intel graphics driver. The other option, discussed under the Forum's Hardware & Laptops section (for example, [here]("http://ubuntuforums.org/showthread.php?t=506744&highlight=X3100")) is to backport the driver from the Gutsy Gibbon repository.

Regards,
C David Rigby

---

### Post by firstc624 on 2007-10-17
whats the latest w/ this if you have it?

---

### Post by yatt on 2007-10-17
> **maniacmusician said:**
> Some of you may have seen my thread about T61 vs Darter. I'm leaning strongly towards the T61 at this point, but I'm still pondering some of the configuration options. In particular, which GPU to get. I'm just interested in what all of you think.

**Note: ** Keep in mind that these options are for a laptop. Make your decision with all the appropriate factors in mind (battery life, weight, etc).

First up is the GMA X3100. I know that it's a step up from GMA950 (I believe the X3100 is GMA965), but how good is this GPU really? Would it be enough to satisfy you? It's advantages are better battery life, reasonable 3D performance, and a little cheaper. 

Second is the nVidia Quadro NVS 140M. This is just another card from nVidia. Powerful, but it has a negative impact on battery life. It's more expensive, of course.

Basically, I want to know if the X3100 is powerful enough for you. Is the prospect of conserving battery life more enticing than better 3D performance? Vote now!

edit: sorry, typo in poll...ignore the "system graphics" bit. Can a mod or admin fix that for me please?I just got a Dell laptop with the Intel GMA X3100, and it can run anything I would need a laptop to run (ie Compiz Fusion). I do not expect to have to run anything intense on it, as I have a desktop for that (at the moment Debian's Xorg is too new for fglrx, so the lappy is faster). Also setup is significantly simpler, if existent. IMO, you should get the GMA unless you have a reason to justify getting a Quadro.

---

### Post by duffolonious on 2007-10-23
Does anyone have any benchmarks in Linux for this card?

LIke Half-Life2 in wine or Doom3, or any other Linux/FOSS game that you can benchmark?

I'm sick of seeing windows benchmarks that I don't trust.

Thanks.

---

### Post by zorkerz on 2007-10-28
No benchmarks here but i can report that it plays civ 4 bts nicely in vista and very poorly in ubuntu but this i attribute to wine. warcraft III also runs well in both vista and ubuntu. I have not gotten around to installing steam yet so I don't know about any more system intense games.

---

### Post by mattclary on 2007-11-03
I have installed 7.10 on a Gateway ML6720 which uses the X3100 (960GL northbridge) and the display does not work correctly. You can get the actual LCD to run at 1280x800 but the desktop runs at 1024x768. If you launch an application and maximize it, it will fill the desktop but you still see wallpaper on the bottom and right side.

If you unmaximize the app, you can drag it to the right and bottom and it display correctly.

As I said, it seems that the DESKTOP size is the problem.

---

### Post by mattclary on 2007-11-04
Found a fix...


[http://ubuntuforums.org/showpost.php?p=3473521&postcount=3](http://ubuntuforums.org/showpost.php?p=3473521&postcount=3)

---

