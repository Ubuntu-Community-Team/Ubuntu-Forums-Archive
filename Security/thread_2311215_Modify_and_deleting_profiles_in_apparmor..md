---
title: "Modify and deleting profiles in apparmor."
date: 2016-01-25
forum: Security
---

### Post by juan53 on 2016-01-25
Hi
I tried to create a apparmor profile for thunderbird and I forgot include an kind of action.
Rigtnow I tried to modify the profile by using:

sudo aa-complain thunderbird

After that I tried to read logs:
cd/ var log

tail -f syslog
(console tells me that that file does not exist)

I tried too to delete the text document of the profile (in orther to create a new one) but I only can find the document.

Could you please help me?

---

### Post by haplorrhine on 2016-01-25
Do you mean edit the plain text file directly?
[https://doc.opensuse.org/documentation/html/openSUSE_121/opensuse-security/cha.apparmor.profiles.html](https://doc.opensuse.org/documentation/html/openSUSE_121/opensuse-security/cha.apparmor.profiles.html)

---

