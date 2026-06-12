---
title: "Another pass through thread [solved]"
date: 2016-08-05
forum: Virtualisation
---

### Post by vuvffufg on 2016-08-05
1

---

### Post by KillerKelvUK on 2016-08-06
Hey, food for thought...your using pci-stub, this is old skool. Since kernel 4.1 binding direct to vfio-pci is possible (Google Alex Williamson vfio).

From your post, suspect you've not blacklisted your nvidia driver as your lspci output clearly shows the gfx portion of ur card is using the nvidia driver instead of the pci-stub driver?  Also your qemu line shows you using the legacy seabios instead of ovmf.

Odd observation, your lspci output shows the audio side of ur gfx card as mapped to the vfio-pci driver instead of the pci-stub driver which your grub line stipulates. Suspect this means you've posted output after trying to start the guest using your scripts which gives us bad info here so clean boot is the way to go before posting.

---

### Post by vuvffufg on 2016-08-07
Never mind, everything is peachy ignore me.

---

### Post by heiko_s on 2016-08-07
> **KillerKelvUK said:**
> Hey, food for thought...your using pci-stub, this is old skool. Since kernel 4.1 binding direct to vfio-pci is possible (Google Alex Williamson vfio).

From your post, suspect you've not blacklisted your nvidia driver as your lspci output clearly shows the gfx portion of ur card is using the nvidia driver instead of the pci-stub driver?  Also your qemu line shows you using the legacy seabios instead of ovmf.

Odd observation, your lspci output shows the audio side of ur gfx card as mapped to the vfio-pci driver instead of the pci-stub driver which your grub line stipulates. Suspect this means you've posted output after trying to start the guest using your scripts which gives us bad info here so clean boot is the way to go before posting.

I run a 3.19 kernel and use vfio-pci, but the 4.1+ kernel brings some improvements.

---

