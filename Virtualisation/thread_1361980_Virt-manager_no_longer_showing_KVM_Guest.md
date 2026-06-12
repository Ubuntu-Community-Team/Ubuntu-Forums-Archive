---
title: "Virt-manager no longer showing KVM Guest"
date: 2009-12-22
forum: Virtualisation
---

### Post by fatmcgav on 2009-12-22
Hi there, 

I've got a strange issue whereby my Virt-Manager installation no longer sees a previously valid KVM guest... 

I've double checked Group membership, file permissions, and they all look fine to me... 

I can connect to 'localhost(user)' and it becomes Active, but doesnt show the guest...

Any ideas???

Cheers
Gavin

---

### Post by xOrphenochx on 2009-12-23
Have you checked the System domain? User and System are 2 different domains, you might have created one under the other.

---

### Post by fatmcgav on 2009-12-23
> **xOrphenochx said:**
> Have you checked the System domain? User and System are 2 different domains, you might have created one under the other.

Yep, definitely not showing on either domain... :S

Any more ideas?

Cheers
Gavin

---

### Post by scottuss on 2009-12-23
Have you restarted the associated daemons? I recall this fixing a similar issue once (still not sure what happened!)

---

### Post by fatmcgav on 2009-12-23
> **scottuss said:**
> Have you restarted the associated daemons? I recall this fixing a similar issue once (still not sure what happened!)

I've rebooted several times :)

---

### Post by fatmcgav on 2009-12-29
Bump...

Any other ideas???

Cheers
Gav

---

