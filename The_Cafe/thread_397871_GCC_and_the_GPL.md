---
title: "GCC and the GPL"
date: 2007-03-31
forum: The Cafe
---

### Post by samjh on 2007-03-31
Just some questions:

If a closed-source proprietary software is developed using GCC, is that breaching the GPL?

What if the software is able to be compiled using an alternative compiler (eg. Mingw, Visual C++, Intel, etc.), and is not exclusively dependent on GCC's functionality?

If the compiled binary (ie. the binary that will be sold) is built using GCC, does that bind the binary under GPL, forcing its release with GPL only?

I'm very aware that the legal issues are uncertain.  I'm legally trained and have read the GPL, but there are many ambiguities.  What is the Linux community's general view of the matter?

---

### Post by Tomosaur on 2007-03-31
You can use GCC to create closed source apps if you choose.

---

### Post by matthew on 2007-03-31
> **Tomosaur said:**
> You can use GCC to create closed source apps if you choose.This is the only view I've ever heard.

---

### Post by G Morgan on 2007-03-31
This is akin to asking if a picture developed in the GIMP must be CC licensed. The GCC is just a tool that compiles your code. That code is not a derived work (unless it linked against GCC itself). The real question is which libraries you are using. GTK is LGPL'd while QT is GPL'd, to develop a closed app for QT you need a license from Trolltech while the LGPL allows proprietary apps.

That's where you will be liable to uphold any licenses.

---

### Post by G Morgan on 2007-03-31
The most vital library (glibc) is LGPL by the way.

---

### Post by mostwanted on 2007-03-31
> **G Morgan said:**
> GTK is LGPL'd while QT is GPL'd, to develop a closed app for QT you need a license from Trolltech while the LGPL allows proprietary apps.

I never really got why Trolltech licensed Qt the way they did, but now I see it makes perfect business sense as well as being in line with the ideals of the FLOSS movement.

---

### Post by izanbardprince on 2007-03-31
Doom 3 was compiled with GCC, so my guess would be that you can create closed-source programs and compile them with it.

---

