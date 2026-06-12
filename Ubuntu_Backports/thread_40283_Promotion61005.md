---
title: "Promotion:6/10/05"
date: 2005-06-08
forum: Ubuntu Backports
---

### Post by jdong on 2005-06-08
Let's clear out staging again...

Currently, I've edited the files for x86. ppc, please start doing so, too.

Also, you may mark packages with a "@" to delete it from the repository. There's a few backports that I don't want.


[http://ubuntubackports.org/ubp/backports-promote](http://ubuntubackports.org/ubp/backports-promote)
[http://ubuntubackports.org/ubp/extras-promote](http://ubuntubackports.org/ubp/extras-promote)


I need help from the community:
[b]
For all the commented-out lines, please tell me if they're stable or not; there's a few where I'm unsure.[/b]

---

### Post by Majlo on 2005-06-08
Blam 1.8 from staging works now perfect and is stable for me ..

---

### Post by Slo Mo Snail on 2005-06-09
Edited backports... should be ok for my stuff atm

---

### Post by RastaMahata on 2005-06-09
does the new j2sdk fix the symlink error for the browsers plugins?

---

### Post by jdong on 2005-06-10
Let's just say it prevents it from happening in the future. It doesn't reset /etc/alternatives, but it does create the symlink properly the first time.

---

### Post by jdong on 2005-06-11
Ok, sorry for the delays. After my RAID degraded, I had to replace a hard drive (go SATA...) and added another gig of RAM, requiring kernel highmem support...

I'm back in business now, and will promote this afternoon.

---

