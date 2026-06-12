---
title: "VirtualBox and 6.8 kernel"
date: 2024-08-16
forum: Virtualisation
---

### Post by makitso on 2024-08-16
[FONT=Arial]Virtualbox from the repository works correctly with kernel 6.5.0-45Generic. 

However, with the 6.8.0-40  upgrade the kernel fails:
[/FONT]
[FONT=Arial]UBSAN: array-index-out-of-bounds in /var/lib/dkms/virtualbox/6.1.50/build/vboxdrv/SUPDrvGip.c:637:59[/FONT]
[FONT=Arial][ 147.546311] index 1 is out of range for type ‘SUPGIPCPU [1]’[/FONT]
[FONT=Arial][ 147.546313] CPU: 4 PID: 7735 Comm: VirtualBoxVM Tainted: G W OE 6.8.0-40-generic #40~22.04.3-Ubuntu[/FONT]

---

### Post by &amp;KyT$0P# on 2024-08-16
I stopped using regular VirtualBox after upgrading kernel beyond 6.2.x.  Switched partially to virt-manager/libvirt/QEMU/KVM and partially to [this third-party KVM backend for VirtualBox]("https://github.com/cyberus-technology/virtualbox-kvm") (based on VirtualBox 7.0.18).  If you need to use 6.8.x kernel, would one or both of these options work for you?

---

