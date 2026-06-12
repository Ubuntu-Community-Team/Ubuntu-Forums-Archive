---
title: "KVM guest  BUG: soft lockup - CPU#1 stuck for 800s! [nmbd:693]"
date: 2010-09-17
forum: Virtualisation
---

### Post by systemshq on 2010-09-17
I'm using ubuntu 10.04 64bit with a kvm ubuntu 10.04 32 bit guest with the standard ubuntu virtual machine kernel. This is all hosted on an athlon64 server. I'm using the kvm guest solely as a samba server but keep running into the following soft lock-up problems on the guest when transferring files across from a a client windows PC:-


[35716.912841] hrtimer: interrupt took 59941409 ns
[39926.497046] BUG: soft lockup - CPU#1 stuck for 800s! [nmbd:693]
[39926.500802] Modules linked in: fbcon tileblit font bitblit softcursor psmouse serio_raw vga16fb vgastate floppy
[39926.500802] 
[39926.500802] Pid: 693, comm: nmbd Tainted: G S      W  (2.6.32-24-generic-pae #42-Ubuntu) Bochs
[39926.500802] EIP: 0073:[<b7484431>] EFLAGS: 00000246 CPU: 1
[39926.500802] EIP is at 0xb7484431
[39926.500802] EAX: 00000001 EBX: 0000000e ECX: bfe35240 EDX: b7484430
[39926.500802] ESI: 00000000 EDI: bfe354b8 EBP: bfe35358 ESP: bfe35244
[39926.500802]  DS: 007b ES: 007b FS: 0000 GS: 0033 SS: 007b
[39926.500802] CR0: 80050033 CR2: b747306c CR3: 0e89f000 CR4: 000006f0
[39926.500802] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[39926.500802] DR6: ffff0ff0 DR7: 00000400
[39926.500802] Call Trace:
[39926.500802] BUG: soft lockup - CPU#0 stuck for 800s! [smbd:10089]
[39926.615447] Modules linked in: fbcon tileblit font bitblit softcursor psmouse serio_raw vga16fb vgastate floppy
[39926.615447] 
[39926.615447] Pid: 10089, comm: smbd Tainted: G S      W  (2.6.32-24-generic-pae #42-Ubuntu) Bochs
[39926.615447] EIP: 0060:[<c0346269>] EFLAGS: 00000202 CPU: 0
[39926.615447] EIP is at __make_request+0x139/0x3f0
[39926.615447] EAX: df8f2000 EBX: df91ca60 ECX: 0001c150 EDX: 00003130
[39926.615447] ESI: deccc578 EDI: 00000000 EBP: dee85bd0 ESP: dee85b9c
[39926.615447]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[39926.615447] CR0: 80050033 CR2: b6faf000 CR3: 1e814000 CR4: 000006f0
[39926.615447] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[39926.615447] DR6: ffff0ff0 DR7: 00000400
[39926.615447] Call Trace:
[39926.615447]  [<c0344df4>] generic_make_request+0x344/0x500
[39926.615447]  [<c023f67e>] ? do_mpage_readpage+0x3de/0x730
[39926.615447]  [<c0345025>] submit_bio+0x75/0x120
[39926.615447]  [<c01e855d>] ? __inc_zone_page_state+0x1d/0x20
[39926.615447]  [<c01d3179>] ? add_to_page_cache_locked+0xb9/0x120
[39926.615447]  [<c023f140>] mpage_bio_submit+0x20/0x30
[39926.615447]  [<c023fb2c>] mpage_readpages+0xec/0x100
[39926.615447]  [<c0272ec0>] ? ext3_get_block+0x0/0x110
[39926.615447]  [<c01d8865>] ? __alloc_pages_nodemask+0xc5/0x170
[39926.615447]  [<c02712a0>] ? ext3_readpages+0x0/0x20
[39926.615447]  [<c02712be>] ext3_readpages+0x1e/0x20
[39926.615447]  [<c0272ec0>] ? ext3_get_block+0x0/0x110
[39926.615447]  [<c01daf74>] __do_page_cache_readahead+0x144/0x200
[39926.615447]  [<c01db056>] ra_submit+0x26/0x30
[39926.615447]  [<c01db1c3>] ondemand_readahead+0x83/0x1d0
[39926.615447]  [<c01db38e>] page_cache_async_readahead+0x7e/0xb0
[39926.615447]  [<c01d3e0e>] T.918+0x21e/0x480
[39926.615447]  [<c01d411a>] generic_file_aio_read+0xaa/0x230
[39926.615447]  [<c02123d4>] do_sync_read+0xc4/0x100
[39926.615447]  [<c016fc70>] ? autoremove_wake_function+0x0/0x50
[39926.615447]  [<c02ff804>] ? security_file_permission+0x14/0x20
[39926.615447]  [<c0212474>] ? rw_verify_area+0x64/0xe0
[39926.615447]  [<c0212d6f>] vfs_read+0x9f/0x1a0
[39926.615447]  [<c0212310>] ? do_sync_read+0x0/0x100
[39926.615447]  [<c0213033>] sys_pread64+0x63/0x80
[39926.615447]  [<c0109763>] sysenter_do_call+0x12/0x28

The server itself has 4Gigs of RAM and the guest is only running samba in console mode - i.e. not running gnome or anything like that and has 512Mb RAM. From what I can see it seems to have got stuck on the nmbd process which seems a bit strange?? Any help most welcome please.

---

### Post by sh1ny on 2010-09-18
If this happens during file transfers from/to the virtual machine, do the following :

1. Make sure you're using virtio disks
2. Make sure you're using raw image ( or lvm volume ) for the virtual machine's disk
3. Add :
    cache='none' 
on the vm's xml file definition of the disk, i.e. :

```
    
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' **cache='none'**/>
      <source file='/srv/storage/virt/dev-sda.img'/>
      <target dev='vda' bus='virtio'/>
    </disk>
```

See if you get any improvements.

---

