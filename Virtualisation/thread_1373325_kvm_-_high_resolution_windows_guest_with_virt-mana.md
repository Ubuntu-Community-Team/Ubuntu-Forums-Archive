---
title: "kvm - high resolution windows guest with virt-manager"
date: 2010-01-05
forum: Virtualisation
---

### Post by retval on 2010-01-05
Is it possible to have virt-manager use high resolutions with Windows guests on KVM?

---

### Post by thelamer on 2010-01-05
All of the virtual video adapters I have used in KVM max out at 1280x1024. (cirrus)

Haven't had any luck manually setting it higher either.

---

### Post by retval on 2010-01-05
Passing kvm the -vga std option seems to help with that

I tried editing the file that virt-manager came up with for my guest but not entirely sure what to edit. And its a fricken xml file....

---

