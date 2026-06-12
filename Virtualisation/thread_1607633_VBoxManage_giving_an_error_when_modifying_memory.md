---
title: "VBoxManage giving an error when modifying memory"
date: 2010-10-28
forum: Virtualisation
---

### Post by hawk2010 on 2010-10-28
Hi,

I created a Virtualbox machine using the following command

VBoxManage createvm -name "test" -register

and tried to modify the memory using
VBoxManage modifyvm "test" -memory "256"

but i get the following error

error: unknown option: -memory

Solved : 
Apparently the correct syntax is --memory "512" for VBoxManage 3.2.0

---

