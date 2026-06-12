---
title: "Request for GDC or DMD"
date: 2007-05-26
forum: Repositories &amp; Backports
---

### Post by samjh on 2007-05-26
Are there any plans to have the Digital Mars D compiler or the GCC D compiler in the Ubuntu repos (Feisty in particular)?

If not, could this please be considered, as D is rapidly gaining interest.  Ubuntu already provides for (arguably) less popular languages like Ada, Fortran, and Pascal with Gnat, G77, and GPC, respectively.  It would be great if GDC could be added to the repos too.

---

### Post by forcotton on 2007-05-26
From their web site, the GNU gdc does not work with gcc 4.1 yet. That's would be the problem, since ubuntu ships 4.1.

the license of Digital Mars DMD seems to be a problem for ubuntu.

---

### Post by WebDrake on 2007-06-14
> **forcotton said:**
> From their web site, the GNU gdc does not work with gcc 4.1 yet. That's would be the problem, since ubuntu ships 4.1.

the license of Digital Mars DMD seems to be a problem for ubuntu.

The website does not mention 4.1.x compatibility but the install notes for gdc 0.23 do.  They don't appear to have tested with any Debian distros though.  I'll try installing from source some time in the next couple of days and report back.

It would be nice to have in Gutsy.  What needs to be done to push this possibility?

---

### Post by predaeus on 2007-06-27
I also would like to have gdc in the repositories (especially the 64bit version).
D is too good to be neglected.

---

### Post by WebDrake on 2007-07-01
Apparently GDC will be entering Debian soon:
[http://www.digitalmars.com/d/archives/D/gnu/gdc_deb_2719.html](http://www.digitalmars.com/d/archives/D/gnu/gdc_deb_2719.html)

... so, one that could make it into 7.10?

---

### Post by smartboyathome on 2007-07-01
The debian import freeze already happened. It is unlikely this will make it into 7.10 because of that.

---

### Post by Goshawk on 2007-07-25
i started working on a gdc .deb package last year, then i was busy and i didn't finished the work.
Now i've more free time. i'll try to finish the work and include it in the next release of ubuntu (maybe gusty?) submitting it to the ubuntu MOTU.

---

