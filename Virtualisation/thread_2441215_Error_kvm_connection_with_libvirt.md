---
title: "Error kvm connection with libvirt"
date: 2020-04-20
forum: Virtualisation
---

### Post by laurent55150 on 2020-04-20
Hello,

I use Ubuntu 19.10 and I try to use a VM with qemu/KVM with virt-manager.

I created my bridge and installed a VM with success, but since the reboot of my conputer, I lost the network. I can communicate between my VMs, but I can't access to Internet from them.

I tried to reinstall the connection, but I have always the same error. 

Help me please...

thanks by advance
++
Laurent

---

### Post by TheFu on 2020-04-22
19.10 will be supported for just a few more months.  Servers should be LTS releases. Either wait a few days and use 20.04 or install 18.04 to get the 5 yrs of support that a Server LTS provides.

How did you setup the bridge?  Netplan config files are the way to do that now, so post your netplan file using **code tags**. If you don't use code tags, nobody can help since spacing is absolutely critical for yaml files.  Be certain to clearly show the routing (**ip route | column -t**)  and **ip address** output for the host and the guests too, please.  

I don't have any 18.04 or 20.04 VM hosts, so it will be guesswork from me.

---

