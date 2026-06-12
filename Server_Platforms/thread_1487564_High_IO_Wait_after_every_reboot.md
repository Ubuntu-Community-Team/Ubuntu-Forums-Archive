---
title: "High I/O Wait after every reboot"
date: 2010-05-19
forum: Server Platforms
---

### Post by atroxes on 2010-05-19
Hello fellow Ubuntu users :)

First and foremost, let me assure you that I've searched high and low for a solution to my problem. I don't simply jump inhere to ask for help if I can avoid it ;)

**The Machine**
Core 2 Duo E4600
2GB DDR2 RAM (1 stick)
Intel ICH10R based motherboard (tried an ICH9R aswell)
4-port SATA controller (PCI Sil 3114)
O/S: Ubuntu Desktop x64 10.04 LTS (using 'desktop' because I like having a remote desktop)

**The Storage Setup**
Disks: Assorted selection of 9 disk. 750GB, 1000GB and 1500GB Seagate and Western Digital disks.

The disks are joined through a standard LVM2 configuration. I don't know the LVM term, but normally you'd call it a JBOD setup.

On that LVM device, I've put a cryptsetup device, made with the LUKS tools (aes-xts-plain 256)

On the cryptsetup device, I've created and mounted an EXT4 partition.

All in all, a completely standard LVM2 and LUKS setup, running EXT4

**The Problem**
After a reboot, I proceed to unlock my cryptsetup encryption device, and then mount the EXT4 partition. All is well, the mount is accessible and everything looks fine.

I then try to send a file to the mount, via Samba. After a few hundred MB written, the I/O wait goes berserk. It stays at 50% (dual core setup remember).

The system becomes unresponsive to network commands (can't browse samba) for about 5-10 minutes. When it finally responds, the I/O wait is gone and everything is now fine. I can write and read hundreds of GB's of data without any issues at all. I can benchmark and stress all disks perfectly fine and no logs are showing disk errors.

I tried monitoring my disks with 'iostat -d 2' while the I/O wait was happening, and there is some slight Blk_read/s activity on 1 disk at a time. First for example /dev/sda is showing a little Blk_read/s acitivty, then it jumps to the next disk, and when every disk has show that slight Blk_read/s activity (500-800 or so) the problem is gone and the I/O wait is no more.

**The solution?**
I've tried changing motherboards, switching disks around on the controllers, checking individual disks, replacing disks and I've tried different versions of Ubuntu. The problem however persists.

I could see it being a network issue, possibly a driver issue. But since the NIC is a standard RTL8111 on-board it seems unlike that the problem wouldn't be more widespread since this NIC is litterally being used everywhere. I did change my motherboard, so a faulty NIC seems unlikely twice in a row.

I could also imagine "self check" feature being done by either cryptsetup/LUKS or LVM, but I can't for the life of me find ANY information about such a feature anywhere.


I really hope someone inhere has experienced a similar problem and has been able to solve it. This problem is the sole reason I'm seriously considering Windows for my fileserver (yes, I'm going insane).

Thank you in advance! Any help is appreciated!

Sincerely
Martin Moerch Aka. Atroxes

---

### Post by atroxes on 2010-05-20
Shameless bump!

---

### Post by atroxes on 2010-05-27
Trying a bump one last time.

---

### Post by CyberCod on 2010-05-28
Just fixed my iowait problem by removing fd0 from /etc/fstab

I didn't actually have a floppy drive in there, so I'm guessing that was the problem.

It took a lot of investigating to track down though.  The program iotop was not helpful as a kernel option dealing with i/o was turned off, and as a result it could not identify i/o percentages.

Watching dmesg tail in a TTY console eventually tipped me off.

Try booting up, and then switching to a TTY console (ctrl+alt+f3) and logging in there.  Run dmesg tail and then switch back to X (ctrl+alt+F7) and log in.

If you're watching the system monitor applet, you can switch over to TTY 3 as soon as you see the iowait activity start up.  Hopefully then you'll have some info to help you figure out what is going on.

Good luck!

PS> I figured if you're working with LVM stuff, you probably know full well how to get into TTY consoles... I put in thorough instructions for any noobs who come along afterward with iowait issues. ;)

---

### Post by atroxes on 2010-06-02
Thanks for the suggestion!
Unfortunately, this didn't resolve my problem.

I removed fd0 from my fstab, and all that's left now is my root partition, /proc and my swap.

Dmesg doesn't give me any further information. When the I/O wait starts, it looks like this in iostat:

```
IOstat
Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0,00         0,00         0,00          0          0
sdc               0,00         0,00         0,00          0          0
sdf             127,00      1016,00         0,00       1016          0
sde               0,00         0,00         0,00          0          0
sdd               0,00         0,00         0,00          0          0
sdb               0,00         0,00         0,00          0          0
sdg               2,00         0,00        32,00          0         32
sdh               0,00         0,00         0,00          0          0
sdi               0,00         0,00         0,00          0          0
sdj               0,00         0,00         0,00          0          0
dm-0            127,00      1016,00         0,00       1016          0
dm-1            127,00      1016,00         0,00       1016          0

Top
Cpu(s):  0.0%us,  1.0%sy,  0.0%ni, 50.8%id, 48.2%wa,  0.0%hi,  0.0%si,  0.0%st

```


As you can see, iostat reports a very slight read on /dev/sdf in this case. This continues on the disks one by one, until it's gone through them all. After that, the problem is gone. The process takes roughly 15-20 minutes and the LVM partition completely hangs during this time.

---

### Post by atroxes on 2010-06-02
UPDATE

Just now, a few min after the IOwait started, I'm seeing some really strange behaviour in dmesg

```
[  720.390396] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.390769] jbd2/dm-1-8   D 00000000ffffffff     0  3823      2 0x00000000
[  720.390777]  ffff88007ae13d20 0000000000000046 0000000000015bc0 0000000000015bc0
[  720.390785]  ffff8800378c31a0 ffff88007ae13fd8 0000000000015bc0 ffff8800378c2de0
[  720.390791]  0000000000015bc0 ffff88007ae13fd8 0000000000015bc0 ffff8800378c31a0
[  720.390798] Call Trace:
[  720.390813]  [<ffffffff8121a64f>] jbd2_journal_commit_transaction+0x1bf/0x1270
[  720.390821]  [<ffffffff81076e2c>] ? lock_timer_base+0x3c/0x70
[  720.390828]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[  720.390834]  [<ffffffff81221c3d>] kjournald2+0xbd/0x220
[  720.390840]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[  720.390845]  [<ffffffff81221b80>] ? kjournald2+0x0/0x220
[  720.390850]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[  720.390856]  [<ffffffff810141ea>] child_rip+0xa/0x20
[  720.390862]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[  720.390866]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[  720.390871] INFO: task flush-252:1:3826 blocked for more than 120 seconds.
[  720.391182] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.391565] flush-252:1   D 00000000ffffffff     0  3826      2 0x00000000
[  720.391572]  ffff88007b0bda50 0000000000000046 0000000000015bc0 0000000000015bc0
[  720.391579]  ffff880065e64890 ffff88007b0bdfd8 0000000000015bc0 ffff880065e644d0
[  720.391586]  0000000000015bc0 ffff88007b0bdfd8 0000000000015bc0 ffff880065e64890
[  720.391592] Call Trace:
[  720.391598]  [<ffffffff81218961>] start_this_handle+0x251/0x4b0
[  720.391604]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[  720.391610]  [<ffffffff81218d61>] ? jbd2_journal_start+0x81/0x100
[  720.391616]  [<ffffffff81218d95>] jbd2_journal_start+0xb5/0x100
[  720.391622]  [<ffffffff811d9ff5>] ? ext4_meta_trans_blocks+0x75/0xf0
[  720.391629]  [<ffffffff811f6d78>] ext4_journal_start_sb+0x58/0x90
[  720.391635]  [<ffffffff811dfae3>] ext4_da_writepages+0x243/0x610
[  720.391643]  [<ffffffff810fcf21>] do_writepages+0x21/0x40
[  720.391648]  [<ffffffff81164cc6>] writeback_single_inode+0xf6/0x3d0
[  720.391654]  [<ffffffff81165930>] writeback_inodes_wb+0x410/0x5e0
[  720.391659]  [<ffffffff81165c0a>] wb_writeback+0x10a/0x1d0
[  720.391665]  [<ffffffff810c91d3>] ? rcu_start_gp+0x53/0x1a0
[  720.391671]  [<ffffffff810c9d2e>] ? call_rcu+0xe/0x10
[  720.391676]  [<ffffffff81165edd>] wb_do_writeback+0x12d/0x1a0
[  720.391681]  [<ffffffff81165fa3>] bdi_writeback_task+0x53/0xe0
[  720.391687]  [<ffffffff8110e8b6>] bdi_start_fn+0x86/0x100
[  720.391692]  [<ffffffff8110e830>] ? bdi_start_fn+0x0/0x100
[  720.391697]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[  720.391702]  [<ffffffff810141ea>] child_rip+0xa/0x20
[  720.391707]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[  720.391712]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[  840.390045] INFO: task jbd2/dm-1-8:3823 blocked for more than 120 seconds.
[  840.390363] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.390736] jbd2/dm-1-8   D 00000000ffffffff     0  3823      2 0x00000000
[  840.390744]  ffff88007ae13d20 0000000000000046 0000000000015bc0 0000000000015bc0
[  840.390752]  ffff8800378c31a0 ffff88007ae13fd8 0000000000015bc0 ffff8800378c2de0
[  840.390759]  0000000000015bc0 ffff88007ae13fd8 0000000000015bc0 ffff8800378c31a0
[  840.390766] Call Trace:
[  840.390780]  [<ffffffff8121a64f>] jbd2_journal_commit_transaction+0x1bf/0x1270
[  840.390788]  [<ffffffff81076e2c>] ? lock_timer_base+0x3c/0x70
[  840.390795]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[  840.390802]  [<ffffffff81221c3d>] kjournald2+0xbd/0x220
[  840.390807]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[  840.390813]  [<ffffffff81221b80>] ? kjournald2+0x0/0x220
[  840.390818]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[  840.390824]  [<ffffffff810141ea>] child_rip+0xa/0x20
[  840.390829]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[  840.390834]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[  840.390838] INFO: task flush-252:1:3826 blocked for more than 120 seconds.
[  840.391150] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.391535] flush-252:1   D 00000000ffffffff     0  3826      2 0x00000000
[  840.391541]  ffff88007b0bda50 0000000000000046 0000000000015bc0 0000000000015bc0
[  840.391548]  ffff880065e64890 ffff88007b0bdfd8 0000000000015bc0 ffff880065e644d0
[  840.391555]  0000000000015bc0 ffff88007b0bdfd8 0000000000015bc0 ffff880065e64890
[  840.391561] Call Trace:
[  840.391567]  [<ffffffff81218961>] start_this_handle+0x251/0x4b0
[  840.391573]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
[  840.391579]  [<ffffffff81218d61>] ? jbd2_journal_start+0x81/0x100
[  840.391585]  [<ffffffff81218d95>] jbd2_journal_start+0xb5/0x100
[  840.391591]  [<ffffffff811d9ff5>] ? ext4_meta_trans_blocks+0x75/0xf0
[  840.391598]  [<ffffffff811f6d78>] ext4_journal_start_sb+0x58/0x90
[  840.391604]  [<ffffffff811dfae3>] ext4_da_writepages+0x243/0x610
[  840.391612]  [<ffffffff810fcf21>] do_writepages+0x21/0x40
[  840.391618]  [<ffffffff81164cc6>] writeback_single_inode+0xf6/0x3d0
[  840.391623]  [<ffffffff81165930>] writeback_inodes_wb+0x410/0x5e0
[  840.391628]  [<ffffffff81165c0a>] wb_writeback+0x10a/0x1d0
[  840.391635]  [<ffffffff810c91d3>] ? rcu_start_gp+0x53/0x1a0
[  840.391640]  [<ffffffff810c9d2e>] ? call_rcu+0xe/0x10
[  840.391645]  [<ffffffff81165edd>] wb_do_writeback+0x12d/0x1a0
[  840.391650]  [<ffffffff81165fa3>] bdi_writeback_task+0x53/0xe0
[  840.391656]  [<ffffffff8110e8b6>] bdi_start_fn+0x86/0x100
[  840.391661]  [<ffffffff8110e830>] ? bdi_start_fn+0x0/0x100
[  840.391666]  [<ffffffff81084fa6>] kthread+0x96/0xa0
[  840.391671]  [<ffffffff810141ea>] child_rip+0xa/0x20
[  840.391676]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
[  840.391681]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
```

I have no idea how to interpret this information. Something looks awfully wrong :confused:

---

### Post by atroxes on 2010-06-11
Still need expert help, please :/

---

### Post by dragos2 on 2010-06-11
> **atroxes said:**
> Still need expert help, please :/

I am no expert but did you checked the cables? Clone your setup, install other OS and see if it
reproduces. Also do you have the latest BIOS ? 

I still bet on hdd cables. If you can try with new ones.

---

### Post by Xianath on 2010-06-12
The most likely culprit is the Sil3114. It's a PCI card and doesn't support SATA2, both of which add a lot of contention. It is also possible that one of your drives is showing signs of imminent failure, trying to save pending bad sectors. Check their SMART status. If they're clean, get a pair of PCIe dual SATA2 or a quad SATA2 controllers. I run 3 Sil3124 cards in my server and have had zero problems in two years.

---

### Post by atroxes on 2010-10-19
> **Xianath said:**
> The most likely culprit is the Sil3114. It's a PCI card and doesn't support SATA2, both of which add a lot of contention. It is also possible that one of your drives is showing signs of imminent failure, trying to save pending bad sectors. Check their SMART status. If they're clean, get a pair of PCIe dual SATA2 or a quad SATA2 controllers. I run 3 Sil3124 cards in my server and have had zero problems in two years.

Actually, my Sil3114 wasn't the culprit. I recently changed to a PCI Express x4 Marvell 88SX7042 based SATA controller and the problems still persists. Throughput on the new card is miles higher than on the old PCI, so that can't be an issue now.

I've still, after 2 years, at a loss here. I have no idea what's causing this, and frankly, it's driving me insane :shock:

I'm not running any snapshots on my LVM. It's encrypted with cryptsetup (LUKS) AES-XTS-plain 256 and it's partitioned with Ext4 with no options other than default.

---

### Post by atroxes on 2010-10-19
**Solution (sort of)**

Long story short: Western Digital likes mother nature. WD implements half-assed feature to save mother nature. Half-assed feature (IntelliPark) makes disks (Green Power) park their data-head every 8 seconds. Mother nature is saved and my Load Cycle count has reached 600.000 in 1 year and we now have extreme io wait on transfers because Linux doesn't cope well with half-assed mother nature saving features.

Solution? Buy a hard drive without IntelliPark.

Until then? Disable IntelliPark with WDidle3 utility from WD (admittance of fail from their side).

WDidle3: [http://support.wdc.com/product/download.asp?groupid=609&sid=113&lang=en](http://support.wdc.com/product/download.asp?groupid=609&sid=113&lang=en)

Making DOS USB boot stick: [http://www.flazh.de/en/bios-boot-usb-stick.htm](http://www.flazh.de/en/bios-boot-usb-stick.htm)


Have fun replacing your many WD GP drives. I know I will :confused:

---

### Post by atroxes on 2010-10-19
That didn't completely fix it either.

When I hammer the LVM over Samba with 80MB/s data, it suddenly stalls and gives up.

I can't even remotely comprehend why Linux has to be this quirky and odd...

---

### Post by atroxes on 2010-10-20
I'm literally pulling out my beard, hair by hair, over this.

The original problem is back.

Through 'iostat -d 2' I can clearly see the disks being read one by one slowly. Full IO wait and then iostat reports slight block read on one disk at a time.

The order it does it in, is the same order as 'pvdisplay' lists my HDD's in, which convinces me this has something to do with the LVM.

I've searched the web far and wide for any "consistency checks" that LVM could be doing, but haven't found anything.

I beg of you... Please. I'm dying here :mad:

---

### Post by macleapa on 2011-05-07
I realize this is an older post, but I had the same problem in early 2010 as well.  Using Quad core Dell 6400 laptop with Ubuntu v10.04, with full disk encryption, I have heavy I/O watis.
 
I feel your pain atroxes.
 
The I/O waits are extremely painful.  If I run a few "cpu intensive" jobs, I will surley get an I/O wait.  The more jobs I run, the longer the subsequent I/O wait.
 
To get around this issue (some what), I will only run up to 3 concurrent jobs... this saves one CPU for what seems to be concurrent I/O releated house keeping.
 
This issue was so bad, I had to flip back to using Windows.  I require encryption, but cannot have this sort of I/O issue.  If I run 4 consecutive jobs everything is fine for about the first 5 to 10 mintues... afterwords ALL CPU relates jobs "pause" and the subsequent I/O housekeeping takes place... which in this case takes 15 to 20 minutes.  OUCH!
 
I can run the same jobs on Windows without any I/O waits penalties.
 
I am replying to this thread because I came back to Ubunut on Friday to see if updating and patching my install would help.  I still have more tests to perform... but initial testing does not look good.
 
I'll let you know if I have any success.
 
Cheers!

---

### Post by cth103 on 2011-05-16
For what it's worth, I'm seeing what may be similar problems.  However, they have only started happening since the upgrade to 11.04, and I haven't yet found a way to reliably trigger them.

In the bug state, load average goes high (usually about 16) and top says that I/O wait is high (~98-99%).  Network and disc IO basically stops working.  I haven't seen the machine recover from this state once its in it.

Sometimes I see stuff like this:

[38403.508297] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[38403.508299] kworker/0:0     D 00000002     0  4785      2 0x00000000
[38403.508303]  e68d1e54 00000046 c183a8c0 00000002 f51032f4 c1049022 f04341ac c183a8c0
[38403.508309]  6a6bd8ca 000022a6 f04341a8 c183a8c0 c183a8c0 f50068c0 f0433f20 c1731f60
[38403.508314]  6a6bee32 000022a6 6a6bd8ca 000022a6 000022a6 00000000 00015057 00989680
[38403.508320] Call Trace:
[38403.508323]  [<c1049022>] ? balance_tasks+0x102/0x190
[38403.508326]  [<c150802d>] schedule_timeout+0x1ed/0x260
[38403.508330]  [<c1022296>] ? native_smp_send_reschedule+0x36/0x50
[38403.508333]  [<c1507bb0>] wait_for_common+0xa0/0x130
[38403.508336]  [<c104a060>] ? default_wake_function+0x0/0x20
[38403.508339]  [<c1507d17>] wait_for_completion+0x17/0x20
[38403.508341]  [<c106cfbc>] kthread_create+0x6c/0xc0
[38403.508344]  [<c1066de0>] ? alloc_worker+0x20/0x60
[38403.508347]  [<c1068d10>] ? worker_thread+0x0/0x2d0
[38403.508350]  [<c1067bb6>] create_worker+0x116/0x190
[38403.508352]  [<c1068d10>] ? worker_thread+0x0/0x2d0
[38403.508356]  [<c1067c84>] maybe_create_worker+0x54/0xe0
[38403.508359]  [<c1067d4f>] manage_workers.clone.19+0x3f/0x110
[38403.508361]  [<c1068f40>] worker_thread+0x230/0x2d0
[38403.508364]  [<c1068d10>] ? worker_thread+0x0/0x2d0
[38403.508367]  [<c106ce04>] kthread+0x74/0x80
[38403.508369]  [<c106cd90>] ? kthread+0x0/0x80
[38403.508372]  [<c100367e>] kernel_thread_helper+0x6/0x10
[38523.508027] INFO: task bdi-default:16 blocked for more than 120 seconds.
[38523.508030] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[38523.508033] bdi-default     D 00000000     0    16      2 0x00000000
[38523.508037]  f4151e6c 00000046 00000000 00000000 c1040672 f4151dfc f40c350c c183a8c0
[38523.508043]  cd4eb0d6 00002274 f40c3508 c183a8c0 c183a8c0 f50068c0 f40c3280 e3a58ca0
[38523.508049]  800f438d 00002274 800f088a 00002274 00002274 f40c357c 000068fc 00989680
[38523.508055] Call Trace:
[38523.508064]  [<c1040672>] ? update_cfs_shares+0x62/0x90
[38523.508069]  [<c150802d>] schedule_timeout+0x1ed/0x260
[38523.508073]  [<c10408df>] ? check_preempt_wakeup+0x16f/0x220
[38523.508076]  [<c1507bb0>] wait_for_common+0xa0/0x130
[38523.508079]  [<c104a060>] ? default_wake_function+0x0/0x20
[38523.508082]  [<c1507d17>] wait_for_completion+0x17/0x20
[38523.508086]  [<c106cfbc>] kthread_create+0x6c/0xc0
[38523.508090]  [<c1149280>] ? bdi_writeback_thread+0x0/0x200
[38523.508094]  [<c10fa075>] bdi_forker_thread+0x2e5/0x3d0
[38523.508097]  [<c1149280>] ? bdi_writeback_thread+0x0/0x200
[38523.508101]  [<c1038d2e>] ? complete+0x4e/0x60
[38523.508104]  [<c10f9d90>] ? bdi_forker_thread+0x0/0x3d0
[38523.508106]  [<c106ce04>] kthread+0x74/0x80
[38523.508109]  [<c106cd90>] ? kthread+0x0/0x80
[38523.508112]  [<c100367e>] kernel_thread_helper+0x6/0x10

in dmesg.

This is a Intel Core 2 Duo E4600 on an Intel board.  File systems are ext4 on LVM.

---

