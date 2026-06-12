---
title: "truecrypt mountoptions to work with apache2"
date: 2010-12-09
forum: Security
---

### Post by nearlymagicman on 2010-12-09
Hey there,

i am taking part in an developing process of an commercial website and we use a truecrypvolume to save out progress and updates. Our local Webserver is apache2.

Unfortunately Apach2 needs "chmod" rights on the partition so it can do caching and other stuff. But even though I do mount the volume with "777" and ls -la says that everybody could do anything Apache2 still throws errors.

My second thought to mount the volume for the group of apache2 didn't have the desired effect either.
It is no option for me to mount the volume for the user "nobody" (which represents apache), because we use vpn to keep track of process and development.

Is there any way to work around that "security feature" of ubuntu, so i will be able to work with ubuntu and apache2.

---

