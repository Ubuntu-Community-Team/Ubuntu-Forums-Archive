---
title: "What's this error about ?"
date: 2010-04-21
forum: Server Platforms
---

### Post by argoson on 2010-04-21
I have a webserver (LAMP) Ubuntu 9.10 32bit which i use for development. it's running on a Pentium 4 3.20 mhz cpu, with 2x80GB SATA HDD's in a  RAID-1 configuration, created  as software raid during setup.
It's a fresh install, about a week old. I encountered this dump in the kernel log file:

```

Apr 21 00:19:19 zepp1 kernel: [ 7350.019486] ------------[ cut here ]------------ 
Apr 21 00:19:19 zepp1 kernel: [ 7350.019535] WARNING: at /build/buildd/linux-2.6.31/fs/quota/dquot.c:964 
dquot_claim_space+0x84/0x130() 
Apr 21 00:19:19 zepp1 kernel: [ 7350.019591] Hardware name: 
Apr 21 00:19:19 zepp1 kernel: [ 7350.019637] Modules linked in: quota_v2 quota_tree ipt_LOG
iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 radeon ttm iptable_filter ip_tables psmouse drm
x_tables intel_agp lp agpgart i2c_algo_bit serio_raw joydev parport hid_logitech ff_memless usbhid raid10 raid456 raid6_pq
async_xor async_memcpy async_tx xor raid1 raid0 multipath linear ohci1394 ieee1394 e100 mii 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021326] Pid: 22, comm: pdflush Tainted: G W 2.6.31-20-generic-pae #58-Ubuntu 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021381] Call Trace: 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021428] [<c014692d>] warn_slowpath_common+0x6d/0xa0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021478] [<c0229934>] ? dquot_claim_space+0x84/0x130 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021527] [<c0229934>] ? dquot_claim_space+0x84/0x130 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021577] [<c0146975>] warn_slowpath_null+0x15/0x20 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021627] [<c0229934>] dquot_claim_space+0x84/0x130 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021677] [<c029158f>] ext4_mb_mark_diskspace_used+0x33f/0x390 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021728] [<c028bb72>] ? ext4_mb_use_preallocated+0x232/0x240 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021776] [<c028bf82>] ? ext4_mb_initialize_context+0x82/0x290 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021827] [<c0292f7e>] ext4_mb_new_blocks+0x2fe/0x580 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021877] [<c0287abf>] ? ext4_ext_find_extent+0xff/0x280 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021927] [<c0289b55>] ext4_ext_get_blocks+0x415/0x5a0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.021977] [<c026aa2f>] ext4_get_blocks+0x23f/0x2c0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022027] [<c026b0b4>] mpage_da_map_blocks+0x94/0x400 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022077] [<c026b68c>] ext4_da_writepages+0x26c/0x520 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022126] [<c01bb260>] ? __writepage+0x0/0x30 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022176] [<c01bc531>] do_writepages+0x21/0x40 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022225] [<c020752e>] writeback_single_inode+0x16e/0x3d0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022274] [<c013cdb4>] ? dequeue_entity+0x14/0x290 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022324] [<c0207c2d>] generic_sync_sb_inodes+0x38d/0x4a0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022373] [<c0207e1d>] writeback_inodes+0x4d/0xe0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022423] [<c01bb422>] wb_kupdate+0xa2/0x110 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022473] [<c01bcc07>] __pdflush+0xf7/0x1f0 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022521] [<c01bcd00>] ? pdflush+0x0/0x40 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022569] [<c01bcd00>] ? pdflush+0x0/0x40 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022617] [<c01bcd39>] pdflush+0x39/0x40 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022665] [<c01bb380>] ? wb_kupdate+0x0/0x110 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022714] [<c015dd9c>] kthread+0x7c/0x90 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022761] [<c015dd20>] ? kthread+0x0/0x90 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022809] [<c0104047>] kernel_thread_helper+0x7/0x10 
Apr 21 00:19:19 zepp1 kernel: [ 7350.022857] ---[ end trace 02ffd09d773f0157 ]--- 

```Can anybody tell me what's the problem and how to fix it (in case there is a problem...)

---

### Post by P4man on 2010-04-21
Maybe this helps:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442799](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442799)

---

