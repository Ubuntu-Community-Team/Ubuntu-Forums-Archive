---
title: "Problem with nfs kernel server"
date: 2014-11-30
forum: Server Platforms
---

### Post by arief-arovah on 2014-11-30
Hi guys,

I need help, i have server with Ubuntu 14.04.1 LTS operating system and kernel 3.16.0-031600-generic 86_64 x86_64 x86_64 GNU/Linux. There are NFS kernel server, openfire, mysql, and apache installed on server. Before my server upgraded from Ubuntu 12.04 to 14.04 that never get high load average. But now some times for 3 days server always get high load average, it can be more than 30,00 and Client can not mount nfs  to server. What's wrong with nfs-kernel-server in my server? and what solution for this issue ? Here log from log.kern :

Dec  1 09:26:26 okusi0 kernel: [165539.146216] kernel BUG at /home/apw/COD/linux/fs/attr.c:238!
Dec  1 09:26:26 okusi0 kernel: [165539.148617] invalid opcode: 0000 [#1] SMP 
Dec  1 09:26:26 okusi0 kernel: [165539.150426] Modules linked in: xt_LOG xt_limit xt_tcpudp iptable_filter ip_tables x_tables nfnetlink_queue nfnetlink_log nfnetlink bluetooth 6lowpan_iphc rpcsec_gss_krb5 nfsv4 nfsd auth_rpcgss nfs_acl nfs lockd sunrpc fscache intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper serio_raw cryptd gpio_ich i7core_edac edac_core lpc_ich ipmi_si tpm_infineon ipmi_msghandler mac_hid lp parport igb i2c_algo_bit dca ptp pps_core
Dec  1 09:26:26 okusi0 kernel: [165539.171740] CPU: 5 PID: 27945 Comm: chown Tainted: G          I   3.16.0-031600-generic #201408031935
Dec  1 09:26:26 okusi0 kernel: [165539.175654] Hardware name: HP ProLiant DL160 G6  , BIOS O33 05/01/2012
Dec  1 09:26:26 okusi0 kernel: [165539.178426] task: ffff88029ff09440 ti: ffff880007058000 task.ti: ffff880007058000
Dec  1 09:26:26 okusi0 kernel: [165539.181603] RIP: 0010:[<ffffffff811fd2ab>]  [<ffffffff811fd2ab>] notify_change+0x34b/0x3b0
Dec  1 09:26:26 okusi0 kernel: [165539.185154] RSP: 0018:ffff88000705bdf8  EFLAGS: 00010202
Dec  1 09:26:26 okusi0 kernel: [165539.187406] RAX: 0000000033bef747 RBX: 0000000000001847 RCX: 0000000033bef747
Dec  1 09:26:26 okusi0 kernel: [165539.190436] RDX: 0000000033bef747 RSI: 00000000547bd1d0 RDI: 0000000000000001
Dec  1 09:26:26 okusi0 kernel: [165539.193466] RBP: ffff88000705be68 R08: ffffea000b9e5080 R09: ffffffff8122bcc8
Dec  1 09:26:26 okusi0 kernel: [165539.196496] R10: ffff880237810800 R11: 0000000000000000 R12: ffff88000705bf38
Dec  1 09:26:26 okusi0 kernel: [165539.199526] R13: ffff88026339c600 R14: ffff88000705be90 R15: ffff880363582040
Dec  1 09:26:26 okusi0 kernel: [165539.349031] FS:  00007f2a03dd1740(0000) GS:ffff88043fc20000(0000) knlGS:0000000000000000
Dec  1 09:26:26 okusi0 kernel: [165539.504848] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Dec  1 09:26:26 okusi0 kernel: [165539.583366] CR2: 0000000001e75018 CR3: 0000000356be4000 CR4: 00000000000007e0
Dec  1 09:26:26 okusi0 kernel: [165539.739629] Stack:
Dec  1 09:26:26 okusi0 kernel: [165539.815319]  ffff880000000000 ffff88000705bee0 ffff8800070585f8 ffffffff00000000

Thank you for any suggestion ....

---

