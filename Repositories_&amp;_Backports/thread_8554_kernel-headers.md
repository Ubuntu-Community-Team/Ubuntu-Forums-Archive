---
title: "kernel-headers"
date: 2004-12-18
forum: Repositories &amp; Backports
---

### Post by Chris H on 2004-12-18
Need to install kernel-headers 2.6.8.1-3-386 so I can install nvidia graphics driver.

Problem is synaptic only shows headers available up to 2.6.7.

Have I missed something?

---

### Post by Chris H on 2004-12-18
Please ignore post.

<idiot mode>  :mrgreen:

---

### Post by GentleHatemonger on 2004-12-27
Be sure to tell the people how you figured it out:

sudo apt-get install linux-headers-2.6-386

which provides the latest available. Replace 386 with whichever processor you're using.

---

### Post by miceng on 2008-04-02
Actually the best way is to use:

sudo apt-get install linux-headers-`uname -r`

which will ensure you get the correct headers for your current kernel.

---

