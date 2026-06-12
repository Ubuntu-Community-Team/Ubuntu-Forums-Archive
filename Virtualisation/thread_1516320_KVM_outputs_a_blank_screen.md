---
title: "KVM outputs a blank screen"
date: 2010-06-23
forum: Virtualisation
---

### Post by karthik.V.M. on 2010-06-23
Hi All,

I am using Ubuntu Karmic 64 bit on Intel Core2 Duo with Intel-VT extensions. Actually KVM was working fine last week but I see only a blank screen now (either directly or using vnc). If I replace KVM with QEMU, I am getting the output. I have no clue why it happened and I don't remember changing any configuration. Also I tried removing KVM and reinstalling it. Still the problem exists. I also checked through lsmod | grep kvm and it shows that kvm_intel is being used. It would be great if some one would give a hint on where to debug. My last resort is to reinstall the linux box.

Thanks for your time,
karthik.

---

