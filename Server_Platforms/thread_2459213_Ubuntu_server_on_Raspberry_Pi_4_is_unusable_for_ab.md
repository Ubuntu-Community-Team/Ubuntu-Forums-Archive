---
title: "Ubuntu server on Raspberry Pi 4 is unusable for about 10 min every night after 12am"
date: 2021-03-13
forum: Server Platforms
---

### Post by tiny-ninja on 2021-03-13
I have Ubuntu server 20.04.2 LTS (GNU/Linux 5.4.0-1029-raspi aarch64) running on Raspberry Pi 4. Every night at 12am, all services stop working for about 10 min, then everything goes back to normal. I'd like to fix this but I have no idea why this is happening. Can someone help?
Syslogs below.

```
Mar 13 00:00:01 raspi systemd[1]: logrotate.service: Succeeded.
Mar 13 00:00:01 raspi systemd[1]: Finished Rotate log files.
Mar 13 00:00:01 raspi CRON[428511]: (root) CMD (   PATH="$PATH:/usr/sbin:/usr/local/bin/" pihole flush once quiet)
Mar 13 00:00:01 raspi CRON[428512]: (root) CMD (   PATH="$PATH:/usr/sbin:/usr/local/bin/" pihole updatechecker local)
Mar 13 00:00:10 raspi kernel: [603629.411236] mmc0: Got data interrupt 0x00000002 even though no data operation was in progress.
Mar 13 00:00:18 raspi kernel: [603637.624238] mmc0: Got data interrupt 0x00000002 even though no data operation was in progress.
Mar 13 00:00:27 raspi kernel: [603645.983337] blk_update_request: I/O error, dev mmcblk0, sector 19569480 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:00:35 raspi kernel: [603654.186345] blk_update_request: I/O error, dev mmcblk0, sector 19569481 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:00:43 raspi kernel: [603662.389350] blk_update_request: I/O error, dev mmcblk0, sector 19569482 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:00:51 raspi kernel: [603670.592338] blk_update_request: I/O error, dev mmcblk0, sector 19569483 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:00:59 raspi kernel: [603678.795343] blk_update_request: I/O error, dev mmcblk0, sector 19569484 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:01:08 raspi kernel: [603686.998340] blk_update_request: I/O error, dev mmcblk0, sector 19569485 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:01:16 raspi kernel: [603695.201360] blk_update_request: I/O error, dev mmcblk0, sector 19569486 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:01:24 raspi kernel: [603703.404386] blk_update_request: I/O error, dev mmcblk0, sector 19569487 op 0x0:(READ) flags 0x80700 phys_seg 14 prio class 0
Mar 13 00:01:32 raspi kernel: [603711.613343] blk_update_request: I/O error, dev mmcblk0, sector 19569496 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:01:40 raspi kernel: [603719.816338] blk_update_request: I/O error, dev mmcblk0, sector 19569497 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:01:49 raspi kernel: [603728.019343] blk_update_request: I/O error, dev mmcblk0, sector 19569498 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:01:57 raspi kernel: [603736.222356] blk_update_request: I/O error, dev mmcblk0, sector 19569499 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:02:05 raspi kernel: [603744.425332] blk_update_request: I/O error, dev mmcblk0, sector 19569500 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:02:13 raspi kernel: [603752.628360] blk_update_request: I/O error, dev mmcblk0, sector 19569501 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:02:21 raspi kernel: [603760.831353] blk_update_request: I/O error, dev mmcblk0, sector 19569502 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:02:30 raspi kernel: [603769.034339] blk_update_request: I/O error, dev mmcblk0, sector 19569503 op 0x0:(READ) flags 0x80700 phys_seg 12 prio class 0
Mar 13 00:02:38 raspi kernel: [603777.243349] blk_update_request: I/O error, dev mmcblk0, sector 19569512 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:02:46 raspi kernel: [603785.446314] blk_update_request: I/O error, dev mmcblk0, sector 19569513 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:02:54 raspi kernel: [603793.649338] blk_update_request: I/O error, dev mmcblk0, sector 19569514 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:02 raspi kernel: [603801.852359] blk_update_request: I/O error, dev mmcblk0, sector 19569515 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:11 raspi kernel: [603810.055367] blk_update_request: I/O error, dev mmcblk0, sector 19569516 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:19 raspi kernel: [603818.258337] blk_update_request: I/O error, dev mmcblk0, sector 19569517 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:27 raspi kernel: [603826.461339] blk_update_request: I/O error, dev mmcblk0, sector 19569518 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:35 raspi kernel: [603834.664337] blk_update_request: I/O error, dev mmcblk0, sector 19569519 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:43 raspi kernel: [603842.867347] blk_update_request: I/O error, dev mmcblk0, sector 19569520 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:03:52 raspi kernel: [603851.070346] blk_update_request: I/O error, dev mmcblk0, sector 19569521 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:00 raspi kernel: [603859.273351] blk_update_request: I/O error, dev mmcblk0, sector 19569522 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:08 raspi kernel: [603867.476337] blk_update_request: I/O error, dev mmcblk0, sector 19569523 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:16 raspi kernel: [603875.679353] blk_update_request: I/O error, dev mmcblk0, sector 19569524 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:24 raspi kernel: [603883.882332] blk_update_request: I/O error, dev mmcblk0, sector 19569525 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:33 raspi kernel: [603892.085347] blk_update_request: I/O error, dev mmcblk0, sector 19569526 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:41 raspi kernel: [603900.288338] blk_update_request: I/O error, dev mmcblk0, sector 19569527 op 0x0:(READ) flags 0x80700 phys_seg 11 prio class 0
Mar 13 00:04:49 raspi kernel: [603908.491335] blk_update_request: I/O error, dev mmcblk0, sector 19569528 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:04:57 raspi kernel: [603916.694346] blk_update_request: I/O error, dev mmcblk0, sector 19569529 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:06 raspi kernel: [603924.897335] blk_update_request: I/O error, dev mmcblk0, sector 19569530 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:14 raspi kernel: [603933.100347] blk_update_request: I/O error, dev mmcblk0, sector 19569531 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:22 raspi kernel: [603941.303337] blk_update_request: I/O error, dev mmcblk0, sector 19569532 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:30 raspi kernel: [603949.506308] blk_update_request: I/O error, dev mmcblk0, sector 19569533 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:38 raspi kernel: [603957.709329] blk_update_request: I/O error, dev mmcblk0, sector 19569534 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:47 raspi kernel: [603965.912351] blk_update_request: I/O error, dev mmcblk0, sector 19569535 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:05:55 raspi kernel: [603974.115328] blk_update_request: I/O error, dev mmcblk0, sector 19569536 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:03 raspi kernel: [603982.318330] blk_update_request: I/O error, dev mmcblk0, sector 19569537 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:11 raspi kernel: [603990.521331] blk_update_request: I/O error, dev mmcblk0, sector 19569538 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:19 raspi kernel: [603998.724359] blk_update_request: I/O error, dev mmcblk0, sector 19569539 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:28 raspi kernel: [604006.927345] blk_update_request: I/O error, dev mmcblk0, sector 19569540 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:36 raspi kernel: [604015.130351] blk_update_request: I/O error, dev mmcblk0, sector 19569541 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:44 raspi kernel: [604023.333342] blk_update_request: I/O error, dev mmcblk0, sector 19569542 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:06:52 raspi kernel: [604031.536348] blk_update_request: I/O error, dev mmcblk0, sector 19569543 op 0x0:(READ) flags 0x80700 phys_seg 10 prio class 0
Mar 13 00:07:00 raspi kernel: [604039.747342] blk_update_request: I/O error, dev mmcblk0, sector 19569560 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:09 raspi kernel: [604047.950309] blk_update_request: I/O error, dev mmcblk0, sector 19569561 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:17 raspi kernel: [604056.153344] blk_update_request: I/O error, dev mmcblk0, sector 19569562 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:25 raspi kernel: [604064.356299] blk_update_request: I/O error, dev mmcblk0, sector 19569563 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:33 raspi kernel: [604072.559344] blk_update_request: I/O error, dev mmcblk0, sector 19569564 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:41 raspi kernel: [604080.762337] blk_update_request: I/O error, dev mmcblk0, sector 19569565 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:50 raspi kernel: [604088.965326] blk_update_request: I/O error, dev mmcblk0, sector 19569566 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:07:58 raspi kernel: [604097.168356] blk_update_request: I/O error, dev mmcblk0, sector 19569567 op 0x0:(READ) flags 0x80700 phys_seg 8 prio class 0
Mar 13 00:08:06 raspi kernel: [604105.875222] mmc0: Got data interrupt 0x00000002 even though no data operation was in progress.
Mar 13 00:08:15 raspi kernel: [604114.112219] mmc0: Got data interrupt 0x00000002 even though no data operation was in progress.
Mar 13 00:08:23 raspi kernel: [604122.440311] blk_update_request: I/O error, dev mmcblk0, sector 19569480 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:08:31 raspi kernel: [604130.643326] blk_update_request: I/O error, dev mmcblk0, sector 19569481 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:08:39 raspi kernel: [604138.846334] blk_update_request: I/O error, dev mmcblk0, sector 19569482 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:08:48 raspi kernel: [604147.049273] blk_update_request: I/O error, dev mmcblk0, sector 19569483 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:08:56 raspi kernel: [604155.252322] blk_update_request: I/O error, dev mmcblk0, sector 19569484 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:09:04 raspi kernel: [604163.455342] blk_update_request: I/O error, dev mmcblk0, sector 19569485 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:09:12 raspi kernel: [604171.658311] blk_update_request: I/O error, dev mmcblk0, sector 19569486 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:09:20 raspi kernel: [604179.861317] blk_update_request: I/O error, dev mmcblk0, sector 19569487 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:09:29 raspi kernel: [604188.077221] mmc0: Got data interrupt 0x00000002 even though no data operation was in progress.
Mar 13 00:09:37 raspi kernel: [604196.302218] mmc0: Got data interrupt 0x00000002 even though no data operation was in progress.
Mar 13 00:09:45 raspi kernel: [604204.503322] blk_update_request: I/O error, dev mmcblk0, sector 19569480 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:09:53 raspi kernel: [604212.706324] blk_update_request: I/O error, dev mmcblk0, sector 19569481 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:10:02 raspi kernel: [604220.909319] blk_update_request: I/O error, dev mmcblk0, sector 19569482 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:10:10 raspi kernel: [604229.112342] blk_update_request: I/O error, dev mmcblk0, sector 19569483 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:10:18 raspi kernel: [604237.315333] blk_update_request: I/O error, dev mmcblk0, sector 19569484 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:10:26 raspi kernel: [604245.518333] blk_update_request: I/O error, dev mmcblk0, sector 19569485 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:10:34 raspi kernel: [604253.721325] blk_update_request: I/O error, dev mmcblk0, sector 19569486 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
Mar 13 00:10:43 raspi kernel: [604261.924301] blk_update_request: I/O error, dev mmcblk0, sector 19569487 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0


```

---

### Post by DuckHook on 2021-03-13
Welcome to the forums, tiny-ninja

You are running a pi hole. I am not familiar with the pi hole implementation but could it be running a cron job every night?

The log entry is telling you that something is trying to write to your SD card unsuccessfully. I/O error could mean a lot of things, but write&#8209;wear is a possibility. In general, RPis need special adjustments when running Ubuntu server because constant log activity and journaling will kill the card quickly. Many turn off journaling (not recommended), hive logs off to a cheap replaceable external USB stick, or buy a good external SSD, then use the SD card only for boot sector and the SSD for the actual OS.

In your case, it is unlikely to be write&#8209;wear, else you would have a lot more problems by now, but I'm not the one to advise you on the inner workings of pi hole.

---

