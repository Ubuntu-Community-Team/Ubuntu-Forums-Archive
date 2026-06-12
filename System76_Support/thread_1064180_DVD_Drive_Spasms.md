---
title: "DVD Drive Spasms"
date: 2009-02-08
forum: System76 Support
---

### Post by r4e on 2009-02-08
I bought my first System76 machine in December and have been really happy with it, so first thanks for offering high quality machines and service.

I'm using KDE 4.2 (Kubuntu 8.10) with the Pangolin Performance. I installed the System76 driver and ran the wizard to install the drivers, and rebooted.

When I put any DVD in the DVD-rom and don't have any software actively reading off the drive, the drive spazzes out. It makes the following noise:

clump, clump... clump
clump, clump... clump
clump, clump... clump
clump, clump... clump
...
...
...
(ad infinitum)

Whatever the drive is doing actually shakes the whole computer. As soon as I read the disc from VLC, any other DVD player, or mount the drive from VirtualBox, it stops doing the continuous drive seeking behavior.

It doesn't seem to do this with CD-roms.

So long as it doesn't eventually damage the drive, I think this is mostly just a nuisance. This might be an upstream problem that System76 doesn't have any control over, but it would be great if this could be fixed with the System76 driver.

Thanks,

r4e

---

### Post by thomasaaron on 2009-02-09
The System76 driver doesn't do anything to configure or enable the dvd drive, so that's definitely not the cause.

My guess is that it is either a Kubuntu or a configuration issue, as it hasn't been reported by any other customers. (Or It is conceivable that it is a drive going bad.)

I would boot from Ubuntu installed on a USB flash drive (not a live CD) and see if the problem occurs. I'd be hesitant to replace the drive on warranty without testing it on standard Ubuntu first.

We don't support Kubuntu, so if it *does* turn out to be a Kubuntu issue, it's not likely that a fix would be put into the System76 driver for it.

Also, does this happen if you put a blank DVD in the drive?

---

