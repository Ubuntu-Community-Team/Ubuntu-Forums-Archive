---
title: "Any news on Low-Voltage CPU support in the kernel?"
date: 2006-10-11
forum: The Cafe
---

### Post by Spif on 2006-10-11
I have read on several websites that some of the kernel hackers are writing a patch to include support for Low-Voltage CPU's by default in the kernel, for instance Thinkpad X60/s. Seems it is only in alpha at the moment, but finding more information regarding this has been quite difficult.

Anyone know what the status of the project is or can direct me to a site where I can find out for myself?

---

### Post by prizrak on 2006-10-11
The X60 comes with an Intel Core Duo, it's been supported in the kernel since it came out. If it's x86 it's supported by the kernel (a bunch of other arch's are supported as well). Frequency scalling has always worked as well, so I'm not too sure what your question is.

---

### Post by Spif on 2006-10-11
The processor in the X60 and x60s uses a speciel Low-Voltage CPU. Core Duo works great with Linux, except for the L-V part, which makes the x60/s run a lot hotter than it is supposed to.

I am asking if anyone know how the development of this kernel patch is going.

---

### Post by Kateikyoushi on 2006-10-11
You could patch the kernel yourself to set the correct voltages.

---

