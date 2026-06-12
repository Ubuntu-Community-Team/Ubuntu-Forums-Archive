---
title: "lightdm other user option gone"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by megamaced on 2012-01-21
Hi,

Following the recent wave of updates to LightDM in Precise the option to log in as "other" user in LightDM is gone. This is needed when using something like likewise-open to log in via active directory. Currently I am using GDM as a work around but I am missing the bling of LightDM!

How can I bring back the "other" user option?

Cheers

---

### Post by ventrical on 2012-01-21
Yep .. just noticed that .. but doesn't just using "guest" represent an economic alternative?

---

### Post by dino99 on 2012-01-21
from "get Changelog": (1.1.1-0ubuntu1)

 * Drop the gtk and qt greeters packaging files from this source

---

### Post by megamaced on 2012-02-10
there is a bug report about it but it seems this is a feature. to get the other user option back, one must disable the user list and guest account in lightdm or use the gtk greeter. The other option is also supposed to become available when something other than compal is listed in nsswitch, but that doesnt work for me as mime also has likewise lsass

---

### Post by Harry33 on 2012-02-11
> **dino99 said:**
> from "get Changelog": (1.1.1-0ubuntu1)

 * Drop the gtk and qt greeters packaging files from this source

That only means the greeters are built separately from now on.
Nothing is dropped.

---

