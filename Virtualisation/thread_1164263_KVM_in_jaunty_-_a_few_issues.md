---
title: "KVM in jaunty - a few issues"
date: 2009-05-19
forum: Virtualisation
---

### Post by bonovoxpsu on 2009-05-19
hi all.  

recently upgrade to jaunty - love it so far but some issues.  apparently with kvm, virtual machine manager does not send the key combinations (like ctrl-alt-delete)to the host.  

it also seems that they've changed so much with regards to virtualization, that my windows VM's need activation if I move from 8.10 to 9.04 hosts.  obviously this sucks - i'm not sure i can really blame the ubuntu guys for this one, its just unfortunate.

finally, anoter issue is the new hardware wizard seems to detect some PCI device on boot.  is this the direct PCI access functionality?  if so, where could i find drivers and documentation on this?

---

### Post by bodhi.zazen on 2009-05-19
> **bonovoxpsu said:**
> hi all.

recently upgrade to jaunty - love it so far but some issues.  apparently with kvm, virtual machine manager does not send the key combinations (like ctrl-alt-delete)to the host.  

Use the kvm terminal 

ctrl-alt-2 (not F2)

then use the command help to see options

In your example use sendkey

```
sendkey ctrl-alt-delete
```

Return to the guest gui with ctrl-alt-1

> it also seems that they've changed so much with regards to virtualization, that my windows VM's need activation if I move from 8.10 to 9.04 hosts.  obviously this sucks - i'm not sure i can really blame the ubuntu guys for this one, its just unfortunate.

Nope, that is Microsoft. When you change hardware -> you need to re-activate. Nothing the Ubuntu / Linux developers can do about it.

> finally, anoter issue is the new hardware wizard seems to detect some PCI device on boot.  is this the direct PCI access functionality?  if so, where could i find drivers and documentation on this?

I will have to pass on that one as I do not use Windows ;)

---

### Post by veloce on 2009-05-21
> **bonovoxpsu said:**
> virtual machine manager does not send the key combinations (like ctrl-alt-delete)to the host.

Yeah, I struggled with that: Use the SendKey menu item to send Ctl+Alt+Bksp

> **bonovoxpsu said:**
> 

finally, anoter issue is the new hardware wizard seems to detect some PCI device on boot.  is this the direct PCI access functionality?  if so, where could i find drivers and documentation on this?

I'd forgotten that, I ignored it and told it not to bother me about it again. Doesn't seem to stop anything working!

---

