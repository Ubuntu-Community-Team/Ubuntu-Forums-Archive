---
title: "Playing Oblivion with a mounted .iso"
date: 2010-08-28
forum: Wine
---

### Post by Twizlerr on 2010-08-28
I'm trying to play Oblivion with an iso file. I have tried mounting it with gISOMount and AcetoneISO. It mounts successfully, and I get to where it says "Play", but then I get an error that says: "Unable to find a CD-ROM/DVD drive on this computer." What's the problem? I'm pretty sure my disk drive works, but that shouldn't matter because the .iso is being mounted on a virtual disk.

I'm on Ubuntu 10.04, and I think my Wine is the newest version.

Thanks in advance.

---

### Post by handy on 2010-08-28
Oblivion is designed to be played with the disk in the optical drive.

Their is a NoCD/DVD patch out there for it, whether you can get it working with with Wine in your situation is another question.

These days I play Oblivion on a PS3, where the disk has to always be in the optical drive also.

---

### Post by spoons on 2010-08-28
The NoCD has worked fine for me.

EDIT: Also go into wine's config and make sure your virtual drive is on the list of drives.

---

### Post by Twizlerr on 2010-08-28
> **spoons said:**
> The NoCD has worked fine for me.

EDIT: Also go into wine's config and make sure your virtual drive is on the list of drives.
Ok. Where can you find the NoCD patch? I tried Googling it and found one at gamecopyword or something like that, but for some reason, I can't extract the .rar file. I forget what the error said, but I'll go try it again.

In Wine's config, I have a C: drive (.../drive-c) and a Z: drive(/).

EDIT: I found a different NoCD patch and I think it is working. Thanks!

---

