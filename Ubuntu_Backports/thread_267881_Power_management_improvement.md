---
title: "Power management improvement?"
date: 2006-09-29
forum: Ubuntu Backports
---

### Post by Duf_Sh on 2006-09-29
Hi buddies,
I don't know exactly what has changed between Dapper and Edgy, but when I upgraded to Edgy I gained 40 minutes of battery time (getting now more or less 2 hours instead of about an hour and twenty minutes in dapper on an Dell Inspiron 1100). 
I'm not requesting this on Launchpad since I don't know which packages need to be backported, but this is definitely a huge gain, that's 50% more!!! Anyway, I'm definitely convinced that someone more knowledgeable than me on this particular matter should report this on Launchpad so that the laptop users of Dapper out there could benefit from this.

---

### Post by jdong on 2006-10-01
It's a combination of work gone into all packages to remove unnecessary activity while idle (such as polling), the kernel for more efficient ACPI, and other changes, too. This would be nearly impossible to isolate for backporting.

---

