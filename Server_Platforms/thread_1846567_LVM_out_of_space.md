---
title: "LVM out of space"
date: 2011-09-19
forum: Server Platforms
---

### Post by gnagnibu on 2011-09-19
Hi everybody.
I'm running ubuntu 10.04.3 with KVM+LVM.
Today I've got this error:

/dev/vms/vm017-Windows-XP-Professional: read failed after 0 of 4096 at 0: Errore di input/output

I look for on internet and I found that this kind of error is given when lv goes out of space, so lvs command says

vm017-Windows-XP-Professional vms  Swi-I- 25,00g vm007-Windows-XP-Professional 100.00                

It seems that my VM used all LV space but, into VM, Windows (yeah, it's a Windows virtual machine) says that it has 15 Gb free on C:

Any ideas?

---

### Post by YesWeCan on 2011-09-19
You probably need to resize one of your logical volumes.
Post the output of
[COLOR="DarkSlateBlue"]df -h[/COLOR]

---

### Post by gnagnibu on 2011-09-19
LVs stay on a dedicated hard disk (/dev/sdb), so my df -h doensn't give you interesting informations (/dev/sda): how to see its occupation?

---

### Post by gnagnibu on 2011-09-23
Volume Group isn't out of space:


# vgs
/dev/vms/vm017-Windows-XP-Professional: read failed after 0 of 4096 at 0: Errore di input/output
/dev/vms/vm014-Windows-2003-SS1: read failed after 0 of 4096 at 0: Errore di input/output
  VG   #PV #LV #SN Attr   VSize   VFree  
  vms    1  17   7 wz--n- 931,51g 487,71g

Any ideas?

---

