---
title: "Running programs from another partition"
date: 2010-10-26
forum: Wine
---

### Post by DoctorEvazan on 2010-10-26
I'm dual-booting Windows 7 Starter and Ubuntu 10.10, and I was wondering if it was possible to run the programs from my windows partition in Ubuntu through wine.  Would I just have to set the mount point as ~/.wine/drive_c/ ? (Right now it mounts at /Windows/)  Would that not work, or is there a simpler method?

I'm new to Linux, but I have used wine on OS X.

EDIT:  Ok, I found my answer.  From the Wine wiki:
> **WARNING**: Do not try to configure Wine to point to your actual Windows C:\ drive. **This will break Windows and require a Windows reinstall.**  We have tried to make this hard to do, so you probably cannot do it by  accident. If you do manage this, Wine may or may not continue to  operate, but your Windows install will be 100% dead due to critical  parts of it being overwritten. The only way to fix Windows after this  has happened is to reinstall it. 

---

