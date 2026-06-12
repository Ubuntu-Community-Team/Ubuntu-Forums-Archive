---
title: "Qemu/KVM and server shutdown/boot"
date: 2011-08-07
forum: Server Platforms
---

### Post by mvip on 2011-08-07
Hi folks,

I finally swapped out VMware Server 2 in favor of Qemu/KVM on one of my servers. It took some time to get used to but now I'm up and running. 

There is however one thing that I haven't figured out -- what is the best practice for suspending/resuming VMs when the host server reboots (or just shuts down)?

VMware server came with this feature out-of-the-box and I really liked it. By default, the system appears to simply be pulling the plug on the VMs on shutdown. This is of course far from ideal, as it will lead to data loss and/or corrupted disks. 

What is the best practice for this? I can't imagine that I'm the only one having this issue. 

(The server is running on 10.04 LTS Server)

---

### Post by Zeosa on 2011-08-07
I don't use kvm (looking into switching to it myself) but from my understanding, libvirt supports doing just this. Are you using Linux guests? if they are Debian/Ubuntu you to have acpid installed on them as well.

You could create a script in init.d and link it to rc6.d to shutdown your guests using libvirt.

Here's an example script I found somewhere during my research


```


#!/bin/bash
CONNECT_STRING="qemu:///system"
for MACHINE in $(virsh -c "$CONNECT_STRING" list | awk '/running$/ {print $2}') ; do
  virsh -c "$CONNECT_STRING" shutdown $MACHINE
done
sleep 600

```

I don't guarantee that it'll work as I haven't tested it myself ;)

---

### Post by mvip on 2011-08-07
The guests are a combination of FreeBSD and Windows nodes. I just tried, and it does not appear as the ACPI command for shutdown is sent.

I was aware of virsh's suspend/resume feature and that it was possible to script it. However, I was curious if there were any built-in feature for this, but that doesn't seem to be the case then.

---

