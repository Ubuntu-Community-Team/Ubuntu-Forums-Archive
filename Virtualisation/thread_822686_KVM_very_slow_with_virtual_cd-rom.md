---
title: "KVM very slow with virtual cd-rom"
date: 2008-06-08
forum: Virtualisation
---

### Post by PilotJLR on 2008-06-08
Hello,
I'm experimenting with KVM on an Ubuntu Hardy 8.04 system.

My computer is Intel based (Core2Quad); VT is enabled in BIOS and only kvm is using the VT features.
kvm and kvm-intel are both loaded as well.

Using KVM, I am able to install some OS's... for example, Ubuntu 8.04 works great as a guest under KVM.

CentOS 5, however, does NOT work as a guest. I can boot the install DVD for CentOS, but it is incredibly slow. I waited 4 hours, and anaconda isn't even done loading! Console 4 shows the following error being repeated many, many times:
```

hdc: DSC: timeout

```

I've googled it like crazy, and but have found nothing helpful.

This problem is also present with Solaris and FreeBSD guests.


Anyone seen this problem before? I'm fairly sure the problem affects virtual CD-ROM only.
Any ideas?

Thanks!!

---

### Post by besson3c on 2008-06-14
FWIW, I'm having this very same problem... It it indeed related to using a virtual CD-ROM (i.e. disk image)? Does this happen with a physical CD (i.e. pointing to /dev/scd0)?

---

### Post by besson3c on 2008-06-14
I'm not sure if I'm getting those same log messages though, they aren't appearing in my libvirt, kern.log, or messages logs... However, performance is indeed painfully, painfully slow.

---

### Post by PilotJLR on 2008-06-15
Thanks for the suggestion! Unfortunately, no improvement... I used a Centos 5.1 DVD that I have (the dvd's worked many times before), but the guest is still very, very slow.

The DSC timeouts I'm getting are actually in the guest, not my ubuntu host. I see those errors by going to console 4 during the centos install.

Please do let me know if you have any other ideas!! I've also filed a bug on this:
[https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/239355](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/239355)

---

### Post by PilotJLR on 2008-06-15
Interestingly enough, Windows Server 2008 works great under KVM! Even using an ISO as a virtual DVD.

---

