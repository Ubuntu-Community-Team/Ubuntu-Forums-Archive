---
title: "Scanning in Ubuntu"
date: 2010-06-19
forum: The Cafe
---

### Post by quinnten83 on 2010-06-19
Am I correct in thinking that now that Ubuntu uses simple scan they no longer use a xsane backend when scanning?
Or does that not work that way?
If they don't use xsane anymore, where can I check the compatibility of my scanner? (or what do they use now?).

---

### Post by wilee-nilee on 2010-06-19
In the terminal ```
sudo apt-get install xsane
```
It is in synaptic.

---

### Post by samjh on 2010-06-19
> **quinnten83 said:**
> Am I correct in thinking that now that Ubuntu uses simple scan they no longer use a xsane backend when scanning?
Or does that not work that way?
If they don't use xsane anymore, where can I check the compatibility of my scanner? (or what do they use now?).

XSane is a front-end GUI.  *Sane* is the back-end. :)

SimpleScan uses the Sane back-end so scanner hardware compatibility is the same as XSane.

---

### Post by quinnten83 on 2010-06-19
> **wilee-nilee said:**
> In the terminal ```
sudo apt-get install xsane
```
It is in synaptic.

well yeah, i get that, but my question was more like, is what is currently being used (if it isn't xsane) compatible with my current scanner. How do I find out if it is (short of connecting my scanner?)

---

### Post by wilee-nilee on 2010-06-19
> **quinnten83 said:**
> well yeah, i get that, but my question was more like, is what is currently being used (if it isn't xsane) compatible with my current scanner. How do I find out if it is (short of connecting my scanner?)
I don't have a scanner, so are you looking for one to purchase that is compatible? If you have one plug it in.

---

### Post by quinnten83 on 2010-06-19
> **wilee-nilee said:**
> I don't have a scanner, so are you looking for one to purchase that is compatible? If you have one plug it in.

Just did, not even detected.
But I can manually install /compile/ sacrfice a goat to get it working if Ubuntu still uses xsane backend.

although, i think i'm just gonna go with windows

---

### Post by wilee-nilee on 2010-06-19
Sane is in synaptic, but as the other posts suggests, it is the backend for what your using I assume they are correct. Look on Google with the scanner name and your distro and see what comes up. If you have windows already then that may be the easiest answer. I think generally if your using either scanner program correctly it should just work if it's going to.

---

### Post by quinnten83 on 2010-06-19
> **samjh said:**
> XSane is a front-end GUI.  *Sane* is the back-end. :)

SimpleScan uses the Sane back-end so scanner hardware compatibility is the same as XSane.

tnx dude

---

### Post by Zlatan on 2010-06-19
> **quinnten83 said:**
> Just did, not even detected.
But I can manually install /compile/ sacrfice a goat to get it working if Ubuntu still uses xsane backend.

although, i think i'm just gonna go with windows

just try to scan. simple scan does not say if it has found any scanner around there. try to scan and see if that works. it did for me with HP3055 in network.

---

