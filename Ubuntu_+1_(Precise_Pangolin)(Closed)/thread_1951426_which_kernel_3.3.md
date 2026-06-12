---
title: "which kernel 3.3"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mosaic2s on 2012-04-02
Will linux kernel 3.3 be available for ubuntu 12.04 sometime after launch?

---

### Post by codemaniac on 2012-04-02
Beta-2 includes the 3.2.0-20.33 Ubuntu kernel which is based on the v3.2.12 upstream stable Linux kernel. This is an update from the 3.2.0-17.27 Ubuntu kernel which shipped in Beta-1 (based on upstream stable Linux kernel v3.2.6).

Still you can compile a newer version of the kernel as it is out in the wild .

---

### Post by woxuxow on 2012-04-02
> **mosaic2s said:**
> Will linux kernel 3.3 be available for ubuntu 12.04 sometime after launch?

it will, but not by default if you want it you should compile it
linux 3.3 is good but 3.4 will be a revolution 
i`m waiting for 3.4

---

### Post by Bobhuber on 2012-04-02
I just compiled 3.4.0-rc1 and guess what ? All went fine untill I tried to install the proprietary nvidia drivers. Tried two different versions from there site with and without the previous file copy patch. No go.

---

### Post by mosaic2s on 2012-04-03
I read somewhere that linux kernel 3.3 will be same for android. hence the query.

---

### Post by xyzzyman on 2012-04-03
They are merging the kernels back together slowly, but 3.3 won't be an official kernel for 12.04. You can always get vanilla 3.3 kernels from the mainline PPA but they lack all the ubuntu "sauce" patches, break ureadahead and apparmor, etc...

---

