---
title: "Mounting a virtual blank CD-RW in VirtualBox"
date: 2010-01-28
forum: Virtualisation
---

### Post by clanmackay on 2010-01-28
OK, this may be a stupid question for reasons I don't understand, but it is possible to mount the iso of a **blank** CD-RW in VirtualBox, using the "Mount CD" function?  Is that even meaningful?

The idea is to get Windows XP in a position from which it is willing to take this .iso-file-or-whatever and **write to it**.  The end product, in my hazy hopes, would be an .iso file (chmodded correctly) on a **non** VirtualBox hard drive that, when it is ejected in XP, could be mounted loop in Ubuntu.

I have utterly no idea if I know enough to ask this question meaningfully.

Thanks!

---

### Post by fouadatmeh on 2010-01-29
Hello,
I don't know about mounting a CD-RW; but it seems you want to share files between host and guest, if so, then use the shared folders option in VirtualBox.

---

### Post by SecretCode on 2010-01-29
If you want to have XP, running under virtualbox, to write to a CD *image* ... I don't think so. But you should ask at the virtualbox forums. 

If you really want to write to a CD image. There may be other ways to do what you really want to do.

---

### Post by clanmackay on 2010-01-29
> **SecretCode said:**
> But you should ask at the virtualbox forums. 

Thank you.

> **SecretCode said:**
> If you really want to write to a CD image. There may be other ways to do what you really want to do.

No, I *really do* want to write to a CD image.  I want to use an audio program that will not run in Ubuntu, even under wine, and will not (for DRM reasons) write a file, but will allow one to burn an audio CD.  I was hoping to do this virtually, so that the CD image is actually written to an Ubuntu partition, without wasting media.

---

### Post by clanmackay on 2010-01-29
If this were iTunes or Audible there are clear workarounds, especially if one has an iPod, but unfortunately this is special-market software.

---

### Post by SecretCode on 2010-01-29
> **clanmackay said:**
> but will allow one to burn an audio CD.

Oh ... I have a bad feeling that virtualbox doesn't support even physical audio CDs.

But this is definitely something you should explore at the virtualbox forums.

---

