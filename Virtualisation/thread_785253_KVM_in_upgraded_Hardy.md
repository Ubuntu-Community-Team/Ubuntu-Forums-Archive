---
title: "KVM in upgraded Hardy"
date: 2008-05-07
forum: Virtualisation
---

### Post by tjajab on 2008-05-07
I upgraded from Gutsy to Hardy and my VMware installation broke, which I read was a known problem. However, I understood that KVM was supposed to be the preferred virtualization software in Hardy, but it did not come with my upgrade, so I guess I will have to install it. Is it enough just to do ```
sudo apt-get install kvm
``` or which more packages are needed? How do I use it when installed (or rather, where could I find a good tutorial or instruction)?

As a bonus question; is there a way to convert my pretty recent vmware WinXP image to KVM? (It seems to consist of several vmdk-files, a vmsd-file and a vmx-file.)

Best regards,
a newbie in the virtualization world

---

### Post by eighto2 on 2008-05-07
you're right, i found some articles in the wiki, and looking through the forums, there's nothing that really shows you how to get it working, or what exactly is needed

---

### Post by Eil on 2008-05-07
The official docs for KVM seem to be very rough and even incorrect in some places. I'm disappointed that they didn't make a better effort at supporting KVM for the Hardy release.

---

### Post by tjajab on 2008-05-14
Bump

---

### Post by ericy on 2008-05-14
> **tjajab said:**
> Is it enough just to do ```
sudo apt-get install kvm
``` or which more packages are needed? 

It's pretty much it. Upon install, it will also show you recommended packages. I believe "qemu" is one of them.
(You'll need qemu-img, which is in qemu package, to create a disk image).

> As a bonus question; is there a way to convert my pretty recent vmware WinXP image to KVM? (It seems to consist of several vmdk-files, a vmsd-file and a vmx-file.)

If I remember it correctly, kvm(qemu) also reads kvm file (compatibility level 6). Or do a Google search.

---

### Post by sndnichols on 2008-05-14
Here is somthing that may be of use. I don't know if you have been here or not. [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by lex1 on 2008-05-14
Hardy unlike debian etch is not tested enough its the same on three or four packages still not ok


lex1

---

