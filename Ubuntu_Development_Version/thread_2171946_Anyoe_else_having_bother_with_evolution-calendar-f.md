---
title: "Anyoe else having bother with evolution-calendar-factory constantly running ~ 25% cp"
date: 2013-09-02
forum: Ubuntu Development Version
---

### Post by philinux on 2013-09-02
Always top of cpu list. Kill it it restarts. So stopped the process. 

Also always asking for password.

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1219805](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1219805)

---

### Post by philinux on 2013-09-02
I've identified the cause.

Would you believe it. I was caused by having seconds displayed in the clock. Unchecking seconds stopped the high cpu activity as evolution-calendar-factory went to sleep.

---

### Post by mc4man on 2013-09-02
Not those numbers but both that & indicator-datetime where using around 2.5 - 3 % each all the time here. 
In the above case was from having seconds displayed in the indicator clock so turned off, not worth the constant cpu usage

---

### Post by philinux on 2013-09-02
> **mc4man said:**
> Not those numbers but both that & indicator-datetime where using around 2.5 - 3 % each all the time here. 
In the above case was from having seconds displayed in the indicator clock so turned off, not worth the constant cpu usage

I've got seconds on in 13.04 and no problems at all.

---

### Post by mc4man on 2013-09-02
I had noticed this some time ago, turned on sec's to time barbqueue, seems a bit worse lately.
Maybe alter bug report to note about sec.'s

---

