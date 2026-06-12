---
title: "Ubuntu Server lspci bug?"
date: 2013-03-16
forum: Server Platforms
---

### Post by MrMustard on 2013-03-16
Hi all,

So I wasted about 3 days figuring this out. 

I have a XenServer 6.1 with all the latest patches. I have enabled SR-IOV in the Dell R620 bios. I have a Ubuntu 12.04 LTS **server **guest. I made all the necessary sr-iov changes on both guest and dom0.

The problem arose when the guest VM could never see the newly attached 10GigE card. lspci always shows empty and I can't attach the pci interface. Is this normal?

I installed 12.04 LTE desktop and it works like a charm. lspci shows everything and it all works.

~# lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.2 USB controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 SCSI storage controller: XenSource, Inc. Xen Platform Device (rev 01)
00:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
[B]00:05.0 Ethernet controller: Intel Corporation 82599 Ethernet Controller Virtual Function (rev 01)
[/B]
~# uname -a
Linux client1 3.2.0-38-virtual #61-Ubuntu SMP Tue Feb 19 12:37:47 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




Is there a major difference between server and desktop?? Both are amd64. I even tried taking a server and running `apt-get install ubuntu-desktop` and it still doesn't work.

Am I missing something? Why does server never show any lspci output??

Thanks in advance.

---

