---
title: "How to stop logging &quot;sdc: can't store path info&quot; error"
date: 2021-01-30
forum: Server Platforms
---

### Post by bravemosquito on 2021-01-30
Any ideas? The machine is a laptop Dell Inc. Inspiron N5110 with Ubuntu 20.04.2 LTS Server
sdc is the generic card reader of the laptop (Realtek probably)
It's not possible to disable it from the BIOS

Thanks in advance

---

### Post by bravemosquito on 2021-02-12
Anyone?

---

### Post by ameinild on 2021-02-12
An almost identical question was posted 2 days ago, and I gave a solution: [https://ubuntuforums.org/showthread.php?t=2457812](https://ubuntuforums.org/showthread.php?t=2457812)

---

### Post by bravemosquito on 2021-02-20
Ok, added the line only blacklisting "sdc" and restarted the multipath service, let's wait some hours and will reply if it's fixed or not

---

### Post by ameinild on 2021-02-21
Fine - but do you need multipath at all? If not, you can as well disable the service and blacklist all devices to prevent future syslog spamming.

---

### Post by bravemosquito on 2021-03-06
Ok, your solution works! No more 'path info' spam into logs

---

### Post by ameinild on 2021-03-06
Great to hear that - cheers!

---

