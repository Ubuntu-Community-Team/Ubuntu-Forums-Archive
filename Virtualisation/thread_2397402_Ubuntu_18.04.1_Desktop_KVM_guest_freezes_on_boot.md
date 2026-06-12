---
title: "Ubuntu 18.04.1 Desktop KVM guest freezes on boot"
date: 2018-07-29
forum: Virtualisation
---

### Post by ammunist on 2018-07-29
Wondering if anyone else has solved this problem.  I have Ubuntu Server 18.04 LTS running, and I'm trying to install Ubuntu desktop 18.04.1 as a KVM guest I'm performing the VM creation/install with this command:

sudo virt-install --connect qemu:///system --virt-type kvm --name evilmanage --vcpus=2 --ram 2048 --disk path=/var/lib/libvirt/images/evilmanage.img,size=50 --network  bridge=br0 --graphics vnc,listen=0.0.0.0,port=5901 --cdrom ~/isos/ubuntu-18.04.1-desktop-amd64.iso --os-variant ubuntu17.10

The install completes, but upon rebooting, the OS hangs and won't boot.

Anybody have 18.04.1 running as a guest?  How in the world did you do it?

---

### Post by ammunist on 2018-07-29
...and of course, I figure it out moments after I post to the forum!

In the libvirt XML configuration for the guest (access this by going into virsh, then doing 'edit <vmname>', the parameter in the XML file under devices->video for the 'type' had to be changed to 'qxl' instead of the default, which is 'cirrus'.  OMG what a pain, this took me 2 days and about 10 hours to figure out. ugh.

---

### Post by gasolino2 on 2018-09-03
Thank you, so much.

I could not figure out why I was having this issue since I pulled my virt-install command right out of bash history, and that VM has been wonderful.  It turns out that one was set to auto logon, so the issue never manifested.

Regards,
gasolino2

---

