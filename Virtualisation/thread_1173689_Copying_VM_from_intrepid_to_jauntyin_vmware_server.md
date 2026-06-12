---
title: "Copying VM from intrepid to jauntyin vmware server"
date: 2009-05-30
forum: Virtualisation
---

### Post by sainathas on 2009-05-30
I have installed Ubuntu intrepid in vm under intrepid host.I am using 64 bit Ubuntu. I copied the vm to Ubuntu jaunty host.
When I started VM, it says

"This kernel requires x86-64 cpu, but only detected an i686 cpu.unable to boot, please use a kernel appropriate for your cpu."

But my Ubuntu host is x86-64 and my vm is also 64bit.

Can any one tell me where it went wrong?

---

### Post by dcstar on 2009-05-31
> **sainathas said:**
> I have installed Ubuntu intrepid in vm under intrepid host.I am using 64 bit Ubuntu. I copied the vm to Ubuntu jaunty host.
When I started VM, it says

"This kernel requires x86-64 cpu, but only detected an i686 cpu.unable to boot, please use a kernel appropriate for your cpu."

But my Ubuntu host is x86-64 and my vm is also 64bit.

Can any one tell me where it went wrong?

Post the following from the host:

```
uname -m
```

---

### Post by sainathas on 2009-06-01
In the host  uname -m gives x86_64

---

