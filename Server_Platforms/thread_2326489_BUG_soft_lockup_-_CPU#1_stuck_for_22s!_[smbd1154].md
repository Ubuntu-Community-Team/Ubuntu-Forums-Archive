---
title: "BUG: soft lockup - CPU#1 stuck for 22s! [smbd:1154]"
date: 2016-06-01
forum: Server Platforms
---

### Post by chrislynch8 on 2016-06-01
Hi Folks,

I've been having the above issue for the last couple of weeks. I've not been able to get to the bottom of it yet. I've been searching forums and have tried a couple of different suggestions but all to no avail.

The server itself is a virtual machine running on VMware ESXi version 5. The Physical Server has 128GB of RAM and 32 Logical Processor. It has 4 Vms running in total and only one is giving problems. 

This is a copy of the error message in syslog and the only way to get the system back to to reboot the virtual server. The other VMs continue to run without issues.

```

May 31 12:50:47 server01 kernel: [85581.435699] BUG: soft lockup - CPU#1 stuck for 22s! [smbd:1154]
May 31 12:50:47 server01 kernel: [85581.435725] Modules linked in: xt_REDIRECT act_police cls_basic cls_flow cls_fw cls_u32 sch_fq_codel sch_tbf sch_prio sch_htb sch_hfsc sch_ingress sch_sfq xt_CHECKSUM ipt_rpfilter xt_statistic xt_CT xt_LOG xt_connlimit xt_realm xt_addrtype xt_comment xt_recent xt_nat ipt_ULOG ipt_REJECT ipt_MASQUERADE ipt_ECN ipt_CLUSTERIP ipt_ah xt_set ip_set nf_nat_tftp nf_nat_snmp_basic nf_conntrack_snmp nf_nat_sip nf_nat_pptp nf_nat_proto_gre nf_nat_irc nf_nat_h323 nf_nat_ftp nf_nat_amanda ts_kmp nf_conntrack_amanda nf_conntrack_sane nf_conntrack_tftp nf_conntrack_sip nf_conntrack_proto_udplite nf_conntrack_proto_sctp nf_conntrack_pptp nf_conntrack_proto_gre nf_conntrack_netlink nf_conntrack_netbios_ns nf_conntrack_broadcast nf_conntrack_irc nf_conntrack_h323 nf_conntrack_ftp xt_TPROXY nf_defrag_ipv6 xt_time xt_TCPMSS xt_tcpmss xt_sctp xt_policy xt_pkttype xt_physdev xt_owner xt_NFQUEUE xt_NFLOG nfnetlink_log xt_multiport xt_mark xt_mac xt_limit xt_length xt_iprange xt_helper xt_hashlimit xt_DSCP xt_dscp xt_dccp xt_conntrack xt_connmark xt_CLASSIFY xt_AUDIT xt_tcpudp xt_state iptable_raw iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack iptable_mangle nfnetlink iptable_filter ip_tables x_tables pppoe pppox arc4 md4 coretemp crct10dif_pclmul crc32_pclmul vmw_balloon aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd mac_hid serio_raw nfsd auth_rpcgss nfs_acl vmwgfx nfs lockd ttm sunrpc drm_kms_helper vmw_vmci drm i2c_piix4 shpchp lp parport nls_utf8 cifs fscache psmouse vmxnet3 mptspi mptscsih mptbase scsi_transport_spi pata_acpi
May 31 12:50:47 server01 kernel: [85581.435798] CPU: 1 PID: 1154 Comm: smbd Not tainted 3.16.0-70-generic #90~14.04.1-Ubuntu
May 31 12:50:47 server01 kernel: [85581.435799] Hardware name: VMware, Inc. VMware Virtual Platform/440BX Desktop Reference Platform, BIOS 6.00 04/14/2014
May 31 12:50:47 server01 kernel: [85581.435801] task: ffff880427a08a30 ti: ffff88041b010000 task.ti: ffff88041b010000
May 31 12:50:47 server01 kernel: [85581.435802] RIP: 0010:[<ffffffff81772042>]  [<ffffffff81772042>] _raw_spin_lock+0x32/0x50
May 31 12:50:47 server01 kernel: [85581.435809] RSP: 0018:ffff88041b013e40  EFLAGS: 00000287
May 31 12:50:47 server01 kernel: [85581.435809] RAX: 0000000000000612 RBX: ffff88041e2626c0 RCX: 0000000000008130
May 31 12:50:47 server01 kernel: [85581.435810] RDX: 000000000000811e RSI: 000000000000811e RDI: ffff88041b00ca90
May 31 12:50:47 server01 kernel: [85581.435811] RBP: ffff88041b013e40 R08: 0000000034353131 R09: ffff88041b013c3c
May 31 12:50:47 server01 kernel: [85581.435812] R10: ffff88041b013ee2 R11: 0000000000000004 R12: ffff88041e216430
May 31 12:50:47 server01 kernel: [85581.435812] R13: 0000000000000000 R14: 00000000000000a8 R15: 0000000400000001
May 31 12:50:47 server01 kernel: [85581.435814] FS:  00007f9c31b98780(0000) GS:ffff88043fd00000(0000) knlGS:0000000000000000
May 31 12:50:47 server01 kernel: [85581.435816] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 31 12:50:47 server01 kernel: [85581.435816] CR2: 00007f084fb04095 CR3: 0000000425bc0000 CR4: 00000000000407e0
May 31 12:50:47 server01 kernel: [85581.435862] Stack:
May 31 12:50:47 server01 kernel: [85581.435863]  ffff88041b013e60 ffffffff8170132c ffff8803ec89b900 ffff880426a10000
May 31 12:50:47 server01 kernel: [85581.435865]  ffff88041b013ea8 ffffffff81704143 ffffffff81cd3800 000000270000006e
May 31 12:50:47 server01 kernel: [85581.435866]  ffff8803ec89b900 000000000000006e ffff88041b013ec0 00007ffef1d64e60
May 31 12:50:47 server01 kernel: [85581.435867] Call Trace:
May 31 12:50:47 server01 kernel: [85581.435872]  [<ffffffff8170132c>] unix_state_double_lock+0x2c/0x70
May 31 12:50:47 server01 kernel: [85581.435874]  [<ffffffff81704143>] unix_dgram_connect+0x93/0x250
May 31 12:50:47 server01 kernel: [85581.435877]  [<ffffffff8164ca57>] SYSC_connect+0xe7/0x120
May 31 12:50:47 server01 kernel: [85581.435881]  [<ffffffff811e7e0a>] ? SyS_fcntl+0x48a/0x610
May 31 12:50:47 server01 kernel: [85581.435882]  [<ffffffff8164d75e>] SyS_connect+0xe/0x10
May 31 12:50:47 server01 kernel: [85581.435884]  [<ffffffff8177258d>] system_call_fastpath+0x1a/0x1f
May 31 12:50:47 server01 kernel: [85581.435885] Code: 89 e5 b8 00 00 02 00 f0 0f c1 07 89 c2 c1 ea 10 66 39 c2 75 02 5d c3 83 e2 fe 0f b7 f2 b8 00 80 00 00 eb 0c 0f 1f 44 00 00 f3 90 <83> e8 01 74 0a 0f b7 0f 66 39 ca 75 f1 5d c3 0f 1f 80 00 00 00

```

I've tried the following so far
[LIST]
[*]Upgrading Kernels current Kernel is 3.16.0-70-generic
[*]Updating Samba - current verison is 2:4.3.9+dfsg-0ubuntu0.14.04.3
[*]I've check PSU voltages and amp all appear to be in order according to the server iDrac
[*]I've even destoryed the VM and built a new one - still has the same problems.
[*]I've disabled acpi & apci with GRUB_CMDLINE_LINUX_DEFAULT="pci=noacpi acpi=off noapic" in /etc/default/grub
[/LIST]

I found a bug report for Samba version 4.3.8 and soft lockups, so my next attempt to do downgrade to 4.1.6 as this appears to be a workaround in the bug report 
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572608](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572608)

Any help or suggestion would be greatly appreciated and If I've not supplied enough information let me know what else to provide

Thanks in Advance
Chris

---

### Post by chrislynch8 on 2016-06-01
Just noticed that I posted this in the general help section and not the server section. Is there a way to move threads to another forum?

---

### Post by ajgreeny on 2016-06-01
*Thread moved to **Server Platforms**.*

---

### Post by QuimNuss on 2016-06-02
EDIT: I've just realised you had already localised the bug report. Dismiss this message /EDIT

There's a bug report regarding this issue:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572608](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572608)

I've personally haven't had the issue in two weeks when the first reports showed up (mine included).

---

