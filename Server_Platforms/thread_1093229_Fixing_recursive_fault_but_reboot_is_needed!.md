---
title: "Fixing recursive fault but reboot is needed!"
date: 2009-03-11
forum: Server Platforms
---

### Post by fab4am on 2009-03-11
Hi,

I'm having a freeze problem on one of my ubuntu servers. I run xen 3.2 on ubuntu hardy, with 1 domU. It works a while, and then the dom0 hangs but not the domU.
On dom0, here's the logs I could see :

```
invalid opcode: 0000 [#1] SMP 
Modules linked in: xt_tcpudp xt_physdev bridge iptable_filter ip_tables x_tables parport_pc lp parport loop evdev ipv6 serio_raw psmouse 8250_pnp 8250 serial_core button iTCO_wdt iTCO_vendor_support intel_rng i82875p_edac edac_core pcspkr shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache sg sd_mod pata_acpi ata_piix ata_generic floppy e100 mii libata scsi_mod ehci_hcd uhci_hcd usbcore e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snapshot dm_mod thermal processor fan fuse

Pid: 560, comm: sh Not tainted (2.6.24-23-xen #1)
EIP: 0061:[<c1ddfb49>] EFLAGS: 00210a86 CPU: 1
EIP is at 0xc1ddfb49
EAX: c1de5520 EBX: c1deaa20 ECX: 00000004 EDX: 00000000
ESI: 00000003 EDI: 40040000 EBP: 00000000 ESP: c24dfe94
DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0069
Process sh (pid: 560, ti=c24de000 task=ed4ce690 task.ti=c24de000)
Stack: c0162355 00000000 c03fd800 c24dfee8 00000003 00000007 c24dfed0 c0162406 
       c18a1d60 c16fe35c c03fd800 0000000b c0165947 0000000b 00000000 00000007 
       00000000 c1a908c0 c1986e20 c1d85900 c1943340 c1de5520 c1ddd280 c18a1d60 
Call Trace:
 [free_hot_cold_page+0x195/0x220] free_hot_cold_page+0x195/0x220
 [__pagevec_free+0x26/0x30] __pagevec_free+0x26/0x30
 [release_pages+0x137/0x160] release_pages+0x137/0x160
 [free_pages_and_swap_cache+0x74/0xa0] free_pages_and_swap_cache+0x74/0xa0
 [exit_mmap+0xe7/0x100] exit_mmap+0xe7/0x100
 [mmput+0x23/0x80] mmput+0x23/0x80
 [do_exit+0x165/0x8b0] do_exit+0x165/0x8b0
 [<c011df90>] default_wake_function+0x0/0x10
 [do_group_exit+0x2a/0xa0] do_group_exit+0x2a/0xa0
 [syscall_call+0x7/0x0b] syscall_call+0x7/0xb
 =======================
Code: 20 00 80 00 00 40 01 00 00 00 ff ff ff ff 00 00 00 00 00 00 00 00 2b 00 00 00 40 01 40 ed 00 90 35 ec 00 00 00 40 00 00 00 00 ff <ff> ff ff 00 00 00 00 00 00 00 00 00 00 00 00 f8 b1 98 c1 d8 68 
EIP: [<c1ddfb49>] 0xc1ddfb49 SS:ESP 0069:c24dfe94
---[ end trace dc724b674c67b8be ]---
Fixing recursive fault but reboot is needed!

```


Have you an idea of what could cause this? What I can try to understand where is the problem?

Thanks for your help

Amandine

---

### Post by majedaly on 2011-02-03
Hi!
I had the same problem,It kept me banging my head in the wall for couple of days.  It was due to Geoforce VGA card. When I removed, everything went OK

---

### Post by smiley97111 on 2012-08-06
I installed a new vid card to bypass the embedded Intel but still had the same problem with a UNetBootin FlashDrive install of Kubuntu 12.04 64bit.  

What did it for me was pulling two half gig sticks and leaving a pair of 2gig sticks.

Smiley

---

### Post by lisati on 2012-08-06
Old thread closed

---

