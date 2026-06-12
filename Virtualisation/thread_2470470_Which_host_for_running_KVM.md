---
title: "Which host for running KVM"
date: 2021-12-31
forum: Virtualisation
---

### Post by satimis on 2021-12-31
Hi all,

I have been running Oracle VirtualBox here with Ubuntu as host for more than 10 years. 

Now I'm prepared adding KVM as second virtualizer on a new SSD HD here. I expect to find out which linux host will be suitable to run KVM other than Ubuntu because I expect to have a 2nd Linux host. 

Debian/Linuxmint/Fedora/CentOs/OpenSUSE etc? Debean-based or RPM-based Linux?

Please advise.  Thanks

Regards

---

### Post by TheFu on 2021-12-31
I think Intel's Clear OS is the fastest. [https://docs.01.org/clearlinux/latest/get-started/virtual-machine-install/virt-manager.html](https://docs.01.org/clearlinux/latest/get-started/virtual-machine-install/virt-manager.html)
But ClearOS isn't exactly end-user friendly. I've been using KVM+libvirt+virt-manager on Ubuntu since 2010. It has all the pros and cons that a base Ubuntu OS brings. I don't think it is worth learning the subtle differences that a new OS would require, without some specific goals known. All those tools are basically the same, regardless of the base distro.

Getting off Virtualbox is a good thing. Much more power and control with KVM/libvirt.

---

### Post by CharlesA on 2021-12-31
I've got Proxmox running on two boxes at home and I've used it for both KVM and LXC. I haven't had many issues with it, either.

---

### Post by SeijiSensei on 2021-12-31
What's wrong with using Ubuntu? I didn't understand what you meant by "because I expect to have a 2nd Linux host." I run KVM on Kubuntu machines without any problems.

---

### Post by MAFoElffen on 2021-12-31
I have been using QEMU/KVM since 2010. I used it first on Ubuntu 10.04 Server LTS and using connections to that server from Ubuntu 10.04 LTS Desktops. Back then, I was connecting via VNC or ssh... My exploration of Docker and LXC was first on Ubuntu...

I use and support a lot of Linux *flavors*... As well as many other OS'es and VM Host systems. My personal go-to is still an Ubuntu, hosting KVM...I have used it on many other Linux based hosts. For a while, I asked myself this same question... I had a mix of many other Distro's and OS's in my personal infrastructure... Then had to ask myself "why" was I making my life complicated?

For a while, I thought of shifting to CentOS as a base... Until they had some internal creative differences that shifted the directions of where they want to go, and technologies they want to support. I have to admit, I am still on a search to simplify a few things... I still support other Distro's, Linux Branches, and Linux as a whole, because that just helps us all. And Linux, is Linux. You can change things and customize things as you please...

Ubuntu has been stable for me and those I support, for a long time. It is easy to use, manage and maintain. I am not always in total agreement with some of the things Canonical 'decides'... LOL. But Ubuntu itself is solid. And the "Ubuntu Community", to me, is unmatched. I feel at home here and take pride in being one of it's members.

My current personal project is building another VM Host Server to shift things to. My Lab went from 14 servers, 7 desktops, 4 Laptops, and 4 mobile devices... to 4 VM Servers and 1 Desktop, and a 2-in-1 that connected to those... to 1 consolidated Desktop/Server, 2 Laptops, and 2 mobile devices. I downsized too much. Now I need to split my VM Host Services back out a it again for my lab.

I still run KVM on '_*everything*_' I personally own, whether it is amd64 or arm64... But I am still evolving with how I do that and how I manage those virtual systems.

---

### Post by satimis on 2022-01-01
> **MAFoElffen said:**
> I have been using QEMU/KVM since 2010. I used it first on Ubuntu 10.04 Server LTS and using connections to that server from Ubuntu 10.04 LTS Desktops. Back then, I was connecting via VNC or ssh... My exploration of Docker and LXC was first on Ubuntu...
I ran KVM/QEMU on Ubuntu as host, long time ago.  Later I built a new PC and ceased running KVM/QEMU.  I have 3 PCs, all of them running VirtualBox on Ubuntu 20.04 host.  Now I'm prepared to build a KVM/QEMU virtualizer for testing, comparing hardware forwarding with VirtualBox.  I expect running KVM/QEMU on another Linux host.

I tested Docker on Ubuntu VMs of Ubuntu host before.  It worked without problem.

> 
I still run KVM on '_*everything*_' I personally own, whether it is amd64 or arm64... But I am still evolving with how I do that and how I manage those virtual systems.
I got your point "KVM on everything"

Regards

---

