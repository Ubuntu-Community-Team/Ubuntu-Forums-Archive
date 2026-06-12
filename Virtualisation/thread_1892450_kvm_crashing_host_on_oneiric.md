---
title: "kvm crashing host on oneiric"
date: 2011-12-08
forum: Virtualisation
---

### Post by pdwerryhouse on 2011-12-08
Hi all,

Has anyone got kvm working successfully under oneiric?  I have just upgraded my test server from lucid, where kvm was working well, to oneric and now it is crashing the host regularly. I can repeat the crash simply by starting up a guest, using Ubuntu, and then runing apt-get dist-upgrade on it.

These are the logs from syslog after it locks up hard:

```
Dec  8 17:32:04 nelson kernel: [  631.968219] BUG: unable to handle kernel paging request at ffffed7fffffffd8
Dec  8 17:32:04 nelson kernel: [  631.970434] IP: [<ffffffffa01f7243>] __mmu_unsync_walk+0xa3/0x250 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.971534] PGD 0
Dec  8 17:32:04 nelson kernel: [  631.972008] Oops: 0000 [#1] SMP
Dec  8 17:32:04 nelson kernel: [  631.972008] CPU 0
Dec  8 17:32:04 nelson kernel: [  631.972008] Modules linked in: snd_hrtimer xt_mac speedstep_lib ip6table_filter ip6_tables ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_CHECKSUM iptable_mangle xt_tcpudp iptable_filter ip_tables x_tables xfrm_user xfrm4_tunnel tunnel4 ipcomp xfrm_ipcomp esp4 ah4 deflate ctr twofish_generic twofish_x86_64 twofish_common camellia serpent blowfish cast5 des_generic xcbc rmd160 sha512_generic crypto_null af_key parport_pc ppdev bridge stp nfsd nfs lockd fscache auth_rpcgss nfs_acl binfmt_misc sunrpc snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm i915 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer drm_kms_helper drm snd_seq_device snd dm_multipath psmouse soundcore snd_page_alloc i2c_algo_bit serio_raw mei(C) video kvm_intel kvm lp parport dummy raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx usbhid hid raid1 raid0 firewire_ohci multipath
Dec  8 17:32:04 nelson kernel: firewire_core crc_itu_t e1000 linear btrfs e1000e zlib_deflate libcrc32c
Dec  8 17:32:04 nelson kernel: [  631.972008]
Dec  8 17:32:04 nelson kernel: [  631.972008] Pid: 8460, comm: kvm Tainted: G         C  3.0.0-13-server #22-Ubuntu                  /DG45ID
Dec  8 17:32:04 nelson kernel: [  631.972008] RIP: 0010:[<ffffffffa01f7243>]  [<ffffffffa01f7243>] __mmu_unsync_walk+0xa3/0x250 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008] RSP: 0018:ffff880221955b48  EFLAGS: 00010212
Dec  8 17:32:04 nelson kernel: [  631.972008] RAX: 0000037fffffffc8 RBX: ffff88021eea3960 RCX: 0000007ffffffff8
Dec  8 17:32:04 nelson kernel: [  631.972008] RDX: 00000000000001ff RSI: 0000000000000200 RDI: 0000000000000040
Dec  8 17:32:04 nelson kernel: [  631.972008] RBP: ffff880221955b88 R08: ffff88021eea39f8 R09: 00000000000001c0
Dec  8 17:32:04 nelson kernel: [  631.972008] R10: 0000000000000000 R11: 0000000000000008 R12: ffff88021eea39c0
Dec  8 17:32:04 nelson kernel: [  631.972008] R13: ffff880221955b98 R14: ffffea0000000000 R15: 000ffffffffff000
Dec  8 17:32:04 nelson kernel: [  631.972008] FS:  00007f8908184700(0000) GS:ffff88023bc00000(0000) knlGS:0000000000000000
Dec  8 17:32:04 nelson kernel: [  631.972008] CS:  0010 DS: 002b ES: 002b CR0: 000000008005003b
Dec  8 17:32:04 nelson kernel: [  631.972008] CR2: ffffed7fffffffd8 CR3: 000000022136f000 CR4: 00000000000026e0
Dec  8 17:32:04 nelson kernel: [  631.972008] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec  8 17:32:04 nelson kernel: [  631.972008] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec  8 17:32:04 nelson kernel: [  631.972008] Process kvm (pid: 8460, threadinfo ffff880221954000, task ffff88022b152e40)
Dec  8 17:32:04 nelson kernel: [  631.972008] Stack:
Dec  8 17:32:04 nelson kernel: [  631.972008]  ffff88021eea31e0 0000000000000001 ffff880221955b88 ffff880220378000
Dec  8 17:32:04 nelson kernel: [  631.972008]  ffff880220378000 ffff880221955cc8 ffff88021eea3960 ffff88022b152e40
Dec  8 17:32:04 nelson kernel: [  631.972008]  ffff880221955d08 ffffffffa01fd738 ffff88021eea3960 0000000000000000
Dec  8 17:32:04 nelson kernel: [  631.972008] Call Trace:
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01fd738>] mmu_sync_children+0x88/0x320 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01f9596>] ? mmu_free_roots+0xe6/0x1c0 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01fab56>] ? kvm_mmu_mark_parents_unsync+0x16/0x20 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01fe0b9>] ? kvm_mmu_get_page+0x389/0x3b0 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa0257a78>] ? skip_emulated_instruction+0x68/0x70 [kvm_intel]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01fda8b>] mmu_sync_roots+0xbb/0x1e0 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01ffd98>] kvm_mmu_load+0x48/0x90 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01f4540>] vcpu_enter_guest+0x470/0x510 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01f4b88>] __vcpu_run+0x158/0x2d0 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01f4d7e>] kvm_arch_vcpu_ioctl_run+0x7e/0x150 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffffa01de02a>] kvm_vcpu_ioctl+0x4ba/0x750 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffff811792c9>] do_vfs_ioctl+0x89/0x310
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffff81097d65>] ? sys_futex+0x105/0x1a0
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffff811795e1>] sys_ioctl+0x91/0xa0
Dec  8 17:32:04 nelson kernel: [  631.972008]  [<ffffffff81607102>] system_call_fastpath+0x16/0x1b
Dec  8 17:32:04 nelson kernel: [  631.972008] Code: 48 3b 05 f9 a0 02 00 0f 84 e3 00 00 00 a8 80 0f 85 db 00 00 00 4c 21 f8 48 c1 e8 0c 48 8d 0c c5 00 00 00 00 48 c1 e0 06 48 29 c8 <4a> 8b 7c 30 10 8b 77 50 85 f6 0f 84 e5 00 00 00 80 7f 49 00 41
Dec  8 17:32:04 nelson kernel: [  631.972008] RIP  [<ffffffffa01f7243>] __mmu_unsync_walk+0xa3/0x250 [kvm]
Dec  8 17:32:04 nelson kernel: [  631.972008]  RSP <ffff880221955b48>
Dec  8 17:32:04 nelson kernel: [  631.972008] CR2: ffffed7fffffffd8
Dec  8 17:32:04 nelson kernel: [  631.972008] ---[ end trace bc7ad497b1e0a559 ]---
Dec  8 17:32:09 nelson kernel: [  636.275887] rmap_remove: ffff880222a23ff8 0->BUG
Dec  8 17:32:09 nelson kernel: [  636.275935] ------------[ cut here ]------------
Dec  8 17:32:09 nelson kernel: [  636.276008] kernel BUG at /build/buildd/linux-3.0.0/arch/x86/kvm/mmu.c:698!
Dec  8 17:32:09 nelson kernel: [  636.276008] invalid opcode: 0000 [#2] SMP
Dec  8 17:32:09 nelson kernel: [  636.276008] CPU 2
Dec  8 17:32:09 nelson kernel: [  636.276008] Modules linked in: snd_hrtimer xt_mac speedstep_lib ip6table_filter ip6_tables ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_CHECKSUM iptable_mangle xt_tcpudp iptable_filter ip_tables x_tables xfrm_user xfrm4_tunnel tunnel4 ipcomp xfrm_ipcomp esp4 ah4 deflate ctr twofish_generic twofish_x86_64 twofish_common camellia serpent blowfish cast5 des_generic xcbc rmd160 sha512_generic crypto_null af_key parport_pc ppdev bridge stp nfsd nfs lockd fscache auth_rpcgss nfs_acl binfmt_misc sunrpc snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm i915 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer drm_kms_helper drm snd_seq_device snd dm_multipath psmouse soundcore snd_page_alloc i2c_algo_bit serio_raw mei(C) video kvm_intel kvm lp parport dummy raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx usbhid hid raid1 raid0 firewire_ohci multipath
Dec  8 17:32:09 nelson kernel: firewire_core crc_itu_t e1000 linear btrfs e1000e zlib_deflate libcrc32c
Dec  8 17:32:09 nelson kernel: [  636.276008]
Dec  8 17:32:09 nelson kernel: [  636.276008] Pid: 8507, comm: kvm Tainted: G      D  C  3.0.0-13-server #22-Ubuntu                  /DG45ID
Dec  8 17:32:09 nelson kernel: [  636.276008] RIP: 0010:[<ffffffffa01f8173>]  [<ffffffffa01f8173>] rmap_remove+0x1b3/0x1c0 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008] RSP: 0018:ffff88022110fb38  EFLAGS: 00010296
Dec  8 17:32:09 nelson kernel: [  636.276008] RAX: 000000000000003a RBX: ffff880222a23ff8 RCX: 0000000000000000
Dec  8 17:32:09 nelson kernel: [  636.276008] RDX: 0000000000000000 RSI: 0000000000000082 RDI: 0000000000000246
Dec  8 17:32:09 nelson kernel: [  636.276008] RBP: ffff88022110fb58 R08: 000000000000000a R09: 0000000000000000
Dec  8 17:32:09 nelson kernel: [  636.276008] R10: 0000000000000000 R11: 0000000000000000 R12: ffff8802211a4000
Dec  8 17:32:09 nelson kernel: [  636.276008] R13: ffff88018b628640 R14: ffff88018b628640 R15: ffffea0000000000
Dec  8 17:32:09 nelson kernel: [  636.276008] FS:  00007f8ebe118700(0000) GS:ffff88023bd00000(0000) knlGS:0000000000000000
Dec  8 17:32:09 nelson kernel: [  636.276008] CS:  0010 DS: 002b ES: 002b CR0: 000000008005003b
Dec  8 17:32:09 nelson kernel: [  636.276008] CR2: 0000000008dd7000 CR3: 00000002208c5000 CR4: 00000000000026e0
Dec  8 17:32:09 nelson kernel: [  636.276008] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec  8 17:32:09 nelson kernel: [  636.276008] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec  8 17:32:09 nelson kernel: [  636.276008] Process kvm (pid: 8507, threadinfo ffff88022110e000, task ffff88021e7c0000)
Dec  8 17:32:09 nelson kernel: [  636.276008] Stack:
Dec  8 17:32:09 nelson kernel: [  636.276008]  0000000000000000 ffff880222a23ff8 ffff8802211a4000 ffff8802211a4000
Dec  8 17:32:09 nelson kernel: [  636.276008]  ffff88022110fb78 ffffffffa01f81b5 ffff880222a23ff8 00000000000001ff
Dec  8 17:32:09 nelson kernel: [  636.276008]  ffff88022110fbb8 ffffffffa01f8fc3 0000000000000000 ffff88018b628640
Dec  8 17:32:09 nelson kernel: [  636.276008] Call Trace:
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01f81b5>] drop_spte+0x35/0x40 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01f8fc3>] kvm_mmu_page_unlink_children+0x53/0xf0 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01f90a9>] kvm_mmu_prepare_zap_page+0x49/0x280 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff810b6719>] ? try_stop_cpus+0x59/0x70
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa020051a>] kvm_mmu_zap_all+0x4a/0x90 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01f5696>] kvm_arch_flush_shadow+0x16/0x30 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01dd393>] __kvm_set_memory_region+0x323/0x950 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa0209e6a>] ? kvm_apic_has_interrupt+0x4a/0xa0 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01dda00>] kvm_set_memory_region+0x40/0x60 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01dea38>] kvm_vm_ioctl_set_memory_region+0x18/0x20 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffffa01dec60>] kvm_vm_ioctl+0x220/0x2e0 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff81096073>] ? futex_wake+0x113/0x130
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff81009702>] ? __switch_to+0x132/0x310
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff811792c9>] do_vfs_ioctl+0x89/0x310
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff81097d65>] ? sys_futex+0x105/0x1a0
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff811795e1>] sys_ioctl+0x91/0xa0
Dec  8 17:32:09 nelson kernel: [  636.276008]  [<ffffffff81607102>] system_call_fastpath+0x16/0x1b
Dec  8 17:32:09 nelson kernel: [  636.276008] Code: e8 ab 06 3f e1 0f 0b 48 89 de 48 c7 c7 cf 55 21 a0 31 c0 e8 98 06 3f e1 0f 0b 48 89 de 48 c7 c7 b4 55 21 a0 31 c0 e8 85 06 3f e1 <0f> 0b 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 48 83 ec 10
Dec  8 17:32:09 nelson kernel: [  636.276008] RIP  [<ffffffffa01f8173>] rmap_remove+0x1b3/0x1c0 [kvm]
Dec  8 17:32:09 nelson kernel: [  636.276008]  RSP <ffff88022110fb38>
Dec  8 17:32:09 nelson kernel: [  636.336819] ---[ end trace bc7ad497b1e0a55a ]---

```

The kernel is the stock Ubuntu x86_64 kernel - 3.0.0-13-server

qemu-kvm version: Version: 0.14.1+noroms-0ubuntu6

The CPU is:  Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz

8Gb of memory, and 10Gb of swap space.

This was all working fine under Lucid; all I've done is upgrade to oneiric, and there weren't any other changes at all.

Anyone have any ideas?

---

