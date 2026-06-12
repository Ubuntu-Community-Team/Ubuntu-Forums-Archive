---
title: "Ultra 10 HDD config"
date: 2007-06-05
forum: Sun Sparc Users
---

### Post by chris_andrew on 2007-06-05
Hi,

I've recently had to reconfigure the harddrive/s in my Ultra 10.  Now hen I boot, OBP is not pointing at the HDD.  I know that the jumpers etc are set correctly on my HDD, but I just need to change wherever OBP thinks my HDD is, to where it actually is.  I can't remember the command to _show_ the settings.  can anyone help?

Cheers,

Chris.

---

### Post by netztier on 2007-06-05
> **chris_andrew said:**
> Hi,

I've recently had to reconfigure the harddrive/s in my Ultra 10.  Now hen I boot, OBP is not pointing at the HDD.  I know that the jumpers etc are set correctly on my HDD, but I just need to change wherever OBP thinks my HDD is, to where it actually is.  I can't remember the command to _show_ the settings.  can anyone help?

Cheers,

Chris.

I hope I don't get busted for this ;-), But for the sake of it, I can't remember where I got it from. Get it while it's there, I'll delete it someday: [Sun OBP Quick Reference]("http://marc.spaceteddy.net/SunOBPQuickReference.pdf") card.

Other thing: does the drive have a Sun Disk label? Normally, the third partition spans the entire disk and is of a special type.. just can't remember which one by heart. But if I remember correctly, Gentoo's [Linux SPARC Handbook ]("http://www.gentoo.org/doc/en/handbook/handbook-sparc.xml") has very good information on this - and two truckloads of more info about Linux on SUNs


best regards

Marc

---

### Post by chris_andrew on 2007-06-05
Now that is a very good document.  I'm sure Sun wouldn't mind it being passed around.

Many thanks for that.  When I install Debian, it seems to put a Sun disklabel on, I can't remember whether Ubuntu does, as I usually write over it, when X won't function.

I wanted to try again, with Feisty, so I'll let you know.

Cheers,

Chris.

BTW, is it possible to install Ubuntu on a 32 bit Sparc?

---

### Post by chris_andrew on 2007-06-05
Still having problems.

I have used show-disks to tell me what the OBP detects, but am not sure what to do, next.

I'm reluctant to take the HDD out and change the jumpers, as I should learn how-to do it in the firmware.

Can anyone help?

Thanks,

Chris.

---

### Post by chris_andrew on 2007-06-05
Think I've sorted it.  OBP is sooo much better than BIOS on PC's.

I used ```
show-disks
```

I then selected the CDROM and HDD in turn, and used ```
nvalias mydevice
``` and CTRL to copy the location of the device.  Very cool.

Thanks, again.

Chris.

---

