---
title: "Xen 4.1 and Ubuntu 12.04 - No Boot"
date: 2012-05-05
forum: Virtualisation
---

### Post by KnightAR on 2012-05-05
Hi, I'm hoping someone would point me in the right direction. I'm currently using a Ubuntu 12.04 install on a dedicated server with no access to KVM or anyway to see the boot screen. So I'm kinda in a jam to figure out what this is.

The system boots up fine in general, I can use it, get internet access, etc. However, Once I switch grub to boot into the Xen enabled kernel, The system never boots. Logs has no information on the boot, so I know that it never even booted into the system. Since I have no idea whats going on, I hope someone could point me in what went wrong.

This is a freshly installed Ubuntu 12.04 system, first thing I did was install Xen with the following command line:

> sudo apt-get install xen-hypervisor-4.1-amd64 xen-utils-4.1 xenwatch xen-tools xen-utils-common xenstore-utils


Grub Boot menu options (No modifications, Ubuntu maintained):

> title           Xen 4.1-amd64 / Ubuntu 12.04 LTS, kernel 3.2.0-24-generic
uuid            b93897e0-b858-48ec-b190-ae7054adbe04
kernel          /xen-4.1-amd64.gz
module          /vmlinuz-3.2.0-24-generic root=UUID=aa06206b-edb4-430f-b632-8039063f666e ro acpi=ht noapic console=tty0
module          /initrd.img-3.2.0-24-generic

title           Ubuntu 12.04 LTS, kernel 3.2.0-24-generic
uuid            b93897e0-b858-48ec-b190-ae7054adbe04
kernel          /vmlinuz-3.2.0-24-generic root=UUID=aa06206b-edb4-430f-b632-8039063f666e ro acpi=ht noapic vga=ext
initrd          /initrd.img-3.2.0-24-generic


The normal kernel boots up with absolutely no issues at all, so I'm stumped.


/etc/network/interfaces (blocked out ip with X's):

> auto xenbr0
iface xenbr0 inet static
  address X.X.X.19
  network X.X.X.0
  netmask 255.255.255.0
  broadcast X.X.X.255
  gateway X.X.X.1
  bridge_ports eth0

auto eth0
iface eth0 inet manual

If anyone has any suggestions at all, it would be so helpful.

Thanks!

---

### Post by hasan.akgoz on 2012-05-06
Guest VM , Can you send the ping?

---

### Post by xkcdcode on 2012-06-17
Did you solve this, I am having the same problem except on a local machine and the boot process hangs on the Ubuntu splash screen!

---

