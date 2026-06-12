---
title: "Cant run kvm"
date: 2009-05-30
forum: Virtualisation
---

### Post by praveesh on 2009-05-30
My processor is Intel Core2Duo E4600 . I installed Kvm . But when tried to run from terminal , it replied that " Ubuntu doesnt support running kvm without hardware acceleration " . I think core2duo support intel vt . What may be the problem ? Please help

---

### Post by Pnuts on 2009-05-30
VT is usually disabled in the bios by default. Boot into BIOS and see if it is enabled or not, it most likely isnt.

Once you enable it, you should be fine.

edit: oh, depending on the chipset on the motherboard, you might have to shut the PC off completely after enabling it. Some let you get by simply doing the restart when you save\exit BIOS, but not all do.

---

### Post by bodhi.zazen on 2009-05-30
Open a terminal and run this command :

```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
```

If you get an output your CPU supports KVM and you need to enable it in your BIOS.

Otherwise your CPU does not support KVM :(

---

