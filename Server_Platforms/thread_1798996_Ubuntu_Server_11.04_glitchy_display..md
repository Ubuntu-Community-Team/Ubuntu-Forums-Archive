---
title: "Ubuntu Server 11.04 glitchy display."
date: 2011-07-06
forum: Server Platforms
---

### Post by EvilMaxWar on 2011-07-06
Hi there 
I just installed Ubuntu Server 11.04 on a machine and i got an error about undefined video mode during install. I lets me open up a menu that lists "available" video modes.
I have installed with the same cd on another machine before and did not have this problem. See pictures:

[IMG]https://lh3.googleusercontent.com/-lppnx6co4L8/ThT8GxVv36I/AAAAAAAAAHU/nqTT5R_jYjw/s1024/P1010296.JPG[/IMG]
[IMG]https://lh4.googleusercontent.com/-C0UoS-f6PEw/ThT8PVPyB-I/AAAAAAAAAHY/1crd-f41RG0/s1024/P1010298.JPG[/IMG]

 I let it continue and the installation went all right, no problem with text display, no problem with the initial graphic Splash screen etc ...  After the install is done and i reboot the system: Everything is ok until after grub loads the OS, then here's what my terminal looks like : 

[IMG]https://lh3.googleusercontent.com/-dB9CK4kxtkY/ThT8SRbB0VI/AAAAAAAAAHc/eX4pz92nAJI/s1024/P1010299.JPG[/IMG]

I tried to "fix broken install" with the cd and tried another resolution when it prompted me the error but it dit not fix the problem. I tried to search on the net for a command that would let me switch to "basic text" mode for the console but could not find anything. 

I am installing this on a Dell Optiplex GX150 desktop, to be used as an internet Router. System uses onboard video. 
  Also to note: if instead of installing when booting from cd i choose to open a terminal, i dont have this glitch. But of course the terminal is in basic text mode instead of vga console. 

I dont mind not having VGA console, any help at this point would be very welcome as i have no clue whatsoever even after 2 hours of messing around and searching. Does not seem to be a common problem as i could not find much info about this particular problem.

Thanks in advance, Max.

---

### Post by ghormley on 2011-07-07
I have exactly the same problem when installing 11.04 server on an old HP Celeron box with very little memory.  However, installed OpenSSH and I can ssh into the box and do everything I've tried thus far.  Just cannot do ANYTHING productive from the console.  This did not happen when installing 10.04 on a similar box.

I installed from a CD created with 11.04 desktop with ISO d/l'ed from Ubuntu site.

---

### Post by ghormley on 2011-07-08
Finally got the console to boot normally in the text mode.  The secret is in the GRUB config file at /etc/default/grub.  The line below was the default:

**GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”**

I added "text" to that line as directed by several web site posts I've seen like this:

**GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”**

As it turns out, quiet causes the start-up information to be suppressed, and splash causes a GRUB graphical screen to be displayed.  Unfortunately, as I had suspected, the system did not respond to ANY graphical capability.  So, I deleted both quiet and splash resulting in the line below:

**GRUB_CMDLINE_LINUX_DEFAULT=”text”**

This worked for me.  Remember to run $*sudo grub-update* after you modify the grub file.

---

### Post by EvilMaxWar on 2011-07-13
Thanks for the lead and sorry for late reply, i had somewhat given up after a whole day with no reply to my thread. 

In  the meantime i installed ubuntu server on another machine (celeron 667)  that had some early nvidia agp card as display adapter. No problems ...

Then i switched the nvidia card for a legacy pci vga adapter (from early 90s ) 
And BAM!  Same problem. 

I tried to update GRUB in the way you suggested but unfortunately it does not work for me.
I  do get additional text informations upon boot time which leads me to  believe the grub update went well, but i still have that "smaller than  BIOS" text in the terminal instead of Good old dos-like display. When i  switch to legacy vga, problem is inevitably here.

I have several more modern cards but they all have fans on them and i dont want that, 
i plan to have this box up and running 24/24 for the next couple years, small fans are noisy and they fail. 

There must be a way to run a ubuntu server terminal on that kind of Hardware ! I do not want to have to do SSH only !

---

### Post by EvilMaxWar on 2011-07-13
I was able to change my terminal resolution to 640x480 which makes it look pretty much the same size as characters from the BIOS however that did not fix the glitchy display problem with legacy video cards. 

I scavenged an ATI wincharger from an old pentium 90 and i get same problem as with the other one. Im starting to wonder if this is not about a color issue, like its trying to force 32bit or 16bit color. 

I could not even get to see a result with VBEINFO in grub console when using the old cards, it simply gives me a black screen, but it does not crash the system as i can type a reboot command and it works. Amazingly grub console WORKS with legacy adapters, albeit in a really ugly resolution. 

Its a shame ubuntu server with such a minimal terminal interface cannot use older display hardware, i was playing warcraft 2 on a 486/ISA vga card when i was a kid....

I guess im the only one trying to run stuff on museum-piece hardware. :roll:

---

### Post by LtPitt on 2011-07-14
I don't want to be off topic but if you plan to use museum hardware and turn it into great network equipment you should check Zeroshell :)

It's lovely, easy, fast and it works on dinosaurs too:

[http://www.zeroshell.net/eng/hw/](http://www.zeroshell.net/eng/hw/)


ps
If your problem is Grub why not using lilo?

---

### Post by EvilMaxWar on 2011-07-14
Thanks for the tips, i had not thought about using lilo. I was starting to consider trying another distro however. Im still quite new to linux, installed ubuntu on my main computer 2 months ago. Since i love it and have been learning much since, i decided to use the server distro of ubuntu for my router project. First one is working great and has been up for a dozen days.  But its not such a dino computer. 

Now im having problems with older boxes. I have a collection of about 20 computers,  from 486 to Quad core. I will check Zeroshell. I would still like to find a way to fix that glitchy display as it has become personal, but i gotta move on with my life also ...

---

### Post by LudgerLinux on 2011-08-10
The thread is a bit old but maybe it will help others. With thanks to ghormley I could solve the problem. But in /etc/default/grub you must add

  **GRUB_GFXMODE=text**

This solved the problem on my very old Dell testing machine.

---

