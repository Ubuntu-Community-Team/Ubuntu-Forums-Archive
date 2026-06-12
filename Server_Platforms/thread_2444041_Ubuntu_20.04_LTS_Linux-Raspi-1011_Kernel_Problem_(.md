---
title: "Ubuntu 20.04 LTS Linux-Raspi-1011 Kernel Problem (Syslog and Kern.Log Uncontrollable)"
date: 2020-05-23
forum: Server Platforms
---

### Post by allsilent on 2020-05-23
Hello!

[COLOR=#242729][FONT=Arial]Maybe similar to other questions about uncontrollable bloat in kern.log and syslog, but in my case I can&#8217;t figure out what in the kernel is causing it because I don&#8217;t recognize the module change and my google searches about it haven&#8217;t helped me much.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Two separate raspberry pi 4&#8217;s running Ubuntu 20.04 for several weeks. All has been well. Last night, I ran a standard apt upgrade and then my kern.log and syslog started growing uncontrollably at a rate of about 0.5-1 Gb per hour with the included upgrade from linux-raspi-5.4.0-1008 to linux-raspi-5.4.0-1011, and now I&#8217;m stuck truncating them over and over again (resorted to having a cron job take care of it) while I try to figure out what *this* is that&#8217;s filling the kernel log. Here&#8217;s the output from tailing the kern.log file, dmesg shows the same. It&#8217;s just this repeating over and over again, 100s of times per second.[/FONT][/COLOR]

```
May 23 07:43:03 raspi2 kernel: [12298.982475] WARNING: CPU: 0 PID: 4409 at drivers/mmc/host/sdhci.c:1101 sdhci_prepare_data+0x3dc/0x7b0
May 23 07:43:03 raspi2 kernel: [12298.982478] Modules linked in: binfmt_misc iptable_filter bpfilter dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua btsdio bluetooth ecdh_generic ecc brcmfmac bcm2835_v4l2(CE) brcmutil bcm2835_mmal_vchiq(CE) videobuf2_vmalloc videobuf2_memops snd_bcm2835(CE) videobuf2_v4l2 cfg80211 videobuf2_common snd_pcm videodev snd_timer mc snd raspberrypi_hwmon vc_sm_cma(CE) rpivid_mem uio_pdrv_genirq uio sch_fq_codel drm ip_tables x_tables autofs4 btrfs zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor xor_neon raid6_pq libcrc32c raid1 raid0 multipath linear crct10dif_ce spidev phy_generic ses enclosure scsi_transport_sas uas usb_storage aes_neon_bs aes_neon_blk crypto_simd cryptd
May 23 07:43:03 raspi2 kernel: [12298.982532] CPU: 0 PID: 4409 Comm: kworker/0:0H Tainted: G        WC  E     5.4.0-1011-raspi #11-Ubuntu
May 23 07:43:03 raspi2 kernel: [12298.982533] Hardware name: Raspberry Pi 4 Model B Rev 1.2 (DT)
May 23 07:43:03 raspi2 kernel: [12298.982545] Workqueue: kblockd blk_mq_run_work_fn
May 23 07:43:03 raspi2 kernel: [12298.982551] pstate: a0400085 (NzCv daIf +PAN -UAO)
May 23 07:43:03 raspi2 kernel: [12298.982553] pc : sdhci_prepare_data+0x3dc/0x7b0
May 23 07:43:03 raspi2 kernel: [12298.982556] lr : sdhci_prepare_data+0x2cc/0x7b0
May 23 07:43:03 raspi2 kernel: [12298.982557] sp : ffff80001156b9b0
May 23 07:43:03 raspi2 kernel: [12298.982558] x29: ffff80001156b9b0 x28: ffff0000eb62ec00 
May 23 07:43:03 raspi2 kernel: [12298.982560] x27: 0000000000000002 x26: 0000000000000000 
May 23 07:43:03 raspi2 kernel: [12298.982562] x25: ffff0000eb5e7000 x24: ffff0000eb5e7580 
May 23 07:43:03 raspi2 kernel: [12298.982564] x23: 0000000000418958 x22: ffff0000eb06a158 
May 23 07:43:03 raspi2 kernel: [12298.982566] x21: ffff0000277d0000 x20: ffff0000eb06a1d8 
May 23 07:43:03 raspi2 kernel: [12298.982568] x19: ffff0000eb5e7580 x18: 0000000000000000 
May 23 07:43:03 raspi2 kernel: [12298.982570] x17: 0000000000000000 x16: 0000000000000000 
May 23 07:43:03 raspi2 kernel: [12298.982572] x15: 0000000000000000 x14: 622061756c615f68 
May 23 07:43:03 raspi2 kernel: [12298.982574] x13: 645f697363732063 x12: 6d655f68645f6973 
May 23 07:43:03 raspi2 kernel: [12298.982576] x11: 637320636164725f x10: 68645f6973637320 
May 23 07:43:03 raspi2 kernel: [12298.982577] x9 : 6874617069746c75 x8 : 6d5f6d6420726574 
May 23 07:43:03 raspi2 kernel: [12298.982579] x7 : 6c69667062207265 x6 : ffffcb8fd5209a44 
May 23 07:43:03 raspi2 kernel: [12298.982581] x5 : ffffffffffffffff x4 : 0000000000000020 
May 23 07:43:03 raspi2 kernel: [12298.982583] x3 : 0000000000000001 x2 : fffffe0003581300 
May 23 07:43:03 raspi2 kernel: [12298.982585] x1 : fffffe0003581300 x0 : 00000000ffffffe4 
May 23 07:43:03 raspi2 kernel: [12298.982588] Call trace:
May 23 07:43:03 raspi2 kernel: [12298.982591]  sdhci_prepare_data+0x3dc/0x7b0
May 23 07:43:03 raspi2 kernel: [12298.982593]  sdhci_send_command+0xe0/0x5f0
May 23 07:43:03 raspi2 kernel: [12298.982595]  sdhci_request+0x110/0x150
May 23 07:43:03 raspi2 kernel: [12298.982599]  __mmc_start_request+0x88/0x1a8
May 23 07:43:03 raspi2 kernel: [12298.982601]  mmc_start_request+0x98/0xc0
May 23 07:43:03 raspi2 kernel: [12298.982603]  mmc_blk_mq_issue_rq+0x30c/0x778
May 23 07:43:03 raspi2 kernel: [12298.982605]  mmc_mq_queue_rq+0x14c/0x320
May 23 07:43:03 raspi2 kernel: [12298.982608]  blk_mq_dispatch_rq_list+0xa4/0x5f8
May 23 07:43:03 raspi2 kernel: [12298.982612]  blk_mq_do_dispatch_sched+0x68/0x108
May 23 07:43:03 raspi2 kernel: [12298.982614]  blk_mq_sched_dispatch_requests+0x164/0x1c0
May 23 07:43:03 raspi2 kernel: [12298.982617]  __blk_mq_run_hw_queue+0xfc/0x158
May 23 07:43:03 raspi2 kernel: [12298.982619]  blk_mq_run_work_fn+0x28/0x38
May 23 07:43:03 raspi2 kernel: [12298.982622]  process_one_work+0x1d0/0x430
May 23 07:43:03 raspi2 kernel: [12298.982624]  worker_thread+0x54/0x4a0
May 23 07:43:03 raspi2 kernel: [12298.982628]  kthread+0xfc/0x128
May 23 07:43:03 raspi2 kernel: [12298.982631]  ret_from_fork+0x10/0x1c
May 23 07:43:03 raspi2 kernel: [12298.982634] ---[ end trace a7bb7a8fcc54873a ]---
```
[COLOR=#242729][FONT=Arial]
Over and over again until the logs are literally filling the disk. Happening exactly the same on both pi&#8217;s, only change I made to them was upgrading via apt upgrade, as described.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Looks like something with sdhci, but I can&#8217;t figure out: a) what part of upgrading the kernel caused this to start [why wasn&#8217;t this happening before now, sdhci is a built in module and this was the recommended 'security' upgrade] and b) how to resolve the underlying issue so I'm not just hiding the logs.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Since operations appear otherwise normal for my systems, do I just need to tell rsyslog to ignore messages from sdhci? If so, I don't know how to go about that. I actually want to fix this, not just ignore if practical.

Of note, I tried going back to the 1008 kernel, but the problem persisted, even though it wasn't there for the past several weeks on that kernel before this upgrade. In order to downgrade the kernel, I was having to do some "hacky" stuff, since the pi has no grub/grub2, so there's no editing of /etc/default/grub, rather you have to work with the flash-kernel setup and replace vmlinuz with vmlinuz.bak to revert, and then manually apt remove headers and modules from 1011 (though I'm hoping maybe someone can point out that I didn't revert correctly and that the only way to fix this is to do so, and point me in the right direction). I'm sure I'm missing something because I found no documentation on reverting to an old kernel when grub doesn't exist, specific to the pi.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Any help greatly appreciated. Thanks![/FONT][/COLOR]

---

