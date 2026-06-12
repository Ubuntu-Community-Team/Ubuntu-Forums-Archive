---
title: "Kernel 5.8.1"
date: 2020-08-14
forum: Ubuntu Development Version
---

### Post by mrfelker on 2020-08-14
Kernel 5.8.1 works fine so far with Govvy in a VMware VM.   I'm thinking of installing it on an SSD but am not sure that that even the latest VMware with the Github host modules patches works with kernel 5.8.   Anybody got that working?

---

### Post by Cavsfan on 2020-08-16
> **mrfelker said:**
> Kernel 5.8.1 works fine so far with Govvy in a VMware VM.   I'm thinking of installing it on an SSD but am not sure that that even the latest VMware with the Github host modules patches works with kernel 5.8.   Anybody got that working?

I have a SATA SSD UEFI system with 5.8.1 installed. It works just fine.

On a side note, Arch Linux updated to the 5.8.1 kernel a few days ago:
```
$ uname -r
5.8.1-arch1-1
```
Linus releases it on August 11th and within a few days Arch implements it.

---

### Post by corradoventu on 2020-09-04
On Ubuntu the new kernel 5.8.0 arrived today:
```
corrado@corrado-n3-gg-0826:~$ uname -a
Linux corrado-n3-gg-0826 5.8.0-18-generic #19-Ubuntu SMP Wed Aug 26 15:26:32 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-n3-gg-0826:~$ 

```

---

