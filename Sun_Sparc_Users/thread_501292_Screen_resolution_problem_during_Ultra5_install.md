---
title: "Screen resolution problem during Ultra5 install"
date: 2007-07-15
forum: Sun Sparc Users
---

### Post by RazerDad on 2007-07-15
I've read a few threads detailing monitor issues but none of them appear to be like mine.

I've an Ultra 5. I tried installing ubuntu and kept getting the "Illegal instruction" message. I upgraded the OBP and set the default boot devide to be the CD and all was going well.

I get to the SILO boot screen asking me to press enter to install.

I tried just pressing enter and the installation appears to be working except after about 1 minute my monitor complains that the video mode is unsupported. This is before I saw any ubuntu installation questions / dialogs etc.

I rebooted and when prompted to press enter to install, I typed "install fb=true" as advised by a couple of threads. Absolutely no joy.. I'm not really sure what the "fb=true" does but it didn't fix my problem.

I'm now stuck. I can't tell wether the ubuntu installation is working correctly because I can't see the screen. I tried pressing enter a couple of times in the vain hope that I was responging to any questions with defaults but I couldn't hear the HD so I assumed it was stuck asking me a question I couldn't see.

I've installed ubuntu on several of my home PCs and was hoping to "upgrade" my sparc with ubuntu.

Any help would be greatly appreciated..

Thx
M.

---

### Post by RazerDad on 2007-07-15
Ok, I think I've cracked it.

It appears that, by default, the installation is trying to use 1152x960 as the screen resolution. I know this is an old Sun resolution and the monitor I was using just wasn't able to display it.

I managed to dig out an old monitor which could handle the resolution and it's busy installing as I type. Oh, and I was a bit confounded by the keyboard as I have a sun 4 keyboard yet when I used it it garbled all the keys. I read on here, though, that you have to use the generic 104 key driver and it's working fine.

Just for my own benefit, does anyone know how to set the default resolution at install time to be something other than 1152 x 960. Just so others don't fall into the same hole...

---

### Post by netztier on 2007-07-15
> **RazerDad said:**
> 

Just for my own benefit, does anyone know how to set the default resolution at install time to be something other than 1152 x 960. Just so others don't fall into the same hole...

At the OBP prompt, try:

```
**ok>** setenv output-device screen:r1024x768x60
```

Choose whatever resolution (here: 1024x768) and refresh rate (here: 60Hz) suits your monitor best.

This certainly helps during the OBP phase; I can't tell for sure what it will do to the setup/configuration screens of the Ubuntu installer, but it's worth a try.

best regards

Marc

---

### Post by RazerDad on 2007-07-15
I tried this and it didn't work. My monitor said unsupported video mode.. This is strange because obviously 1024x768x60 is a very lowly screen resolution and I'd have thought the sun video card would have been able to handle it.

---

### Post by deserthowler on 2007-07-15
It might help if you reported type monitor.  What video card?

Or if you did a google of the web to see what resolutions the monitor supports.  Sometimes Sun monitors support only very limited resolutions.

Earl

---

### Post by RazerDad on 2007-07-16
I've no idea what video card is installed my ultra5. I got it some years ago from a company I worked for who went bust. The box has 256Mb ram, 270 Mhz processor.

The three LCD monitors I used are all fairly new, all being less than 3 years old. The one which accepted the 1152 x 900 resolution was a samsung 171P. 

Funnily enough, I tried setting the output-device to r1152x900x60 and this also failed so I'm wondering if the output-device specification is wrong and that it sets itself to some wierd resolution when the output-device settings are wrong in some way.

I've tried to find documentation on the output-device settings but could find any (other than the PROM quick reference card cited elsewhere on this forum). (I admit thought that I didn't spend more than about 10 seconds looking)

M.

---

### Post by deserthowler on 2007-07-17
I think the graphics card is a PCX series by ATI.  I have one in a U10.  From what I gather they are pretty much alike.

I run Debian Etch on it.  I used it with a Gateway monitor since deceased.  I now run it headless and use it to back up my network so it's buried in a corner behind a snarl of cables.

OK, this is how I remember getting it going.  The first time I booted the machine, I held down the STOP and N keys until the Sun Logo came up.  Then I did the install and installed X.  I only downloaded the ati driver.  I went into the xorg.conf file and saw that I had a maximum available resolution of 1280x1024 (or whaterer that is) so I set the colordepth to 16 from 24 and got it.  You might have to run 

dpkg-reconfigure xserver-xorg 

to get things going.

Hope this helps.

Earl

---

### Post by RazerDad on 2007-07-17
I'm running it as a server so am not bothered about any X configuration.

My issue is that when it's booting linux it flips resolution to 1152 x 900. I would like to know if it's possible to prevent this and have it boot to a more ubiquitouis resolution, say 800 x 600 or 1024 x 768 so it wouldn't matter which monitor I plugged in.

Thx
M.

---

### Post by netztier on 2007-07-17
> **RazerDad said:**
> I'm running it as a server so am not bothered about any X configuration.

My issue is that when it's booting linux it flips resolution to 1152 x 900. I would like to know if it's possible to prevent this and have it boot to a more ubiquitouis resolution, say 800 x 600 or 1024 x 768 so it wouldn't matter which monitor I plugged in.

Thx
M.

Try passing "vga=NNN" as kernel boot option. Where at the first prompt you would hit "enter" to install (or "rescue" for the rescue system), type "install vga=NNN". Pick a number for "NNN" from this table (stolen and adapted from [http://wiki.ubuntuusers.de/Booten](http://wiki.ubuntuusers.de/Booten)).

```
**Color Depth      |    640x480      800x600      1024x768      1280x1024**
256        (8bit)|     769          771           773           775
32768     (15bit)|     784          787           790           793
65536     (16bit)|     785          788           791           794
16.7M     (24bit)|     786          789           792           795

```

*Edit: alternative source for this table: [http://en.wikipedia.org/wiki/VBE#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VBE#Linux_video_mode_numbers)*

This works on a PC and is a bliss when you drop back from X to a shell and need some "space on screen". I am not perfectly sure if this will actually work on a sun (and I can't test right now), but it might :-)


best regards

Marc

---

### Post by RazerDad on 2007-07-17
Thanks :) , I'll try that over the weekend..

---

