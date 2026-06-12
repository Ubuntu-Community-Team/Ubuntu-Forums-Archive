---
title: "pcidevice in KVM."
date: 2009-03-31
forum: Virtualisation
---

### Post by typerrrrrrrr on 2009-03-31
Hi!

I'm running KVM (1:84+dfsg-0ubuntu9) with a Windows XP guest on top of a Jaunty host upgraded to be up to date as of March 31.  In normal use everything works quite well in the guest.  My problem occurs when I try to hand off a PCI device to the guest OS.  The two devices that I have tried are a SmartCard reader, and a Wireless card.  I've made sure that they do not have any modules loaded for them on the host, and that they are not on shared interrupts.

To share the devices I am using

kvm -pcidevice host=0c:00.0 ....

The lspci for the host in question looks like:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


When the guest OS starts I begin to see a solid stream of the following errors in kern.log:

[  144.057166] WARNING: at /build/buildd/linux-2.6.28/kernel/irq/manage.c:225 __enable_irq+0x2f/0x80()
[  144.057169] Unbalanced enable for IRQ 18
[  144.057170] Modules linked in: tun binfmt_misc ppdev bnep kvm_intel kvm input_polldev bridge stp lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event joydev snd_seq snd_timer snd_seq_device psmouse iTCO_wdt iTCO_vendor_support video snd soundcore serio_raw dcdbas usbhid output snd_page_alloc intel_agp tg3 fbcon tileblit font bitblit softcursor
[  144.057206] Pid: 3386, comm: kvm Tainted: G        W  2.6.28-11-generic #38-Ubuntu
[  144.057208] Call Trace:
[  144.057214]  [<ffffffff80250927>] warn_slowpath+0xb7/0xf0
[  144.057219]  [<ffffffff802b6676>] ? get_page_from_freelist+0xd6/0x190
[  144.057224]  [<ffffffff80225f6d>] ? native_send_call_func_single_ipi+0x2d/0x30
[  144.057241]  [<ffffffffa0240000>] ? ack_flush+0x0/0x10 [kvm]
[  144.057245]  [<ffffffff8027a225>] ? smp_call_function_single+0xc5/0x100
[  144.057255]  [<ffffffffa0240000>] ? ack_flush+0x0/0x10 [kvm]
[  144.057265]  [<ffffffffa0241041>] ? gfn_to_hva+0x11/0x90 [kvm]
[  144.057276]  [<ffffffffa02411b2>] ? kvm_read_guest_page+0x62/0x70 [kvm]
[  144.057287]  [<ffffffffa025635d>] ? pic_irq_request+0x2d/0x80 [kvm]
[  144.057291]  [<ffffffff8029fd4f>] __enable_irq+0x2f/0x80
[  144.057294]  [<ffffffff8029fdf2>] enable_irq+0x52/0x80
[  144.057304]  [<ffffffffa02408eb>] kvm_assigned_dev_ack_irq+0x2b/0x40 [kvm]
[  144.057315]  [<ffffffffa0243f1a>] kvm_notify_acked_irq+0x3a/0x60 [kvm]
[  144.057325]  [<ffffffffa0243adc>] kvm_ioapic_update_eoi+0x4c/0xa0 [kvm]
[  144.057336]  [<ffffffffa02582f5>] apic_mmio_write+0x215/0x440 [kvm]
[  144.057346]  [<ffffffffa024614e>] ? vcpu_find_mmio_dev+0x3e/0x80 [kvm]
[  144.057356]  [<ffffffffa0248e7b>] emulator_write_emulated_onepage+0x9b/0x120 [kvm]
[  144.057366]  [<ffffffffa0248f70>] emulator_write_emulated+0x70/0x90 [kvm]
[  144.057378]  [<ffffffffa025338f>] x86_emulate_insn+0x4ef/0x32e0 [kvm]
[  144.057388]  [<ffffffffa025152e>] ? do_insn_fetch+0x8e/0x100 [kvm]
[  144.057399]  [<ffffffffa0252d82>] ? x86_decode_insn+0x852/0x970 [kvm]
[  144.057409]  [<ffffffffa0241041>] ? gfn_to_hva+0x11/0x90 [kvm]
[  144.057419]  [<ffffffffa024a23f>] emulate_instruction+0x15f/0x2f0 [kvm]
[  144.057430]  [<ffffffffa024fbf5>] kvm_mmu_page_fault+0x65/0xb0 [kvm]
[  144.057438]  [<ffffffffa0272cdf>] handle_exception+0x2ef/0x360 [kvm_intel]
[  144.057443]  [<ffffffffa0271ca5>] kvm_handle_exit+0xb5/0x1d0 [kvm_intel]
[  144.057453]  [<ffffffffa0245978>] vcpu_enter_guest+0x1f8/0x400 [kvm]
[  144.057463]  [<ffffffffa0242749>] ? gfn_to_pfn+0x49/0x180 [kvm]
[  144.057474]  [<ffffffffa0247c49>] __vcpu_run+0x69/0x2d0 [kvm]
[  144.057484]  [<ffffffffa024b90a>] kvm_arch_vcpu_ioctl_run+0x8a/0x1f0 [kvm]
[  144.057494]  [<ffffffffa0240582>] kvm_vcpu_ioctl+0x2e2/0x5a0 [kvm]
[  144.057499]  [<ffffffff8041c1c5>] ? rb_erase+0xe5/0x170
[  144.057504]  [<ffffffff80210529>] ? __switch_to+0x109/0x490
[  144.057509]  [<ffffffff802f62d1>] vfs_ioctl+0x31/0xa0
[  144.057514]  [<ffffffff8069c97c>] ? thread_return+0x37/0x36b
[  144.057517]  [<ffffffff802f6685>] do_vfs_ioctl+0x75/0x230
[  144.057521]  [<ffffffff802f68d9>] sys_ioctl+0x99/0xa0
[  144.057524]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[  144.057526] ---[ end trace 3252113f61a5e73c ]---



These errors slow the host greatly and i do not see the device inside of the guest OS.

The host is running on a Intel Core2 T5600.

Is there anything obvious that I am missing, or known bugs/patches?  (I did try searching Launchpad, but couldn't see anything.

Help help would be welcomed, thank you!

---

