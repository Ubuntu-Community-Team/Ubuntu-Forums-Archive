---
title: "Clone VPS"
date: 2015-07-24
forum: Server Platforms
---

### Post by arnold.pietersen on 2015-07-24
Hi

Just checking.

How would I go about if I want to clone a VPS to another VPS?

Any guidance will be appreciated.

Kind Regards

ARNOLD

---

### Post by PaulW2U on 2015-07-24
For me it's just a simple process of making a snapshot and then creating a new server using that snapshot as a starting point rather than using one of the images provided by the VPS provider. I seem to remember that a few tweaks are then needed to make the second VPS unique. For instance I think you need to go through everything that refers to the VPS's hostname. But you would have to refer to any documentation issued by your VPS provider for the exact procedure or ask in any user forum that they might have.

Presumably you're wanting to have both running at the same time?

If you're wanting to clone your VPS at another provider then I doubt it can be done, there being too many variables in the way their systems are set up. Mine certainly does not allow images to be downloaded or uploaded.

Does that help? Perhaps you could tell us exactly what you're trying to do.

---

### Post by houstonbofh on 2015-07-28
As paulW2U said, "it depends."  Taring up /etc and /var/www may get you what you need, or it may not.  We need to know more about what you are doing.

---

