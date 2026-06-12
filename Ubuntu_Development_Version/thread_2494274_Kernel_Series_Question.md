---
title: "Kernel Series Question"
date: 2024-01-10
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2024-01-10
Here we are since yesterday with Noble
```

6.6.0-14-generic
mafoelffen@noble00:~$ lsb_release -d
No LSB modules are available.
Description:    Ubuntu Noble Numbat (development branch)

```
Curious enough, we got into the 6.5.0 series yesterday with 22.04 w/ HWE:
```

mafoelffen@Mikes-ThinkPad-T520:~$ uname -r
6.5.0-14-generic
mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 22.04.3 LTS

```
Now the question: Where does Canonical plan on being by April with kernels for the Noble LTS release?

Why am I asking?

Well, I've been working with the upstream Intel Graphics Support Team with them trying to get their OOT i915 drivers working with 6.2.0 kernels since September, when Jammy with HWE went to 6.2.0 series kernels. That's when they (intel-i915-dkms) broke for Ubuntu. They were just about there, except that it broke zfs-zed.service. They promised me that they would have it ready to test with 6.5.0 kernels, so that I could test them for Noble...

Of course Noble yesterday went to the 6.6.0 series kernels...

See where that goes? LOL. Anyone here know? Or should I post that as a LaunchPad Question?

---

### Post by IanW on 2024-01-11
Kernel 6.6 and Noble are both labelled LTS. I think that answers your question.

---

### Post by IanW on 2024-01-29
UPDATE - Canonical just announced their intent to run kernel 6.8 as standard for Noble.
[https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/](https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958/)

---

### Post by MAFoElffen on 2024-01-30
I saw that last night... I'm wondering if 22.04 will go to 6.6.0 over time. Thinking about what Mark Shuttleford let slip when he announced 24.04 as getting 12 years of support and same "also" for some earlier released LTS'es...

Right now the Intel Graphics Support Teams are working on the OOT drivers for 22.04 to get then to work with 6.5.0, and working on 6.2.0 on not causing ZFS installs to be non-booting... Been busy trying to get those to work for us. I do not think they will be ready for Noble's release with 6.8. At least for the extended drivers. Basic i915 is fine.

Parallel testing Intel Graphics SR-IOV drivers... but my tests on those are still early.

NVidia and amdgpu are another story yet... But those are just different.

---

