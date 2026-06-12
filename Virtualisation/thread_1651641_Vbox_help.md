---
title: "Vbox help"
date: 2010-12-23
forum: Virtualisation
---

### Post by linden940 on 2010-12-23
Ok I upgraded to vbox 4.0 on 10.10 and now its not working an I have tried everything..so after talkin with someone in IRC they said try to install linux-headers-2.6.32-25-generic 64bit ver. But the only ver i can find is for 32bit so I am hitting a brick wall here an startin to lose some hair. any ideas?

---

### Post by scradock on 2010-12-23
> **linden940 said:**
> Ok I upgraded to vbox 4.0 on 10.10 and now its not working an I have tried everything..so after talkin with someone in IRC they said try to install linux-headers-2.6.32-25-generic 64bit ver. But the only ver i can find is for 32bit so I am hitting a brick wall here an startin to lose some hair. any ideas?
What kernel are you running in 10.10? Mine is in the 2.6.35-series; the 2.6.32 series sounds like a lucid kernel to me. Adding headers that are not in-sync with your kernel probably won't help....

What is your machine running - 64-bit or 32-bit? 

I have vbox-4.0 running in Ubuntu 10.10 host, amd64 version on a dual-core athlon.

---

### Post by linden940 on 2010-12-24
> **scradock said:**
> What kernel are you running in 10.10? Mine is in the 2.6.35-series; the 2.6.32 series sounds like a lucid kernel to me. Adding headers that are not in-sync with your kernel probably won't help....

What is your machine running - 64-bit or 32-bit? 

I have vbox-4.0 running in Ubuntu 10.10 host, amd64 version on a dual-core athlon.

sorry for late reply but I got it now. What happened is like what you said for some reason I had a old kernel and it would not update *i tried* an so i took the easy path....I just poped it another drive put all my data onto it an wiped the drive an started all over. Not sure why that had happened but yea.

---

