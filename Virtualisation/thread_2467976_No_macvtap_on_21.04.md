---
title: "No macvtap on 21.04"
date: 2021-10-14
forum: Virtualisation
---

### Post by biite on 2021-10-14
Hi,

Got both 20.04.3 LTS and 21.04 running and using Virtual Machine Manager.
I'm just using the default configuration created by the installation of Virtual Machine Manager and the virtualization stack. So no extra bridges etc. created.

20.04.3 is showing a macvtap network when creating a new VM, with selectable 'Source mode' (e.g. Bridge, VEPA etc.). It also show the possibility to install a VM via PXE.
21.04 is NOT showing a macvtap network when creating a new VM and also no option for PXE booting.

How can I check what is different?
nmcli shows no big differences, brctl shows no big differences

Has the macvtap option disappeared in the versions after 20.04.3?

Regards,
Martien

---

### Post by MAFoElffen on 2021-10-16
Am I confused? Others can tell me if I am... I have only been using KVM since Ubuntu Server 12.04 LTS, so 2012.

I am not aware that you could even setup a bridge or macvtap virtual network from within virt-manager... Is that even possible? I have always had to do either of those virtual networking setups "manually"... Before they would show up as an asset to use in virt-manager.

If I look in 20.04.x, in Virt Manager, I only see these 4 options for creating a New Virtual Network from within Virt Manager: NAT, Routed, Open, Isolated, SR-IOV pool.

Which are all documented in places like:
[https://www.linux-kvm.org/page/Networking](https://www.linux-kvm.org/page/Networking)
[https://wiki.libvirt.org/page/VirtualNetworking](https://wiki.libvirt.org/page/VirtualNetworking)
[https://kb.novaordis.com/index.php/KVM_Virtual_Networking_Concepts](https://kb.novaordis.com/index.php/KVM_Virtual_Networking_Concepts)

As for setting of macvtap...
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-virtual_networking-directly_attaching_to_physical_interface](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-virtual_networking-directly_attaching_to_physical_interface)
[https://www.math.cmu.edu/~gautam/sj/blog/20140303-kvm-macvtap.html](https://www.math.cmu.edu/~gautam/sj/blog/20140303-kvm-macvtap.html)
[https://blog.scottlowe.org/2016/02/09/using-kvm-libvirt-macvtap-interfaces/](https://blog.scottlowe.org/2016/02/09/using-kvm-libvirt-macvtap-interfaces/)
[https://www.ibm.com/docs/en/linux-on-systems?topic=configurations-kvm-guest-virtual-network-configuration-using-macvtap](https://www.ibm.com/docs/en/linux-on-systems?topic=configurations-kvm-guest-virtual-network-configuration-using-macvtap)

Non of those mention anything except setting up manually... Whereas, just like when you create a Bridge for a virtual network, then it exists, and then that virtual network shows up in Virt Manager to use, because it see's them as a Virtual Network asset...

Please... If you know an easier way that is not manual, and is GUI driven, I, for one, would like to know. That would be a lot easier than I have been doing with Terminal Commands, Virsh and/or manually editing files. Am I missing a piece of that puzzle somewhere?

I don't know. Maybe I have been doing that the old way and just have been unaware of anything different than that, but "I" am not aware of any other way.

Can anyone else shed more light on this?

---

### Post by biite on 2021-10-18
Nope, you're not confused :).

Maybe I've should defined it more clear. I get the macvtap option during the creation of a new VM. See the screenshots attached.
[IMG]https://i.imgur.com/imWpefC.png[/IMG]
[IMG]https://i.imgur.com/alrpbV2.png[/IMG]

I do not have those options in 21.04 and 21.10 (those I've checked).

---

### Post by MAFoElffen on 2021-10-18
Okay, and... Yes I was a bit confused in what you were asking "about". That is sort of a bit different. What you are talking about has not really "changed" conceptually, except in the wording in those menus...

That way, (just shown in parentheses as ending up as being macvtap) you dedicate/lose a NIC to each VM you do that with..., which they just renamed in the menu's there, but always has and is now named there in those menu's as a "Passthrough" ...directly to a Network Device. I never thought that was an efficient use of network resources, even when I use my main Server that has 8 NIC's. Other Virtual Systems call this "External Network", etc. But is a passthrough to a NIC.

Even with a Bridge for your Virtual Network, you end up dedicating one NIC for the Bridge to get your VM's on the same Network ID as the Host. (and using external switches and router resources) But at least with that, you can share it between many many VM's.

No. What I was talking about, and thought you were asking about... Is something "else" I do which involes SR-IOV and MacVtap. Using SR-IOV to create a pool of SR-IOV adapters. That also uses MacVtap, but it creates many virtual adapters to be used by your VM's. Intel has a good article explaining what that is, how it works and how to do that:
[Configure SR-IOV Network Virtual Functions in Linux* KVM*]("https://www.intel.com/content/www/us/en/developer/articles/technical/configure-sr-iov-network-virtual-functions-in-linux-kvm.html")

Now combine that with an internal virtual switch and a virtual router appliance... and you can do a whole lot of things.

Basically, under the hood, it gets down to whether you are using NAT or macvtap for the VMs...But most Users asking question here are running very few VM's at the same time, so don't have to worry about that, nor anything very complex at all.

---

### Post by MAFoElffen on 2021-10-19
I should probably throw in the disclaimer, that not all hardware is capable of supporting SR-IOV...

---

