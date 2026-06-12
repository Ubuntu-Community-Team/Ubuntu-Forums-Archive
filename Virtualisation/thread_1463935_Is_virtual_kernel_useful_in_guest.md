---
title: "Is virtual kernel useful in guest?"
date: 2010-04-27
forum: Virtualisation
---

### Post by yitzhakbg on 2010-04-27
Had problems after installing linux-image-virtual in Karmic (now about to install Lucid) as guest under Windows XP host using VirtualBox. Can't describe them since I reverted, but my questions are:
[LIST=1]
[*]What exactly is the linux-image-virtual kernel
[*]What are the advantages of installing linux-image-virtual when running Ubuntu Desktop as guest?
[*]Are there any specific installation guidelines for linux-image-virtual? What is the proper procedure?
[*]Is it commonly used, or do most people running Ubuntu as a guest just leave the default generic kernel and be done with it?
[/LIST]
Thanks,
Yitzhak

---

### Post by rtilson on 2010-04-27
The virtual kernel is a kernel that can be used in unbuntu guest. It is a very lean kernel, this helps in reducing overhead. In my opinion is for virtual servers that needs only a few drivers such as networking, frame buffer, etc. 

As for running it in a ubuntu guest, I wouldn't recommend it. You wont have sound or be able to have 3D acceleration. 

Im assuming that most people just use the generic kernel and be done with it. That is what I do with my ubuntu guests.

---

### Post by yitzhakbg on 2010-04-27
Thanks

---

### Post by dcstar on 2010-05-01
> **yitzhakbg said:**
> Had problems after installing linux-image-virtual in Karmic (now about to install Lucid) as guest under Windows XP host using VirtualBox. Can't describe them since I reverted, but my questions are:
[LIST=1]
[*]What exactly is the linux-image-virtual kernel
[*]What are the advantages of installing linux-image-virtual when running Ubuntu Desktop as guest?
[*]Are there any specific installation guidelines for linux-image-virtual? What is the proper procedure?
[*]Is it commonly used, or do most people running Ubuntu as a guest just leave the default generic kernel and be done with it?
[/LIST]
Thanks,
Yitzhak

[LIST=1]
[*]It installs the server kernel via a new name.
[*]There are nothing but disadvantages when running a Desktop as guest - as in no sound to start with.
[*]No. Just install the package in Synaptic.
[*]It is a misleading piece of rubbish IMHO, as it does not state that it is only for server VMs and therefore misleads people.
[/LIST]

---

### Post by JPorter on 2011-07-07
> **dcstar said:**
> [LIST=1]
[*]It installs the server kernel via a new name.
...
[*]It is a misleading piece of rubbish IMHO, as it does not state that it is only for server VMs and therefore misleads people.
[/LIST]
[-X

This is an older thread, but it comes up on Google searches for "Ubuntu virtual kernel" frequently, so I felt I should respond regarding the linux-virtual kernel package. 

[LIST=1]
[*]It is **NOT the same as the server kernel**, it is significantly stripped down and lacks a large number of hardware drivers for devices that would not normally be seen in a virtual environment.
[*]It **IS designed for server virtualization**, certainly... which is what the vast majority of users would be using it for.  Desktop virtualization is the special/unusual case, not server virtualization.
[/LIST]

Per the [Ubuntu Server FAQ]("https://help.ubuntu.com/community/ServerFaq#What%20are%20the%20differences%20between%20the%20server%20and%20virtual%20kernels?"):
> [I]What are the differences between the server and virtual kernels?

The difference between the Virtual and Server kernels is that the Virtual kernel is intended to be utilized inside a virtual machine. The virtual kernel only includes the necessary drivers to run inside popular virtualization technologies such as KVM, Xen, and VMWare. The server kernel in contrast contains the necessary drivers to work with a wide range of hardware, and should be installed directly on host systems. Other than that, all other options are identical between the server and the virtual kernel.[/I]

---

### Post by sbike on 2013-02-06
The virtual kernel used to be useful because it has various virtual drivers (random numbers, network, and disk) and none of the useless hardware dependent kernels.  This resulted in a saving some disk space, less complications, and I wouldn't be surprised if it booted somewhat faster.

However they botched the kernels I've looked at.  Specifically the virtio-rng and virtio_console.  Seems mighty strange to have a kernel tuned for virtual use, but not having the needed virtio drivers to act as a guest.  Installing this package used to install a new kernel, initrd, and /lib/modules/ dir.

From what I can tell they ditched this with the current linux-image-virtual.  The package now only contains a copyright file and changelog.gz.

And you still need to install linux-image-extra to get the virtio drivers:
dpkg -S /lib/modules/3.5.0-23-generic/kernel/drivers/char/hw_random/virtio-rng.ko
linux-image-extra-3.5.0-23-generic: /lib/modules/3.5.0-23-generic/kernel/drivers/char/hw_random/virtio-rng.ko

---

### Post by wildmanne39 on 2013-02-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

