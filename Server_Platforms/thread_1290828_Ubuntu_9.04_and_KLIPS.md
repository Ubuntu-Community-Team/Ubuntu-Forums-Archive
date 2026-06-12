---
title: "Ubuntu 9.04 and KLIPS"
date: 2009-10-13
forum: Server Platforms
---

### Post by ramoneiro on 2009-10-13
Hello list,
 
I'm trying to get Ubuntu 9.04 to work with openswan-2.6.23 with KLIPS support, but I'm getting a kernel Oops when connecting a windows client through L2TP/Ipsec. This is a brand new install, no other services running and openswan is compiled from source. Here is the Oops:
 
[ 465.815762] BUG: unable to handle kernel NULL pointer dereference at 00000000
[ 465.817640] IP: [<f7d416ad>] aes_32+0x3/0x496 [ipsec]
[ 465.827466] *pde = 00000000
[ 465.828658] Oops: 0002 [#1] SMP
[ 465.831186] last sysfs file: /sys/module/ccm/initstate
[ 465.831186] Dumping ftrace buffer:
[ 465.831186] (ftrace buffer empty)
[ 465.831186] Modules linked in: binfmt_misc ipsec ccm serpent blowfish twofish twofish_common ecb xcbc cbc sha256_generic sha512_generic des_generic aes_i586 aes_generic bridge stp bnep video output input_polldev lp ppdev psmouse serio_raw pcspkr i2c_piix4 parport_pc parport pcnet32 mii floppy e1000 fbcon tileblit font bitblit softcursor
[ 465.831186]
[ 465.831186] Pid: 3545, comm: pluto Not tainted (2.6.28-15-generic #52-Ubuntu) VirtualBox
[ 465.831186] EIP: 0060:[<f7d416ad>] EFLAGS: 00210202 CPU: 0
[ 465.831186] EIP is at aes_32+0x3/0x496 [ipsec]
[ 465.831186] EAX: f5222400 EBX: f5222400 ECX: 00000004 EDX: 00000000
[ 465.831186] ESI: 00000208 EDI: f5222000 EBP: f6119aa8 ESP: f6119a94
[ 465.831186] DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[ 465.831186] Process pluto (pid: 3545, ti=f6118000 task=f52f3ed0 task.ti=f6118000)
[ 465.831186] Stack:
[ 465.831186] f5222000 00000208 f5222400 00200286 00200286 f6119ab8 00200286 f7d3ff52
[ 465.831186] 00000000 f6119ac0 f7d3fb6f f6119af8 f7d3c9b8 00000010 c182bb90 00200286
[ 465.831186] c0152b2a 00000001 f7d6d280 f6119b10 f5222000 f5222400 00000003 00000000
[ 465.831186] Call Trace:
[ 465.831186] [<f7d3ff52>] ? AES_set_key+0x12/0x20 [ipsec]
[ 465.831186] [<f7d3fb6f>] ? _aes_set_key+0xf/0x20 [ipsec]
[ 465.831186] [<f7d3c9b8>] ? ipsec_alg_enc_key_create+0x228/0x320 [ipsec]
[ 465.831186] [<c0152b2a>] ? hrtimer_try_to_cancel+0x3a/0x90
[ 465.831186] [<f7d19d80>] ? ipsec_sa_init+0x2a0/0xb20 [ipsec]
[ 465.831186] [<c014f0a8>] ? remove_wait_queue+0x38/0x50
[ 465.831186] [<c01cb9bd>] ? poll_freewait+0x3d/0xa0
[ 465.831186] [<c01cc3b4>] ? do_select+0x5a4/0x610
[ 465.831186] [<c048723b>] ? fn_hash_lookup+0x1b/0xd0
[ 465.831186] [<c0483160>] ? inet_addr_type+0x80/0xf0
[ 465.831186] [<f7d2dc04>] ? pfkey_add_parse+0xc4/0x850 [ipsec]
[ 465.831186] [<f7d34d74>] ? pfkey_address_parse+0xc4/0x340 [ipsec]
[ 465.831186] [<f7d35341>] ? pfkey_msg_parse+0x351/0x9a0 [ipsec]
[ 465.831186] [<f7d31795>] ? pfkey_key_process+0x85/0x210 [ipsec]
[ 465.831186] [<f7d31710>] ? pfkey_key_process+0x0/0x210 [ipsec]
[ 465.831186] [<f7d2af56>] ? pfkey_msg_interp+0x276/0x390 [ipsec]
[ 465.831186] [<c018eeb9>] ? find_lock_page+0x29/0x70
[ 465.831186] [<c018fea0>] ? filemap_fault+0x1c0/0x3e0
[ 465.831186] [<f7d2a717>] ? pfkey_sendmsg+0x2e7/0x4d0 [ipsec]
[ 465.831186] [<c04228f1>] ? __sock_sendmsg+0x51/0x60
[ 465.831186] [<c04229da>] ? sock_aio_write+0xda/0x130
[ 465.831186] [<c01bd751>] ? do_sync_write+0xd1/0x110
[ 465.831186] [<c014ede0>] ? autoremove_wake_function+0x0/0x50
[ 465.831186] [<c02a9999>] ? apparmor_file_permission+0x19/0x40
[ 465.831186] [<c02879bf>] ? security_file_permission+0xf/0x20
[ 465.831186] [<c01bd8f4>] ? rw_verify_area+0x54/0xd0
[ 465.831186] [<c01bde4d>] ? vfs_write+0xfd/0x110
[ 465.831186] [<c01bdf1d>] ? sys_write+0x3d/0x70
[ 465.831186] [<c0104062>] ? syscall_call+0x7/0xb
[ 465.831186] Code: 89 e5 83 ec 08 53 56 57 8b 55 0c 8b 4d 14 81 f9 80 00 00 00 72 03 c1 e9 03 83 f9 20 74 0a 83 f9 18 74 05 b9 10 00 00 00 c1 e9 02 <89> 0a 8d 41 06 89 42 04 8b 75 10 8d 7a 08 fc 55 89 c8 f3 a5 8b
[ 465.831186] EIP: [<f7d416ad>] aes_32+0x3/0x496 [ipsec] SS:ESP 0069:f6119a94
[ 465.973404] ---[ end trace e21bf571223fbfb7 ]---
 
It's worth mentioning that I've got the same crash on a Fedora 7 install. What I need to know is: should I fill a bug report? If so, where?
 
Any help would be greatly appreciated.
 
Thanks,
 
Giovani

---

