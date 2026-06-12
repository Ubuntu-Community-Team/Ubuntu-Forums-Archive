---
title: "[Help]  Ubuntu Server Dom0 in Xen...EFI boot help needed"
date: 2013-07-14
forum: Virtualisation
---

### Post by KillerKelvUK on 2013-07-14
[FONT=arial]Hi, I'm struggling to write a correct xen-4.2.2.cfg file to accompany my xen-4.2.2.efi to boot my Ubuntu Server 12.04.2 as Dom0.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Built Xen from source, put the built .efi file into the same dir as the grubx64.efi file, created a .cfg file and put it in the same location.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Boot works to a point, EFI says its using the configuration file and then errors say No Dom0 kernel image specified.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Partitions:[/FONT]
[FONT=arial]500MB - EFI Partition[/FONT]
[FONT=arial]500MB - /boot[/FONT]
[FONT=arial]60GB - LVM[/FONT]
[FONT=arial]--15GB VG0-Dom0[/FONT]
[FONT=arial]--4GB VG0-Dom0_swap[/FONT]
[FONT=arial]--41GB spare[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]/boot/efi/EFI/ubuntu contains the Ubuntu grub .efi installed by default.  Also contains my xen-4.2.2.efi and .cfg.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Where should I be placing the Dom0 kernel image and initrd files?  I've currently put them into the same location as the .efi?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]xen-4.2.2.cfg looks like...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][global][/FONT]
[FONT=arial]default=xen[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][xen][/FONT]
[FONT=arial]options=console=vga dom0_mem=1024M,max=1024M dom0_max_vcpus=1 loglvl=all noreboot[/FONT]
[FONT=arial]kernel=vmlinuz-3.5.0-36-generic root=/dev/mapper/VG0-Dom0[/FONT]
[FONT=arial]ramdisk=initrd.img-3.5.0-36-generic[/FONT]
[FONT=arial]*******************End of file***************************[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any help appreciated.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Kelvin[/FONT]

---

