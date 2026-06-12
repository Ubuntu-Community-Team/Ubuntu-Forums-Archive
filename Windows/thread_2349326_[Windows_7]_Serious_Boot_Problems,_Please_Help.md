---
title: "[Windows 7] Serious Boot Problems, Please Help"
date: 2017-01-13
forum: Windows
---

### Post by zrk4444 on 2017-01-13
Alright, so I went go put in 16 GB of new Ram and turned on my computer and I got something along the lines of 'Boot MSR is missing / OS is missing'. I've tried to use a boot-repair, but it did not work. I do not have a Windows install/cannot use MS Windows Recovery Disc due to this installation not being 'legit'. I'll post what Boot-repair put out below, much help appreciated!
-


-
[COLOR=#000] [h=1]Ubuntu Pastebin[/h] [h=1]Paste from boot-repair at Fri, 13 Jan 2017 16:32:34 +0000[/h] [Download as text]("http://paste.ubuntu.com/23792959/plain/") [TABLE="class: pastetable"]
+
```
[h=1]Ubuntu Pastebin[/h] [h=1]Paste from boot-repair at Fri, 13 Jan 2017 16:32:34 +0000[/h] [Download as text]("http://paste.ubuntu.com/23792959/plain/") [TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
[/TD]
[TD="class: code"] Boot Info Script e7fc706 + Boot-Repair extra info [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

=> Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
=> Windows 7/8/2012 is installed in the MBR of /dev/sdb.
=> Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows 7/2008: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: 

sdb1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows 7/2008: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: /bootmgr /Boot/BCD

sdb2: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows 7/2008: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sdc1: __________________________________________________ ________________________

File system: vfat
Boot sector type: SYSLINUX 4.03 debian-20101222 ...........>...s>........\.....0...~.~...~...f...M .f.f....f..8~....>E}
Boot sector info: Syslinux looks at sector 1357290 of /dev/sdc1 for its 
second stage. SYSLINUX is installed in the directory. 
No errors found in the Boot Parameter Block.
Operating System: 
Boot files: /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
/EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 2,048 1,953,521,663 1,953,519,616 7 NTFS / exFAT / HPFS


Drive: sdb __________________________________________________ ___________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sdb2 * 206,848 1,953,521,663 1,953,314,816 7 NTFS / exFAT / HPFS


Drive: sdc __________________________________________________ ___________________

Disk /dev/sdc: 16.0 GB, 16018046976 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 2,048 31,285,247 31,283,200 c W95 FAT32 (LBA)


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs 
/dev/sda1 4616DE1716DE07B7 ntfs 
/dev/sdb1 2C96F36D96F335C4 ntfs System Reserved
/dev/sdb2 6E181C64181C2E19 ntfs 
/dev/sdc1 7AD7-18BB vfat 
/dev/zram0 04d6dcd6-c217-4d8f-ba4d-53cc1a2b91b4 swap 
/dev/zram1 ab939914-98cf-4691-9281-43f05554a0ef swap 
/dev/zram2 7a9e61ce-5658-403a-b4e7-a345c2388eeb swap 
/dev/zram3 2de75bc1-15f0-4e04-b0c8-3f943b7c139b swap 

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 9 Jan 13 16:32 ata-Hitachi_HDT721010SLA360_STF605MS0GGD1K -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 13 16:32 ata-Hitachi_HDT721010SLA360_STF605MS0GGD1K-part1 -> ../../sda1
lrwxrwxrwx 1 root root 9 Jan 13 11:22 ata-ST1000DM003-1ER162_Z4YB9Z01 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan 13 16:32 ata-ST1000DM003-1ER162_Z4YB9Z01-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jan 13 16:32 ata-ST1000DM003-1ER162_Z4YB9Z01-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 9 Jan 13 11:22 ata-TSSTcorp_CDDVDW_SH-S223B_0e23E56789ALMNOP -> ../../sr0
lrwxrwxrwx 1 root root 9 Jan 13 11:22 usb-Lexar_USB_Flash_Drive_AABAU88QZ8DVGC6L-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jan 13 11:22 usb-Lexar_USB_Flash_Drive_AABAU88QZ8DVGC6L-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 9 Jan 13 11:22 wwn-0x5000c500879c29cb -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan 13 16:32 wwn-0x5000c500879c29cb-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jan 13 16:32 wwn-0x5000c500879c29cb-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 9 Jan 13 16:32 wwn-0x5000cca35ec69335 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 13 16:32 wwn-0x5000cca35ec69335-part1 -> ../../sda1

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sdc1 /cdrom vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,ioc harset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
set gfxmode=auto
insmod efi_gop
insmod efi_uga
insmod gfxterm
terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Boot-Repair-Disk session" {
set gfxpayload=keep
linux	/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

menu.c32 : COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/2184/mounts) leaked on lvs invocation. Parent PID 10376: bash
File descriptor 63 (pipe:[27082]) leaked on lvs invocation. Parent PID 10376: bash
No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-01-13__11h22 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2184/mounts) leaked on lvs invocation. Parent PID 4614: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s): 32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="4616DE1716DE07B7" TYPE="ntfs"
/dev/sdb1: LABEL="System Reserved" UUID="2C96F36D96F335C4" TYPE="ntfs"
/dev/sdb2: UUID="6E181C64181C2E19" TYPE="ntfs"
/dev/sdc1: UUID="7AD7-18BB" TYPE="vfat"
/dev/zram0: UUID="04d6dcd6-c217-4d8f-ba4d-53cc1a2b91b4" TYPE="swap"
/dev/zram1: UUID="ab939914-98cf-4691-9281-43f05554a0ef" TYPE="swap"
/dev/zram2: UUID="7a9e61ce-5658-403a-b4e7-a345c2388eeb" TYPE="swap"
/dev/zram3: UUID="2de75bc1-15f0-4e04-b0c8-3f943b7c139b" TYPE="swap"

Windows not detected by os-prober on sdb2.

efibootmgr -v
BootCurrent: 0009
Timeout: 1 seconds
BootOrder: 0008,0009,0006,0007,0002
Boot0002* UEFI: Built-in EFI Shell Vendor(5023b95c-db26-429b-a648-bd47664c8012,)..BO
Boot0006* Hard Drive BIOS(2,0,00)..GO..NO........o.H.i.t.a.c.h.i. .H.D.T.7.2.1.0.1.0.S.L.A.3.6.0................... .A...........................>..Gd-.;.A..MQ..L. . . . . . .T.S.6.F.5.0.S.M.G.0.D.G.K.1........BO..NO....... .o.S.T.1.0.0.0.D.M.0.0.3.-.1.E.R.1.6.2....................A................ ...........>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.B.Y.Z.9.1.0........BO
Boot0007* CD/DVD Drive BIOS(3,0,00)..GO..NO........o.T.S.S.T.c.o.r.p. .C.D.D.V.D.W. .S.H.-.S.2.2.3.B....................A.................. .........>..Gd-.;.A..MQ..L.e.0.3.2.5.E.7.6.9.8.L.A.N.M.P.O. . . . ........BO
Boot0008* Unknown Device BIOS(b,0,00)..GO..NO........i.L.e.x.a.r. .U.S.B. .F.l.a.s.h. .D.r.i.v.e. .1.1.0.0....................A.................... .........6..Gd-.;.A..MQ..L.A.A.B.A.U.8.8.Q.Z.8.D.V.G.C.6.L...... ..BO
Boot0009* UEFI: (FAT) Lexar USB Flash Drive 1100	ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(0,0)HD(1,800,1 dd5800,a25e3efe)..BO
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [email]boot.repair@gmail.com[/email]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid, no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid, bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.
sdb2	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid, no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb2.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, not-usb,	no-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 1000GB 1000GB primary ntfs boot


Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs
2 106MB 1000GB 1000GB primary ntfs boot


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 16.0GB 16.0GB primary fat32 lba




Error: /dev/zram0: unrecognised disk label



Error: /dev/zram1: unrecognised disk label



Error: /dev/zram2: unrecognised disk label



Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA Hitachi HDT72101;
1:1049kB:1000GB:1000GB:ntfs::boot;

BYT;
/dev/sdb:1000GB:scsi:512:4096:msdos:ATA ST1000DM003-1ER1;
1:1049kB:106MB:105MB:ntfs::;
2:106MB:1000GB:1000GB:ntfs::boot;

BYT;
/dev/sdc:16.0GB:scsi:512:512:msdos:Lexar USB Flash Drive;
1:1049kB:16.0GB:16.0GB:fat32::lba;



Error: /dev/zram0: unrecognised disk label



Error: /dev/zram1: unrecognised disk label



Error: /dev/zram2: unrecognised disk label



Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,ioc harset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered): autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper: control

=================== hexdump -n512 -C /dev/sda1
00000000 eb 52 90 4e 54 46 53 20 20 20 20 00 02 08 00 00 |.R.NTFS .....|
00000010 00 00 00 00 00 f8 00 00 3f 00 ff 00 00 08 00 00 |........?.......|
00000020 00 00 00 00 80 00 80 00 ff 57 70 74 00 00 00 00 |.........Wpt....|
00000030 00 00 0c 00 00 00 00 00 02 00 00 00 00 00 00 00 |................|
00000040 f6 00 00 00 01 00 00 00 b7 07 de 16 17 de 16 46 |...............F|
00000050 00 00 00 00 fa 33 c0 8e d0 bc 00 7c fb 68 c0 07 |.....3.....|.h..|
00000060 1f 1e 68 66 00 cb 88 16 0e 00 66 81 3e 03 00 4e |..hf......f.>..N|
00000070 54 46 53 75 15 b4 41 bb aa 55 cd 13 72 0c 81 fb |TFSu..A..U..r...|
00000080 55 aa 75 06 f7 c1 01 00 75 03 e9 dd 00 1e 83 ec |U.u.....u.......|
00000090 18 68 1a 00 b4 48 8a 16 0e 00 8b f4 16 1f cd 13 |.h...H..........|
000000a0 9f 83 c4 18 9e 58 1f 72 e1 3b 06 0b 00 75 db a3 |.....X.r.;...u..|
000000b0 0f 00 c1 2e 0f 00 04 1e 5a 33 db b9 00 20 2b c8 |........Z3... +.|
000000c0 66 ff 06 11 00 03 16 0f 00 8e c2 ff 06 16 00 e8 |f...............|
000000d0 4b 00 2b c8 77 ef b8 00 bb cd 1a 66 23 c0 75 2d |K.+.w......f#.u-|
000000e0 66 81 fb 54 43 50 41 75 24 81 f9 02 01 72 1e 16 |f..TCPAu$....r..|
000000f0 68 07 bb 16 68 70 0e 16 68 09 00 66 53 66 53 66 |h...hp..h..fSfSf|
00000100 55 16 16 16 68 b8 01 66 61 0e 07 cd 1a 33 c0 bf |U...h..fa....3..|
00000110 28 10 b9 d8 0f fc f3 aa e9 5f 01 90 90 66 60 1e |(........_...f`.|
00000120 06 66 a1 11 00 66 03 06 1c 00 1e 66 68 00 00 00 |.f...f.....fh...|
00000130 00 66 50 06 53 68 01 00 68 10 00 b4 42 8a 16 0e |.fP.Sh..h...B...|
00000140 00 16 1f 8b f4 cd 13 66 59 5b 5a 66 59 66 59 1f |.......fY[ZfYfY.|
00000150 0f 82 16 00 66 ff 06 11 00 03 16 0f 00 8e c2 ff |....f...........|
00000160 0e 16 00 75 bc 07 1f 66 61 c3 a0 f8 01 e8 09 00 |...u...fa.......|
00000170 a0 fb 01 e8 03 00 f4 eb fd b4 01 8b f0 ac 3c 00 |..............<.|
00000180 74 09 b4 0e bb 07 00 cd 10 eb f2 c3 0d 0a 41 20 |t.............A |
00000190 64 69 73 6b 20 72 65 61 64 20 65 72 72 6f 72 20 |disk read error |
000001a0 6f 63 63 75 72 72 65 64 00 0d 0a 42 4f 4f 54 4d |occurred...BOOTM|
000001b0 47 52 20 69 73 20 6d 69 73 73 69 6e 67 00 0d 0a |GR is missing...|
000001c0 42 4f 4f 54 4d 47 52 20 69 73 20 63 6f 6d 70 72 |BOOTMGR is compr|
000001d0 65 73 73 65 64 00 0d 0a 50 72 65 73 73 20 43 74 |essed...Press Ct|
000001e0 72 6c 2b 41 6c 74 2b 44 65 6c 20 74 6f 20 72 65 |rl+Alt+Del to re|
000001f0 73 74 61 72 74 0d 0a 00 8c a9 be d6 00 00 55 aa |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000 eb 52 90 4e 54 46 53 20 20 20 20 00 02 08 00 00 |.R.NTFS .....|
00000010 00 00 00 00 00 f8 00 00 3f 00 ff 00 00 08 00 00 |........?.......|
00000020 00 00 00 00 80 00 80 00 ff 1f 03 00 00 00 00 00 |................|
00000030 55 21 00 00 00 00 00 00 02 00 00 00 00 00 00 00 |U!..............|
00000040 f6 00 00 00 01 00 00 00 c4 35 f3 96 6d f3 96 2c |.........5..m..,|
00000050 00 00 00 00 fa 33 c0 8e d0 bc 00 7c fb 68 c0 07 |.....3.....|.h..|
00000060 1f 1e 68 66 00 cb 88 16 0e 00 66 81 3e 03 00 4e |..hf......f.>..N|
00000070 54 46 53 75 15 b4 41 bb aa 55 cd 13 72 0c 81 fb |TFSu..A..U..r...|
00000080 55 aa 75 06 f7 c1 01 00 75 03 e9 dd 00 1e 83 ec |U.u.....u.......|
00000090 18 68 1a 00 b4 48 8a 16 0e 00 8b f4 16 1f cd 13 |.h...H..........|
000000a0 9f 83 c4 18 9e 58 1f 72 e1 3b 06 0b 00 75 db a3 |.....X.r.;...u..|
000000b0 0f 00 c1 2e 0f 00 04 1e 5a 33 db b9 00 20 2b c8 |........Z3... +.|
000000c0 66 ff 06 11 00 03 16 0f 00 8e c2 ff 06 16 00 e8 |f...............|
000000d0 4b 00 2b c8 77 ef b8 00 bb cd 1a 66 23 c0 75 2d |K.+.w......f#.u-|
000000e0 66 81 fb 54 43 50 41 75 24 81 f9 02 01 72 1e 16 |f..TCPAu$....r..|
000000f0 68 07 bb 16 68 70 0e 16 68 09 00 66 53 66 53 66 |h...hp..h..fSfSf|
00000100 55 16 16 16 68 b8 01 66 61 0e 07 cd 1a 33 c0 bf |U...h..fa....3..|
00000110 28 10 b9 d8 0f fc f3 aa e9 5f 01 90 90 66 60 1e |(........_...f`.|
00000120 06 66 a1 11 00 66 03 06 1c 00 1e 66 68 00 00 00 |.f...f.....fh...|
00000130 00 66 50 06 53 68 01 00 68 10 00 b4 42 8a 16 0e |.fP.Sh..h...B...|
00000140 00 16 1f 8b f4 cd 13 66 59 5b 5a 66 59 66 59 1f |.......fY[ZfYfY.|
00000150 0f 82 16 00 66 ff 06 11 00 03 16 0f 00 8e c2 ff |....f...........|
00000160 0e 16 00 75 bc 07 1f 66 61 c3 a0 f8 01 e8 09 00 |...u...fa.......|
00000170 a0 fb 01 e8 03 00 f4 eb fd b4 01 8b f0 ac 3c 00 |..............<.|
00000180 74 09 b4 0e bb 07 00 cd 10 eb f2 c3 0d 0a 41 20 |t.............A |
00000190 64 69 73 6b 20 72 65 61 64 20 65 72 72 6f 72 20 |disk read error |
000001a0 6f 63 63 75 72 72 65 64 00 0d 0a 42 4f 4f 54 4d |occurred...BOOTM|
000001b0 47 52 20 69 73 20 6d 69 73 73 69 6e 67 00 0d 0a |GR is missing...|
000001c0 42 4f 4f 54 4d 47 52 20 69 73 20 63 6f 6d 70 72 |BOOTMGR is compr|
000001d0 65 73 73 65 64 00 0d 0a 50 72 65 73 73 20 43 74 |essed...Press Ct|
000001e0 72 6c 2b 41 6c 74 2b 44 65 6c 20 74 6f 20 72 65 |rl+Alt+Del to re|
000001f0 73 74 61 72 74 0d 0a 00 8c a9 be d6 00 00 55 aa |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb2
00000000 eb 52 90 4e 54 46 53 20 20 20 20 00 02 08 00 00 |.R.NTFS .....|
00000010 00 00 00 00 00 f8 00 00 3f 00 ff 00 00 28 03 00 |........?....(..|
00000020 00 00 00 00 80 00 80 00 ff 37 6d 74 00 00 00 00 |.........7mt....|
00000030 00 00 0c 00 00 00 00 00 02 00 00 00 00 00 00 00 |................|
00000040 f6 00 00 00 01 00 00 00 19 2e 1c 18 64 1c 18 6e |............d..n|
00000050 00 00 00 00 fa 33 c0 8e d0 bc 00 7c fb 68 c0 07 |.....3.....|.h..|
00000060 1f 1e 68 66 00 cb 88 16 0e 00 66 81 3e 03 00 4e |..hf......f.>..N|
00000070 54 46 53 75 15 b4 41 bb aa 55 cd 13 72 0c 81 fb |TFSu..A..U..r...|
00000080 55 aa 75 06 f7 c1 01 00 75 03 e9 dd 00 1e 83 ec |U.u.....u.......|
00000090 18 68 1a 00 b4 48 8a 16 0e 00 8b f4 16 1f cd 13 |.h...H..........|
000000a0 9f 83 c4 18 9e 58 1f 72 e1 3b 06 0b 00 75 db a3 |.....X.r.;...u..|
000000b0 0f 00 c1 2e 0f 00 04 1e 5a 33 db b9 00 20 2b c8 |........Z3... +.|
000000c0 66 ff 06 11 00 03 16 0f 00 8e c2 ff 06 16 00 e8 |f...............|
000000d0 4b 00 2b c8 77 ef b8 00 bb cd 1a 66 23 c0 75 2d |K.+.w......f#.u-|
000000e0 66 81 fb 54 43 50 41 75 24 81 f9 02 01 72 1e 16 |f..TCPAu$....r..|
000000f0 68 07 bb 16 68 70 0e 16 68 09 00 66 53 66 53 66 |h...hp..h..fSfSf|
00000100 55 16 16 16 68 b8 01 66 61 0e 07 cd 1a 33 c0 bf |U...h..fa....3..|
00000110 28 10 b9 d8 0f fc f3 aa e9 5f 01 90 90 66 60 1e |(........_...f`.|
00000120 06 66 a1 11 00 66 03 06 1c 00 1e 66 68 00 00 00 |.f...f.....fh...|
00000130 00 66 50 06 53 68 01 00 68 10 00 b4 42 8a 16 0e |.fP.Sh..h...B...|
00000140 00 16 1f 8b f4 cd 13 66 59 5b 5a 66 59 66 59 1f |.......fY[ZfYfY.|
00000150 0f 82 16 00 66 ff 06 11 00 03 16 0f 00 8e c2 ff |....f...........|
00000160 0e 16 00 75 bc 07 1f 66 61 c3 a0 f8 01 e8 09 00 |...u...fa.......|
00000170 a0 fb 01 e8 03 00 f4 eb fd b4 01 8b f0 ac 3c 00 |..............<.|
00000180 74 09 b4 0e bb 07 00 cd 10 eb f2 c3 0d 0a 41 20 |t.............A |
00000190 64 69 73 6b 20 72 65 61 64 20 65 72 72 6f 72 20 |disk read error |
000001a0 6f 63 63 75 72 72 65 64 00 0d 0a 42 4f 4f 54 4d |occurred...BOOTM|
000001b0 47 52 20 69 73 20 6d 69 73 73 69 6e 67 00 0d 0a |GR is missing...|
000001c0 42 4f 4f 54 4d 47 52 20 69 73 20 63 6f 6d 70 72 |BOOTMGR is compr|
000001d0 65 73 73 65 64 00 0d 0a 50 72 65 73 73 20 43 74 |essed...Press Ct|
000001e0 72 6c 2b 41 6c 74 2b 44 65 6c 20 74 6f 20 72 65 |rl+Alt+Del to re|
000001f0 73 74 61 72 74 0d 0a 00 8c a9 be d6 00 00 55 aa |start.........U.|
00000200

=================== df -Th:

Filesystem Type Size Used Avail Use% Mounted on
/cow overlayfs 16G 7.4M 16G 1% /
udev devtmpfs 16G 12K 16G 1% /dev
tmpfs tmpfs 3.2G 1.3M 3.2G 1% /run
/dev/sdc1 vfat 15G 648M 15G 5% /cdrom
/dev/loop0 squashfs 549M 549M 0 100% /rofs
none tmpfs 4.0K 0 4.0K 0% /sys/fs/cgroup
tmpfs tmpfs 16G 8.0K 16G 1% /tmp
none tmpfs 5.0M 4.0K 5.0M 1% /run/lock
none tmpfs 16G 0 16G 0% /run/shm
none tmpfs 100M 16K 100M 1% /run/user
/dev/sda1 fuseblk 932G 116M 932G 1% /mnt/boot-sav/sda1
/dev/sdb1 fuseblk 100M 25M 76M 25% /mnt/boot-sav/sdb1
/dev/sdb2 fuseblk 932G 743G 190G 80% /mnt/boot-sav/sdb2

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4514726d

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 1953521663 976759808 7 HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf12461d9

Device Boot Start End Blocks Id System
/dev/sdb1 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sdb2 * 206848 1953521663 976657408 7 HPFS/NTFS/exFAT

Disk /dev/sdc: 16.0 GB, 16018046976 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa25e3efe

Device Boot Start End Blocks Id System
/dev/sdc1 2048 31285247 15641600 c W95 FAT32 (LBA)



=================== Recommended repair
The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sdb2.
Additional repair will be performed: unhide-bootmenu-10s fix-windows-boot


Quantity of real Windows: 1
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer.
-

[/TD]
[/TR]
[/TABLE]
-
[Download as text]("http://paste.ubuntu.com/23792959/plain/")
```

---

### Post by howefield on 2017-01-13
Thread closed.

---

