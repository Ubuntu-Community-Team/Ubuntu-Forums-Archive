---
title: "Do I need a swap file or partition"
date: 2022-06-26
forum: Server Platforms
---

### Post by blackxiao on 2022-06-26
I am going setup a HPC server with a large memory, about 2T to 4T memory. I learned that by default ubuntu will install a swap file about 2G. Do I still need a swap file for such a large memory? If not, how to install the ubuntu server without a swapfile. Thanks.

---

### Post by TheFu on 2022-06-26
"Some" swap enables some important capabilities in the kernel, so it is generally recommended to have 0.5G-1G of swap as a minimum.
There was a long thread in these forums in 2020 about swap, the purpose, why it should be used and how to size it.

At the time, I attempted to size my VM servers RAM allocations to ensure that no swap was necessary. After all, if the workload is extremely well-known and only uses 450MB of RAM and I provide 512MB of vRAM, what's the point in providing 1G of swap that will never be used too?

Even with TB of RAM, a tiny bit of swap will help performance.  Odd, but true.

Should it be a partition, Logical volume, or file?  That's a different question.  I really dislike swap files - with no real good reason, except that when it was new, the swap files were eating storage in / that I had planned to be used for programs. Swap files arrived much too late to solve the real problem that MBR partitioning causes (limit of 4 primary partitions). With GPT and LVM, we don't have any real limits on the number of partitions.  LVM is more flexible than using full partitions, but since it is for enterprise storage needs, it is more complex than most home users are willing to learn.  If you have a system with that much RAM, it is probably an enterprise server, so you should be using enterprise storage management - either ZFS or LVM.

---

### Post by oldfred on 2022-06-26
It will not create a swap file, if it finds a swap partition. So I might partition in advance, and using gpt partitioning, not old MBR(msdos).

If UEFI, be sure to include ESP - efi system partition. Only if old BIOS, with gpt you need a bios_grub partition. And you can create / and any other partitions you require. I typically do not fully partition a drive in advance.

---

