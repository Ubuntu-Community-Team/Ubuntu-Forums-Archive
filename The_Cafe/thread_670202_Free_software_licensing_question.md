---
title: "Free software licensing question"
date: 2008-01-17
forum: The Cafe
---

### Post by Ozor Mox on 2008-01-17
Should be fairly simple...

The GNU GPL requires that the software be distributed along with the source code and a copy of the license, and anyone who further distributes must do so as well. You and I cannot change the license of the software, but the copyright holder can. So what happens if the owner decides to change the license of their software to proprietary? My understanding is that the software would become closed for all future releases under the new license, but the previous versions must remain under the GPL with source code available. If the owner changed their site to no longer contain the source code, are they in violation of previous versions of their software, or not because it is no longer open source?

Something I've been wondering about.

---

### Post by az on 2008-01-17
Yes.  But what is relevant is that anyone else who is/was interested in the project is under the obligation to distribute the code with the program.

If your project was at all worth anything, there are bound to be copies of it around.

---

### Post by RussianVodka on 2008-01-17
Doesn't Gnome only exist because a long time ago KDE said they may stop being open source?

Edit: Never mind, reread the OP. My comment is pretty irrelevent.

---

### Post by Ozor Mox on 2008-01-17
> Doesn't Gnome only exist because a long time ago KDE said they may stop being open source?

I have seen your edit, but I think it was actually that Qt (whatever that is exactly) that KDE was built on top of was originally proprietary, so Gnome was started. Qt then later became open source.

---

### Post by TBOL3 on 2008-01-17
Actually, they were both OSS, but they just used different licenses.

---

### Post by forrestcupp on 2008-01-17
To the OP:

If the creator wanted to release new versions as proprietary and stop hosting the original code, all they would have to do is stop distributing the GPL version.  Then they aren't required to host the code anymore.  They could just let the other people who have decided to distribute the GPL version have the responsibility of making the code available.

---

### Post by saulgoode on 2008-01-17
> **Ozor Mox said:**
> So what happens if the owner decides to change the license of their software to proprietary? My understanding is that the software would become closed for all future releases under the new license, but the previous versions must remain under the GPL with source code available. **If the owner changed their site to no longer contain the source code**, are they in violation of previous versions of their software, or not because it is no longer open source?

It should be noted that it is **always** permitted to share GPLed *source code* without restriction (other than retaining licensing notices and disclaimers) -- this is covered by Sections 1 and 2 of the GPL2. Obligations only come into play when *compiled binaries* are distributed. 

The part of the OP's post which I highlighted suggests the premise that the source code was originally made available at the same location as a compiled version (if no binary was distributed then no restrictions apply). This means it was being distributed under the terms of Section 3a of the GPL2 and there would be no obligation to continue hosting the source once the binary was removed from the site.

However, if a compiled version was distributed in some manner *without the source* (i.e., the website did not provide the source or CDs without source were distributed) then the source code would have to have been offered through a written offer (per the terms of GPL Section 3b). In this case it would be necessary to honor that offer for three years after distribution of the binaries ceased. This obligation would be a separate issue from that of the preceding paragraph (removing source from the website).

At least that's how I would interpret it. Most upstream developers (i.e., program authors) who release under GPL only distribute binaries as a convenient adjunct to the source (Section 3a). It is downstream distributors who would be more likely to rely upon the terms of Section 3b.

---

