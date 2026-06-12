---
title: "First Time Using VirtualBox..."
date: 2010-04-14
forum: The Cafe
---

### Post by Brent0 on 2010-04-14
I'm impressed! :guitar: I am currently running Lubuntu Beta2 with Virtual Box and I'm surprised at how easy it is to set up and how fast it runs. The only thing that annoys me is the small screen size. Is there a way to make my screen a bit bigger than a netbook? :confused:

Anyway, now that I have tried it with Linux, does it work the same way with Windows? All I did with Linux was download the ISO and turn it into a virtual live CD.

---

### Post by dominiquec on 2010-04-14
Install the VirtualBox Guest Additions on your guest OS.  Then you can expand to maximum screen size by pressing Right Ctrl-F.

---

### Post by samalex on 2010-04-14
I agree, if you can get the Guest Additions installed it will add TONS of new features to your VBox install like seamlessly moving your mouse into and out of the virtual desktop.

There were some caveats getting it to work using Ubuntu 10.04 Beta 1/2 so if Lubuntu Beta2 is based on 10.04 you may have similar problems.  There's a thread someplace upstream in this forum with more info on fixing it.

But yeah, VBox is awesome!  I have about 6 operating systems installed on my laptop through it, one of which being Windows XP which I'm now running VS2010 on :)

Sam

---

### Post by WinterRain on 2010-04-14
I agree that vbox is fun to try different distros/OS's with.

---

### Post by Bachstelze on 2010-04-14
> **WinterRain said:**
> I agree that vbox is fun to try different distros/OS's with.

The fun wears out pretty quickly (unless you're RAV TUX).

---

### Post by gemmakaru on 2010-04-14
It's even more fun with compiz <giggles>.

---

### Post by samalex on 2010-04-14
> **Bachstelze said:**
> The fun wears out pretty quickly (unless you're RAV TUX).

Depends on what you consider fun...  I've installed Haiku (BeOS clone), OS/2, MS-DOS 6.2 and Win 3.11, FreeDOS, FreeBSD, OpenSolaris, various Linux distros, AROS (Amiga OS Clone), and I'm sure others.  Win XP though is probably the main app I run in VBox, plus I'm working through Linux From Scratch, though it's slow moving.

I only wish it could also emulate the PowerPC architecture so I could install Mac OS 9 or MorphOS.  I'd love to get OSX installed, but I wrote that off LONG ago given Apple is actively preventing it.  Mac OS 9 and MorphOS though I assume would work virtually given the processor and a few other devices could be emulated well enough.

Sam

---

### Post by gemmakaru on 2010-04-14
Any idea how to tell the guess oses that they can go to 1680x1050, not just 800x600?

---

### Post by Crunchy the Headcrab on 2010-04-14
It requires a registration on their website, but I've found that Vmware's free VMplayer is superior in many ways.  It uses the USB and CD-Rom so much more effectively.

---

### Post by gemmakaru on 2010-04-14
> **Crunchy the Headcrab said:**
> It requires a registration on their website, but I've found that Vmware's free VMplayer is superior in many ways.  It uses the USB and CD-Rom so much more effectively.

Thanks

---

### Post by swoll1980 on 2010-04-14
> **samalex said:**
> 

I only wish it could also emulate the PowerPC architecture so I could install Mac OS 9 or MorphOS.  I'd love to get OSX installed, but I wrote that off LONG ago given Apple is actively preventing it.  Mac OS 9 and MorphOS though I assume would work virtually given the processor and a few other devices could be emulated well enough.

Sam

You can install mac OSX in VBox. Google and ye shall find.

---

### Post by Objekt on 2010-04-14
> **gemmakaru said:**
> Any idea how to tell the guess oses that they can go to 1680x1050, not just 800x600?

Again, you'll need the Guest Additions.  The problem is that the virtual "video card" doesn't actually exist.  Therefore you cannot simply download and install video drivers, as you would with a real Windows machine.

The Guest Additions let you emulate higher screen resolutions and (very, very limited!) 3D acceleration, by providing Windows XP drivers for the virtual video card.

---

