---
title: "vbox error"
date: 2009-08-09
forum: Virtualisation
---

### Post by madinc on 2009-08-09
how do i disable the kvm kernel extension, and recompile the kernel?
some help please:confused:

---

### Post by jocampo on 2009-08-09
This is a workaround but if you are not using KVM extensions, you can try ...

```
sudo /etc/init.d/kvm stop
```

Try it and let us know ...

---

### Post by arsogukpinar on 2009-08-11
You need to remove kvm kernel modules. I am running KVM and Virtualbox on my laptop. 

First you need to find out name of the kvm module, with this command you can find that out.
```
lsmod  | grep kvm
```

I am using Intel CPU so on my laptop i have kvm_intel module. You can remove it with the command below. It will be reloaded with next boot.
```
sudo rmmod kvm_intel
```

Cheers
Ali

---

