---
title: "min_free_kbytes vs vm.min_free_kbytes in /etc/sysctl.conf"
date: 2019-09-18
forum: Virtualisation
---

### Post by mephisto2019 on 2019-09-18
I was trying to set up my first QEMU KVM Win10 machine according to the guide in the following link: [https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/#Configure_hugepages](https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/#Configure_hugepages)

The author recommends, for performance tuning reasons, to add the following lines to  ***/etc/sysctl.conf***:



```
kernel.shmmax = 8589934592

vm.hugetlb_shm_group = 129

min_free_kbytes = 112640


```

But when I run ***sudo sysctl -p*** to put the new settings into effect., I get the following error:



```
kernel.shmmax = 8589934592

vm.hugetlb_shm_group = 127

sysctl: cannot stat /proc/sys/min_free_kbytes: No such file or directory


```

When I replace ***min_free_kbytes*** with ***vm.min_free_kbytes***, I do not get any error.

1.) Did author actually want to write ***vm.min_free_kbytes*** instead of ***min_free_kbytes***? Did he make a mistake?


2.) Is there a difference between these two?

---

### Post by mephisto2019 on 2019-09-20
My question got answered on another platform. However, I should share information here as well. Here are the right answers:

For question #1:

> Yes, probably

For question #2:

> The vm.min_free_kbytes version is correct, the other is not.

All of the entries in /etc/sysctl.conf will correspond directly to a file in /proc/sys/, but with the . characters replaced by /. Thus, vm.min_free_kbytes refers to the file /proc/sys/vm/min_free_kbytes.



---

