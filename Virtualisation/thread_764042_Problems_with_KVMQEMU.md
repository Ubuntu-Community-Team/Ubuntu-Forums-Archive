---
title: "Problems with KVM/QEMU"
date: 2008-04-23
forum: Virtualisation
---

### Post by Titan8990 on 2008-04-23
Alright, I am trying to run a virtual instance of Windows XP using KVM/QEMU in Ubuntu 7.10. Hardware virtualization is enabled in the BIOS. At first everything was perfect. I followed the step by step guide found here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM).

I got everything running correctly then I followed the instructions for Virtual NICs Bridged Directly to Outside. Since I did this I get an error message when launching my virtual instance of Windows. 

```
open /dev/kvm: File or directory not found
Could not initialize KVM, will disable KVM support
```

So I made a symbolic link from /usr/bin/kvm to /dev.

Then I get the following error:

```
open /dev/kvm: Text file busy
Could not initialize KVM, will disable KVM support
```

Anyone have any idea on what went wrong?

---

### Post by Titan8990 on 2008-04-23
Sorry guys but I got it figured out. Next time I will search the forums a bit better before posting.

---

