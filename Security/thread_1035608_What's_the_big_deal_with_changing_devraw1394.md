---
title: "What's the big deal with changing /dev/raw1394?"
date: 2009-01-09
forum: Security
---

### Post by thinking2loud on 2009-01-09
Can somebody explain to me--and everybody else who just 'fixes' it--what the issue is with changing the group of /dev/raw1394 from "disk" to "video" in /etc/udev/rules.d/40-permissions.rules?  Does this create a security hole that can be exploited remotely?

(P.S. for those not following multimedia, enabling access to this device to ordinary users enables applications to control camcorders)

---

### Post by Dr Small on 2009-01-10
It depends on how many users you have on your system and if you trust them with this privilege.

---

### Post by thinking2loud on 2009-01-10
Yeah, this is a personal computer.  

But the real question is how could somebody exploit this change, and what could they do after exploiting it?  Does it require a 1394 device and physical access to the machine?  Or could it be exploited remotely?

---

