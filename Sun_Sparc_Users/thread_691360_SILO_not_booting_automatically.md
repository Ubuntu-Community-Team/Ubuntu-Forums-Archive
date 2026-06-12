---
title: "SILO not booting automatically"
date: 2008-02-08
forum: Sun Sparc Users
---

### Post by bgervasi on 2008-02-08
I have a T5120 Sparc server running Solaris 10 with LDOMS.  I have 2 LDOMS running ubuntu gutsy.  I have modified silo.conf to boot automatically after 10secs with the timeout option.  When I boot, is stops at the   <boot:>   and waits for a return endlessly.  Am I missing something ?

---

### Post by arfonzo on 2008-02-08
Hi,

Yeah, I believe the bit you're missing is to set the system to auto-boot in OpenBoot.

You will have to set the auto-boot? variable to true in the openboot console.

- Art

---

### Post by bgervasi on 2008-02-08
autoboot is already set to true in OBP.  As mentioned it's stuck on the Boot: prompt, so it actually boots.  It is Silo which is waiting for a return.  The timeout in /etc/silo.conf is set to 10.  But does not do anything.

---

