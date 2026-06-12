---
title: "Kvm problem in GNS3 VM"
date: 2020-03-23
forum: Virtualisation
---

### Post by mlcmadayag on 2020-03-23
Good day. I hope you can help me fix this. I'm having a problem with GNS3 VM giving this error, "kvm support available: false" even if its already have virtualization.
[ATTACH=CONFIG]285256[/ATTACH][ATTACH=CONFIG]285257[/ATTACH]

---

### Post by coffeecat on 2020-03-23
Support, not chat.

*Thread moved to the **Virtualisation** sub-forum.*

---

### Post by deadflowr on 2020-03-24
Seeing that you have Windows Task Manager in the second image I assume this is running on Windows.
If so, then you probably have Windows' hyper-v virtualization hypervisor running.
kvm is a linux hypervisor, so it wouldn't be able to run on Windows.

---

### Post by deadflowr on 2020-03-25
After thinking it over I remember that,
You can try to set it up to run nested virtualization.
See: [https://superuser.com/a/1330323]("https://superuser.com/a/1330323")

---

### Post by kevincook01 on 2020-03-25
Thank you for the responses.  It looks like this end of the pool is deeper than I had hoped.  I guess I'll be diving in and hoping I resurface.

Kevin

---

