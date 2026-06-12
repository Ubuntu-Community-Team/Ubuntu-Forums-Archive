---
title: "Hyper-V new 'Quick Create' Ubuntu 18.04.01 LTS errors on boot"
date: 2019-01-28
forum: Virtualisation
---

### Post by oschoices on 2019-01-28
Hi,

After enabling Hyper-V in Windows 10 Pro and following the 'Quick Create' type wizard in Hyper-V to create a Ubuntu 18.04.01 LTS virtual machine, Hyper-V encounters the following two errors when trying to boot this virtual machine.

This is following the completion of the 'Quick Create' wizard to establish the Hyper-V settings for this particular virtual machine.

When starting this virtual machine the window that this is occurring in displays the following two errors:


[LIST]
[*]Spectre V2: Spectre mitigation LFENCE not serializing, switching to generic retpoline.
[*]PCI: Fatal: No config space function found.
[/LIST]

This results in the Ubuntu boot up failing and falling back to the Grub menu.

I'm using Windows 10 Pro 64bit, version 1809 on a HP EliteBook 745 G5 notebook which uses an AMD Ryzen 5 2500u CPU.

Any help much appreciated.

---

