---
title: "Support SSD by default"
date: 2011-10-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by andrewabc on 2011-10-19
Will 12.04 enable discard (TRIM) option by default when SSD detected? Or are "linux for humans" distro still require people to edit fstab?

I assume it already aligns properly using proper block size. Has to be same as page size(?), this was not done back in 2009 (it assumed everything was hard drive), so I'm not sure if that was even fixed yet.

I usually ask this for every release and either no one is sure on answers, or it turns out you still have to manually edit stuff just to get two important things done (align to page size and enable TRIM).

12.04 is LTS, hopefully it will properly support SSD.

---

### Post by MacUntu on 2011-10-20
Oneiric is the same as in Natty (and I think also in Maverick). Partitions are aligned to 1MB which is fine. 'discard' has to be added as mount option in '/etc/fstab'. Keep in mind that not all controllers are affected the same by missing TRIM, e.g. the performance hit for current gen SandForce controllers seems to be neglectable (if I remember messages in the OCZ forums right).

---

### Post by andrewabc on 2011-10-20
Why can't linux distros detect SSD and enable discard by default?

If for example a HDD is mistaken for an SSD, would discard option screw up an install to hdd? Is that the reason linux distros don't think any SSD need TRIM by default? Too dangerous to implement? Or are they just lazy?

---

