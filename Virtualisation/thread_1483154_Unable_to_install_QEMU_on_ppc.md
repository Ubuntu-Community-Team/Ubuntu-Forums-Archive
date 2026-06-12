---
title: "Unable to install QEMU on ppc"
date: 2010-05-14
forum: Virtualisation
---

### Post by Coldplayfan on 2010-05-14
I'm sorry if this is in the wrong forum section, but whenever I try to compile and install the QEMU emulator on my iBook G4 running Ubuntu, I get this message after the ./configure && make command:

```
/home/wyatt/qemu-0.12.3/target-ppc/kvm.c: In function &#8216;kvm_arch_init_vcpu&#8217;:
/home/wyatt/qemu-0.12.3/target-ppc/kvm.c:50: error: &#8216;struct kvm_sregs&#8217; has no member named &#8216;pvr&#8217;
make[1]: *** [kvm.o] Error 1
make: *** [subdir-ppc-softmmu] Error 2

```

wyatt is the name of my home folder. Can anyone help me, or even direct me towards a forum that could help solve my problem? Thanks.

---

