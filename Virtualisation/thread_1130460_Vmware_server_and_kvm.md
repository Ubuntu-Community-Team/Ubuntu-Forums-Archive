---
title: "Vmware server and kvm"
date: 2009-04-19
forum: Virtualisation
---

### Post by veloce on 2009-04-19
I installed kvm on my laptop that is also running vmware server (2.01). I planned to test kvm in the hope of switching over. However, I then started getting this error from vmware: 

The virtualization capability of your processor is already in use. Disable any other running hypervisors before running VMware Server. 

And my vms won't start.

So I removed kvm and rebooted.  Unfortunately the error hasn't gone away!

There are now no other hypervisors running as far as I can see from the process list.

Anyone any ideas how to solve this?

---

### Post by pytheas22 on 2009-04-19
Are you sure that none of the kvm modules are loaded?  The command:
```

lsmod | grep kvm
```

returns nothing?

---

### Post by veloce on 2009-04-20
> **pytheas22 said:**
> Are you sure that none of the kvm modules are loaded?  The command:
```

lsmod | grep kvm
```

returns nothing?

You're quite right, kvm and kvm_intel were still loaded. I've now removed them and everything is back to normal.  (I naively thought that they would show up as processes but, being kernel modules they didn't.)

Thanks!

---

