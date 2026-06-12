---
title: "Managing Hugepages in 18.04LTS"
date: 2018-12-27
forum: Server Platforms
---

### Post by KillerKelvUK on 2018-12-27
So I have a clean 18.04LTS install and have been reading about 1) disabling Transparent Hugepages and then 2) enabling and specifying 1G static hugepages and I'm getting nowhere fast.  Before I go loosing myself in random config I can't backout (coz I'm a crap admin) has anyone already trodden this path that can help me out?

Primarily I'm using two reference sources....
[https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#Huge_memory_pages](https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#Huge_memory_pages)
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_tuning_and_optimization_guide/sect-virtualization_tuning_optimization_guide-memory-huge_pages-1gb-runtime](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_tuning_and_optimization_guide/sect-virtualization_tuning_optimization_guide-memory-huge_pages-1gb-runtime)

My grub looks like...
```

GRUB_CMDLINE_LINUX_DEFAULT="iommu=1 amd_iommu=on transparent_hugepage=never default_hugepagesz=1G hugepagesz=1G hugepages=4"

```

I definitely support 1G hugepages because...
```

$ hugeadm --pool-list      Size  Minimum  Current  Maximum  Default
   2097152        0        0        0        *
1073741824        0        0        0      

and...

$ dmesg | grep Huge
[    0.109211] HugeTLB registered 1.00 GiB page size, pre-allocated 0 pages
[    0.109211] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages

```

To disable transparent hugepages I have issued a...
```

hugeadm --thp-never

```
Which returned a success via inspecting /sys/kernel/mm/transparent_hugepage/enabled which occurs in runtime however on reboot this reverts to [madvise] regardless of the above kernel parameter.

And I'm drawing a blank on specifying 1g pages as again the kernel parameters seem to have no effect :-?

(@admins, I appreciate this is a virt centric topic but the usage of hugepages I understand is much broader than my linked articles hence posting it here, can this thread be linked into the virt section also or can I do a justifiable double post to try and catch the relevant forum members?)

Thanks all,

K

---

### Post by KillerKelvUK on 2018-12-29
[COLOR=#000000]So turns out I was experiencing this ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1569567](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1569567)[/COLOR][COLOR=#000000]) bug/feature which once I resolved managed to get me on track with this.[/COLOR]

---

