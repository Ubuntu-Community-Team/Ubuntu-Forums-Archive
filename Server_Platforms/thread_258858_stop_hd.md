---
title: "stop hd"
date: 2006-09-16
forum: Server Platforms
---

### Post by Compact on 2006-09-16
Is there any way to stop a hard disc when it is not used in a specific time?

---

### Post by lcg on 2006-09-16
> **Compact said:**
> Is there any way to stop a hard disc when it is not used in a specific time?
hdparm has the -S parameter to set the spin down time of a hdd.

Have a look at /etc/hdparm.conf to set options at system startup. However, the time format -S uses is pretty strange, 'man hdparm' contains an explanation of the possible numbers and their meaning.

HTH,
Lars

---

### Post by Compact on 2006-09-17
This is what I was looking for. Thank you.

---

