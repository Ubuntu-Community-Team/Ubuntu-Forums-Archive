---
title: "KVM Nesting"
date: 2010-03-17
forum: Server Platforms
---

### Post by pcmanning on 2010-03-17
Am interested in getting nested kvm working, but can't find any good information.  putting "nested=1" seems to be part as does starting vms with enable-nesting.

But there's go guidance as to which files to place these commands in.

Anyone help please?

Paul

PS:  Reason for doing so is to enable me to build a single box demo of Eucalyptus/OpenNebula with a couple of nodes, perhaps a virtual iSCSI server and a front end controller.

---

### Post by pcmanning on 2010-03-17
Ok have found some of the info I require.  

If I unload and reload kvm_amd with it's nested parameter...

modprobe -r kvm_amd
modprobe kvm_amd nested=1

(it updates /sys/modules/kvm_amd/parameter/nested)

I see that nested virtualization is enabled in the logs (dmesg | tail).

So next is how to change my xml config file in /etc/libvirt/qemu for the VM so that it is equavalent to starting qemu with the enable_nesting parameter?

Paul

---

### Post by pcmanning on 2010-03-17
Nailed it anyway:  Create a script to replace the emulator in the XML file.  This script must be named in /etc/apparmor.d/abstractions/libvirt-qemu

I choose to create /usr/bin/emu-sparc rather than add a name - not sure if it's a good idea to edit the apparmor file?  Anyway looked like this...

```
#!/bin/bash
exec /usr/bin/kvm -enable-nesting "$@"
```

This script just adds the extra QEMU parameter to the rest of the arguments.

Then I used virsh to edit the VM XML file - can't do this directly in /etc/libvirt/qemu??? and changed the emulator from /usr/bin/kvm to /usr/bin/qemu-sparc

Restarting the VM and logging in shows that svm is enabled (cat /proc/cpuinfo | grep svm).

Next to see if actually will run KVM in the VM!?!

Hope someone finds this useful, and someone else updates libvirt to support nesting as an option - maybe in Lucid Lynx?

Paul

---

### Post by Jeff Anthony on 2010-03-17
Thanks for answering it!

---

### Post by RussHayward on 2010-03-18
Hi Paul - this certainly helped me a great deal! - being a complete Linux newbie, I'd of never figured it out!

I can now finally enable Hyper-V role within a Windows 2008 guest! (it still doesnt work - but I guess I need to wait for the new KVM patches for that - I think patching diff files is definitely beyond me for now :-))

Cheers

---

### Post by pcmanning on 2010-03-22
Update - battled this on 9.10 - no joy.  Working with 10.04 beta - seems I may have cracked it.  Have a 10.04 virtual server running kvm on top of a physical 10.04 server running kvm.  The virtual server is now running a 9.10 installer...

:)

---

### Post by pcmanning on 2010-03-22
Or not - installer hangs!

---

### Post by pcmanning on 2010-03-23
Am asking on the KVM forums about this...

[http://www.linux-kvm.com/content/nested-kvm]("http://www.linux-kvm.com/content/nested-kvm")

See what comes up  from over there.

Paul

---

### Post by yosu on 2011-01-23
Hi Paul,

I wonder if you had any success with your nested UEC installation; I am looking forward to do the same myself, any advice would be very apretiated.

Yosu.:popcorn:

---

