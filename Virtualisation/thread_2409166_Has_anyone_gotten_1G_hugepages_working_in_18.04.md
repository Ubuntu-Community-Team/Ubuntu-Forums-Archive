---
title: "Has anyone gotten 1G hugepages working in 18.04?"
date: 2018-12-28
forum: Virtualisation
---

### Post by KillerKelvUK on 2018-12-28
Recently upgraded and my rig now supports 1G hugetables but no matter what I do I just cannot get the config to persist through a reboot and in all cases the standard hugetables defaults to using the 2M configuration and won't even disable transparent hugetables.

I'm pushing config to the kernel at boot time via grub which just seems to be ignored or overwritten but I just can't find out from where...

```

GRUB_CMDLINE_LINUX_DEFAULT="iommu=1 amd_iommu=on default_hugepagesz=1G hugepagesz=1G hugepages=8 hugepagesz=2M hugepages=0"

```

My only success thus far is to edit /etc/sysctl.conf and adding in  "vm.nr_hugepages = 4096" which just applies to the defaulted 2M page sizes.

I did spot that systemd is running dev-hugepages.mount by default which I masked out as per [https://www.freedesktop.org/wiki/Software/systemd/APIFileSystems/](https://www.freedesktop.org/wiki/Software/systemd/APIFileSystems/) and replaced with my own config in /etc/fstab but still nothing.

Lastly, I have installed the hugepages package and tried applying the configuration using this which works fine but just doesn't persist through a system reboot and provides no means to making the config permanent :-?

I'll look to get further support via launchpad but before I do has anyone gotten this working that can give me some pointers?

Thanks,

K

---

### Post by KillerKelvUK on 2018-12-29
So  turns out I was experiencing this ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1569567](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1569567)) bug/feature which once I resolved managed to get me on track with this.

---

