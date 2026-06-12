---
title: "W7 &amp; KUBUNTU 13.10beta both in UEFI boot problem"
date: 2013-09-27
forum: Ubuntu Development Version
---

### Post by mario20 on 2013-09-27
Hi, I've a asrock FM2 A85X motherboard that supports UEFI. I've one Crucial M4 128GB SSD.
I installed W7 in UEFI mode and then partitioned to install kubuntu 13.10 beta in UEFI mode.
I used W7 efi partition to install grub2(in the menu I selected /dev/sda1 instead of /dev/sda) and /dev/sda4 to install kubuntu, no swap partition.
The problem is that the UEFI boot entry created(KUBUNTU) is not working and I've lost the ability to boot both W7 and Kubuntu.
I would use my usb stick with kubuntu live to resque the system, but I can't succeed, even if i chroot into kubuntu installation, I can't create a working boot entry using efibootmgr.

Can someone help me?

This is actual configuration, note that of the two entry works, Windows 7 enty falls back to selection menu(loop), kubuntu entry falls to grub command line with no more warnings.


```

kubuntu@kubuntu:~$ sudo efibootmgr -v
BootCurrent: 0007
Timeout: 3 seconds
BootOrder: 0000,0003,0007,0001,0006,0005,0002
Boot0000* Windows 7     HD(1,800,32000,cbc38c48-d688-42db-83ee-b15d3880a320)File(\EFI\Microsoft\Boot\bootmgr.efi)
Boot0001* Hard Drive    BIOS(2,0,00)AMGOAMNO........o.M.4.-.C.T.1.2.8.M.4.S.S.D.2....................A...........................>..Gd-.;.A..MQ..L.0.0.0.0.0.0.0.0.3.1.7.1.9.0.7.3.3.F.7.6......AMBO
Boot0002  CD/DVD Drive  BIOS(3,0,00)AMGOAMNO........o.H.L.-.D.T.-.S.T.D.V.D.-.R.O.M. .D.H.1.6.N.S.1.0....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . . . . . . . . . ......AMBO
Boot0003* kubuntu       HD(1,800,32000,cbc38c48-d688-42db-83ee-b15d3880a320)File(\EFI\kubuntu\shimx64.efi)
Boot0005  UEFI: Built-in EFI Shell      Vendor(5023b95c-db26-429b-a648-bd47664c8012,)AMBO
Boot0006* USB   BIOS(5,0,00)AMGOAMNO........q.V.e.r.b.a.t.i.m.S.T.O.R.E. .N. .G.O. .1.1.0.0....................A.......................D..Gd-.;.A..MQ..L.V.e.r.b.a.t.i.m.S.T.O.R.E. .N. .G.O. .1.1.0.0......AMBO
Boot0007* UEFI: VerbatimSTORE N GO 1100 ACPI(a0341d0,0)PCI(12,2)USB(3,0)HD(1,800,1de7800,49464555)AMBO

```

---

### Post by oldfred on 2013-09-27
Your efi shows Windows bootmgr.efi, but I thought it was bootmgfw.efi. But I have mostly seen Windows 8 systems. (I have neither).

Grub converted to use the secure boot shim64.efi for all systems. Before it used grubx64.efi for non-secure boot systems. If you have Windows 7, you will not have secure boot as that is only pre-installed Windows 8 systems (currently).

           Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by mario20 on 2013-09-28
Thanks, I solved the problem with boot-repair, very useful!
You were right, at least regarding grub, it should be grubx64.efi instead of shim64.efi. I can't say nothing about windows 7 boot because now it boots from grub2 menu, but at least I can try to change the non working entry with the one you suggested, anyway... thanks!

---

### Post by oldfred on 2013-09-28
Glad you got it working. :)

I would back up efi partition. Most users do not do that, but it could be useful to have those files.

---

### Post by a-list-l on 2013-10-16
Just a quick note: same thing happened to me - Kubuntu 13.10beta was unable to boot on UEFI enabled motherboard (no Windows was installed).
Boot Repair fixed that. Thanks for the advice.

---

