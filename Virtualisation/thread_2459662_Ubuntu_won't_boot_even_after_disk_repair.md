---
title: "Ubuntu won't boot even after disk repair"
date: 2021-03-23
forum: Virtualisation
---

### Post by aceojack on 2021-03-23
Hi all,
I recently tried to increase the space on my VM copy of Ubuntu via fdisk. This is due to the VM being unable to boot properly due to lack of space. I have done this before following this ([https://codesilence.wordpress.com/2013/03/14/live-resizing-of-an-ext4-filesytem-on-linux/](https://codesilence.wordpress.com/2013/03/14/live-resizing-of-an-ext4-filesytem-on-linux/)) tutorial. I did it today but when rebooting, was met with the error "unknown filesystem". 

I tried to solve the issue doing "ls" and seeing where the boot is located. Sadly it returned "unknown filesystem" for everything. I resorted to trying to use boot-repair as suggested by many people. I follow their instructions however, it did not work. The tutorials said to post the link to the paste-bin the repair-boot created. [http://paste.ubuntu.com/p/cW94phbD7w/](http://paste.ubuntu.com/p/cW94phbD7w/)

Please let me know if there is anything I can do.

Thank you for your help
Jack

---

### Post by mikewhatever on 2021-03-23
The output of fdisk has this:
```

fdisk -l (filtered): ___________________________________________________________

Disk sda: 110 GiB, 118111600640 bytes, 230686720 sectors
Disk identifier: 0x6fe04560
      Boot    Start       End   Sectors Size Id Type
sda1           2048  23068671  23066624  11G 83 Linux
sda2       23068672 230686719 207618048  99G  5 Extended
sda5       23070720 230686719 207616000  99G 82 Linux swap / Solaris
...

```

Is that what you wanted?
It looks like the linux partitions are still there, but the root partition is still too small, and swap is way too big.

---

### Post by slickymaster on 2021-03-23
Thread moved to **Virtualisation** for a better fit

---

### Post by ActionParsnip on 2021-03-23
The reboot part isn't needed. Did you fsck the partition after the resize?

---

### Post by aceojack on 2021-03-23
I didn't fsck I don't believe. What does it do?

---

### Post by aceojack on 2021-03-23
> **mikewhatever said:**
> The output of fdisk has this:
```

fdisk -l (filtered): ___________________________________________________________

Disk sda: 110 GiB, 118111600640 bytes, 230686720 sectors
Disk identifier: 0x6fe04560
      Boot    Start       End   Sectors Size Id Type
sda1           2048  23068671  23066624  11G 83 Linux
sda2       23068672 230686719 207618048  99G  5 Extended
sda5       23070720 230686719 207616000  99G 82 Linux swap / Solaris
...

```

Is that what you wanted?
It looks like the linux partitions are still there, but the root partition is still too small, and swap is way too big.

[COLOR=#000000]Ok thank you. How do I increase the size of the root partition from the grub rescue console? Do I have to use repair-boot and use the console through there?[/COLOR]

---

### Post by mikewhatever on 2021-03-26
> **aceojack said:**
> [COLOR=#000000]Ok thank you. How do I increase the size of the root partition from the grub rescue console? Do I have to use repair-boot and use the console through there?[/COLOR]

I don't think grub has fdisk to resize partitions. Use the same howto you've linked to in post #1.

---

### Post by oldfred on 2021-03-26
But in Boot-Repair's report, it says sda1 is FAT32. That cannot be a Linux / (root) partition.
UEFI uses a FAT32 partition for the ESP - efi system partition. But only if booting in UEFI boot mode, may you have that as first partition.
And UEFI normally uses gpt, which does not use extended & logical partitions.

Did you convert / from ext4 to fAT32 somehow?

---

