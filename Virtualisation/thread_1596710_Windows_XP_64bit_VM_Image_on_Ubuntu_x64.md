---
title: "Windows XP 64bit VM Image on Ubuntu x64"
date: 2010-10-14
forum: Virtualisation
---

### Post by badguyanil on 2010-10-14
Hi all,

I have a Windows XP 64 bit vm image. I am trying to play the same in VMPlayer 3.0. It keeps throwing me the error saying:

```

Attempting to load an x64 operating system, however this CPU is not compatible with x64 mode.
```

but i am running a 64 bit Ubuntu OS 10.04 as the host. Cant figure out what is going wrong.

any help will be appreciated. :)

---

### Post by bhaverkamp on 2010-10-15
You need VT capability to run a 64 bit VM. 64 bit CPU != VT. Look up your CPU on vendor website and I am sure you will find this to be the case.

---

### Post by badguyanil on 2010-10-15
> **bhaverkamp said:**
> You need VT capability to run a 64 bit VM. 64 bit CPU != VT. Look up your CPU on vendor website and I am sure you will find this to be the case.

Yeah i have enabled VT on the BIOS settings.

---

