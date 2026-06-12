---
title: "Efi and gpt partition on installer"
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Fantu on 2011-12-20
As currently support (u)efi and gpt partitions? Is planned with the inclusion of choice in the installer?
Thanks for any reply

---

### Post by satanselbow on 2011-12-20
Grub2 supports EFI/GPT and will install the required components as required at install ;)

---

### Post by Fantu on 2011-12-20
Thanks for reply.
I know about grub2 efi/gpt support but if I not wrong now on ubuntu installer is not possible to choose to install efi and create gpt partitions instead of dos partitions.

---

### Post by satanselbow on 2011-12-20
I don't believe you can format the disk as gpt directly from the installer - but someone else might want to elaborate or confirm.

I would use gparted on a liveCD to create the gpt partiton table and partitions before running the installer ;)

---

### Post by oldfred on 2011-12-20
I format in advance and have used gpt with BIOS on two drives. My precise install is on my new SSD with gpt and I hope it will be my new standard working system.

Some have posted that with UEFI, you really need to partition in advance and have the efi partition created and then the installer will work. With BIOS you have to have a bios_grub partition so grub2's core.img has somewhere to go.

We have seen with drives somewhat over 1TB will automatically be formated to gpt if not formated in advance.

---

### Post by AnrDaemon on 2012-02-20
While installer don't offer you a choice between MBR and GPT, it will make a GPT label, if booted from EFI. That's my conclusion after trying (unsuccessfully) to install it on VirtualBox with EFI boot enabled.

---

