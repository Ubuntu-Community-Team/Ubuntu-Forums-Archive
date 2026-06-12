---
title: "anyway to find out if x86 or x86-64"
date: 2009-06-21
forum: Server Platforms
---

### Post by Radio91 on 2009-06-21
Is there anyway to find out which version and which architecture you version of ubuntu is?  I need to find out if its x86 or x86-64.

Its a VPS so not sure.

---

### Post by s3a on 2009-06-21
Open terminal then do:
uname -a

---

### Post by Kareeser on 2009-06-21
uname -a will return the OS version... but if you're looking for the physical capability, I use:

```
lshw -C cpu
```

i.e.
```
kareeser@machineofdeath:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Pentium(R) 4 CPU 1300MHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 15.0.10
       size: 1300MHz
       **width: 32 bits**
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
       configuration: id=0
```

---

