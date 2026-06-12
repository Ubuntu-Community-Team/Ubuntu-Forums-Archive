---
title: "UTC time correct but 'date' ignores timezone"
date: 2009-03-20
forum: Server Platforms
---

### Post by skelooth on 2009-03-20
**[Solved]**

Hello,

Someone brought it to my attention that mysql's NOW() has been time stamping things 4 hours in the future, so I logged into my server and ran date, it gives the UTC time. I really need date and NOW() to return the GMT -4 (east coast US). 

I tried running date --set "new time", it echos out the the time I give it, but never actually alters anything. I tried googling around but haven't found anything I can use.

Any advice would be greatly appreciated.

(Things I've tried:
setting time zone with tzselect
setting date with date --set "string"
changing ntp servers
editing /etc/default/rcS to say UTC=no)

---

### Post by Wayne_V on 2009-03-20
What does 'cat /etc/timezone' say?

BTW - rcS UTC=yes just means your hardware clock is set to UTC, date should translate that to whatever /etc/timezone says.   Not an expert at MySQL -- not sure if or how now() translates to local time.

---

### Post by Wayne_V on 2009-03-20
Also, from 'man tzselect':

 Note that tzselect will not actually change the timezone for  you.  Use
       ’dpkg-reconfigure tzdata’ to achieve this.

---

### Post by skelooth on 2009-03-20
> **Wayne_V said:**
> Also, from 'man tzselect':

 Note that tzselect will not actually change the timezone for  you.  Use
       ’dpkg-reconfigure tzdata’ to achieve this.

dpkg-reconfigure tzdata did the trick. For posterity the contents of /etc/timezone was "Etc/UTC".  Thank you for helping to clear that up!

---

### Post by Dr Small on 2009-03-20
Best to setup openntpd, and sync your clock with the timeservers to eliminate problems. ;)

---

### Post by skelooth on 2009-03-20
> **Dr Small said:**
> Best to setup openntpd, and sync your clock with the timeservers to eliminate problems. ;)

Yeah, it is. NTP has nothing to do with timezone config though. ;)

---

