---
title: "Did anyone else's clock spring forward this weekend?"
date: 2012-04-02
forum: System76 Support
---

### Post by mgolden on 2012-04-02
I didn't use my Gazelle Pro over the weekend, but when I logged in this morning the clock was an hour fast.  This was odd, because it sprang forward at the correct time as well.  Could it be some BIOS thing?

---

### Post by ubuntu27 on 2012-04-02
Did you try to connect your computer to the Internet and do an system update?

When it connects to the Internet, the clock should update itself automatically.

---

### Post by isantop on 2012-04-02
Indeed. Check that the system is fully up to date. My guess is this is just a small issue with tzdata.

---

### Post by mgolden on 2012-04-03
My machine is up to date.  I seem to have tzdata 2012b-0ubuntu0.11.10 from oneiric-updates repository.

My machine wasn't (until just now) set to use network time.  I am using Kubuntu 11.10.

My question is Is the BIOS clock on these machines set to GMT or to Local time?  If the later, it could be that the BIOS has some sort of DST adjustment which might work on the old date, which was the first weekend in April.  I believe they changed it a few years ago.

---

### Post by isantop on 2012-04-03
> **mgolden said:**
> My machine is up to date.  I seem to have tzdata 2012b-0ubuntu0.11.10 from oneiric-updates repository.

My machine wasn't (until just now) set to use network time.  I am using Kubuntu 11.10.

My question is Is the BIOS clock on these machines set to GMT or to Local time?  If the later, it could be that the BIOS has some sort of DST adjustment which might work on the old date, which was the first weekend in April.  I believe they changed it a few years ago.

They are set to GMT (by default), as a standard for UNIX-like systems.

---

