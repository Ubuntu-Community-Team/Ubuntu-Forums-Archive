---
title: "REALLY old computer"
date: 2013-08-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Axxon95 on 2013-08-21
Just wanted to share this.
I finally went out to the shed with my father and looked at all of the computer parts(omg there are tons), and I found this computer completely in tact. I had to replace Windows 98 though. :p
Ubuntu 10.04 Minimal + LXDE
CPU: Intel Pentium 200MHz with MMX
RAM: 80MB SIMM
GPU: S3 Virge GX(reverted to 2.1 Software Raster but oh well)
Audio: Ensoniq AudioPCI(1370)
LAN: Realtek 8029(AS) 10Mbps
Modem: Some random Conexant 56k modem.
1x 1.44, ZIP, CD-ROM.
It even has 2 USB ports! An I/O in the back attached to internal USB connectors.

I am also taking in suggestions for other Linux distros. I am comfortable with CLI.

---

### Post by lykwydchykyn on 2013-08-21
Sounds like a good candidate for TinyCore.

I spent some time testing operating systems on an old windows 98 computer or two a few months back, and blogged about it:

[http://www.alandmoore.com/blog/2012/12/14/replacing-windows-98-and-other-seemingly-impossible-tasks/](http://www.alandmoore.com/blog/2012/12/14/replacing-windows-98-and-other-seemingly-impossible-tasks/)

There are options outside the Linux world, if you want to try some interesting things.

---

### Post by King Dude on 2013-08-21
Intel Pentium 200Mhz?! EEEEK!

---

### Post by mastablasta on 2013-08-22
actually 200mhz were quite good CPUs at the time.

what about Slitaz? should also run a bit better as it has lower sytem requirements.

DSL - though they are probably still using old kernel.

---

### Post by King Dude on 2013-08-22
> **mastablasta said:**
> actually 200mhz were quite good CPUs at the time.

Yeah, *at the time*. Now, not so much. If I were to guess the minimum processor speed requirement, it would be about 400-500Mhz. With 200Mhz I'm not sure if you can do much of anything with, even if you use a CLI environment. HOWEVER, you may be able to build a MAME Arcade machine out of the computer.

[http://mamedev.org/](http://mamedev.org/)

---

### Post by mastablasta on 2013-08-22
i think the last Mars rover has 250 mhz pentium (pIII). so it seems you can use it for soemhting else than just acrade.

edit: i was wrogn the PCU is equivalent or close to to  200-250Mhz pentium

though DOS games do run nicely on such old hardware. and there was plenty of good ones back then...

---

### Post by Axxon95 on 2013-08-22
A few days ago I had FreeDOS on it and was running a collection of DOS games, but with not a lot of audio goodness.
I originally went out into the shed to find the 2 Sound Blaster 16s we had out there but came in with 2 machines. Pentium 200MHz and K6 223MHz.
I'm probably going to have a 2 HDDs for the Pentium, for Linux and FreeDOS.

---

### Post by King Dude on 2013-08-22
> **mastablasta said:**
> i think the last Mars rover has 250 mhz pentium (pIII). so it seems you can use it for soemhting else than just acrade.

edit: i was wrogn the PCU is equivalent or close to to  200-250Mhz pentium

Yeah, but I meant as a normal user you wouldn't be able to do much of anything.

---

### Post by Erik1984 on 2013-08-22
> **mastablasta said:**
> actually 200mhz were quite good CPUs [COLOR=#ff0000]**at the time**[/COLOR].

what about Slitaz? should also run a bit better as it has lower sytem requirements.

DSL - though they are probably still using old kernel.

Highlighted the essential part :P

---

### Post by mastablasta on 2013-08-22
it could also be used as some kind of backup maschine. though probably the size of HD isn't big enough to do that. maybe as a game server for an older game :-D

---

### Post by Axxon95 on 2013-08-22
I'll try that SliTaz that was mentioned.
The computer is taunting me. As mentioned I have an AudioPCI card in it right now but they don't have DOS drivers. And I went here there and everywhere across Google(I even went past page 2 o.o) for days with nothing to show. Tried SoundBlaster compatibility... nothing.
The only way I can get DOS gaming and Audio is if I install ME.

Maybe I should go get the 486DX2 66(I think it's older than I am) I found and see if you all can suggest an OS for that? :P

---

### Post by Axxon95 on 2013-08-22
Slitaz doesn't look too bad, and it does support my older hardware(it activated i815 on an i82815 chipset and is working decent).
Back to the original machine, the kernel panics on boot because the video card is the S3 Virge and they only have FB support(no OpenGL at all). I'll play around with the boot parameters and get back.

Edit 1: If I don't find it by then, can someone inform me of the boot parameters for xvesa?

---

### Post by squakie on 2013-08-23
Any chance in all those parts there is another video card you could use that might be at least something better?Also - I don't know so I'm just throwing this out there for others to tell me no I suppose......BUT......perhaps such an old system could be used as some type of NAS (I don't know if FreeNAS or others will work on that old of hardware).

---

### Post by Axxon95 on 2013-08-23
Almost all of those old parts are 90-95, 97 at the latest.
I only have 1 working PCI video card here that is supported on 2.6 Linux and 3.x.x, I'm always swapping the card around to test OSes on different machines.
I'll test the Radeon 9200SE 128MB on a P 200MHz with 80MB RAM, just to see how the OS runs. Computer configuration is all over the place but if that's what I have to do.

---

### Post by Axxon95 on 2013-08-23
I think its a problem in between the old PnP bios and modern OSes, I even turned off the PnP bios and set my own settings.
I put the Radeon in it and still got an error of some sorts, similar to having the S3 ViRGE in. I see it normally messes up around the time it seeks for PCI cards and goes to load their modules.
I ran SliTaz on a Dell GX150(P3 1GHz, 512RAM, 32MB On-board i815), and Dimension L667R(P3 667MHz, 384MB, 8-24MB? On-board i815) and it found and activated the correct modules.
I'll probably have to keep fooling around with the boot parameters.

Edit 1.5: It almost gets to X when I put the ViRGE into the L667R machine, it gets some type of X error and locks up(num lock won't turn off, can't give any commands)

---

### Post by squakie on 2013-08-24
You actually may need to do a few steps to get the s3-virge working much at all.  First you need to install a x driver for it.  You will also need to create, depending on which release of ubuntu you are trying, either entries in the xorg.conf file or in the individual video configuration files that have been the norm for several releases now.

Not saying this link provides anything for you, but it might give you ideas:

[http://manpages.ubuntu.com/manpages/lucid/man4/s3virge.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/s3virge.4.html)

EDIT:  this would also indicate you'll need to boot to recovery mode first so you have a terminal screen and not an attempt to get X started.  From the terminal you can use apt-get to install the driver and also to modify the files as needed.

---

### Post by RadicaX on 2013-08-24
You could go straight to Debian with no DE installed. minimum recommended for that to run I believe is 60 MB of ram. Though they recommend 1 GHz of processor speed... That might not be so without a de though. But you sure would not be doing much unless you were a CLI warrior. Maybe you could install some kind of small windows manager or something that hardly needs a thing to run... but still that might be a bit much.

---

### Post by Axxon95 on 2013-08-28
I was thinking about doing Debian and adding packages manually, but my older router kept releasing and leasing IP addresses from our ISP making the internet connection unstable. We now have a brand new 200$ router that's acting right this time, so I can get around to it now. I don't have enough room to get the machine back into the house where I need it to be, so this thread is probably going to run cold for a bit. Thanks for the suggestions and such.

---

### Post by dhunt84971 on 2013-08-28
Wow!  That is really old.  I don't think you could run PuppyLinux on  that which I believe requires 256MB of RAM.  Maybe you should buy a  Raspberry Pi?  They're only $35 and they have 512mb of RAM.  If it were  me I would probably junk it.  ;)

---

### Post by mr-woof on 2013-08-29
I wonder would Crunchbang run on that?

---

### Post by Axxon95 on 2013-08-29
I refrain from junking machines that work perfectly. I can easily install an older Windows to it and make it a DOS gaming machine, but I want to fool around with Linux on it first, since I only have a few older HDDs I want to make installing Windows to it last.
And I have tried CrunchBang, and runs out of processes to kill and panics.

---

### Post by lykwydchykyn on 2013-08-30
The vast majority of Linuxes, even the so-called lightwieght ones, fall apart when you get something older than a Pentium 3 or Pentium 2.  If you want to play with some unconventional free OS's on equipment this old, you might try SyllableOS, Kolibri, Menuet, or one of the interesting FreeDOS distros like LightDOS.

Or, hey, if you want to tinker with assembly language, you can make your own respin of [MikeOS](http://mikeos.berlios.de/).

---

### Post by sudodus on 2013-08-30
> **mastablasta said:**
> actually 200mhz were quite good CPUs at the time.
...
DSL - though they are probably still using old kernel.

+1 for ***DSL***, an old kernel and old hardware drivers are perfect for such an old jewel :KS
There would be many security holes, but you are not going to use it to pay your bills anyway ;-)

+1 for ***kolibri***. It is not linux, but extremely light-weight.

You might be able to run something modern without graphics too, provided you can install it, for example the simplest system available from the Ubuntu ***mini.iso*** (basically an Ubuntu Server without any server packages installed).

---

### Post by RichardET on 2013-08-31
> **Axxon95 said:**
> Just wanted to share this.
I finally went out to the shed with my father and looked at all of the computer parts(omg there are tons), and I found this computer completely in tact. I had to replace Windows 98 though. :p
Ubuntu 10.04 Minimal + LXDE
CPU: Intel Pentium 200MHz with MMX
RAM: 80MB SIMM
GPU: S3 Virge GX(reverted to 2.1 Software Raster but oh well)
Audio: Ensoniq AudioPCI(1370)
LAN: Realtek 8029(AS) 10Mbps
Modem: Some random Conexant 56k modem.
1x 1.44, ZIP, CD-ROM.
It even has 2 USB ports! An I/O in the back attached to internal USB connectors.

I am also taking in suggestions for other Linux distros. I am comfortable with CLI.

I would go with 32 bit FreeBSD, it is cli, or OpenBSD, it includes
A minimal X server which works fine.

---

### Post by Axxon95 on 2013-08-31
BSD, TC Linux, and DSL was on my list of stuff to try.
FreeDOS works great but I get no audio support(even SoundBlaster compatibility doesn't work), Ensoniq 1370 doesn't have DOS drivers.

@Lykw With Lubuntu, I have 2 P3 machines that run great with Linux 1GHz with 512RAM and 667MHz with 384RAM. Even ran it on a laptop with a Celeron 1.somethingGHz with 256RAM.

---

### Post by RichardET on 2013-08-31
With OpenBSD 5.3, it is easy to install nano, XFCE 4.10, Firefox 3.6;  Its all you need really, and it is lightweight, stable, and a pleasure to use;  for modern equipment, where the desktop is important, I would still go with Ubuntu.

---

### Post by lykwydchykyn on 2013-09-01
> **Axxon95 said:**
> 
@Lykw With Lubuntu, I have 2 P3 machines that run great with Linux 1GHz with 512RAM and 667MHz with 384RAM. Even ran it on a laptop with a Celeron 1.somethingGHz with 256RAM.

Yeah, later P3's will do fine with a good lightweight distro if you can get the RAM up to an acceptable level.  It's when you get slower than that, things get pretty dodgy; I've got a stack of P2 machines in my workroom, and while I can get a distro (with X) on them, they aren't good for much, especially if you have better things to do with your time than wait for programs to load.  Hardware support gets hit-and-miss, too, because you start getting back into the era when there were about 17 different companies making video chipsets rather than 3.

---

