---
title: "Transfers to RAID array freeze"
date: 2011-06-25
forum: Server Platforms
---

### Post by searing on 2011-06-25
I'm running Ubuntu Server 10.04 LTS.  I have eight data hard drives, each one is 1.5TB, and they are in a RAID6 array created with mdadm.  I installed XFS directly over this array (I have no need for the features in LVM), and am using Samba to access the server (my server is my only Linux machine - all my other machines are Windows).

The performance is great:  I can saturate my gigabit connection on reads, and I seem to average about 85 MB/s on writes.

The only problem is that when I write data to the RAID array, it sometimes freezes.  To clarify, my entire system freezes and will not respond.  Any SSH windows I have open to the server (from other computers) cease responding.  I am forced to cut the power to my system, after which the RAID array resyncs.

I have searched for this problem, and I found this thread:  [http://ubuntuforums.org/showthread.php?t=980828](http://ubuntuforums.org/showthread.php?t=980828).  However, those participating in that thread do not seem to have solved my problem.  My symptoms are exactly the same though.

Does anyone have any idea what might be causing this problem, and how I might solve it?

Thanks for your time.


EDIT:  I HAVE SOLVED THE PROBLEM.  I am editing this post in the hopes that it will help someone else searching for a solution.

I upgraded from 10.04 to 11.04 and the problem went away.  Normally I prefer to stay on LTS, but there's no point in the extra "stability" if it comes with a crippling bug.  Anyways, if possible, upgrade your version of Ubuntu and you should be fine.

---

### Post by TechSupportx86 on 2011-06-25
Don't know if this is in any way related, but just last night my server (10.10) would seize up, as in stop responding COMPLETELY and the num-lock and caps-lock LED would flash about 5 mins into a transfer to my samba share. 

The problem (for me anyway) was a stick of RAM i added earlier in the day. The system worked perfectly fine otherwise, but about 5 mins into a transfer (up or down) it would freak the hell out and lock up. Once i pulled the RAM i now assume was defective, i could transfer just fine.

I don't know if it's the same problem, but it sounds similar to me. I would run memtest or remove any newly added hardware to see if it makes any difference.

---

### Post by searing on 2011-06-25
Hmm - I haven't installed any new hardware in it for several months.  Perhaps one of the RAM sticks did go faulty though.  I'll run a memtest on it shortly.

Edit:  Memtest86 has done a complete pass with no errors.  I think it's safe to rule RAM hardware issues out at this point.  I'm still open to any other suggestions as to what might be causing this problem.

---

### Post by tgalati4 on 2011-06-26
Are these "green" drives?

Any messages in /var/log?

---

### Post by ian dobson on 2011-06-26
Hi,

Do you see any messages in your sysem log (dmesg)?

Once I day I transfer about 20-30Gb onto my RAID5 array (ext4) over samba without any problems, so it should work for you. The only problem I had at the beginning was with cheap SATA cables. After buying several different sets of SATA cables I finally found a set that worked 100% and I sticking with them. Don't ask me who the manufacturer is, thry came without any packaging, just a price tag.

Could your problem be file system corruption? Can you try a different file system? When the system hangs what do you see on the servers terminal window?

Regards
Ian Dobson

---

### Post by searing on 2011-06-26
> **tgalati4 said:**
> Are these "green" drives?

Any messages in /var/log?

Yes, they are Samsung Spinpoint F2 EcoGreen drives, 5400 rpm.

> **ian dobson said:**
> Hi,

Do you see any messages in your sysem log (dmesg)?

Once I day I transfer about 20-30Gb onto my RAID5 array (ext4) over samba without any problems, so it should work for you. The only problem I had at the beginning was with cheap SATA cables. After buying several different sets of SATA cables I finally found a set that worked 100% and I sticking with them. Don't ask me who the manufacturer is, thry came without any packaging, just a price tag.

Could your problem be file system corruption? Can you try a different file system? When the system hangs what do you see on the servers terminal window?

Regards
Ian Dobson

I would be surprised if the problem was filesystem corruption - it's a relatively new filesystem (it's only been used for a few days, and it did this on the first day).

Here's a snippet of stuff I found in messages that looks like a stack trace.  It appears to have occurred before one of my transfers failed.

```
Jun 25 11:16:35 titanium kernel: [59480.737150] CPU 2
Jun 25 11:16:35 titanium kernel: [59480.737329] Modules linked in: xfs exportfs fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_codec_realtek
 snd_hda_intel nouveau snd_hda_codec snd_hwdep ttm drm_kms_helper snd_pcm ppdev snd_timer serio_raw parport_pc intel_agp drm i2c_algo_bit xhci snd soundcore
snd_page_alloc lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 r8169 raid0 mii e1000 multipath e1000e
 pata_jmicron ahci linear
Jun 25 11:16:35 titanium kernel: [59480.743069] Pid: 1977, comm: flush-9:0 Not tainted 2.6.32-32-server #62-Ubuntu P55-USB3
Jun 25 11:16:35 titanium kernel: [59480.743420] RIP: 0010:[<ffffffffa034a8f5>]  [<ffffffffa034a8f5>] xfs_submit_ioend+0x65/0xf0 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.743909] RSP: 0018:ffff880159d978f0  EFLAGS: 00010202
Jun 25 11:16:35 titanium kernel: [59480.744143] RAX: 0000000000001000 RBX: fffd8800c84dd4d0 RCX: 000000000000001d
Jun 25 11:16:35 titanium kernel: [59480.744426] RDX: 00000000c50b2000 RSI: 0000000000000000 RDI: 0000000000001000
Jun 25 11:16:35 titanium kernel: [59480.744711] RBP: ffff880159d97920 R08: 00000000000000e0 R09: 00000001cdf0a900
Jun 25 11:16:35 titanium kernel: [59480.744994] R10: 0000000000000000 R11: 0000000000000002 R12: ffff880159e68b40
Jun 25 11:16:35 titanium kernel: [59480.745279] R13: ffff8800df43c960 R14: 0000000000000000 R15: 0000000039be153d
Jun 25 11:16:35 titanium kernel: [59480.745566] FS:  0000000000000000(0000) GS:ffff880007480000(0000) knlGS:0000000000000000
Jun 25 11:16:35 titanium kernel: [59480.745920] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 25 11:16:35 titanium kernel: [59480.746166] CR2: 00007f1b6e9ec8b4 CR3: 0000000001001000 CR4: 00000000000006e0
Jun 25 11:16:35 titanium kernel: [59480.746449] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 25 11:16:35 titanium kernel: [59480.746733] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 25 11:16:35 titanium kernel: [59480.747025] Process flush-9:0 (pid: 1977, threadinfo ffff880159d96000, task ffff8801967cae00)
Jun 25 11:16:35 titanium kernel: [59480.786950]  ffff8800df43c960 0000000000005d04 0000000000000001 00000000017e7000
Jun 25 11:16:35 titanium kernel: [59480.800633] <0> ffff8800df43c960 ffffea0002b55a58 ffff880159d97a20 ffffffffa034b82f
Jun 25 11:16:35 titanium kernel: [59480.827794] <0> ffff880100000000 0000000000005d04 0000000000000001 0000000000000004
Jun 25 11:16:35 titanium kernel: [59480.882779]  [<ffffffffa034b82f>] xfs_page_state_convert+0x39f/0x720 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.896449]  [<ffffffffa034bd0a>] xfs_vm_writepage+0x7a/0x130 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.909971]  [<ffffffff8110f91e>] ? __dec_zone_page_state+0x2e/0x30
Jun 25 11:16:35 titanium kernel: [59480.923366]  [<ffffffff810fe7e7>] __writepage+0x17/0x40
Jun 25 11:16:35 titanium kernel: [59480.936605]  [<ffffffff810ff967>] write_cache_pages+0x1d7/0x3e0
Jun 25 11:16:35 titanium kernel: [59480.949508]  [<ffffffff810fe7d0>] ? __writepage+0x0/0x40
Jun 25 11:16:35 titanium kernel: [59480.962245]  [<ffffffff810ffb94>] generic_writepages+0x24/0x30
Jun 25 11:16:35 titanium kernel: [59480.974876]  [<ffffffffa034aafd>] xfs_vm_writepages+0x5d/0x80 [xfs]
Jun 25 11:16:35 titanium kernel: [59480.987385]  [<ffffffff810ffbc1>] do_writepages+0x21/0x40
Jun 25 11:16:35 titanium kernel: [59480.999744]  [<ffffffff81168db6>] writeback_single_inode+0xf6/0x3d0
Jun 25 11:16:35 titanium kernel: [59481.011861]  [<ffffffff811694e5>] writeback_sb_inodes+0x195/0x280
Jun 25 11:16:35 titanium kernel: [59481.023761]  [<ffffffff81169d00>] writeback_inodes_wb+0xa0/0x1b0
Jun 25 11:16:35 titanium kernel: [59481.035403]  [<ffffffff8116a04b>] wb_writeback+0x23b/0x2a0
Jun 25 11:16:35 titanium kernel: [59481.046763]  [<ffffffff81077bec>] ? lock_timer_base+0x3c/0x70
Jun 25 11:16:35 titanium kernel: [59481.057945]  [<ffffffff81078732>] ? del_timer_sync+0x22/0x30
Jun 25 11:16:35 titanium kernel: [59481.068887]  [<ffffffff8116a159>] wb_do_writeback+0xa9/0x190
Jun 25 11:16:35 titanium kernel: [59481.079519]  [<ffffffff81077d00>] ? process_timeout+0x0/0x10
Jun 25 11:16:35 titanium kernel: [59481.089876]  [<ffffffff8116a293>] bdi_writeback_task+0x53/0xf0
Jun 25 11:16:35 titanium kernel: [59481.099957]  [<ffffffff81111636>] bdi_start_fn+0x86/0x100
Jun 25 11:16:35 titanium kernel: [59481.109944]  [<ffffffff811115b0>] ? bdi_start_fn+0x0/0x100
Jun 25 11:16:35 titanium kernel: [59481.119804]  [<ffffffff81085d16>] kthread+0x96/0xa0
Jun 25 11:16:35 titanium kernel: [59481.129299]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 25 11:16:35 titanium kernel: [59481.138902]  [<ffffffff81085c80>] ? kthread+0x0/0xa0
Jun 25 11:16:35 titanium kernel: [59481.148345]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun 25 11:16:35 titanium kernel: [59481.203395]  RSP <ffff880159d978f0>
Jun 25 11:16:35 titanium kernel: [59481.222015] ---[ end trace 85bba6ef59ec74e3 ]---
Jun 25 11:16:35 titanium kernel: [59481.238975] SMP
Jun 25 11:16:35 titanium kernel: [59481.238982] CPU 0
Jun 25 11:16:35 titanium kernel: [59481.238983] Modules linked in: xfs exportfs fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_codec_realtek
 snd_hda_intel nouveau snd_hda_codec snd_hwdep ttm drm_kms_helper snd_pcm ppdev snd_timer serio_raw parport_pc intel_agp drm i2c_algo_bit xhci snd soundcore
snd_page_alloc lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 r8169 raid0 mii e1000 multipath e1000e
 pata_jmicron ahci linear
Jun 25 11:16:35 titanium kernel: [59481.239005] Pid: 985, comm: md0_raid6 Tainted: G      D    2.6.32-32-server #62-Ubuntu P55-USB3
Jun 25 11:16:35 titanium kernel: [59481.239006] RIP: 0010:[<ffffffff812bfa4b>]  [<ffffffff812bfa4b>] memcpy_c+0xb/0x20
Jun 25 11:16:35 titanium kernel: [59481.239013] RSP: 0018:ffff88019015fb68  EFLAGS: 00010246
Jun 25 11:16:35 titanium kernel: [59481.239015] RAX: ffff880190730000 RBX: ffff88019015e000 RCX: 0000000000000200
Jun 25 11:16:35 titanium kernel: [59481.239016] RDX: 0000000000000000 RSI: 23ff8800c508b000 RDI: ffff880190730000
Jun 25 11:16:35 titanium kernel: [59481.239017] RBP: ffff88019015fbd0 R08: 0000000000001000 R09: ffff88019015fbf0
Jun 25 11:16:35 titanium kernel: [59481.239019] R10: 0000000000000000 R11: 0000000000000000 R12: ffff88019015fbf0
Jun 25 11:16:35 titanium kernel: [59481.239020] R13: 0000000000001000 R14: 0000000000000000 R15: 0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239022] FS:  0000000000000000(0000) GS:ffff880007400000(0000) knlGS:0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239024] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun 25 11:16:35 titanium kernel: [59481.239025] CR2: 00007f4111adb000 CR3: 0000000198b7b000 CR4: 00000000000006f0
Jun 25 11:16:35 titanium kernel: [59481.239026] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239028] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 25 11:16:35 titanium kernel: [59481.239030] Process md0_raid6 (pid: 985, threadinfo ffff88019015e000, task ffff880195e85c00)
Jun 25 11:16:35 titanium kernel: [59481.239032]  ffffffffa00bc0e7 0000000000000000 0000000000000000 0000000000000000
Jun 25 11:16:35 titanium kernel: [59481.239034] <0> fffdea0002b19e68 ffffea0005799280 0000000000001000 0000000000000286
Jun 25 11:16:35 titanium kernel: [59481.239036] <0> 0000000000001000 0000000000000015 0000000000001000 0000000000001000
Jun 25 11:16:35 titanium kernel: [59481.239044]  [<ffffffffa00bc0e7>] ? async_memcpy+0xe7/0x25c [async_memcpy]
Jun 25 11:16:35 titanium kernel: [59481.239050]  [<ffffffffa00d7ff5>] async_copy_data+0x85/0x130 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239054]  [<ffffffffa00d899e>] __raid_run_ops+0x35e/0x7d0 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239058]  [<ffffffff81061b70>] ? load_balance_newidle+0xc0/0x350
Jun 25 11:16:35 titanium kernel: [59481.239062]  [<ffffffffa00d6ca0>] ? ops_complete_reconstruct+0x0/0xa0 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239065]  [<ffffffffa00da368>] handle_stripe6+0x828/0xb40 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239068]  [<ffffffffa00d694c>] ? __release_stripe+0xcc/0x1c0 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239072]  [<ffffffffa00db045>] handle_stripe+0x25/0x30 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239075]  [<ffffffffa00db442>] raid5d+0x202/0x320 [raid456]
Jun 25 11:16:35 titanium kernel: [59481.239079]  [<ffffffff81559ff9>] ? _spin_unlock_irqrestore+0x19/0x30
Jun 25 11:16:35 titanium kernel: [59481.239084]  [<ffffffff8142ca6c>] md_thread+0x5c/0x130
Jun 25 11:16:35 titanium kernel: [59481.239088]  [<ffffffff81086090>] ? autoremove_wake_function+0x0/0x40
Jun 25 11:16:35 titanium kernel: [59481.239091]  [<ffffffff8142ca10>] ? md_thread+0x0/0x130
Jun 25 11:16:35 titanium kernel: [59481.239092]  [<ffffffff81085d16>] kthread+0x96/0xa0
Jun 25 11:16:35 titanium kernel: [59481.239096]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 25 11:16:35 titanium kernel: [59481.239098]  [<ffffffff81085c80>] ? kthread+0x0/0xa0
Jun 25 11:16:35 titanium kernel: [59481.239100]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
Jun 25 11:16:35 titanium kernel: [59481.239116]  RSP <ffff88019015fb68>
Jun 25 11:16:35 titanium kernel: [59481.239144] ---[ end trace 85bba6ef59ec74e4 ]---
Jun 25 11:16:35 titanium kernel: [59481.239148] note: md0_raid6[985] exited with preempt_count 2


```I could probably restore the data to the array if needed, but it is a pain - I would like to explore more options not related to the filesystem before wiping the filesystem out and trying with a new one (possibly not XFS).

Nothing is printed to my SSH terminal when the transfer freezes.  I've noticed that it sometimes lets me continue to use SSH, and sometimes it does not.  (However, if I try to navigate to the directory that I was copying to, and list files, my terminal freezes.)

I do not know what is printed on the actual server terminal.  This server is headless, so I don't have any monitor or keyboard attached to it, just a power cable and an ethernet cable.

---

### Post by ian dobson on 2011-06-26
Hi,

That's a really nasty kernel panic. I see your running an "old" kernel, is it possible to try a newer kernel. I know in the .36--37 series the devs added quite afew xfs updates.

Also try running a file system check. The panic looks abit like fs corruption causing xfs to attempt to write to an invalid block.

Regards
Ian Dobson

---

### Post by searing on 2011-06-26
Hmm... I opted for the 10.04 LTS version - would upgrading the kernel entail moving to the 11.04 version?  Or can I upgrade it and remain with the 10.04 LTS version?

The man page for xfs_check warns against using it on mounted filesystems, so I guess I won't be able to use my server while I check it.  As a result, I'm going to run the check over the week while I'm not home, so I'll know the results on Friday.

I'd like to know what caused this corruption though.  As I said before, the filesystem is rather new - it would be a shame if I had to run xfs_check and bring the whole thing down every other week.

Edit:  Foolish me - when I reinstalled Linux a short while ago, I forgot to disable the write caches on all of my data drives!  That may explain a possible filesystem corruption.  I hope that's the case, because that's easy enough to fix.

Edit 2:  I'm actually going to run the check this afternoon, I'll just have to do something that doesn't involve my server today.

Edit 3: I'm either using xfs_check wrong, or it's ridiculously fast.  I unmounted my XFS filesystem and ran xfs_check on it - it printed nothing to the terminal and finished execution in about a minute.  I checked htop, and nothing is using any system resources (literally - 0% usage on 3 cores, 0.7% usage on core 2), so I assume it's not running anything in the background.

---

### Post by ian dobson on 2011-06-26
Hi,

Does xfs_check have a force option? If xfs_check thinks the fs is clean it won't do a check.

Regards
Ian Dobson

---

### Post by searing on 2011-06-26
I do not see a force option anywhere in the man page.  Furthermore, it takes a nontrivial amount of time to complete - it's just that this time is quite short (about 30 seconds or so).

Although the total array size is 9 TB (about 8 TiB), I am only using about 1.5 TB of it currently.

---

### Post by tgalati4 on 2011-06-26
Green drives should not be used in RAID configurations--you are taking your chances.

---

### Post by searing on 2011-06-26
> **tgalati4 said:**
> Green drives should not be used in RAID configurations--you are taking your chances.

I've heard this before, but I never got a clean explanation about it.  Attempting to google it seems to bring up many threads along the lines of "Are green drives bad for software RAID?" / "No."  They mostly seem to mention timeout issues causing the software to incorrectly assume the drive is offline - surely you could tune the software to give the drives more time before deciding they are offline (after all, flexibility is one of the strongpoints of software RAID systems).

Either way, I don't see mdadm reporting any drives are dropping out of the array.

Edit:  After doing some more searching, it appears that everybody's issues with green drives are specifically with WD green drives.  I'm using Samsung drives.

---

### Post by ian dobson on 2011-06-26
Hi,

I'm running 7 WD 2Tb green drives in a raid array (mdadm) and I'm not seeing any problems.

Regards
Ian Dobson

---

### Post by tgalati4 on 2011-06-27
I'll retract what I said about green drives.  Green drives are OK to use in RAID.  But if you are running Samsung Spinpoints in a RAID6 configuration with XFS and Ubuntu 10.04 server, then you may experience hard lockups.

---

### Post by searing on 2011-06-27
Why?  Does it have to do with timeout issues?  Isn't there a way I can configure mdadm to wait longer before declaring a disk dead, and wouldn't there be some mention of such an event in the log?

---

### Post by tgalati4 on 2011-06-28
If the kernel requests data and a disk goes to sleep, then the scheduler is in an I/O Wait mode.  This looks like a hard freeze (but it's not).  Some folks mistakenly hit the power button to reboot rather than wait.  Of course waiting for a particular drive to wake up again is problematic.

I had an Ubuntu server with several years (6) of uptime.  It started freezing with IO Waits.  I pulled the machine apart and cleaned it and found that the power connector on it was loose!  The machine had been on for so long that the disk had vibrated the power connector loose. Now I use tiestraps to secure those power connectors to the drives.  The kernel was simply waiting for the disk to come alive again.

If you log in through another machine and run:

dmesg | tail -f

And another terminal (use screen to get multiple terminals) run htop:

sudo apt-get install htop
htop

You will either see IO Waits in htop or kernel error messages in dmesg.  If you see tracebacks and kernel panics then there is either a race condition or a hardware issue.

I don't know anything about green drives or mdadm except the stories that I read on the forums.

---

