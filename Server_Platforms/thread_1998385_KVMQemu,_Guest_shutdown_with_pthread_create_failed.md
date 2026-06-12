---
title: "KVM/Qemu, Guest shutdown with pthread_create failed: Resource temporarily unavailabl"
date: 2012-06-06
forum: Server Platforms
---

### Post by jbos on 2012-06-06
Hello,

on my host I run 4 guests linux systems in KVM. 

Lately I see completely unmotivated shutdowns of one or more of those guests, all with the following error in qemu log:

```

# tail -f /var/log/libvirt/qemu/guest0.log

2012-06-06 17:09:10.443: shutting down
char device redirected to /dev/pts/3
pthread_create failed: Resource temporarily unavailable

```This is usually happening while the system is more or less idle. 

Any Idea whats going wrong here?

---

### Post by jbos on 2012-06-07
Alright, though I think I found a solution.

It all looks like that kvm / libvirt- user is hitting the "max process" limit.

Short-Way solution is to set (overwrite) "max processes" in /etc/libvirt/qemu.conf

---

### Post by jiangli on 2012-09-17
Hello,i met the same problem,but i didn't find the 'etc/libvirt/qemu.conf',can you help me?thank you

---

