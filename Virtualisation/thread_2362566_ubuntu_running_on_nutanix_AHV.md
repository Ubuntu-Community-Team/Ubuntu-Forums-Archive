---
title: "ubuntu running on nutanix AHV"
date: 2017-05-30
forum: Virtualisation
---

### Post by dteague39 on 2017-05-30
I am trying to move a couple of ubuntu systems (12.05 LTS for now) from vmware to nutanix AHV hypervisor (KVM BASED). When I do a  grep -i virtio /boot/config-`uname -r` I am not seeing the CONFIG_SCSI_VIRTIO=m in the kernel. I unfortunalty cannot figure out how to add this into my kernel. 

So I figured I would ask here for some help.

Thank You
David

---

### Post by howefield on 2017-05-30
Thread moved to the "*Virtualisation*" forum.

---

### Post by KillerKelvUK on 2017-05-30
Hi, is the current vmware guest running an unmodified kernel i.e. stock download from the ubuntu repo/cd image? What version is it (uname -a)? Also I think you have a typo and mean your distro is release 12.04 but please can you provide the specific release details (lsb_release -a)?

You can't add CONFIG_SCSI_VIRTIO=m into an existing kernel to my understanding, you'd need to compile a new kernel after adding this option into the config, however it maybe the module you need could be loaded manually but that may not work for you. Also it maybe your kernel is old and updating to a later release will give you what you want (hence the requested info above).

I've just span up a clean 12.04.5 install and here are the defaults straight out of install...

```

kelvin@ubuntu:~$ uname -a
Linux ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

kelvin@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

kelvin@ubuntu:~$ grep -i virtio /boot/config-`uname -r`
CONFIG_NET_9P_VIRTIO=m
CONFIG_VIRTIO_BLK=y
CONFIG_SCSI_VIRTIO=m
CONFIG_VIRTIO_NET=y
CONFIG_CAIF_VIRTIO=m
CONFIG_VIRTIO_CONSOLE=y
CONFIG_HW_RANDOM_VIRTIO=m
CONFIG_VIRTIO=y
# Virtio drivers
CONFIG_VIRTIO_PCI=y
CONFIG_VIRTIO_BALLOON=y
CONFIG_VIRTIO_MMIO=y
CONFIG_VIRTIO_MMIO_CMDLINE_DEVICES=y

```

So this may be addressable by installing a newer kernel from stock repo if that's possible for you.

---

### Post by dteague39 on 2017-05-31
thanks for the relpy here a are the relese detials.
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

This is the result on that box for the  grep -i virtio /boot/config-`uname -r` commandCONFIG_NET_9P_VIRTIO=m
CONFIG_VIRTIO_BLK=y
CONFIG_VIRTIO_NET=y
CONFIG_VIRTIO_CONSOLE=m
CONFIG_HW_RANDOM_VIRTIO=m
CONFIG_VIRTIO=y
CONFIG_VIRTIO_RING=y
# Virtio drivers
CONFIG_VIRTIO_PCI=y
CONFIG_VIRTIO_BALLOON=m
CONFIG_VIRTIO_MMIO=m


I like your Idea of installer a newer kernel that maybe the answer. I am not sure why the virtio-scsci drivers is not there as I have usually seen available by default.

---

### Post by KillerKelvUK on 2017-05-31
Hey, you've not said what kernel version you're using (uname -a), is it older than what I posted or newer?

Also a correction to my first reply an "=m" in the config file would mean the module you need isn't built into the kernel but is loadable separately, with it not being present for you then you wouldn't be able to load this manually so installing a new(er) kernel maybe your only option.

---

### Post by dteague39 on 2017-05-31
Whoops here it is.

Linux configurator 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Looks like it is much older.

---

### Post by KillerKelvUK on 2017-05-31
Wow yeah, you okay with the next steps to install a later kernel or still need some pointers?

---

