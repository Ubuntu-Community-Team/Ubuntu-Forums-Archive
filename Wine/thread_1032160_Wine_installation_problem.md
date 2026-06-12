---
title: "Wine installation problem"
date: 2009-01-06
forum: Wine
---

### Post by dE_logics on 2009-01-06
Ok...I decided to install wine.

While compiling it...it said it requires flex.

I downloaded flex...while compiling it, it said it requires JAVA.

I downloaded the RMP package for JAVA when on opening with the inbuilt package manage, it could not open it, and so I realised I require an RPM package manager to install it.

I downloaded the GNOME RMP package manager...which was packed in RMP format...so I again realised I NEED  a command line installer for RMP packages...so I went for the red hat packet installer.

on compiling that, it said it needs zlib and beecrypt...while zlib installed easily, beecrypt needed C++...it said 
"configure: error: C++ preprocessor "/lib/cpp" fails sanity check"

So I downloaded GCC from somewhere...which inspite of being a .deb package, failed to install with the inbuilt package manager...you know the package manager is useless, it does nothing accept saying 
"Error: dependency not satisfiable gcc-4.2-base".

So I downloaded another source code version...which on configuring says 
"configure: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+."


WHAT AM I SUPPOSE TO DO...TRY THIS FOREVER?:mad:

Now I see the reason for success of Windows...and it IS definitely a window!

---

### Post by david_kt on 2009-01-06
> **dE_logics said:**
> Ok...I decided to install wine.

While compiling it...it said it requires flex.

You just want to install, don't compile. Follow below instruction:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

DK

---

### Post by dE_logics on 2009-01-06
How stupid of me...but I possibly couldn't have navigated to "Software Sources"

Anyway...thanks...but how to use it?...it didn't make associations with .exe files at least.

---

### Post by david_kt on 2009-01-06
> **dE_logics said:**
> How stupid of me...but I possibly couldn't have navigated to "Software Sources"

Anyway...thanks...but how to use it?...it didn't make associations with .exe files at least.

Have you installed wine? If yes, right click and any exe file > choose properties > click open with tab > add > and select wine > select the radio button of wine

If wine is not listed, use custom command and type wine.

DK

---

### Post by dE_logics on 2009-01-06
I think I have to install first...of course I need to install first.

---

### Post by dE_logics on 2009-01-06
Ok...done.

Driver issue...going to support for the troublesome and good for  nothing company "Dell".

And of course the infamous 'x1270' about which ATI doesn't wanna talk

---

