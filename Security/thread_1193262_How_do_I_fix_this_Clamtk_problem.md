---
title: "How do I fix this Clamtk problem?"
date: 2009-06-21
forum: Security
---

### Post by joelw135 on 2009-06-21
I am a new born Ubuntu and Clamtk user and need help. I need help that is easy as possible for me to follow. Step by step would be great. I have uploaded a screen capture of the problem. I am using Ubuntu 9.04. Thanks.:confused:

---

### Post by medic2000 on 2009-06-21
What is your exact problem?

And why are you using an antivirus program?

---

### Post by joelw135 on 2009-06-21
> **medic2000 said:**
> What is your exact problem?

And why are you using an antivirus program?

The engine is out of date.

---

### Post by cariboo on 2009-06-21
You don't really need the newer engine, as long as the definitions are up-to-date. I have to question why you need a scanner for Windows viruses though. Clamav does say it scans for Linux viruses, but there are virtually zero Linux viruses in the wild.

---

### Post by joelw135 on 2009-06-21
> **cariboo907 said:**
> You don't really need the newer engine, as long as the definitions are up-to-date. I have to question why you need a scanner for Windows viruses though. Clamav does say it scans for Linux viruses, but there are virtually zero Linux viruses in the wild.

I am not worried about the Linux OS I am concerned about the Windows OS on the partition and the system is on a mixed network. There is Mac, Ubuntu, XP and Windows server.

---

### Post by the_phenom on 2009-07-01
You have to wait for Ubuntu to release the newest version of ClamAV.

---

### Post by wojox on 2009-07-01
Easy

```
sudo apt-get remove clamtk
```

Sorry couldn't resist.

---

### Post by joelw135 on 2009-07-01
> **the_phenom said:**
> You have to wait for Ubuntu to release the newest version of ClamAV.

OK I will wait for next build.

---

