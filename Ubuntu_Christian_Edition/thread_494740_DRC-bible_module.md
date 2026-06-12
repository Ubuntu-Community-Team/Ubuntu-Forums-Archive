---
title: "DRC-bible module"
date: 2007-07-07
forum: Ubuntu Christian Edition
---

### Post by anv on 2007-07-07
From where I can remove DRC bible module, if I try it through gnome sword or bibletime it still stays, so fastly tought it is put in somewhere in code itself, also it is not the original state when delivering Gnomesword or Bibletime that drc module would come as permanent not allowed to remove if individual wants to have different translations. even when using bible desktop it bumps there so it is inbuilt somewhere inside Ubuntu_ce itself or am I wrong?

---

### Post by mhancoc7 on 2007-07-07
> **anv said:**
> From where I can remove DRC bible module, if I try it through gnome sword or bibletime it still stays, so fastly tought it is put in somewhere in code itself, also it is not the original state when delivering Gnomesword or Bibletime that drc module would come as permanent not allowed to remove if individual wants to have different translations. even when using bible desktop it bumps there so it is inbuilt somewhere inside Ubuntu_ce itself or am I wrong?

You can do this:

```
sudo rm -rf "/usr/share/sword/modules/texts/ztext/drc"
sudo rm -rf "/usr/share/sword/mods.d/drc.conf"
```

Jereme

---

### Post by anv on 2007-07-08
I let it be, because it is possible so easily to remove.

---

### Post by califman831 on 2009-06-17
> **anv said:**
> From where I can remove DRC bible module, if I try it through gnome sword or bibletime it still stays, so fastly tought it is put in somewhere in code itself, also it is not the original state when delivering Gnomesword or Bibletime that drc module would come as permanent not allowed to remove if individual wants to have different translations. even when using bible desktop it bumps there so it is inbuilt somewhere inside Ubuntu_ce itself or am I wrong?

Why do you wish to remove the only real bible included with bibletime?  Are you a heretical protestant?  Has the module become damaged?

---

### Post by jonathonblake on 2009-06-17
> **califman831 said:**
> Why do you wish to remove the only real bible included with bibletime? 

Why are you claiming it is the only real Bible included in BibleTime. (It obviously isn't due to content.)

jonathon

---

### Post by refdoc on 2009-06-19
Apart from the rather silly comment above about heretics and "real bibles" following:

If you installed the module with synaptic then you need to remove it with synaptic. It is impossible to remove it as a normal user with the help of the module manager.

If you follow the advice of removing it by hand - you create yourself a bigger problem as the .deb package  which installed this bible module will now be broken. Not good.

Cheers

---

