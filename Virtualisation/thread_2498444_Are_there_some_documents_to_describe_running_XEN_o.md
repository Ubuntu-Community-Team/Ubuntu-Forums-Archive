---
title: "Are there some documents to describe running XEN on ubuntu 2022.04"
date: 2024-06-13
forum: Virtualisation
---

### Post by jekygg on 2024-06-13
Hi ,

  I'm working on XEN 4.18,  and trying to run it on ubuntu 22.04. 
  Options of the kernel of ubuntu 22.04 about XEN are following:[INDENT]CONFIG_XEN=y[/INDENT]
[INDENT]CONFIG_XEN_PV=y[/INDENT]
[INDENT]CONFIG_XEN_512GB=y[/INDENT]
[INDENT]CONFIG_XEN_PV_SMP=y[/INDENT]
[INDENT]CONFIG_XEN_PV_DOM0=y[/INDENT]
[INDENT]CONFIG_XEN_PVHVM=y[/INDENT]
[INDENT]CONFIG_XEN_PVHVM_SMP=y[/INDENT]
[INDENT]CONFIG_XEN_PVHVM_GUEST=y[/INDENT]
[INDENT]CONFIG_XEN_SAVE_RESTORE=y
[/INDENT]
I compiled the XEN from the source code which download from the URL([https://github.com/xen-project/xen/blob/stable-4.18](https://github.com/xen-project/xen/blob/stable-4.18)),  install it and update the grub. The system is suspended during the boot phase.  

So my question is whether the ubuntu 22.04 can be used as the dom0 of the XEN?  if Yes,  what's the other configurations except to the compiling and instaling of XEN and grub updating, which are required to do so the XEN can run on ubuntu 22.04.

Thanks,
Jeky

---

### Post by volkswagner on 2024-06-15
If you are interested in XEN as a hypervisor, you may want to check out [XCP-ng]("https://xcp-ng.org/").

---

