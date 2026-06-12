---
title: "Partial Upgrade for Gnome Shell"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by forrestcupp on 2012-04-20
I've had this partial upgrade sitting for Gnome Shell for a couple of days. Does anyone know what's going on with this? Is it missing dependencies, or is it offering this because it's a safe replacement of a new version?

They have less than a week left, so I guess they'd better sort this out pretty soon.

---

### Post by dino99 on 2012-04-20
3.4.1-0ubuntu2 installed here on i386. maybe a dependency conflict from some ppa; try purging then reinstalling or use ppa-purge

---

### Post by kurt18947 on 2012-04-20
I'm not sure of the reason.  I updated via Synaptic.  Afterward I checked update manager and everything showed up-to-date.

---

### Post by sgage on 2012-04-20
> **dino99 said:**
> 3.4.1-0ubuntu2 installed here on i386. maybe a dependency conflict from some ppa; try purging then reinstalling

Yes, 3.4.1-0ubuntu2 installed without incident here, and is running fine. If you run Synaptic and update, it will tell you exactly what is being held back and what the problem is so you can get an idea what's going on.

---

### Post by forrestcupp on 2012-04-20
> **dino99 said:**
> 3.4.1-0ubuntu2 installed here on i386. maybe a dependency conflict from some ppa; try purging then reinstalling or use ppa-purgeI don't have the Gnome3 PPA installed. I'm only using what comes with Precise.

> **sgage said:**
> Yes, 3.4.1-0ubuntu2 installed without incident here, and is running fine. If you run Synaptic and update, it will tell you exactly what is being held back and what the problem is so you can get an idea what's going on.
It wants to remove gir1.2-gjs-1.0 and install gir1.2-gjsdbus-1.0. When I researched the dbus version, UbuntuUpdates says that package has been deleted from Precise.

I'm not accepting it until I can figure out what's going on. Any suggestions?

Edit: Never mind. It was just moved from Proposed to Universe, which seems like a good sign. I guess I'll try it out and hope for the best.

---

### Post by dino99 on 2012-04-20
> **forrestcupp said:**
> 

It wants to remove gir1.2-gjs-1.0 and install gir1.2-gjsdbus-1.0. 

its ok to accept, watch the changelog into synaptic (update-manager is really too buggy)

---

### Post by forrestcupp on 2012-04-20
Thanks guys. Everything is working fine afterwards. I guess this is one case I've found where it was ok to do a partial upgrade. I learned a lot through this.

They never should have taken Synaptic out of the default installation.

---

### Post by alphacrucis2 on 2012-04-20
> **forrestcupp said:**
> Thanks guys. Everything is working fine afterwards. I guess this is one case I've found where it was ok to do a partial upgrade. I learned a lot through this.

They never should have taken Synaptic out of the default installation.

There's been other cases during this cycle too.

---

### Post by sgage on 2012-04-20
> **forrestcupp said:**
> 
They never should have taken Synaptic out of the default installation.

I agree 100%! The first thing I do in a new installation is sudo apt-get install synaptic...

---

### Post by Quackers on 2012-04-20
> **sgage said:**
> I agree 100%! The first thing I do in a new installation is sudo apt-get install synaptic...

Same here - it's too useful to be without, imho ;)

---

### Post by forrestcupp on 2012-04-20
> **alphacrucis2 said:**
> There's been other cases during this cycle too.

I know. Earlier on, I jacked my system up to the point of having to reinstall just because of a Partial Upgrade. That's why I was trying to be *a lot* more careful this time. ;)

---

### Post by rburkartjo on 2012-04-20
yes that is also the first thing i do when testing an ubuntu release put in spm. also clueless why they took it out of the default applications.

---

### Post by jbicha on 2012-04-20
Yes, the GNOME Shell 3.4.1-0ubuntu2 upgrade is safe. We just had to rename a gjs package.

---

