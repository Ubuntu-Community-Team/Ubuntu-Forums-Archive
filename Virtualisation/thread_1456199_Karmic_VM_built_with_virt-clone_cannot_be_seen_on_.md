---
title: "Karmic VM built with virt-clone cannot be seen on network"
date: 2010-04-16
forum: Virtualisation
---

### Post by fimbar on 2010-04-16
Hi guys,

I've got a problem I've been pulling my hair out over for days now and I really need some help!

I'm running KVM and using vmbuilder to build karmic kvm guests. My host is running a bridged network and the guests built using vmbuilder can see the network just fine. Everything on my network can see the VMs. Life is good.

However, when I use virt-clone to clone one of the above guests the cloned vm cannot see my network at all. It doesn't get an IP address from my router. All I get when I run "ifconfig" on the cloned guest is an entry for my local loopback, whereas the machine I've just cloned shows an entry for the local loopback AND eth0.

The entries in the xml file for the original and cloned VMs shows the same (obviously the MAC addrresses are different):

```
    <interface type='bridge'>
      <source bridge='br0'/>
    </interface>

```For info here is the virt-clone command I'm using:

```
virt-clone --connect=qemu:///system -o newhost -n oldhost -f /home/fimbar/ubuntu-kvm/newhost.gcow2

```Can anyone give me some pointers as to what's going wrong please?

I'm using Karmic, 64 bit ubuntu server.

Many thanks.

---

### Post by fimbar on 2010-04-17
I've made a bit of progress. It's something to do with the MAC address but I've no idea what exactly :confused:

If I copy the MAC address from a working VM to a cloned, "broken", VM then the cloned suddenly works and gets an IP address from my router.

So the question is why is that? Obviously I can't use the same MAC address for every cloned VM. I must confess to knowing very little about MAC addresses. Maybe there is a bug in the MAC address generator on virt-clone?

Can someone help me please?

---

### Post by Elemmire on 2010-04-28
hello
you have to access to the directory of the VM : /etc/udev/rules.d/ 
then you delete the file 70-persistent-net.rules

then reboot the VM and it will have the net

---

### Post by fimbar on 2010-04-28
> **Elemmire said:**
> hello
you have to access to the directory of the VM : /etc/udev/rules.d/ 
then you delete the file 70-persistent-net.rules

then reboot the VM and it will have the net

Goodness me, so you do! Thank you...thank you.....THANK YOU :)

I'd have never worked that out for myself in a million years! :biggrin:

---

