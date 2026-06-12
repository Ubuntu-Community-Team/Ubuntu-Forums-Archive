---
title: "libgnutls13 Not updating to 2.0.4-1ubuntu2.6"
date: 2009-09-08
forum: Security
---

### Post by Tuvok41 on 2009-09-08
I have a problem with CrossOver saying I am missing libgnutls26, and I know that Hardy needs libgnutls13, so I checked and saw there was some security flaw and that I should update to 2.0.4-1ubuntu2.6 but it is not found when I try to update in terminal :

```

sudo apt-get install libgnutls13 2.0.4-1ubuntu2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnutls13 is already the newest version.
E: Couldn't find package 2.0.4-1ubuntu2.6

```
If the fix is released why is it not in the repo?

I installed the package manually and now i am updated.

---

### Post by cariboo on 2009-09-08
You won't get new packages unless you update to a newer version, most packages that have security flaws get updated, but the version number it self doesn't get changed, the only change you will see, is the Ubuntu version number at the end will get incremented

---

### Post by Tuvok41 on 2009-09-08
Thanks Cariboo, I guess I will have to upgrade sigh! Now that I have issues with this version, I think now is the time or never, btw that number never got incremented, but I did get it installed but still not working for CrossOver it still cries for the libgnutls26, I will try to down grade cx to the last version as it never did ask for that, only since i upgraded to CX Pro 8. Thanks for your reply and help it is much appreciated,

Tuvok

---

### Post by cariboo on 2009-09-08
Your welcome.

---

### Post by Bachstelze on 2009-09-09
Just upgrade your packages normally, and you will get the new version.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Tuvok41 on 2009-09-11
> **Bachstelze said:**
> Just upgrade your packages normally, and you will get the new version.

```
sudo apt-get update && sudo apt-get upgrade
```@Bachstelze : Merci!
I did try what you said and it didnt work at all, I had to replace hardy for intrepid in all the sources.list document, and now I can really say all my problems have been solved and the only issue I had after upgrade was that my NVidia configurations needs to be reconfigured everything else is doing much much better now, thx for those who took the time to post something here, hope this can help some who have had the same problem, cheers, 

A happy camper :-P

---

