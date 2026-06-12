---
title: "Preseed.cfg for virtual servers ?"
date: 2010-12-01
forum: Server Platforms
---

### Post by r3dlight on 2010-12-01
Hi all,

I'm about to set up an installation howto for my work and I just can't find information about this in the server guide :

Actually 2 questions : 

1) Is there a way to specify that I want to boot on the minimal installation kernel (virtual kernel for esx and kvm) inside the preseed.cfg ?

2) Is there a thread somewhere dealing with differences between preseed syntax for 10.04 and 10.10 (I got many strange behaviour with a 10.10 and my old preseed is working well with 10.04 lts) ?

Many thanks :)

---

### Post by sendmoreinfo on 2010-12-08
Do you want to boot virtual kernel at install time, or after install has completed?

---

### Post by r3dlight on 2010-12-09
Hi, yes I want to boot virtual kernel at the installation time ... with a preseed.cfg 
Any ideas ?

---

### Post by sendmoreinfo on 2010-12-27
I don't see the point in that, but anyway, preseed.cfg is loaded by installer, at which point the kernel is already loaded and running.  You'll have to replace the actual kernel binary that is loaded by PXELINUX (or whatever else that you use).

---

