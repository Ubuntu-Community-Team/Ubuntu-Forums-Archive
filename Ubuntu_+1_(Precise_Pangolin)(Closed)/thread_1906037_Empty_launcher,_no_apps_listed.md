---
title: "Empty launcher, no apps listed"
date: 2012-01-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by chmac on 2012-01-08
I installed precise last night. When I press super-a there's an empty list. Nothing shows up. Screenshot attached.

Any advice on how to investigate / resolve?

---

### Post by ventrical on 2012-01-08
> **chmac said:**
> I installed precise last night. When I press super-a there's an empty list. Nothing shows up. Screenshot attached.

Any advice on how to investigate / resolve?

  I just had a weird experience today , a while back, where I was workijng on a borked install and at one point I had something similar to what you have with the exception that the unity sidebar had the lenses but no icons in them. It was weird.

  I finally  backgraded to Oneiric and then manually upgraded to Precise.

  I'm not sure if it has anything to do with your issue.

---

### Post by chmac on 2012-01-12
After FernandoMiguel's suggestion on #ubuntu+1, I tried a guest session, and all the apps are listed there. What would cause apps not to be listed for my profile only? A setting somewhere in my profile? Something wonky in my home dir? I copied my home dir from 11.04, but I didn't run the upgrade procedure, I reinstalled my root and boot partitions.

---

### Post by zika on 2012-01-12
> **chmac said:**
> I installed precise last night. When I press super-a there's an empty list. Nothing shows up. Screenshot attached.

Any advice on how to investigate / resolve?
That could happen if Zeitgeist is not installed... No matter if You do not want to use it and do not like it, it seems to be needed just for that what You want... I may be wrong...

---

### Post by chmac on 2012-01-12
Thanks for the suggestion. Looks like zeitgeist is installed, and the dash works as expected in a guest profile, so I'm guessing it's not related to a program missing but something specific in my home dir / gconf / whatever.

---

