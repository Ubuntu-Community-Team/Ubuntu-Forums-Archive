---
title: "Burnable CD or DVD"
date: 2012-10-31
forum: Ubuntu Development Version
---

### Post by thotz on 2012-10-31
When I insert a CD or DVD that is writeable and then I eject the CD or DVD and then I push it back into the drive I get an error. This already happened in Ubuntu 12.10.

---

### Post by dannyboy79 on 2012-10-31
what error do you get? also, why are you inserting it, then ejecting it, and then reinserting it again?

---

### Post by thotz on 2012-10-31
It's the problem: I insert the CD / DVD, then I erase it and Brasero ejects it and then I have to insert it again.

The error I get is in German: Translated it would mean that the CD / DVD is already mounted, so here must be something wrong.

In Ubuntu 12.04 LTS everything is fine.

---

### Post by dino99 on 2012-10-31
i've never been able to burn something without errors, but with k3b

---

### Post by thotz on 2012-10-31
> **dino99 said:**
> i've never been able to burn something without errors, but with k3b

I don't even need to burn something. I just instert a CD / DVD (thats writeable) and then I eject it and then insert it in the drive -> *error message*

I tested this with various CDs and DVDs.

This is under Unity.

In Ubuntu 12.04 LTS everything is fine with the same disks.

---

### Post by dannyboy79 on 2012-10-31
> **thotz said:**
> It's the problem: I insert the CD / DVD, then I erase it and Brasero ejects it and then I have to insert it again.

The error I get is in German: Translated it would mean that the CD / DVD is already mounted, so here must be something wrong.

In Ubuntu 12.04 LTS everything is fine.
sounds like when brasero ejects it after erasing it the system is unaware it was unmounted. you could try from a terminal 
```
sudo umount /media/cdrom
```
***replace cdrom with either cdrom0 or dvd or dvd0 whereever your optical discs get mounted

---

### Post by dannyboy79 on 2012-10-31
> **thotz said:**
> **I don't even need to burn something.** I just instert a CD / DVD (thats writeable) and then I eject it and then insert it in the drive -> *error message*

I tested this with various CDs and DVDs.

This is under Unity.

In Ubuntu 12.04 LTS everything is fine with the same disks.
sounds silly but if you don't need to burn anything then STOP putting in discs, ejecting them, then putting them back in.

Not sure what else to tell you. Sorry

---

### Post by jerome1232 on 2012-10-31
> **dannyboy79 said:**
> sounds silly but if you don't need to burn anything then STOP putting in discs, ejecting them, then putting them back in.

Not sure what else to tell you. Sorry


If I went to the doctor and told him that my back hurts when I twist like this and he told me to stop twisting like that I would get a new doctor.

Likewise the point I believe the OP is making you shouldn't be getting error messages just because you have ADHD and can't stop pressing the eject button on your optical drive.

---

### Post by cariboo on 2012-10-31
The number of times I've had a problem with Brassero, I can count on one hand. Regardless, what errors if any, are you seeing in dmesg?

---

### Post by thotz on 2012-11-01
> **cariboo907 said:**
> The number of times I've had a problem with Brassero, I can count on one hand. Regardless, what errors if any, are you seeing in dmesg?

Currently I can't give you outputs because I have other problems. Sometimes 12.10 even doesn't start.

I just want to know if someone can reproduce this on 12.10 / 13.04?

---

### Post by jerome1232 on 2012-11-01
I can't reproduce it on 12.04, although brasero spits an "error" at me every time it's done burning a disc, it's not really an error it just can't seem to figure out how to eject the burnt disc itself and pop's up an "error" asking me to press the eject button.

---

### Post by thotz on 2012-11-01
> **jerome1232 said:**
> I can't reproduce it on 12.04, although brasero spits an "error" at me every time it's done burning a disc, it's not really an error it just can't seem to figure out how to eject the burnt disc itself and pop's up an "error" asking me to press the eject button.

I have experienced this also. Strange. In 12.10 this is gone. 

Perhaps I wait for 14.04 LTS :)

---

### Post by dannyboy79 on 2012-11-02
> **jerome1232 said:**
> I can't reproduce it on 12.04, although brasero spits an "error" at me every time it's done burning a disc, it's not really an error it just can't seem to figure out how to eject the burnt disc itself and pop's up an "error" asking me to press the eject button.pffft, i have this error on 10.04 as well, i just eject it myself and close the error about ejecting dialog.

---

### Post by Chdslv on 2012-11-02
> **thotz said:**
> It's the problem: I insert the CD / DVD, then I erase it and Brasero ejects it and then I have to insert it again.

The error I get is in German: Translated it would mean that the CD / DVD is already mounted, so here must be something wrong.

In Ubuntu 12.04 LTS everything is fine.

Use K3B instead. Brasero is problematical.

---

### Post by thotz on 2012-11-03
> **Chdslv said:**
> Use K3B instead. Brasero is problematical.

The error you said you get in 10.04 or 12.04 is not reproduceable here on 12.10, but I can confirm it happened in 12.04.

---

### Post by cariboo on 2012-11-03
> **Chdslv said:**
> Use K3B instead. Brasero is problematical.

We are here to try and help solve problems with packages, using an alternate may make things work better for you, but it doesn't help solve the problem for others.

---

### Post by thotz on 2012-11-04
I just played arround a bit with mount -l and I saw that a blank CD-R or DVD-R doesn't show up here at least at my system.

---

