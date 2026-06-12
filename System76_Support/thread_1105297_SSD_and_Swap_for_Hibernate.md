---
title: "SSD and Swap for Hibernate"
date: 2009-03-24
forum: System76 Support
---

### Post by Cowchip7 on 2009-03-24
Would System76 computers with SSD's include a swap partition to enable hibernation? A lot of people worry about the limited write capabilities on SSD's and consequently do not include a swap partition. In fact, even netbooks with more than 30gb SSD's do not include swap. Seems a little silly to me. What do you guys think?

Thanks guys.

---

### Post by thomasaaron on 2009-03-24
We definitely include swap partitions on them now.

---

### Post by Cowchip7 on 2009-03-25
Thanks T.A. That's what I assumed. Seems silly not to allow hibernation! :P

---

### Post by AusIV4 on 2009-03-25
Can't you specify a file within your filesystem as a hibernate file, without swapping to it? That way you could have hibernation, but not be concerned about the extra frequent writes to the drive.

That said, I don't think there's really much concern. SSDs do have a technical limitation on the number of writes, but unless you're writing to them constantly day in and day out, the computer will become pretty outdated before the drive becomes unusable.

---

### Post by jdb on 2009-03-25
> **AusIV4 said:**
> Can't you specify a file within your filesystem as a hibernate file, without swapping to it? That way you could have hibernation, but not be concerned about the extra frequent writes to the drive.

That said, I don't think there's really much concern. SSDs do have a technical limitation on the number of writes, but unless you're writing to them constantly day in and day out, the computer will become pretty outdated before the drive becomes unusable.

If you have lots of memory I don't think swap gets used much except for hibernation.
I use the program "top" a lot and it usually shows 0 swap usage.
Does anyone know for sure???

jdb

---

### Post by thomasaaron on 2009-03-25
jdb,

That's correct. It's primarily for hibernation. Suspend is more popular on notebooks, though, since it is significantly faster than hibernation.

So it could be that less emphasis is being put on hibernation by some oem's, and more is being put on suspend.

---

