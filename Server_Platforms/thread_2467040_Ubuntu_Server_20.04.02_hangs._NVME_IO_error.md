---
title: "Ubuntu Server 20.04.02 hangs. NVME I/O error?"
date: 2021-09-14
forum: Server Platforms
---

### Post by ryan170 on 2021-09-14
Hi all,

I'm running Ubuntu Server 20.04.02 on an Intel NUC10i5. It runs primarily as a media server, running plex, sonarr, radarr, and other tools through docker-compose. I don't have any problems with that, but the server does occasionally hang/freeze and needs a reboot.

I tried running dmesg -w until it froze, and this was the output:

[https://pastebin.com/hrk173YW](https://pastebin.com/hrk173YW)

I'm no expert at reading these logs, but it looks to be an NVME I/O error? I'm not quite sure how that would happen. Any other tests I can do to narrow down the culprit? And does that mean replacing the NVME SSD? Or do I need to do something else?

Thanks so much for the help!

---

### Post by ameinild on 2021-09-14
I/O error is usually a symptom of disk failure. How old is the disk, and what is the [SMART status]("https://askubuntu.com/questions/528072/how-can-i-check-the-smart-status-of-a-ssd-or-hdd-on-current-versions-of-ubuntu-1")?

On a server, I would recommend setting up [smartmontools]("https://www.howtoforge.com/tutorial/monitor-harddisk-with-smartmon-on-ubuntu/"), to automatically monitor disk health.

Anyway, you should be prepared to replace the disk in any case.

---

### Post by ryan170 on 2021-09-14
It's a 500gb Kingston NVME M.2 SSD drive. I bought it new less than a year ago.

According to smartmontools, it's not S.M.A.R.T. capable, so smartmontools won't be any help here.

The only other disk is a Kingston 1tb SSD. I'm running a SMART test on that as I type this, but the log seems to indicate that it's the NVME with the I.O. errors.

I think I'll try to reseat the drive and see how it goes. If I don't get any further, I'll have to replace the drive, I guess.

Thanks for the help.

---

### Post by MAFoElffen on 2021-09-14
I'm a bit confused... As I also run server, SSD's and Plex. 

I looked at the logs you posted, and it says that is during Plex. That would have been on a "read"... Because media files are stored and read when played in the media server... 

The kernel show's in that log as version 5.4.0-84-generic., #94. That is current.

When is the last time you did a fsck on your disks? Don't you think if i had disk issues, that before changing things and chasing down possibles, that it might be good to check that first? And is ext4, there would be journal entries pointing to possible problems...

Just saying... maybe you need to check a few things before making some major changes. That and a good backup.

---

### Post by ryan170 on 2021-09-14
> **MAFoElffen said:**
> I'm a bit confused... As I also run server, SSD's and Plex. 

I looked at the logs you posted, and it says that is during Plex. That would have been on a "read"... Because media files are stored and read when played in the media server... 

Thanks for the pointing that out. As stated, I'm not sure what to make of these logs. I'm basically a Linux noob that has put this media server together through tutorials and googling. It works great, except when it hangs/freezes. Hence this post.

> **MAFoElffen said:**
> The kernel show's in that log as version 5.4.0-84-generic., #94. That is current.

When is the last time you did a fsck on your disks? Don't you think if i had disk issues, that before changing things and chasing down possibles, that it might be good to check that first? And is ext4, there would be journal entries pointing to possible problems...

Just saying... maybe you need to check a few things before making some major changes. That and a good backup.

Good idea. Thank you. I'll run an fsck on the disk(s) and see if that turns up anything. How would I check the "journal entries pointing to possible problems" through the CLI? I'll gladly check them and even post them if it helps sort this problem out.

---

### Post by MAFoElffen on 2021-09-15
You didn't say which /dev/xxxx is was, but if that is not your root drive, you can check it while online. If it is, you can reboot and select the Recovery mode from the Grub Menu... and do it from there. (Meaning the root disk has to be unmounted be able to check itself.)

To check the filesystem journal:
```

sudo debugfs -R 'logdump -S' /dev/sdxxx | more

```

---

### Post by ryan170 on 2021-09-15
> **MAFoElffen said:**
> You didn't say which /dev/xxxx is was, but if that is not your root drive, you can check it while online. If it is, you can reboot and select the Recovery mode from the Grub Menu... and do it from there. (Meaning the root disk has to be unmounted be able to check itself.)

To check the filesystem journal:
```

sudo debugfs -R 'logdump -S' /dev/sdxxx | more

```

Thank you.

The only NVME drive I have in this system is a Kingston 500gb M.2 NVME SSD. It is the root drive. here is df -h:
```
/dev/nvme0n1p2            457G   84G  350G  20% /
/dev/nvme0n1p1            511M  5.3M  506M   2% /boot/efi
```

The only other drive in this system is a 2tb SSD used for /downloads (where SABNZBD/Qbittorrent download all files). Otherwise, Plex should be reading off of my NAS (a Synology), which makes this weird: why is Plex hanging while reading from the boot drive?

---

### Post by MAFoElffen on 2021-09-16
That is stranger that I thought... Maybe I should download that whole log to my main desktop and analyze it in my program editor.

Now you have me more curious...

---

### Post by MAFoElffen on 2021-09-16
Here you go:
```

mafoelffen@ubuntu:~/Downloads$ egrep -e 'INFO' ./test.log
[304131.870874] INFO: task kworker/u16:1:234421 blocked for more than 120 seconds.
[304252.701603] INFO: task Plex Media Serv:38619 blocked for more than 120 seconds.
[304373.532235] INFO: task jbd2/nvme0n1p2-:356 blocked for more than 120 seconds.
[304373.532326] INFO: task systemd-journal:434 blocked for more than 120 seconds.
[304373.532452] INFO: task .NET ThreadPool:235025 blocked for more than 120 seconds.
[304373.532527] INFO: task Thread Pool Wor:234825 blocked for more than 120 seconds.
[304373.532593] INFO: task Lidarr:234972 blocked for more than 120 seconds.
[304373.532660] INFO: task Plex Media Serv:38619 blocked for more than 241 seconds.
[304373.532742] INFO: task kworker/u16:1:234421 blocked for more than 120 seconds.
[304373.532820] INFO: task apport:235011 blocked for more than 120 seconds.
mafoelffen@ubuntu:~/Downloads$ egrep -e 'ext4' ./test.log
[304131.870954]  ? ext4_init_io_end+0x1f/0x40
[304131.870955]  ext4_io_submit+0x4d/0x60
[304131.870956]  ext4_writepages+0x44e/0x950
[304252.701691]  ext4_ext_remove_space+0x183/0x930
[304252.701692]  ext4_ext_truncate+0x86/0x90
[304252.701694]  ext4_truncate+0x339/0x400
[304252.701694]  ? __ext4_journal_start_sb+0x69/0x120
[304252.701695]  ext4_evict_inode+0x2de/0x600
[304373.532379]  ext4_mpage_readpages+0x476/0xac0
[304373.532381]  ext4_readpage+0x4d/0xb0
[304373.532388]  ext4_filemap_fault+0x32/0x50
[304373.532507]  ext4_sync_file+0x8f/0x3b0
[304373.532580]  ext4_sync_file+0x8f/0x3b0
[304373.532640]  ? ext4_enable_quotas+0xb0/0x200
[304373.532643]  ext4_io_submit+0x4d/0x60
[304373.532643]  ext4_writepages+0x673/0x950
[304373.532649]  ext4_sync_file+0x8f/0x3b0
[304373.532717]  ext4_ext_remove_space+0x183/0x930
[304373.532718]  ext4_ext_truncate+0x86/0x90
[304373.532719]  ext4_truncate+0x339/0x400
[304373.532719]  ? __ext4_journal_start_sb+0x69/0x120
[304373.532720]  ext4_evict_inode+0x2de/0x600
[304373.532794]  ext4_io_submit+0x4d/0x60
[304373.532794]  ext4_writepages+0x673/0x950
[304373.532869]  ext4_mpage_readpages+0x476/0xac0
[304373.532870]  ext4_readpage+0x4d/0xb0
[304373.532874]  ext4_filemap_fault+0x32/0x50
[304491.475176] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 2755361 (offset 520192 size 4096 starting block 17499455)
[304491.475180] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 20316580 (offset 10448896 size 40960 starting block 23094007)
[304491.475196] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 20316738 (offset 0 size 0 starting block 17501750)
[304491.475201] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 20316694 (offset 0 size 0 starting block 83166643)
[304491.475202] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080232 (offset 0 size 208896 starting block 21019059)
[304491.475226] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080489 (offset 0 size 16384 starting block 28495620)
[304491.475230] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080382 (offset 0 size 20480 starting block 28495615)
[304491.475258] EXT4-fs error (device nvme0n1p2): __ext4_get_inode_loc:4712: inode #12329105: block 49283625: comm sh: unable to read itable block
[304491.475264] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 2755361 (offset 0 size 0 starting block 17499455)
[304491.475287] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080214 (offset 0 size 16384 starting block 28495610)
[304491.475360] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 2755361 (offset 524288 size 4096 starting block 21027200)
[304491.475512] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6953556: comm .NET ThreadPool: reading directory lblock 0
[304491.475730] EXT4-fs error (device nvme0n1p2): ext4_evict_inode:307: comm Plex Media Serv: couldn't truncate inode 20316600 (err -5)
[304491.475768] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #7079902: comm .NET ThreadPool: reading directory lblock 0
[304491.476059] EXT4-fs error (device nvme0n1p2): ext4_wait_block_bitmap:517: comm kworker/u16:1: Cannot read block bitmap - block_group = 620, block_bitmap = 19922956
[304491.476102] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6953556: comm .NET ThreadPool: reading directory lblock 0
[304491.476149] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #20316652: comm Plex Script Hos: reading directory lblock 0
[304491.476207] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #20316652: comm Plex Script Hos: reading directory lblock 0
[304491.476277] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6425870: comm Plex Script Hos: reading directory lblock 0
[304491.476288] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6425870: comm Plex Script Hos: reading directory lblock 0
[304491.477572] EXT4-fs error (device nvme0n1p2): ext4_journal_check_start:61: Detected aborted journal
mafoelffen@ubuntu:~/Downloads$ egrep -e 'error' ./test.log
[304250.369739] blk_update_request: I/O error, dev nvme0n1, sector 171617400 op 0x0:(READ) flags 0x80700 phys_seg 13 prio class 0
[304250.369777] blk_update_request: I/O error, dev nvme0n1, sector 171617512 op 0x0:(READ) flags 0x80700 phys_seg 4 prio class 0
[304250.369820] blk_update_request: I/O error, dev nvme0n1, sector 137576752 op 0x0:(READ) flags 0x80700 phys_seg 3 prio class 0
[304250.369947] blk_update_request: I/O error, dev nvme0n1, sector 215453104 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
[304491.475176] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 2755361 (offset 520192 size 4096 starting block 17499455)
[304491.475178] Buffer I/O error on device nvme0n1p2, logical block 117657320
[304491.475180] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 20316580 (offset 10448896 size 40960 starting block 23094007)
[304491.475182] Buffer I/O error on device nvme0n1p2, logical block 22962679
[304491.475186] Buffer I/O error on device nvme0n1p2, logical block 117657321
[304491.475189] blk_update_request: I/O error, dev nvme0n1, sector 140013976 op 0x1:(WRITE) flags 0x800 phys_seg 3 prio class 0
[304491.475192] blk_update_request: I/O error, dev nvme0n1, sector 488779720 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[304491.475193] blk_update_request: I/O error, dev nvme0n1, sector 168152320 op 0x1:(WRITE) flags 0x0 phys_seg 6 prio class 0
[304491.475194] Buffer I/O error on dev nvme0n1p2, logical block 60966137, lost sync page write
[304491.475196] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 20316738 (offset 0 size 0 starting block 17501750)
[304491.475197] blk_update_request: I/O error, dev nvme0n1, sector 665333120 op 0x1:(WRITE) flags 0x800 phys_seg 3 prio class 0
[304491.475198] blk_update_request: I/O error, dev nvme0n1, sector 168152064 op 0x1:(WRITE) flags 0x4000 phys_seg 11 prio class 0
[304491.475199] Buffer I/O error on device nvme0n1p2, logical block 17370419
[304491.475201] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 20316694 (offset 0 size 0 starting block 83166643)
[304491.475202] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080232 (offset 0 size 208896 starting block 21019059)
[304491.475203] Buffer I/O error on device nvme0n1p2, logical block 83035312
[304491.475205] Buffer I/O error on device nvme0n1p2, logical block 20887680
[304491.475207] Buffer I/O error on device nvme0n1p2, logical block 17368127
[304491.475207] Buffer I/O error on device nvme0n1p2, logical block 20887681
[304491.475208] Buffer I/O error on device nvme0n1p2, logical block 17370420
[304491.475208] Buffer I/O error on device nvme0n1p2, logical block 20887682
[304491.475224] blk_update_request: I/O error, dev nvme0n1, sector 227964928 op 0x1:(WRITE) flags 0x0 phys_seg 2 prio class 0
[304491.475226] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080489 (offset 0 size 16384 starting block 28495620)
[304491.475229] blk_update_request: I/O error, dev nvme0n1, sector 227964880 op 0x1:(WRITE) flags 0x0 phys_seg 2 prio class 0
[304491.475230] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080382 (offset 0 size 20480 starting block 28495615)
[304491.475233] blk_update_request: I/O error, dev nvme0n1, sector 227964848 op 0x1:(WRITE) flags 0x0 phys_seg 2 prio class 0
[304491.475258] EXT4-fs error (device nvme0n1p2): __ext4_get_inode_loc:4712: inode #12329105: block 49283625: comm sh: unable to read itable block
[304491.475262] blk_update_request: I/O error, dev nvme0n1, sector 139995632 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[304491.475264] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 2755361 (offset 0 size 0 starting block 17499455)
[304491.475287] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 7080214 (offset 0 size 16384 starting block 28495610)
[304491.475323] Buffer I/O error on dev nvme0n1p2, logical block 0, lost sync page write
[304491.475347] blk_update_request: I/O error, dev nvme0n1, sector 227964808 op 0x1:(WRITE) flags 0x0 phys_seg 2 prio class 0
[304491.475360] EXT4-fs warning (device nvme0n1p2): ext4_end_bio:309: I/O error 10 writing to inode 2755361 (offset 524288 size 4096 starting block 21027200)
[304491.475363] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.475512] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6953556: comm .NET ThreadPool: reading directory lblock 0
[304491.475593] Buffer I/O error on dev nvme0n1p2, logical block 6, lost async page write
[304491.475612] Buffer I/O error on dev nvme0n1p2, logical block 0, lost sync page write
[304491.475647] Buffer I/O error on dev nvme0n1p2, logical block 39, lost async page write
[304491.475669] Read-error on swap-device (259:0:4178952)
[304491.475683] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.475684] Read-error on swap-device (259:0:6799200)
[304491.475721] Buffer I/O error on dev nvme0n1p2, logical block 11010050, lost async page write
[304491.475722] systemd-journal[434]: segfault at 7fcddddeac60 ip 00007fcddddeac60 sp 00007ffd1a8c7628 error 15
[304491.475730] EXT4-fs error (device nvme0n1p2): ext4_evict_inode:307: comm Plex Media Serv: couldn't truncate inode 20316600 (err -5)
[304491.475732] EXT4-fs (nvme0n1p2): previous I/O error to superblock detected
[304491.475735] Buffer I/O error on dev nvme0n1p2, logical block 0, lost sync page write
[304491.475736] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.475768] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #7079902: comm .NET ThreadPool: reading directory lblock 0
[304491.475785] Buffer I/O error on dev nvme0n1p2, logical block 19922956, lost async page write
[304491.475823] Buffer I/O error on dev nvme0n1p2, logical block 0, lost sync page write
[304491.475841] Buffer I/O error on dev nvme0n1p2, logical block 19922957, lost async page write
[304491.475883] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.476059] EXT4-fs error (device nvme0n1p2): ext4_wait_block_bitmap:517: comm kworker/u16:1: Cannot read block bitmap - block_group = 620, block_bitmap = 19922956
[304491.476102] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6953556: comm .NET ThreadPool: reading directory lblock 0
[304491.476118] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.476149] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #20316652: comm Plex Script Hos: reading directory lblock 0
[304491.476151] EXT4-fs (nvme0n1p2): previous I/O error to superblock detected
[304491.476152] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.476207] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #20316652: comm Plex Script Hos: reading directory lblock 0
[304491.476208] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.476277] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6425870: comm Plex Script Hos: reading directory lblock 0
[304491.476278] EXT4-fs (nvme0n1p2): I/O error while writing superblock
[304491.476288] EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #6425870: comm Plex Script Hos: reading directory lblock 0
[304491.477502] Read-error on swap-device (259:0:6799064)
[304491.477514] Read-error on swap-device (259:0:6406504)
[304491.477518] Read-error on swap-device (259:0:6406416)
[304491.477523] JBD2: Detected IO errors while flushing file data on nvme0n1p2-8
[304491.477572] EXT4-fs error (device nvme0n1p2): ext4_journal_check_start:61: Detected aborted journal
[304491.477865] Read-error on swap-device (259:0:4702944)
[304491.477866] Read-error on swap-device (259:0:4438896)
[304491.479286] Write-error on swap-device (259:0:14989688)
[304491.479296] JBD2: Detected IO errors while flushing file data on nvme0n1p2-8
[304491.480241] Read-error on swap-device (259:0:4438368)
[304491.480251] Read-error on swap-device (259:0:4045216)
[304491.480261] Read-error on swap-device (259:0:4831616)
[304491.480743] Read-error on swap-device (259:0:4045416)
[304491.480880] Read-error on swap-device (259:0:4045232)
[304491.482202] Write-error on swap-device (259:0:14989648)
[304491.491524] Read-error on swap-device (259:0:4441064)
[304491.491677] Write-error on swap-device (259:0:14989656)
[304491.492881] Read-error on swap-device (259:0:4438408)
[304491.494319] Write-error on swap-device (259:0:14989664)
[304491.496108] Read-error on swap-device (259:0:4045312)
[304491.497659] Write-error on swap-device (259:0:14989672)
[304491.499355] Read-error on swap-device (259:0:4048000)
[304491.501025] Write-error on swap-device (259:0:14989680)
[304491.502792] Read-error on swap-device (259:0:4441088)
[304491.535466] Read-error on swap-device (259:0:4308144)
[304491.565336] systemd[235297]: systemd-journal-flush.service: Failed to execute command: Input/output error
[304491.574959] Read-error on swap-device (259:0:4046024)
[304491.577814] Read-error on swap-device (259:0:4569104)
[304491.577821] Read-error on swap-device (259:0:4308136)
[304491.577839] Read-error on swap-device (259:0:4307008)
[304491.577864] Read-error on swap-device (259:0:4046008)
[304491.577868] Read-error on swap-device (259:0:4045984)
[304491.578064] Read-error on swap-device (259:0:4047992)
[304491.578334] Read-error on swap-device (259:0:4175904)
[304491.578336] Read-error on swap-device (259:0:4175912)
[304491.578337] Read-error on swap-device (259:0:4175920)
[304491.578338] Read-error on swap-device (259:0:4175928)

```

Okay. I have questions now (many). please run the system-info script in my signature line. When it asks if you want to post the results to Pastebin, choose Y(es)... It i just going to collect support types of system and computer information... Especially after this:
```

mafoelffen@ubuntu:~/Downloads$ egrep -a2 'RIP' ./test.log
[304252.701702]  do_syscall_64+0x57/0x190
[304252.701703]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[304252.701704] RIP: 0033:0x7f5df25e65c0
[304252.701707] Code: Bad RIP value.
[304252.701708] RSP: 002b:00007f5deef517d8 EFLAGS: 00000282 ORIG_RAX: 0000000000000057
[304252.701709] RAX: ffffffffffffffda RBX: 00007f5deef51858 RCX: 00007f5df25e65c0
--
[304373.532396]  do_page_fault+0x2c/0xe0
[304373.532397]  page_fault+0x34/0x40
[304373.532398] RIP: 0033:0x7fcddddeac60
[304373.532401] Code: Bad RIP value.
[304373.532402] RSP: 002b:00007ffd1a8c7628 EFLAGS: 00010202
[304373.532403] RAX: 0000000000000002 RBX: 0000000000000003 RCX: 0000000000000020
--
[304373.532514]  do_syscall_64+0x57/0x190
[304373.532515]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[304373.532515] RIP: 0033:0x7fd0fdcaa3eb
[304373.532516] Code: Bad RIP value.
[304373.532517] RSP: 002b:00007fd049ff7d00 EFLAGS: 00000293 ORIG_RAX: 000000000000004b
[304373.532518] RAX: ffffffffffffffda RBX: 00007fcfe0099538 RCX: 00007fd0fdcaa3eb
--
[304373.532585]  do_syscall_64+0x57/0x190
[304373.532586]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[304373.532586] RIP: 0033:0x7fb599b260c7
[304373.532587] Code: Bad RIP value.
[304373.532588] RSP: 002b:00007fb5337f9b30 EFLAGS: 00000293 ORIG_RAX: 000000000000004b
[304373.532588] RAX: ffffffffffffffda RBX: 000000000000000c RCX: 00007fb599b260c7
--
[304373.532654]  do_syscall_64+0x57/0x190
[304373.532655]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[304373.532656] RIP: 0033:0x7f92a4c5a0c7
[304373.532657] Code: Bad RIP value.
[304373.532657] RSP: 002b:00007f9200ff5cd0 EFLAGS: 00000293 ORIG_RAX: 000000000000004b
[304373.532657] RAX: ffffffffffffffda RBX: 0000000000000113 RCX: 00007f92a4c5a0c7
--
[304373.532726]  do_syscall_64+0x57/0x190
[304373.532726]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[304373.532727] RIP: 0033:0x7f5df25e65c0
[304373.532728] Code: Bad RIP value.
[304373.532728] RSP: 002b:00007f5deef517d8 EFLAGS: 00000282 ORIG_RAX: 0000000000000057
[304373.532728] RAX: ffffffffffffffda RBX: 00007f5deef51858 RCX: 00007f5df25e65c0
--
[304373.532880]  do_page_fault+0x2c/0xe0
[304373.532881]  page_fault+0x34/0x40
[304373.532882] RIP: 0033:0x7fe2dd5995c3
[304373.532883] Code: Bad RIP value.
[304373.532883] RSP: 002b:00007ffc211d6038 EFLAGS: 00010206
[304373.532883] RAX: 00007fe2dc555f60 RBX: 00007ffc211d60d0 RCX: 00007fe2dc555fa0

```
*** Important that you do not reboot yuor computer before running that. I want to get an accurate picture of what is going on... What it is running on... And the boundaries that it is working within... To recommend a solution for that.

It is paging heavily. It is going into Kernel Panic... So the read/writes may just be a side-product of those. That is an early guess-sta-mation of what I see there so far.

---

### Post by MAFoElffen on 2021-09-16
No answer, so I'll just say it... It looks as if there is a memory leak somewhere... where it then builds up and starts paging, until the the kernel goes into panic and affects other things, such as I/O. 

It's like it doesn't start out with the I/O problem, but then as things build up that becomes one of the other symptoms of. The disk I?O isn't causing the CPU bad pointer addressing problem... where it gets dementia and loses it's place of where is wants to return to, and gets "lost"..

Not saying that is definitely what is going on, without more information. Based on that information, one of the alternatives may be to try a different kernel version (earlier or mainline) or series (HWE).

---

### Post by TheFu on 2021-09-16
I'd check for high temperatures.  Small cases don't often have great cooling and NVMe devices using an m.2 slot sometimes need a heatsink to help effectively cool them down.

My CPU is currently +50.4°C, but under transcode loads, I've seen it as high as 95°C before it self-throttles.  My m.2 SSD is currently, 
```
Disk: /dev/sdb
Current Temperature:                    45 Celsius
```
Under load, it runs about 10°C hotter than spinning disks do - so 55°C is about the highest I've ever seen.  Some enterprise 10K rpm HDDs run hotter.
For example, can you guess which is the enterprise disk in this list?  
```
Disk: /dev/sda
Current Temperature:                    39 Celsius
Disk: /dev/sdc
Current Temperature:                    47 Celsius
Disk: /dev/sdd
Current Temperature:                    35 Celsius
Disk: /dev/sde
Current Temperature:                    38 Celsius
Disk: /dev/sdf
Current Temperature:                    34 Celsius
Disk: /dev/sdg
Current Temperature:                    33 Celsius
```
Hint, none are SSDs.

If a name-brand SSD doesn't support SMART, there is definitely a connectivity issue.  Kingston will support SMART.  BTW, new, reputable, SSDs fail from time to time within the first few months. All storage fails, so having backups really isn't optional for anything you don't want to lose.  A 2TB USB3 spinning disk is just $50, so there is little chance that the time needed to recreate that data will be less than $50 of your time and effort.  Especially if you actually got a 2TB SSD for media serving?  Srsly?  No need regardless of the media involved.  A cheapo external USB2 HDD would almost certainly be faster than needed to provide streaming 4K videos to the house.

Page faults can be caused by bad RAM.  If you had a Ryzen, I'd say to stick with DOCP settings, but back off on the speed a few hundred Mhz to get a stable setup and perhaps raise the voltage +0.05V.  With Intel, all I can say is to run memtest for at least 24 hours straight.

---

### Post by MAFoElffen on 2021-09-16
Like I said, the ramp up to those in his logs, look like they start as memory leakage errors... Which then turns to paging... then kernel panic.

And for Plex... LOL. My son and I both do. Not a lot of load demand or blazing speed needed. His is on a Raspberry Pi with some old portable USB2.0 2.5" HDD's. Mine run's in background on one of my servers. I forget most of the time that it is even there.

---

### Post by insom2 on 2022-04-06
I have the same issue occurring on a server I manage. I tried upgrading the firmware for the Samsung 980 PRO SSDs but still happening. Used to take 30 days, now it did it in 5 days so seems random. It is primarily used for Plex.. common theme and a few docker containers for stuff.

What can I do to provide logs etc?

---

