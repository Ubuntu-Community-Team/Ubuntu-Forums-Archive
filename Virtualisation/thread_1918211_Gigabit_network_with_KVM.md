---
title: "Gigabit network with KVM"
date: 2012-01-31
forum: Virtualisation
---

### Post by josir on 2012-01-31
Hi folks,

**Host:** Ubuntu 10.04.3 with KVM 
lspci | grep net
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

**Guest:** Ubuntu 10.04.3 
lspci:
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.2 USB Controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 Ethernet controller: Qumranet, Inc. Virtio network device

**Problem:** The virtio network device operates on 100Mbits. 

How do I know that it operates on 100Mbits ? 
I copy a single big file via rsh and I can see the real speed. The network is completely dedicated to this operations, that is, there is no other traffic between other machines.

**Question:** What do I have to do to use full bandwidth ?

Thanks in advance,
Josir Gomes

---

