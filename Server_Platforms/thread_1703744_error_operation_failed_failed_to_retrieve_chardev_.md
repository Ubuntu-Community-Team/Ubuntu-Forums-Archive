---
title: "error: operation failed: failed to retrieve chardev info in qemu with 'indev'"
date: 2011-03-09
forum: Server Platforms
---

### Post by Rohan Nigam on 2011-03-09
Hello Everyone,

I was not sure if I should report this as a bug before taking your opinions. But I have been using Ubuntu-10.10 Server to create KVM guests.

I used **virt-install** and **vmbuilder** tools to create these images. Using both I get the same error: operation failed: failed to retrieve chardev info in qemu with 'info char dev'

Here are some more details:
Machine: Ubuntu server -10.10  ubuntu 2.6.35-22-server
**Libvirt and virsh versions:**
root@ubuntu:/# virsh version
Compiled against library: libvir 0.8.3
Using library: libvir 0.8.3
Using API: QEMU 0.8.3
Running hypervisor: QEMU 0.12.5


[I]virsh # list --all
 Id Name                 State
----------------------------------
  - mav-vm1              shut off
  - mav-vm2              shut off

virsh # start mav-vm2
error: Failed to start domain mav-vm2
error: operation failed: failed to retrieve chardev info in qemu with 'info char dev'[/I]


At the beginning I was thinking the problem might be with vmbuilder or virt-install. Here are the commands I used:


vmbuilder kvm ubuntu --suite maverick --flavour virtual --arch amd64 -o --libvirt qemu:///system --ip 192.168.2.212 --hostname 'mav-vm2' --cpus 2 --mem '2048' --rootsize '8192' --swapsize '1024' --mask 255.255.255.0 --bcast 192.168.2.255 --gw 192.168.2.1 --dns 192.168.2.30 --bridge br0 --user rnigam --pass default --addpkg wget --addpkg cron --addpkg vim --addpkg ntp --addpkg ntpdate --addpkg ssh --addpkg build-essential --addpkg linux-headers-virtual --addpkg acpid

Using the ISO:
virt-install --connect qemu:///system -n mav-vm1 -r 2048 --vcpus=4 -f /root/vmimages/kvm1.qcow2 -s 12 --cpuset=4,5,6,7 -c /root/vmimages/ubuntu-10.10-server-amd64.iso --os-type linux --network bridge=br0 --accelerate --virt-type kvm --hvm


There was a suggestion from the #virt on OFTC and #ubuntu-server that this problem might be because of the older version of libvirtd running. (0.8.3) compared to the latest available libvirtd 0.8.8.

At this moment, I am unable to use KVM and libvirt on Maverick to create any guests at all. All comments and suggestions are welcome.

Thanks.

Rohan

---

### Post by Rohan Nigam on 2011-03-10
Ok I figured out what the problem was. Apparently this is Maverick related bug. I have checked and confirmed it with couple of guys on #ubuntu-server who were running Lucid.  All the options in /etc/libvirt/qemu.conf are commented out by default. 

I had to uncomment these two out:

[I]# The user ID for QEMU processes run by the system instance
user = "root"

# The group ID for QEMU processes run by the system instance
group = "root"[/I]


This needs to be filed as a bug(if it can be called so)


- Rohan

---

### Post by bl8n8r on 2011-08-23
> I had to uncomment these two out:

I am getting this error from virt-manager (since recent update) when trying to start guests. Opteron 12 core system. Un-commenting those entries does not work for me.

---

### Post by JonathanRRogers on 2011-09-02
> **bl8n8r said:**
> > I had to uncomment these two out:

I am getting this error from virt-manager (since recent update) when trying to start guests. Opteron 12 core system. Un-commenting those entries does not work for me.

Did you restart libvirtd? I used this command "sudo restart libvirt-bin".

---

### Post by kkaland on 2012-07-31
This is still relevant in Ubuntu 12.04 LTS, at least when running ```
virt-install
``` as root.

---

