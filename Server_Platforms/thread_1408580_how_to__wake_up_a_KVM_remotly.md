---
title: "how to  wake up a KVM remotly"
date: 2010-02-16
forum: Server Platforms
---

### Post by markp1989 on 2010-02-16
I have made a virtual machine on my server using virt-manager that i access using  virt-viewer from my desktop/laptop.


currently im having to leave the vm on all the time. which is a waste of cpu/ram etc. 

idealy i would like to be able to wake the vm up from virt-viewer or from a bash script being ran on my desktop.

thanks , Markp1989

---

### Post by markp1989 on 2010-02-21
I sorted this out. for any one interested

i edited my launcher to run this command (on the guest pc) , it boots the vm, connects to it, then shuts it down after i dissconnect :)

```
ssh 192.168.1.1 virsh start winxp ; virt-viewer --connect qemu+ssh://mark@192.168.1.1/system winxp ; ssh 192.168.1.1 virsh shutdown winxp & ;; 
```

---

