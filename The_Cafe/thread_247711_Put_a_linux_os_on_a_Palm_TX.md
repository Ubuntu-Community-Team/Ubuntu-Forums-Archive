---
title: "Put a linux os on a Palm TX"
date: 2006-08-31
forum: The Cafe
---

### Post by CameronCalver on 2006-08-31
Hello i have a palm tx and i love it but i would like it if i could somehow put a linux os on it BUT
1. i would like it if i could do a hard reset at any time and i would have my palm os back on it
2. i would still like to play mpeg's mp3's ogg's jpg and gif write spread sheets etc
If this would be possible i think it would be great

---

### Post by Brunellus on 2006-08-31
I'm not aware of any effort to port Linux onto the Palm TX.

---

### Post by bruce89 on 2006-08-31
[http://www.hackndev.com/](http://www.hackndev.com/)

Mind you PalmOS in the future will run on top of Linux, with nice GTK+ stuff too.

---

### Post by TecnoVM64 on 2006-08-31
I saw it working, in one of those Linux user groups mettings :D there was a guy with a Palm TX running Debian on it, was perfectly great looking but the problem was the lack of a driver for the wireless thingy :)

---

### Post by CameronCalver on 2006-08-31
Ok that looks great but does that save on the internal memory and if you do a hard reset do you get tothe original palm tx ? and do u still get blue tooth wifi and infra red

---

### Post by TecnoVM64 on 2006-08-31
Nope, It was stored on the SD Card, he had to do something with the bootloader though, and yeah, it was something like a dual-boot between linux and palm os.
His blog is down at the moment, but he had a post about it, whenever it comes up again I'll find it :)

---

### Post by CameronCalver on 2006-09-01
ok im going to buy a 2gb sd card and then ill post back on this thread for help on how to get it set up so make sure you check your posts :p

---

### Post by rioghal on 2006-12-11
OMG! I have a Palm T|X and I'd love to be able to run Linux on it. If someone has some info or a tutorial, please post it here. I'm subscribing to this thread :D

---

### Post by bennyp on 2008-01-02
[http://forum.brighthand.com/showthread.php?t=252266](http://forum.brighthand.com/showthread.php?t=252266)

---

### Post by RodrigoRodrigues on 2008-03-14
Hi, I have a Palm TX and I use linux on it!

Its a lot better than Palm OS, but it is still beta
If you want to test, go to hackndev.com and download the miska´s last build for TX.
I work greats but there is no suport to wifi ou bluetooth, but you can connect using usb to upload packages(yes it have a package manager)

there is a version in handheld.org that may work after you do the right config (I spend some days to have a half stable system) and the Angstrom-distribution.org version in wich the hackndev kernel is based, the packages  from diferent sites wont work as should in wrong version.

I have installed gcc and g++, it gives a good help on college, and the performance is good, it also have a shellscript lib for graphic windows on bash scripts

Oh, depending on the interface you install you will use the x-server, i prefer opie, it´s a bit faster, have it´s own "x-server", its realy cool to minimize aplication to the taskbar and drag windows, something you cant imagine on palm os, serch for Opie you may find some videos

for those who are afraid to lost palm os:
the suport for recording the system on the pda rom have only some days, and none I heard about is brave enogth to test.
you can install a bootloader in you palm and switch between linux and palm on a reset (wont lose data)
or you can just install a bootloader in palm os, so you boot linux after loading palm os, you wont even touch the internal memory, just use card

but if you try linux on TX, there is an important warning i discovered the worst way

DO NOT USE THE REBOOT ON PANEL!!!
you will have to wait the baterry end to turn it on again lol

---

### Post by thundercles on 2008-04-24
Yeah, There is a large effort to port ARM-based compilations of linux onto most handhelds now. I'm running Angstrom Opie using all the binaries from the site mentioned above, and I've used a couple other kernel/WM combos from the many different embedded/mobile linux sites around and that one is by far the champ for precompiled setups. I'm in the middle of building my own kernel from source though off hackndev's git, I'm hoping to get into that USB host controller the PXA XScale 270 happens to have included and get some usb devices working with it, although I don't know if the controller is rigged up to send signals out of that port at the bottom, I was thinking the USB controller might be in the cable until I saw the specs, oh well fun times
but also a note is that in those precompiled binaries wifi does not work! so it is not yet a complete replacement for the palmOS yet, it is still a little buggy and will lock up from time to time too, but I attribute a lot of that on mine to the fact that I'm running it off the SD card instead of OBEX pushing it onto the actual internal memory. You hit the restart button on the back of the palm and it reboots right back into palmOS, as the bootloader is a palmOS application. 
The wifi might just not work because they didn't bother to compile the wifi modules when they compiled the kernel, when I trolled through their .config I noticed they left it out, I don't know if there is an issue or if they just didn't feel like testing it, so if you compile your own kernel, you can try including that module, as Opie has wifi software on it, so if the module works the way it's supposed to, and the wifi card is put in the /dev correctly, then wifi should work.
But anyone else who is running the Angstrom Opie on the TX, is it buggy and locking up a bit for you, and are you running it off the internal memory or the MMC? I'm just wondering, I assume a lot of my problems are from it going into some kind of power save mode after it's been in standby for a while which screws with it's connection to the MMC card which unfortunately is where my root is mounted, and if that's the case pushing all the binaries right onto the internal memory will make it run a lot better.
But I have a lot of good things to say about Angstrom Opie, it's top notch the handwriting recognition (I think, and I have terrible handwriting so I consider myself a good test candidate)is much better then in the palm OS, and it feels more natural. The PIM is surprisingly much better too, but there are still some bugs at least in my install and it's not a full replacement yet.

---

### Post by radioraheem on 2008-05-06
I just installed Angstrom Opie using all the prebuilt downloads above and it does run, but unfortunately not well enough to become my full time OS of choice for my TX.

Yes, I also am experiencing lockups and other problems (like some apps that just won't launch).  Thankfully the hard reset button on the back of the device seems to work without a problem.

Has anyone actually succeeded in getting wireless to work?

---

### Post by bieli on 2008-06-07
@RodrigoRodrigues:

you said, that you tapped on reboot and have to wait until battery is empty.
how long have you wait?

i think i have a similar issue, my tx doesn't reset to palm os, it's just blank and averything i try doesn't help :( 
i think my mistake was, to remove first the sd card and after that trying to reset :/ what a bullsh....uggar

---

