---
title: "Create a VirtualBox VM from a current install"
date: 2012-04-03
forum: Virtualisation
---

### Post by OliverHaslam on 2012-04-03
Hi,

I've got a fully working install of Ubuntu on a USB stick that I want to turn into something that I can run as a VM via Virtualbox.

Is it a case of turning the stick into an ISO and importing it?

Cheers.

---

### Post by OliverHaslam on 2012-04-03
Just to add - I'm trying to use VMWare's converter, but I am struggling at the point where I choose a destination. The app seems a bit overkill for what I want...

---

### Post by CharlesA on 2012-04-03
You can use clonezilla to close the drive and then restore it to the VM's hard drive. Not the best way to do it, I guess, but it works.

You could also try remastersys.

---

### Post by OliverHaslam on 2012-04-03
> **CharlesA said:**
> You can use clonezilla to close the drive and then restore it to the VM's hard drive. Not the best way to do it, I guess, but it works.

You could also try remastersys.

Funnily enough, I've just downloaded the Clonezilla boot disc. I'm thinking, create an ISO on one of the internal HDDs, then boot the VM into the boot disc I just made. Then, tell it to restore the ISO I made previously.

Should work, no?

---

### Post by CharlesA on 2012-04-03
That should work. You'd have to image the drive, make the ISO and then restore it that way.

---

### Post by OliverHaslam on 2012-04-03
> **CharlesA said:**
> That should work. You'd have to image the drive, make the ISO and then restore it that way.

I've not used Clonezilla. Can it just write the image straight to an ISO?

In fact, can't DD write to an ISO?

---

### Post by CharlesA on 2012-04-03
It can't do it that way. You'd have to create the image to something first, like an external drive.

Best bet would be to use remastersys imo.

---

### Post by OliverHaslam on 2012-04-03
So Remastersys would create a bootable disc that I would just throw at VMware or VirtualBox?

---

### Post by CharlesA on 2012-04-03
Yeah. It creates a bootable livecd.

---

### Post by OliverHaslam on 2012-04-04
> **CharlesA said:**
> Yeah. It creates a bootable livecd.

Does it also offer a way to copy the contents to the virtual HDD too?

---

### Post by CharlesA on 2012-04-04
> **OliverHaslam said:**
> Does it also offer a way to copy the contents to the virtual HDD too?
I believe so.

---

