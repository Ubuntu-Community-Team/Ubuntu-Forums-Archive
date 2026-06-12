---
title: "Best camera brand (photo, not webcam) for Linux users"
date: 2017-05-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Replicon on 2017-05-01
Hello,

This isn't a pure software problem per se, but I figure it's fitting, and I'm not seeing other posts about this on this site.

I'm about to get my first "fancy" camera, and as a pure Linux user, I want to make sure I don't get something that's unfriendly with my environment. For example, I'm really leery of Sony, as in my experience (not with cameras), they tend to write crappy software to go with their products, instead of just allowing me to plug it into USB and reading it like a standard drive.

I assume the big brands are generally fine (Nikon, Canon, Fuji, and... probably Sony even given what I wrote above), but just want to make sure there's nothing I'm missing.

Things I'm looking for:

[LIST]
[*]Easy transfer of files from camera to computer (should NOT require special software - I'm looking at you, Sony)
[*]Standard file format that works with the likes of darktable (not some weird esoteric custom file format that only Adobe products have written support for)
[*]Support for some kind of 'remote control' (when you have the camera plugged into laptop and can control shutter remotely, for self-portraits, etc.)
[/LIST]

I think file processing should be pretty well-covered with things like gimp and darktable, so it's mostly about finding the most linux-friendly camera.

And like I said, I'm interested in remote control stuff on my laptop, which I'm not sure if there's a good answer to. It looks like darktable has the feature, and a list of cameras it supports.

Thanks!

---

### Post by LastDino on 2017-05-01
I've Canon and it works for all 3 of the above. The only thing I've not tried is the 3rd one using my Linux as a remote control because I have a separate click device for that. Also, usually smiley detection and such a features work well for auto-detect and click from within camera, so you will probably be not needing that 3rd one tbh

Also, darktable <3 

It is surprisingly good for free stuff. You can also try GIMP for more detailed editing.

---

### Post by Replicon on 2017-05-01
Awesome, thanks for the insight!

Is there a Nikon user in the house, who can speak to these? I'm assuming Nikon is on par with Canon as far as this stuff is concerned, but if I'm going to widen my options and consider them, I'd like to know for sure it'll work... it's not cheap, after all hehe. :)

I'll definitely rent once before I buy, just to make sure.

Thanks again!

---

### Post by speedwell68 on 2017-05-01
I've got a Fujifilm that works just fine.

---

### Post by Frogs Hair on 2017-05-01
I have an olympus camera that covers the first two requirements , but I've not tried the third.

---

### Post by Geoffrey_Arndt on 2017-05-02
All these cameras use SD cards so no need to connect camera via USB.   Just pop out the card and insert to the PC SD port.   It will be seen as a mass storage device just like a usb flash-stick.    And all DSLR's use the same standard formats for files from RAW to jpeg to png, etc.    So, no problem there.   The remote control thing via a laptop is not important to me as even a smart phone can do the same via bluetooth - - but Linux software does exist for camera control (I just don't know much about it).

It's probably more important to know how to get the best camera for the $$$ . . . starter DSLR kits not especially impressive.    Even a Fuji x200 Digital Range Finder model has better/faster lens than many starter kits (and not reliant on LED display to frame shots).

---

### Post by Bucky Ball on 2017-05-03
> **Geoffrey_Arndt said:**
> All these cameras use SD cards so no need to connect camera via USB.

Exactly what I do. Transfer pics, copy to another drive so I have two copies on hard drive, wipe the card and I'm done.

Any camera that uses an SD card, in this case, is compatible with Ubuntu. The larger cards need exfat-utils and exfat-tools installed in Ubuntu. They're both in the repos so installing them takes about ... less than a minute. ;)

---

### Post by mastablasta on 2017-05-03
some cameras have wi-fi. would that work on linux?

oh and as for Sony they really like to lock you in to their own formats and their own stuff. forget about starndards when you get Sony. they used to have a few smaller things that at the time were actualyl better than at other cameras, but now their lock in practices are irritating. i mean my bro has DVD cam and it would constantly ocmplain that the inserted DVD is not Sony DVD. so ?!?! it's a standard DVD. ridiculous. then they have or at leats they had their own memorry sticks etc. etc.

SD card (or some form of it) seems to be standard these days and moving data from them to PC is easy and can be done in various ways. via USB cable or with the card inserted into the PC. if you do not have the port for memorry cards on your PC, you can buy cheap USB device for it for about 2 EUR, or install an adapter into one of the floppy drive slots (on desktop) that costs about 5 EUR here.

---

### Post by oldrocker99 on 2017-05-03
I have always used Nikon and have had zero problems using either a card reader or a direct USB connection.

---

### Post by Replicon on 2017-05-07
Thanks, everyone! I've had the chance to play with a bunch of cameras/lenses, and I've settled on Olympus.

---

### Post by cariboo on 2017-05-08
I have two Nikons, a CoolPix L310 and a D3100. both work with zero problems, I use raw images on the D3100, and every program I've tried has no problem with them.

---

### Post by carusoswi on 2018-01-27
This is an old thread, but, if I am reading it, others might.  The knock on Sony is unjustified in my view.  There is nothing so proprietary about Sony cameras that would cause them not to play nicely with Ubuntu.  Yes, my camera's each have one slot that uses the Sony memory sticks (I use 32gb cards).  No issue transferring image files to the computer.  Just insert the card into a card reader, and Ubuntu (or Windows) will recognize it as a mass storage device as with any other memory card.  The other card slot in each of my cams takes compact CompactFlash cards, a very standard (if somewhat dated) form factor.  Again, one just slips the CompactFlash card into a card reader, connect the reader to your computer via a USB card, and copy the files to the storage location of your choice.

I have a Sony Handicam for video, also.  It shipped with proprietary software for which I do not care.  No problem, slip out the memory card (this model has a slot for an SD card, but with an adapter, I can also use the small microSD card that fits in my mp3 player.  None of these card sizes are hard to find, most not that expensive, so, I feel that Sony deserves a pass on this particular criticism.

I'm glad the OP did his/her research and settled on a camera.  I don't know the Olympus products, but, in the days when film was the only choice, I used to salivate for their SLRs.  By now, the OP is likely right at home with his "new" DSLR.  I wish him and all happy shooting.

Caruso

---

### Post by corradoventu on 2018-01-29
I'm using entangle (available in Ubuntu software) to connect my Nikon d5100 with Ubuntu using  an USB cable: 
Entangle is a program used to control digital cameras that are connected to the computer via USB.
Entangle can trigger the camera shutter to capture new images. When supported by the camera, a continuously updating preview of the scene can be displayed prior to capture. Images will be downloaded and displayed as they are captured by the camera. Entangle also allows the settings of the camera to be changed from the computer.
Entangle is compatible with most DSLR cameras from Nikon and Canon, some of their compact camera models, and a variety of cameras from other manufacturers.

---

