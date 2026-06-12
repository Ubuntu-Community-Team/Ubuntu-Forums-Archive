---
title: "how do i find a failed  disk in raid 5 array"
date: 2009-12-18
forum: Server Platforms
---

### Post by twidget on 2009-12-18
Hi,
my server just killed a drive in my raid 5 array. Does anyone know of a good way of figuring out which physical drive is the dead one so i can replace it? after i find it do i just plug in the new raw drive in its place or do i have to do some other stuff to make it be part of the array?

---

### Post by Vegan on 2009-12-18
you may have an indicator lamp on the controller

of not use smartmontools and smartctl to identify the failed drive

---

### Post by twidget on 2009-12-20
I noticed an interesting thing, my sata controller detects all three drives but mdadm lists one of the drives as being removed. could it be that mdadm lost track of a disk somehow? maybe i put a sata cable in the wrong position or something? I would like to think not but mistakes happen.on another note how bad of an idea is it to try to find the missing drive by powering down and unplugging a drive then starting up again and seeing if i see any changes when i run ```
mdadm --detail /dev/md1
```? sorry if I'm asking dumb questions but i'm new to the server side of things

---

### Post by pentas on 2009-12-20
> **twidget said:**
> I noticed an interesting thing, my sata controller detects all three drives but mdadm lists one of the drives as being removed. could it be that mdadm lost track of a disk somehow?

The SATA controller lists it because the drive is physically there and physically connected.  Mdadm shows the drive as being removed because the drive has failed in the data portions (lost data, not retrieved data, etc).

> **twidget said:**
> maybe i put a sata cable in the wrong position or something?

Highly unlikely.  The SATA cables are keyed (L shaped) so you can't put them in upside down.

> **twidget said:**
> I would like to think not but mistakes happen.on another note how bad of an idea is it to try to find the missing drive by powering down and unplugging a drive then starting up again and seeing if i see any changes when i run ```
mdadm --detail /dev/md1
```? sorry if I'm asking dumb questions but i'm new to the server side of things

NO!  Do not unplug random drives and hope to get the right one!  RAID 5 has tolerance for a single drive failure.  If one drive has already failed and you unplug a working drive, the RAID thinks that two drives have failed and the RAID collapses.  There might be a way to reconstruct it, but its not something you want to deal with, especially if you are new.

Follow vegans advice and run smartctl to list the drive serial numbers.  For example, if your failed drive is listed as: /dev/sdc, use the following command:

```
sudo smartctl -i /dev/sdc
```It should print out the drives information (model family, device model, serial number, firmware, etc).  What you need to know is the Serial Number.  Write this down, power down the system, open up the computer, and find the drive with the matching serial number.  This is your bad drive.  Remove, replace and proceed with RAID rebuilding.

---

### Post by twidget on 2009-12-20
> Highly unlikely. The SATA cables are keyed (L shaped) so you can't put them in upside down.
nah i was asking if accidentally moving one of the drive cables to a different sata connector might have caused mdadm to decide that the drive was removed.

---

### Post by twidget on 2009-12-24
just finished scanning all the drives one at a time with the manufacturers software interestingly enough none of them come up with any errors so either there was some kind of issue with software or i had a broken sata cable somewhere. its sort of academic at this point since i managed to back up everything and i'm gonna be re-installing, but it is interesting

---

