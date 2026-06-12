---
title: "KVM live migration with virsh (Ubuntu 8.04)"
date: 2009-01-05
forum: Virtualisation
---

### Post by Hark on 2009-01-05
Hi,

I'm trying to get KVM live migration working, but when I do 'migrate webserver.abc.xyz ssh://hostname.company.ext' in virsh I get the very cryptic message:

libvir: Remote error : remoteDispatchClientRequest: internal error: library function returned error but did not set virterror

How can I find out what the problem is?

All certificates are set, and on the server I want to migrate to I can start the KVM manually without problems.

---

### Post by Hark on 2009-01-12
Does nobody know how to do this? Let me ask a more general question; is it possible to do KVM live migration at all using 8.04? If so, how do I do it?

---

### Post by PilotJLR on 2009-01-13
This is on my to-do list as well, but I can't answer your question now. Once my schedule permits, I'm going to test this... no promises, it could be a while! But I will post back if/when I get this figured out.
Good luck

---

### Post by Hark on 2009-01-15
Well I finally found out that the libvirt in Hardy doesn't support KVM migration. When you give the correct command in virsh (the one I wrote before is wrong)
```
migrate webserver.abc.xyz qemu+ssh://hostname.company.ext/system
```
You get the error
```
libvir: error : this function is not supported by the hypervisor: virDomainMigrate
```
KVM can do live migration, but libvirt has only started supporting this for KVM at version 0.5.0 (released in November 2008 ). So in Hardy (and Intrepid) this will not work.
It should be possible to do KVM live migration when you don't use libvirt, but omitting libvirt will make running KVM a lot more difficult. When somebody still wants to do this, you have to use the 'migrate' command in the qemu monitor (see the -monitor option in the qemu manual page)

---

### Post by redbrain on 2009-01-15
KVM live migration is pretty intereasting! It has changed ALOT in the last few versions on the logic behind it.

anyways with virsh i'll check now in a sec, but i usualy just use the qemu-console.

So with KVM live migration what do you need first:

-Have 2 computers
-Have KVM running on Both
-Have same CPU AMD/Intel probably easiest (unless you want to add in some of the recent patches for migrating to different acheitectures!)

So say you start your kvm machine on your local machine with something like:
```

kvm -m 4096 -smp 2 -hda bla.img -net nic,macaddr bla,model=rtl8139 -net tap -vnc :10 &

```

So ok thats dead on. Its Best if you use vnc for this setup because one of the connections will go down etc..

So yeah thing is your need your virtual disk image available to both computers so what i do is set up an NFS share iscsi using qemu-nbd is kind of useless. 

So once you have an NFS share setup move your virtual disk over to his share and make sure both hosts have acess i am not going to go into detail into nfs setup there is plenty out there on how to do it.

So start your virtual machine like normal from the nfs share, then on the other machine you want to migrate to start the virtual machine with that virtual disk 

WITH THE EXACT SAME OPTIONS!!! (very important)

But you must append -incoming tcp://0:4444 (or other port!)
So it would be like on machine B:
```

kvm -m 4096 -smp 2 -hda bla.img -net nic,macaddr bla,model=rtl8139 -net tap -vnc :10 -incoming tcp://0:4444 &

```
This just makes the virtual machine halt untill migration starts!

Then with your running virtual machine you do ctrl-alt-2 to bring up the qemu-console and do migrate -d tcp://<machine B's ip/hostname>:4444

info migration is intereasting too:
check out: [http://kvm.qumranet.com/kvmwiki/Migration]("http://kvm.qumranet.com/kvmwiki/Migration")

If you compile your own version of KVM you can get access to LOTS of cool features now doing migration thorugh ssh etc.. and compression etc.. 
 
I have some tutorials on my blog:
[http://redbrain.co.uk/?page_id=29]("http://redbrain.co.uk/?page_id=29")
[http://redbrain.co.uk/?page_id=35]("http://redbrain.co.uk/?page_id=35")

Hope this helps i am not sure if virsh from libvirt actualy has support for  KVM live migration yet...

But i am sure it will be comming its more setup for Xen hosts for admin so far because KVM is still in heavy heavy developement :)

But its getting there!

---

### Post by Hark on 2009-01-16
That works great Redbrain, thanks!
But this only works without libvirt, can I expect any problems when I start kvm manually (or with a custom build script), without libvirt? For example libvirt creates vnetX interfaces, and when kvm is started manually I get tapX interfaces. It works fine, but I have no clue what the difference is.

---

### Post by redbrain on 2009-01-24
Ah sorry for the late reply yeah i dont understand why libvirt does these awkward settings. I prefer to use KVM manualy but thing is libvirt is going to take a while longer to more useful it needs more hacking together to get better support for KVM/Qemu/Kqemu libvirt is pretty much the only way to control Xen which is where its pretty good at! If you want to see libvirt in all its glory :)

---

### Post by canturkisci on 2009-03-17
Hello, I have a similar problem described in this thread regarding libvirt. When I try virsh migrate, i get the "libvir: QEMU error : operation failed: failed to start listening VM" error. 

I have since then stopped libvirtd and removed libvirt processes, and can do the kvm-qemu approach for live migration. This works fine and blazing fast. 

I rather use the virsh interface though. Is there a resolution to the virsh migrate issue or has anyone successfully done this with kvm?

Thanks,

---

### Post by bidwell on 2009-12-30
When I try the virsh with migrate base32 qemu+ssh://vm1/system on  Ubuntu 9.10 it tries to start the migration, starts the client on vm1, but never completes.  This seems to be supported on 9.10.  Any ideas on how to find out what is wrong?

---

