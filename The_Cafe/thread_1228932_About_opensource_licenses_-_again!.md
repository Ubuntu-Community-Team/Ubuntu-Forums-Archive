---
title: "About opensource licenses - again!"
date: 2009-08-01
forum: The Cafe
---

### Post by adamitj on 2009-08-01
Hi folks!

I'm such a human being that doesn't understand well software licenses. I know I'm dumb when dealing with this kind of subject.

Over the years I started some Java projects and now I want to share them in opensource community. However, I want a license that allows anyone to *USE* the software (JARs and .class), even for commercial use, but allow the use and modification of the codes (.java and .sql) only for the opensource community and other opensource projects.

The question is: Should I use GPL v3 to satisfy my needs?

---

### Post by shadylookin on 2009-08-01
It should since the gpl allows anyone to use the software, but requires you to distributed the source if you distribute a derivative. Of course the only way to be sure if you read through it yourself or hire a lawyer and tell him what you want.

---

### Post by HermanAB on 2009-08-01
The FSF has a list of commonly used licences on their web site.  The LGPL may do what you want.

Hope that helps!

---

### Post by nrs on 2009-08-01
You want the LGPL.

---

### Post by Delever on 2009-08-01
My short summary:

If it is library and you want anyone* to be able to use it even with closed source projects, but want license unchanged - LGPL
If it is a program (executable), you want to allow anyone* to use it, but want license unchanged - GPL

* - commercial included

Damn, it is still not clear enough:

GPL requires those who modify your source to use the same license, and provide modified source.
If you are making library, have same requirements as with GPL, but want to be able to use your library from any program with any license, use LGPL (lesser-GPL).

---

### Post by adamitj on 2009-08-01
> **Delever said:**
> GPL requires those who modify your source to use the same license, and provide modified source.
If you are making library, have same requirements as with GPL, but want to be able to use your library from any program with any license, use LGPL (lesser-GPL).

Well... after hours reading carefully the GPL and LPGL licenses, the resume above is exactly what they mean.

In my case, I have projects which are standalone applications that should use GPL license, and others are re-distributable libraries that will be available under LGPL.

Surprisingly, I become very happy to understand that GPL doesn't prevent companies to use and modify the source code, since all their modifications must be shared with everyone (I took a long time to really understand it).

Thanks everybody for your answers!

---

