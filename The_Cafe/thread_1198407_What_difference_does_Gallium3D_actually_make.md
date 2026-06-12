---
title: "What difference does Gallium3D actually make?"
date: 2009-06-27
forum: The Cafe
---

### Post by Blood//Stain//Child on 2009-06-27
I have read a lot about this, but don't actually see what huge benefit it has. 

Can someone please explain?

---

### Post by DeadSuperHero on 2009-06-27
The main benefit is that it's entirely Free Software, and as such would be a major help to both the Noveau and Radeon driver projects. ATI and Nvidia cards use a wide range of different graphics APIs across their products. (To illustrate, some ATI cards use FireGL, while others use different variations of OpenGL)

The idea is that Gallium is used as a backend as a basis for drivers so that graphics systems can be more standardized in linux.

More info here: [http://www.tungstengraphics.com/wiki/index.php/Gallium3D](http://www.tungstengraphics.com/wiki/index.php/Gallium3D)

---

### Post by Blood//Stain//Child on 2009-06-27
Does this mean that we can install Nvidia drivers through a GUI interface?

---

### Post by DeadSuperHero on 2009-06-27
Yes, but more importantly it means that drivers can be written using the same APIs, and with Free Software drivers being based on this, they can come bundled with the system. Meaning you don't even have to bother with installing them, DeviceKit will autodetect your hardware on the first run.

---

### Post by Blood//Stain//Child on 2009-06-27
> **Mr. Psychopath said:**
> Yes, but more importantly it means that drivers can be written using the same APIs, and with Free Software drivers being based on this, they can come bundled with the system. Meaning you don't even have to bother with installing them, DeviceKit will autodetect your hardware on the first run.

I see. But I will keep installing Nvidia's proprietary drivers.

---

### Post by DeadSuperHero on 2009-06-27
Hey, whatever floats your boat.

---

### Post by DaVince21 on 2009-12-03
Sorry for the necropost.

> **Blood//Stain//Child said:**
> I see. But I will keep installing Nvidia's proprietary drivers.

When Gallium3D is complete, it will be *better, faster, more complete and more stable* than any current video drivers, as well as being able to develop said drivers a lot more quickly.

---

### Post by DeadSuperHero on 2009-12-03
Not to mention, portable between 32 and 64 bit.

---

### Post by MaxIBoy on 2009-12-03
Gallium3D has an excellent design. You complete the backend as your driver, then the Gallium3D state-tracker frontends give you OpenGL, OpenCL, OpenVG, OpenGL-ES, video acceleration, even DirectX 9, all "for free." Plus your drivers will be more easily cross-platform. Wherever Gallium3D runs, your drivers will probably work as well with little adaptation.

Or at least, it will be that way when it's done.

Far as I know, Gallium3D will be better than any other driver model in existence.

---

### Post by Xbehave on 2009-12-03
> **MaxIBoy said:**
> Gallium3D has an excellent design. You complete the backend as your driver, then the Gallium3D state-tracker frontends give you OpenGL, OpenCL, OpenVG, OpenGL-ES, video acceleration, even DirectX 9, all "for free." Plus your drivers will be more easily cross-platform. Wherever Gallium3D runs, your drivers will probably work as well with little adaptation.

Or at least, it will be that way when it's done.

Far as I know, Gallium3D will be better than any other driver model in existence.
Yeah my understanding from my following of radeon drivers is that once they do Gallium3D support they get openGL,etc support without having to re-write it for each chipset, so while users probably won't notice it much drivers will get better faster :D

---

### Post by DeadSuperHero on 2009-12-03
And finally, it'll be portable to pretty much any operating system, I'd think. Suddenly, all the issues for trying a lesser-supported OS such as OpenSolaris, FreeBSD, or Haiku goes away thanks to having free quality drivers. 

And in a sick, hypothetical way, perhaps even HURD would support 3D graphics.

---

### Post by MaxIBoy on 2009-12-03
I'm hoping it gets ported to plan9, and in fact someone on the 9fans mailing list has expressed interest in doing this.

---

