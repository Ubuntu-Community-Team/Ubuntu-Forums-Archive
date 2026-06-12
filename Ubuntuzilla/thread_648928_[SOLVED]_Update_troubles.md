---
title: "[SOLVED] Update troubles"
date: 2007-12-24
forum: Ubuntuzilla
---

### Post by snkiz on 2007-12-24
I little Help please, I updated my firefox form 2.0.0.10 to 2.0.0.11 by running firefox as sudo and using the bulitin update manager, and I thought while I was at it I would update my extensions as well. Now even though the extensions I updated say they are enabled they don't work. I've got a pretty good idea as to the why just not to sure how to fix it, short of reinstalling all my extensions :(

---

### Post by nanotube on 2007-12-24
> **snkiz said:**
> I little Help please, I updated my firefox form 2.0.0.10 to 2.0.0.11 by running firefox as sudo and using the bulitin update manager, and I thought while I was at it I would update my extensions as well. Now even though the extensions I updated say they are enabled they don't work. I've got a pretty good idea as to the why just not to sure how to fix it, short of reinstalling all my extensions :(

ah hmm, well, if you ran firefox as "sudo" rather than as "gksudo", that would explain it, because your extensions must have been written to your user profile with root ownership.
look in your .mozilla/firefox folder and see if there are files owned by root, probably in the extensions folder. 

as a quick fix, run a 
```
sudo chown -R yourusername:yourusername /home/yourusername/.mozilla/firefox

```
(obviously plug in your actual username instead of "yourusername" :) )

and that /i think/ should fix your extension problems.

and in the future, when you do this update, use gksudo instead of the plain sudo. :)

---

### Post by snkiz on 2007-12-25
> 
and in the future, when you do this update, use gksudo instead of the plain sudo. :)

Darn! I keep forgetting gksudo!!
I Had a feeling thats what happened, but I have trouble remembering how to order the chown command. Thanks nanotube, you are a gentleman and a scholar. Merry Christmas ( or  witch ever... Happy holidays! :) )

---

