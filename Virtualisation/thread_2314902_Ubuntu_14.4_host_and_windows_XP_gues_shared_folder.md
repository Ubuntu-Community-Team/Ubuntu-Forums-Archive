---
title: "Ubuntu 14.4 host and windows XP gues: shared folder does not work"
date: 2016-02-24
forum: Virtualisation
---

### Post by 171742 on 2016-02-24
Hi,
tried to set it up in the settings as bidirectional: Does not work. How to do it? I am really bad at programming...
Thanks!

---

### Post by TheFu on 2016-02-24
Uh, which of the 20 different virtualization technologies are you using? QEMU, KVM, VMware Player, Workstation, or that thing from Oracle?  There are others, but those probably don't apply.
Plus, XP support ended years ago, so I can't imagine that any virtualization tools have tested with it since that time, that means any "guest additions" may or may not work correctly, if installed, which also means that bi-directional directory sharing may or may not work under XP.

I just use normal network sharing - NFS, CIFS  and treat VMs just like any other machine.  Makes life easy.

---

### Post by MAFoElffen on 2016-02-25
He said Ubuntu Host and XP VM Guest. (But did not say which version of Ubuntu)

I am also asking about with virtual hypervisor you are using in Ubuntu to run your guest in... Thinking you are probably either using VirtualBox or VMlPlayer. The reason TheFu needs to know is that there are different explanations for each. For instance a host's folder could be set up to the VM as a shared resource with the VM from the host, to the VM (as if it where another virtual sik or applicance)... Or if the virtual NIC is set up on a bridge network (same network as the host) then it could be shared between both as an smb share (Workgroup).

---

