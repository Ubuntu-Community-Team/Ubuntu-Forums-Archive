---
title: "QEMU/KVM Network Issues"
date: 2015-08-01
forum: Virtualisation
---

### Post by ipeek90 on 2015-08-01
I've got another thread going about GPU Passthrough here: [http://ubuntuforums.org/showthread.php?t=2286897](http://ubuntuforums.org/showthread.php?t=2286897)

I've gotten that to work successfully but my current issue is that the VM is being given the default 10.0.2.15 IP address. From my understanding thats what is given by vmbuilder settings or something of the sort.

If I create the VM using virt-manager the network seems to be using the correct bridge. I don't want to use virt-manager because when I do use it, the AMD drivers don't actually work.

Any ideas? I'm fine with the IP staying 10.0.2.15 but I need to be able to connect to it.

---

### Post by TheFu on 2015-08-01
virsh edit {vm-name}

Change the network to a manually created bridge. Do not use th libvirt-created bridges or networking for anything.  For a long time those networks were - how to say this - flaky.  Never had any issues with manually made bridges - /etc/network/interfaces  is the file to edit. If you only have 1 NIC, this bridge will be used both for the hostOS IP and for the bridge IPs taken by each guestVM.

It is much easier to just ignore the libvirt network stuff. That way you aren't disappointed when things don't work.

Of course, you want to create the bridge BEFORE editing the VM settings.

---

### Post by ipeek90 on 2015-08-01
Thanks for the tip.

I tried virsh edit win7 to no avail, mostly because I didnt create it with the virsh command. I've dd a .img and then ran my start script from the other thread and just installed windows there.

I have gotten Synergy to work though. However the network speeds are TERRIBLE...Well they work but it took me like an hour to downloads 6gbs. Which should not have taken as long.

---

### Post by TheFu on 2015-08-02
So what you need to do is to get libvirt to know about this VM. That's easy with virt-manager. 
Create a new VM - when it asks if you want to create new storage or use existing ... "use existing" is the choice. Point it at the .img file.  
As you setup the VM settings, make everything match what the old settings were - except the networking. Fix that as I've outlined above using a manual bridge (pre-setup that).  From a performance standpoint, make certain both the disk and network cards are virtio.

Don't know anything about synergy or what it might have to do with virtual machines.  VM network performance shouldn't be more than 10% off native performance, if the network adapter isn't flooded with traffic from other VMs.

---

