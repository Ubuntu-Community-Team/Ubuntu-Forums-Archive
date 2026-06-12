---
title: "Home Server"
date: 2009-01-03
forum: Server Platforms
---

### Post by indiekid97 on 2009-01-03
Thanks in advance to al who reply :]
Note: if this is in the wrong thread, feel free to flame me 

I recently got a new box and was looking to set up my old one as a cheap home server, here are the specs: 
1.4 Ghz Athlon processor
256Mb Nvidia Geforce GPU (Forgot the model, but since its a server, I doubt it realy matters?)
1 GB of DDR2 Ram

I wanted to set it up as with an FTP capability so I could store files, but also load an SSH client so I could cue it to do something (convert video with ffmpeg , etc.) remotely.

My question to you is, would I be better off putting a regular Ubuntu install on there and just leaving it on, or should I install Ubuntu server. I've never used server before, so please forgive the newbie question

---

### Post by troyready on 2009-01-03
There really isn't a right or wrong answer. I'd probably recommend using the regular ubuntu install, then installing your server services (using synaptic or apt-get) on top of it -- as a new server user, you might like having the GUI available.

That said, configuring a service like ftp will almost certainly require command line work, so it might just be best to jump right in with the server install (I'm personally much more comfortable now with my GUI-less server).

---

### Post by cpetercarter on 2009-01-03
256Mb of RAM is rather low for a successful install of the desktop edition, but should be fine for the server edition.

---

### Post by albinootje on 2009-01-03
> **indiekid97 said:**
> 
I recently got a new box and was looking to set up my old one as a cheap home server, here are the specs: 
1.4 Ghz Athlon processor
256Mb Nvidia Geforce GPU (Forgot the model, but since its a server, I doubt it realy matters?)
1 GB of DDR2 Ram
--- cut ---
My question to you is, would I be better off putting a regular Ubuntu install on there and just leaving it on, or should I install Ubuntu server. I've never used server before, so please forgive the newbie question

The Ubuntu server installation cdrom offers a server specific kernel, and some server specific installation options.

However, after an installation from the Ubuntu server cdrom you can still do :
```

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install linux-image-generic

```
And then.. you have basically the same result as when you would have used the Ubuntu desktop installation cdrom.
Makes sense ?
In other words, no need to reinstall with the server installation cdrom.

And.. that machine is overkill for a home server :)

---

### Post by indiekid97 on 2009-01-03
Thanks to all of you :D

@troyready:
Thanks for the advice, I think I'm going to install server right off the bat, as I find myself working from a maximized terminal in the Desktop Edition all too often.

@cpetercarter:
I believe you misread, I stated that the machine had 256Mbof VRAM, not regular RAM, it has 1Gb of DDR2

@albinootje:
Again, thanks for the advice. If its overkill, do you have a better idea of what to use it for?
XD

---

### Post by albinootje on 2009-01-03
> **indiekid97 said:**
> 
@albinootje:
Again, thanks for the advice. If its overkill, do you have a better idea of what to use it for?
XD

That's totally up to you. 
It's just more than enough as a home server imho.

If I were in your shoes I would be thinking about the following :

A pentium I could probably do the same thing, and eat less electricity, but then again, you might run into BIOS-restrictions with large hard disks, and the pentium I might die sooner etc.etc.

If you really want to save energy, and if your old machine is noisy, you can buy a little box like this for your home server :
[http://www.linutop.com/linutop2/index.en.html](http://www.linutop.com/linutop2/index.en.html)
or a little Soekris machine with one usb port to have an external disk,
or a little Asus EEE box (the box, not the netbook).

In those cases your old machine could be a desktop machine elsewhere again, give it away to friends or some "good cause", as I think it's a pity about the video card to start with (If that would be my home server i'd replace the video card by some old 4 or 8 Mb video card).

Anyway, just my 2 cents :| :)

---

