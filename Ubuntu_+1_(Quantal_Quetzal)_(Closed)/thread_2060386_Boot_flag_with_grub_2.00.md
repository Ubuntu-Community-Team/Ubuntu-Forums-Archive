---
title: "Boot flag with grub 2.00"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-09-20
Report here the issue i got with the 1.99/2.00 grub transition on a system having two hdds:

- first that config was booting without issue with 1.99, booting on a hdd or on the other (1 pata / 1sata)

- moving to 2.00 my surprise was that the system was booting fine on a hdd but not on the other.

- after trying different bios hdd setting order, the problem was still the same.

- Looking at hdds with gparted, i've seen that the problem was with the boot flag set on the fourth partition. That fourth partition is embedded at the beginning of an extended one. So that boot flag was set at about 30 / 32 Gib of the beginning.

- setting the boot flag on the first partition, then i also can boot on that hdd.

Conclusion: grub2.0 does not like boot flag set inside an extended partition, and/or it need that flag set on the first partition. 

:p

---

