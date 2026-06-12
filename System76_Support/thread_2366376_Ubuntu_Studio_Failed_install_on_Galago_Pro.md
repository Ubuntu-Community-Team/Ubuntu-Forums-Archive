---
title: "Ubuntu Studio: Failed install on Galago Pro"
date: 2017-07-17
forum: System76 Support
---

### Post by muteaudio on 2017-07-17
Hi

I tried to install Ubuntu Studio 16.04 (64bit Version) on the new Galago pro today: 
the installation failed due to "Grub-efi-amd64-signed" could not be installed in /target/.
Has anybody an idea on that?
best regards

---

### Post by april-system76 on 2017-07-18
Hmm, do you have an NVMe drive? The 16.04.1 GRUB installer doesn't play nice with those. I'm not sure what version Studio is built on, though.

Still, this looks like it might be something else. Did you manually partition, or did the installer create an EFI partition for you?

---

### Post by muteaudio on 2017-07-20
> **april-system76 said:**
> Hmm, do you have an NVMe drive? The 16.04.1 GRUB installer doesn't play nice with those. I'm not sure what version Studio is built on, though.

I do indeed have a 512 GB PCIe M2 SSD drive built in (no second drive). Would it make sense to try Burg, or the 17.04 release of Ubuntu Studio?

> **april-system76 said:**
>  Still, this looks like it might be something else. Did you manually partition, or did the installer create an EFI partition for you? do indeed have a 512 Gb PCIe M2 hard drive built in (no second drive). Would it make sense, to try Burg?

I let the installer handle the job (since I trust the Ubuntu installer and just wanted to try, if the installation of Ubuntu Studio works without problems.

Thanx for getting back at me!
best regards

---

### Post by april-system76 on 2017-07-21
I'd say it's worth trying 17.04, though it looks like a 16.04.2 version exists. It *should* contain the updated GRUB installer which can handle NVMe drives. I'm still not 100% sure that's the issue, since I'd expect an error like "failed to install to target /dev/nvme" in that case.

So, maybe try writing a new 16.04.2 Studio USB, or try 17.04?

---

### Post by muteaudio on 2017-08-08
> **april-system76 said:**
> I'd say it's worth trying 17.04, though it looks like a 16.04.2 version exists. It *should* contain the updated GRUB installer which can handle NVMe drives. I'm still not 100% sure that's the issue, since I'd expect an error like "failed to install to target /dev/nvme" in that case.

So, maybe try writing a new 16.04.2 Studio USB, or try 17.04?

I tried out both 16.04.2 and 17.04 - unfortunately with the same results.

---

### Post by muteaudio on 2017-08-21
Disabling UEFI secure boot did the trick. Tried that before but  apparently forgot to save the changes (embarrassing as it is). Ubuntu  studio 17.04 is running fine.

---

