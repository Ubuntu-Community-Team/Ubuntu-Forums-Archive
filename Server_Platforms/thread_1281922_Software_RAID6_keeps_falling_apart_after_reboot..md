---
title: "Software RAID6 keeps falling apart after reboot."
date: 2009-10-03
forum: Server Platforms
---

### Post by laluz on 2009-10-03
A few weeks ago I have created a RAID6 array from five 1,5TB disks, 3 Samsung and 2 WD. Kubuntu 8.10 Intrepid. 

The array has fallen apart three times already after a reboot.

What might be a reason for this and what can be done to stop this?

I am happy to do additional research, but just not sure which direction to look.

This is what I saw in the log last time it failed:
```
Oct  1 19:47:25 Kubuntu kernel: [  614.997612] sd 8:0:0:0: Attached scsi generic sg6 type 0
Oct  1 19:47:45 Kubuntu kernel: [  634.843776] eth0: link down.
Oct  1 19:47:49 Kubuntu kernel: [  638.991344] eth0: link up.
Oct  1 19:57:50 Kubuntu -- MARK --
Oct  1 20:17:50 Kubuntu -- MARK --
Oct  1 20:26:38 Kubuntu kernel: [ 2968.256734] md: md0 stopped.
Oct  1 20:26:38 Kubuntu kernel: [ 2968.256756] md: unbind<sdd1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.260096] md: export_rdev(sdd1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.260135] md: unbind<sde1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.264020] md: export_rdev(sde1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.264047] md: unbind<sdc1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.268020] md: export_rdev(sdc1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.268052] md: unbind<sdb1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.275671] md: export_rdev(sdb1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.275699] md: unbind<sda1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.280018] md: export_rdev(sda1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.287565] md: bind<sdb1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.287689] md: bind<sdc1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.287813] md: bind<sdd1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.287940] md: bind<sde1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.288070] md: bind<sda1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.288098] md: kicking non-fresh sdc1 from array!
Oct  1 20:26:38 Kubuntu kernel: [ 2968.288104] md: unbind<sdc1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.296196] md: export_rdev(sdc1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.296201] md: kicking non-fresh sdb1 from array!
Oct  1 20:26:38 Kubuntu kernel: [ 2968.296205] md: unbind<sdb1>
Oct  1 20:26:38 Kubuntu kernel: [ 2968.301826] md: export_rdev(sdb1)
Oct  1 20:26:38 Kubuntu kernel: [ 2968.369725] raid5: device sda1 operational as raid disk 0
Oct  1 20:26:38 Kubuntu kernel: [ 2968.369730] raid5: device sde1 operational as raid disk 4
Oct  1 20:26:38 Kubuntu kernel: [ 2968.369733] raid5: device sdd1 operational as raid disk 3
Oct  1 20:26:38 Kubuntu kernel: [ 2968.370562] raid5: allocated 5268kB for md0
Oct  1 20:26:38 Kubuntu kernel: [ 2968.370570] RAID5 conf printout:
Oct  1 20:26:38 Kubuntu kernel: [ 2968.370571]  --- rd:5 wd:3
Oct  1 20:26:38 Kubuntu kernel: [ 2968.370573]  disk 0, o:1, dev:sda1
Oct  1 20:26:38 Kubuntu kernel: [ 2968.370575]  disk 3, o:1, dev:sdd1
Oct  1 20:26:38 Kubuntu kernel: [ 2968.370576]  disk 4, o:1, dev:sde1
Oct  1 20:37:50 Kubuntu -- MARK --
Oct  1 20:57:50 Kubuntu -- MARK --
Oct  1 21:17:50 Kubuntu -- MARK --
Oct  1 21:24:11 Kubuntu kernel: [ 6421.039745] usb 2-8.5: USB disconnect, address 6
Oct  1 21:37:50 Kubuntu -- MARK --
Oct  1 21:57:50 Kubuntu -- MARK --
Oct  1 22:17:50 Kubuntu -- MARK --
Oct  1 22:37:50 Kubuntu -- MARK --
Oct  1 22:46:26 Kubuntu kernel: [11356.449145] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
Oct  1 22:57:50 Kubuntu -- MARK --
Oct  1 23:17:50 Kubuntu -- MARK --
Oct  1 23:37:50 Kubuntu -- MARK --
Oct  1 23:57:50 Kubuntu -- MARK --
Oct  2 00:17:50 Kubuntu -- MARK --
Oct  2 00:37:50 Kubuntu -- MARK --
Oct  2 00:57:50 Kubuntu -- MARK --
Oct  2 01:17:50 Kubuntu -- MARK --
Oct  2 01:37:50 Kubuntu -- MARK --
Oct  2 01:57:50 Kubuntu -- MARK --
Oct  2 02:17:50 Kubuntu -- MARK --
Oct  2 02:37:50 Kubuntu -- MARK --
Oct  2 02:57:50 Kubuntu -- MARK --
Oct  2 03:07:26 Kubuntu kernel: llllled
Oct  2 03:07:26 Kubuntu kernel: lllled
Oct  2 03:07:26 Kubuntu kernel: llll) failed
Oct  2 03:07:26 Kubuntu kernel: ) failed
Oct  2 03:07:26 Kubuntu kernel: ) faile))))))))  1948) fa        1940) fai        1948) f
 1block 194bbbbbbbblock 1949bbbbbbbblock 19bbbbbbbblread(blocrrrrrrrread(blockrrrrrrrread(blorrrrrrrrory bread(oooooooory bread(oooooooory breaoooooooorirectory iiiiiiiirectory biiiiiiiirectoryiiiiiiiirAT: DirecAAAAAAAAT: DirectorAAAAAAAAT: DirecAAAAAAAA51] FAT: D566778836] FAT: D445566714] FAT:12234459.897104] F........897182] F........897267]........827015.897222222227015.8974222222227015.89222222227
Oct  2 03:07:26 Kubuntu kernel:
Oct  2 03:07:26 Kubuntu last message repeated 4 times
Oct  2 03:07:26 Kubuntu kernel: ailed
Oct  2 03:07:26 Kubuntu kernel: ailaaaaaaaailed
Oct  2 03:07:26 Kubuntu kernel: aa50) failed555334442) faile444444450) fail555334442ck 1943) cccccccck 1951) cccccccck 1943)cccccccckd(block 1dddddddd(block 1dddddddd(block 1dddddddd bread(blo        bread(bl        bread(bl        ctory brecccccccctory breacccccccctory brcccccccc Directory        Director        Director         FAT: Dire       FAT: Dire        FAT: Di        9875] FAT:99999999952] FAT99990000056] FAT0000000015.900139111111115.900225]111111115.9003011111111>[27015.90>>>>>>>>[27015.9>>>>>>>>[27015.9>>>>>>>>ed
Oct  2 03:07:26 Kubuntu kernel: eeeeeeeed
Oct  2 03:07:26 Kubuntu kernel: eeeeeed
Oct  2 03:07:26 Kubuntu kernel: eeeee failed
Oct  2 03:07:26 Kubuntu kernel:   failed
Oct  2 03:07:26 Kubuntu kernel:  failed
Oct  2 03:07:26 Kubuntu kernel: 1945) fail1111111953) fail11111111945) fa11111111lock 1938)llllllllock 1946llllllllock 1938llllllead(block eeeeeeead(block eeeeeeeead(bloceeeeeeeery bread(brrrrrrrry bread(rrrrrrrry breadrrrrrrrrrectory brrrrrrrrrectory brrrrrrrrectory rrrrrrrrT: DirectoTTTTTTTT: DirectTTTTTTTT: DirecTTTTTTTT5] FAT: Di05727272] FAT: D83272727] FAT: 27949494902909] FA9999999902995] F9999999903072] 999999997015.9031677777777015.903277777777015.90337777777<3>[27015.<<<<<<<<3>[27015<<<<<<<<3>[27015<<<<<<<<iled
Oct  2 03:07:26 Kubuntu kernel: iiiled
Oct  2 03:07:26 Kubuntu kernel: iiiiled
Oct  2 03:07:26 Kubuntu kernel: iii7) failed
Oct  2 03:07:26 Kubuntu kernel: 9) failed
Oct  2 03:07:26 Kubuntu kernel: 7) failed89012389k 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) kkkkkkkk 1948) failkkkkkkkk 1940) fkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) kkkkkkkk 1948) fakkkkkkkk 1940) kkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) kkkkkkkk 1940) kkkkkkkk 1948) fakkkkkkkk 1940) kkkkkkkk 1948) fakkkkkkkk 1940) kk kkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948)fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) faikkkkkkkk 1940) kkkkkkkk 1948) faikkkkkkkk 1940) kkkkkkkk 1948) faikkkkkkkk 1940) fkkkkkkkk 1948) failkkkkkkkk 1940) fkkkkkkkk 1948) faikkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940
Oct  2 03:07:26 Kubuntu kernel: kk kkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fkkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) faikkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948)kkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkk 1kkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940)kkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) fakkkkk
Oct  2 03:07:26 Kubuntu kernel: 1kkkk 1948) fakkkkkkkk 1940) fkkkkkkkk 1948) faikkkkkkkk 1948) fkkkkkc67) failed
Oct  2 03:07:26 Kubuntu kernel: 7) fail89012367) failed
Oct  2 03:07:26 Kubuntu kernel: iled
Oct  2 03:07:26 Kubuntu kernel: iiled
Oct  2 03:07:26 Kubuntu kernel: iiiiiled
Oct  2 03:07:26 Kubuntu kernel: ii<3>[27015.<<<<<<<<3>[27015<<<<<<<<3>[27015.<<<<<<<<3>[2701577777777015.9156077777777015.915677777777015.915767999999915855] F9999999915939] FAT9999999916081]F99494950] FAT: Di50740627] FAT: D38061616] FAT: Di162TTTTT: DirectTTTTTTTT: DirectorTTTTTTTT: DirectoTTTTrrrrectory brerrrrrrrrectory brrrrrrrrectory brrrrrTrrry bread(rrrrrrrry bread(brrrrrrrry bread(rrrrrdeead(block eeeeeeeead(b1953) fa11111111953) faile11111111953) fain       failed
Oct  2 03:07:26 Kubuntu kernel:  fai        failed
Oct  2 03:07:26 Kubuntu kernel: eed
Oct  2 03:07:26 Kubuntu kernel: eeeeed
Oct  2 03:07:26 Kubuntu kernel: eeeeeeed
Oct  2 03:07:26 Kubuntu kernel: >>>>>[27015.91>>>>>>>>[27015.9>>>>>>>>[27015.91>>>111115.918696111111115.918779] 111111115.91885611118888944] FAT:88889999027] FAT99999999105] FAT:99999   FAT:Dir        FAT: Dire        FAT: Dir        Directory        Director        Directory       ctory brecccccccctory breacccccccctory brecccccccread failed       bread(bl        bread(blo bread(blfddddddd(block 19dddddddd(block 1dddddddd(block 19ddcccck cck 1951) cccccccck 1951) fcccccccck 1951) cco444450) failed555447) 4450) faile555444450) failed
Oct  2 03:07:26 Kubuntu kernel: ailed
Oct  2 03:07:26 Kubuntu kernel: ailed
Oct  2 03:07:26 Kubuntu kernel: aaaaailed
Oct  2 03:07:26 Kubuntu kernel:
Oct  2 03:07:26 Kubuntu last message repeated 2 times
Oct  2 03:07:26 Kubuntu kernel: <
Oct  2 03:07:26 Kubuntu kernel:
Oct  2 03:07:26 Kubuntu kernel: 227015.921222222227015.9215222222227015.921222222..921758] F........921840] ........921920] F.......09] FAT: 112233492] FAT: D901122373] FAT: 788990015] FAT: FAAAAAAAAT: DirecAAAAAAAAT: DirectAAAAAAAAT: DirecAiiiiiiirectory biiiiiiiirectory iiiiiiiirectory briAoooooory breaoooooooory bread(oooooooory breadooarrrrread(blockrrrrrrrread(blocrrrrrrrread(blockrrribbbblock 194bbbbbbbblock 1949bbbbbbbblock 194bbbb(   1948) fai        1948) fa        1948) fai     k)) failed
Oct  2 03:07:26 Kubuntu kernel: ) fai)))))))) failed
Oct  2 03:07:26 Kubuntu kernel: led
Oct  2 03:07:26 Kubuntu kernel: lllled
Oct  2 03:07:26 Kubuntu kernel: lllled
Oct  2 03:07:26 Kubuntu kernel: <lllllll3>[2701533333333>[27015.924333333333>[27015.33333333>[27015.90000000015.924580000000015.9246700000000015.92474022222224832] FAT222222224919] FA222222224996] FAT22]]]]]] FAT: D]]]]]]]] FAT: Dir]]]]]]]] FAT: Di]]]::::: Direct:::::::: Directo::::::::Director::::eeeectory breeeeeeeectory breeeeeeeeectory breeee yyy bread(blyyyyyyyy bread(yyyyyyyy bread(blyyyyy aad(block aaaaaaaad(block 1aaaaaaaad(block aaaaaaeock 1946) oooooooock 1946)oooooooock 1946) ooooooolocknr 939999999953) faile9999999953) fai9999999953) failerfffffffailed
Oct  2 03:07:26 Kubuntu kernel: failed
Oct  2 03:07:26 Kubuntu kernel: failed
Oct  2 03:07:26 Kubuntu kernel: ddd
Oct  2 03:07:26 Kubuntu kernel: ddddd
Oct  2 03:07:26 Kubuntu kernel: dddddd
Oct  2 03:07:26 Kubuntu kernel: dd[[[[[[27015.9[[[[[[[[27015.927[[[[[[[[27015.92[[[55555.927637] 55555555.927724]55555555.927802] 55555555.927886]55555555.927963] 55555555.928067]55555555.928145] 55555555.928232]55555555.928310] FAT: Direct55555555.928394]55555555.928474] 55555555.928558]55555555.928635] 55555555.928720]55555555.928799] 55555555.928885]55555555.928963] 55555555.929047]55555555.929124] 55555555.929208]555555.929287] 55555555.929371]55555555.[27015.92[[[[[[[[27015.929[[[[[[[[27015.92[[[[[[[[d
Oct  2 03:07:26 Kubuntu kernel: ddddddd
Oct  2 03:07:26 Kubuntu kernel: ddddddd
Oct  2 03:07:26 Kubuntu kernel: <ddddddddfailed
Oct  2 03:07:26 Kubuntu kernel: failed
Oct  2 03:07:26 Kubuntu kernel: ffailed
Oct  2 03:07:26 Kubuntu kernel: f953) faile9999999945) faile9999999953) fail99999999ock 1946) oooooooock 1938) oooooooock 1946)ooooooooad(block 1aaaaaaaad(block 1aaaaaaaad(block aaaaaaaay bread(blyyyyyyyy bread(blyyyyyyyy bread(byyyyyyyyectory breeeeeeeeectory breeeeeeeeectory breeeeeeee: Director:::::::: Director:::::::: Directo::::::::] FAT: Dir]]]]]]]] FAT: Dir]]]]]]]] FAT: Di]]]]]]]]32071] FAT333333332150] FAT333333332235] FA33333333015.932318] 0000000015.9324030000000015.932480000000013>[27015.33333333>[27015.933333333>[27015.33333333led
Oct  2 03:07:26 Kubuntu kernel: lllled
Oct  2 03:07:26 Kubuntu kernel: llled
Oct  2 03:07:26 Kubuntu kernel: lllle) failed
Oct  2 03:07:26 Kubuntu kernel: ) failed
Oct  2 03:07:26 Kubuntu kernel: ) fa))))        1940) fai        1948) fa        1block 1941bbbbbbblock 1949bbbbbbbblock 194bbbbbbbblread(blockrrrrrrrread(blockrrrrrrrread(blocrrrrrrrreory bread(oooooooory bread(oooooooory breadoooooooorirectory biiiiiiiirectory biiiiiiiirectory iiiiiiiirAT: DirectAAAAAAAAT: DirectAAAAAAAAT: DirecAAAAAAAAT54] FAT: D566778838] FAT: D455667824] FAT:233445508.935215] F.......935299] F........935386] ........927015.9354222222227015.9355222222227015.935222222227
Oct  2 03:07:26 Kubuntu kernel:
Oct  2 03:07:26 Kubuntu last message repeated 3 times
Oct  2 03:07:26 Kubuntu kernel: <
Oct  2 03:07:26 Kubuntu kernel: ailed
Oct  2 03:07:26 Kubuntu kernel: ailed
Oct  2 03:07:26 Kubuntu kernel: aaaailed
Oct  2 03:07:26 Kubuntu kernel: 50) failed555334442) failed
Oct  2 03:07:26 Kubuntu kernel: 444444450) faile555334442ck 1943) fccccccck 1951) fcccccccck 1943) cccccccckd(block 1dddddddd(block 19dddddddd(block 1dddddddd( bread(blo        bread(blo  bread(bl        cccccctory breacccccccctory brecccccccc Directory        Directory        Director        D FAT: Dir        FAT: Dire        FAT: Dir        F8112] FAT88888888190] FAT:88888888273] FAT88888888315.938356111111115.938441]111111115.938518111111115>[27015.9>>>>>>>>[27015.93>>>>>>>>[27015.9>>>>>>>>[ed
Oct  2 03:07:26 Kubuntu kernel: eeeeed
Oct  2 03:07:26 Kubuntu kernel: eeeeeed
Oct  2 03:07:26 Kubuntu kernel: eeeeed failed
Oct  2 03:07:26 Kubuntu kernel:  failed
Oct  2 03:07:26 Kubuntu kernel:   failed
Oct  2 03:07:26 Kubuntu kernel: 1945) fail11111111953) fail11111111945) fai111111119lock 1938llllllllock 1946)llllllllock 1938lllllllloead(blockeeeeeeeead(block eeeeeeeead(blockeeeeeeeery bread(brrrrrrrry bread(brry rrrrrry bread(rrrrrrrryrectory brrrrrrrrrectory brrrrrrrrrectory brrrrrrrreT: DirectTTTTTTTT: DirectoTTTTTTTT: DirectTTTTTTTT:3] FAT: D83505050] FAT: Di49838383] FAT: D83505050]941215] F99999941303] FA9999999941389] F9999999947015.941477777777015.9415577777777015.9416777777770<3>[27015<<<<<<<<3>[27015.<<<<<<<<3>[27015<<<<<<<<3iled
Oct  2 03:07:26 Kubuntu kernel: iled
Oct  2 03:07:26 Kubuntu kernel: iiiiled
Oct  2 03:07:26 Kubuntu kernel: iii7) failed
Oct  2 03:07:26 Kubuntu kernel: 9) failed01234567) failed89012389k 1940) fakkkkkkkk 1948) failed
Oct  2 03:07:26 Kubuntu kernel: k 1940) fkkkkkkkk 1948) kkkkkkkk (block 19((((((((block 1949) failed
Oct  2 03:07:50 Kubuntu kernel: [27040.713043] eth0: link down.
Oct  2 03:08:06 Kubuntu kernel: [27055.767329] nfsd: last server has exited, flushing export cache
Oct  2 03:08:07 Kubuntu exiting on signal 15
Oct  2 19:10:00 Kubuntu syslogd 1.5.0#2ubuntu6: restart.
Oct  2 19:10:00 Kubuntu kernel: Inspecting /boot/System.map-2.6.27-11-generic
Oct  2 19:10:00 Kubuntu kernel: Cannot find map file.
Oct  2 19:10:00 Kubuntu kernel: Loaded 69732 symbols from 93 modules.
Oct  2 19:10:00 Kubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  2 19:10:00 Kubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  2 19:10:00 Kubuntu kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)


```
It seems at 20:26:38 1st of October the array has stopped and two disks were kicked out. But then the same night at 03:07:26 2nd of October I have asked the machine to shutdown (via KDE4 shutdown applet). And then the kernel started printing out garbage. After a boot at the same day 19:10:00 the array was no longer assembling
```
Oct  2 19:10:00 Kubuntu kernel: [    9.653312] md: md0 stopped.
Oct  2 19:10:00 Kubuntu kernel: [    9.848859] md: bind<sdb1>
Oct  2 19:10:00 Kubuntu kernel: [    9.848992] md: bind<sdc1>
Oct  2 19:10:00 Kubuntu kernel: [    9.849127] md: bind<sda1>
Oct  2 19:10:00 Kubuntu kernel: [    9.869685] md: md0 stopped.
Oct  2 19:10:00 Kubuntu kernel: [    9.869697] md: unbind<sda1>
Oct  2 19:10:00 Kubuntu kernel: [    9.876159] md: export_rdev(sda1)
Oct  2 19:10:00 Kubuntu kernel: [    9.876175] md: unbind<sdc1>
Oct  2 19:10:00 Kubuntu kernel: [    9.880017] md: export_rdev(sdc1)
Oct  2 19:10:00 Kubuntu kernel: [    9.880022] md: unbind<sdb1>
Oct  2 19:10:00 Kubuntu kernel: [    9.884016] md: export_rdev(sdb1)
Oct  2 19:10:00 Kubuntu kernel: [    9.899350] md: bind<sdb1>
Oct  2 19:10:00 Kubuntu kernel: [    9.899478] md: bind<sdc1>
Oct  2 19:10:00 Kubuntu kernel: [    9.899599] md: bind<sdd1>
Oct  2 19:10:00 Kubuntu kernel: [    9.899721] md: bind<sde1>
Oct  2 19:10:00 Kubuntu kernel: [    9.899842] md: bind<sda1>
Oct  2 19:10:00 Kubuntu kernel: [    9.899867] md: kicking non-fresh sdc1 from array!
Oct  2 19:10:00 Kubuntu kernel: [    9.899871] md: unbind<sdc1>
Oct  2 19:10:00 Kubuntu kernel: [    9.905039] md: export_rdev(sdc1)
Oct  2 19:10:00 Kubuntu kernel: [    9.905042] md: kicking non-fresh sdb1 from array!
Oct  2 19:10:00 Kubuntu kernel: [    9.905045] md: unbind<sdb1>
Oct  2 19:10:00 Kubuntu kernel: [    9.909014] md: export_rdev(sdb1)
Oct  2 19:10:00 Kubuntu kernel: [    9.917239] raid5: device sda1 operational as raid disk 0
Oct  2 19:10:00 Kubuntu kernel: [    9.917241] raid5: device sde1 operational as raid disk 4
Oct  2 19:10:00 Kubuntu kernel: [    9.917243] raid5: device sdd1 operational as raid disk 3
Oct  2 19:10:00 Kubuntu kernel: [    9.917658] raid5: allocated 5268kB for md0
Oct  2 19:10:00 Kubuntu kernel: [    9.917663] RAID5 conf printout:
Oct  2 19:10:00 Kubuntu kernel: [    9.917665]  --- rd:5 wd:3
Oct  2 19:10:00 Kubuntu kernel: [    9.917666]  disk 0, o:1, dev:sda1
Oct  2 19:10:00 Kubuntu kernel: [    9.917668]  disk 3, o:1, dev:sdd1
Oct  2 19:10:00 Kubuntu kernel: [    9.917669]  disk 4, o:1, dev:sde1
Oct  2 19:10:00 Kubuntu kernel: [   19.490819] PM: Starting manual resume from disk
Oct  2 19:10:00 Kubuntu kernel: [   19.521336] kjournald starting.  Commit interval 5 seconds
Oct  2 19:10:00 Kubuntu kernel: [   19.521347] EXT3-fs: mounted filesystem with ordered data mode.
Oct  2 19:10:00 Kubuntu kernel: [   28.026922] udevd version 124 started

```
I am not sure if this garbage from kernel is an indication of the bug in the kernel that could cause the array to fall apart? Or was it some other root cause that damaged the array and the kernel?


After forced assembling the array comes back again clean with 3 disks and 2 spares that sync for 5 hours each. 
```
sudo mdadm --assemble --force /dev/md0 --uuid=47656f5c:e2ba2593:f8416ba2:468310b2 /dev/sd{a,b,c,d,e}1
sudo fsck.jfs -v /dev/md0

```
To force assemble I hand to download and install fresh mdadm version from sources. The first time the array had fallen apart with the stock mdadm packaged from Ubuntu. This Ubuntu version had a known bug preventing the force assemble.
So far I have not noticed any data damage.

I believe different drives got kicked out of array at these three fails I have seen.
```

gunzip -c messages.*.gz | grep kick
Sep 16 00:53:20 Kubuntu kernel: [ 1346.380111] md: kicking non-fresh sde1 from array!
Sep 16 00:53:20 Kubuntu kernel: [ 1346.381039] md: kicking non-fresh sdd1 from array!
Sep 16 00:53:20 Kubuntu kernel: [ 1346.382231] md: kicking non-fresh sdc1 from array!
Sep 16 08:46:57 Kubuntu kernel: [ 5534.826010] md: kicking non-fresh sdd1 from array!
Sep 16 08:46:57 Kubuntu kernel: [ 5534.826943] md: kicking non-fresh sdc1 from array!

Sep 13 18:49:31 Kubuntu kernel: [   17.837568] md: kicking non-fresh sdb1 from array!

```

```

$uname -a
Linux Kubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

```

---

### Post by Vegan on 2009-10-03
Get a real RAID 6 card, but I have not seen Linux drivers handy for some.

Software RAID is problematic as all hell.

---

### Post by fjgaude on 2009-10-04
I've been using a four-drive raid5 array under **mdadm** for years without any issues. I agree you have to know what you are doing, when and why, to not get in trouble with software raid. OTOH it is fast, costs no money, and reliable, unless some command is entered that messes things up... I've never lost data even when experimenting, always able to re-assemble the array.

Is your array raid5 or raid6?

---

### Post by laluz on 2009-10-04
My array is RAID6. And it seems something goes wrong on software or hardware side. I do not believe I could mess things up while setting up the array. Apart from having this problem now and then it works fine. 

Do you think mdadm stability could vary depending on the RAID type?

---

### Post by laluz on 2009-10-04
update. I have checked the disks SMART status and there are no errors on disks in the array. There are errors on my other hdd that the Ubuntu is installed on. But these errors seems to have happened way before I have set up the array.

---

### Post by fjgaude on 2009-10-04
Well, as you likely know raid6 is a late comer to the party... I've never used it and can't say if it is less reliable compared to raid5... but **mdadm** is solid, and over the years has just about got all the bugs out of it.

---

### Post by laluz on 2009-10-04
> **fjgaude said:**
>  but **mdadm** is solid, and over the years has just about got all the bugs out of it.
FYI The version in the Intrepid still has a known bug. ( --assemble --force does not work)

---

### Post by fjgaude on 2009-10-04
Well, I'm not sure that is a bug... something to do with arrays being stopped during creation... yes, a later version fixes this but I've never had the occation to need it. I don't know why Ubuntu team hasn't seen fit to use the latest version of **mdadm**... something is there though.

---

### Post by laluz on 2009-10-04
This is what the bug was [http://marc.info/?l=linux-raid&m=121381784820652&w=2](http://marc.info/?l=linux-raid&m=121381784820652&w=2)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499643](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499643)

---

### Post by fjgaude on 2009-10-04
Okay, and thanks... I'm still using version 2.6.7.1... I have 2.6.8 but haven't had the motivation to install it... I believe 2.6.9 is out... I don't know the down side of the newer versions, but I do believe there is a reason why Ubuntu hasn't made them available in the distros.

---

### Post by brettg on 2009-10-04
If this is a production server in a commercial environment then get a linux compatible RAID adapter from 3Ware or Adaptec. Warning, these are NOT cheap.

If this is a home server and money is a concern then take a look [here]("http://tuxnetworks.blogspot.com/search?q=raid")

---

### Post by laluz on 2009-10-05
In case anybody involved with RAID in Ubuntu reads this topic I would like to have your opinion on my problem. I would like to know whether this might be related to Ubuntu specifics or it is proper to go to mdadm author? 
Until now I have received a general advice along the line "drop the mdadm and get a hardware card". At the same time people say mdadm is rock solid. This is a bit confusing.

---

### Post by brettg on 2009-10-05
The trouble with all software raid is that it relies on the OS to be working properly. If the OS has a problem you have to rebuild your array, which can be troublesome. One tiny error and your entire logical drive is borked.

Hardware raid works, unsurprisingly, at the hardware level. Once you have built the array it is assembled by the raid adapters firmware before the OS starts and is presented to the OS as if it were a single physical drive and it can be treated as such from there on in.

El cheapo Windows softraid adapters are the equivalent to those crappy WinModems from a few years ago. They pretend to be hardware raid and indeed they do allow you to "define" the array details in the firmware but the raid array is not actually assembled until the OS loads and the raid adapter's (Windows) drivers are invoked. They are in effect a software raid implemented in the adapters driver software that pulls its configs out of the firmware.

Some manufacturers make softraid adapters that allegedly have linux drivers but in practice these drivers are closed source and are *very* badly written. I currently run a Promise softraid card but it is just configured as a simple sata adapter and the raid is done using mdadm.

So, while there is nothing actually wrong with mdadm, it is nevertheless a software raid solution which suffers from the same inherent problems as all software raid solutions.

In a commercial environment where reliability and performance are required then you should always use hardware raid. Software raid is OK for situations where a potential array failure is not considered to be a catastrophic event. 

HTH

---

### Post by laluz on 2009-10-05
> **brettg said:**
> The trouble with all software raid is that it relies on the OS to be working properly. If the OS has a problem you have to rebuild your array, which can be troublesome. One tiny error and your entire logical drive is borked.
 Software raid is OK for situations where a potential array failure is not considered to be a catastrophic event. 


Hi brettg,

my environment is a home server. And I am doing backups. So what I need is just that the raid does not fall apart every week.
Now I have posted the logs. Can you say anything as to where the problem may lay? 
I do not want to buy a hardware raid card, because in case it goes broken, it is not 100% sure that the new one will hook up the old array either. And it costs as much as the raid itself. And I have cheap time (my own) to figure out what goes wrong with my mdadm. It's only I am not getting any further with the root cause analysis.

---

### Post by brettg on 2009-10-05
When you do;
```
ls -al /dev/md*
```

does it list one of your devices as being /dev/md_d0 ?

I ask this because the same thing happens to me every time I rebuild a machine with a raid array on it.

Every time I reboot I would have to manually rebuild the array because the OS would build it incorrectly itself. 

I wrote instructions to myself on my blog for when I have to fix it (see the link I posted)

---

### Post by Xianath on 2009-10-06
You're not using EcoGreen/GreenPower disks, are you? These disks (especially the Samsung EG) take forever to spin up after an idle period, and might appear as being down to the RAID controller, including mdadm. Make sure you disable all disk powersaving, including SATA link powersaving and the drive's own APM.

Does your array has an internal bitmap? If not, you should add one with mdadm -G ... -b internal.  You may also want to check whether /etc/mdadm/mdadm.conf reflects the true nature of your array. If it does not, update it with mdadm --examine --scan. Also, sudo update-initramfs -u to make sure it's used at boot time. I had this problem while live-migrating my system from one array to another.

The kernel 'garbage' you've posted is very worrying. I'd try seeking help in LKML (and risk being RTFM'ed or worse :) ). If you have a different box or at least another motherboard, try plugging the drives there and see if it works. You may also try a newer kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), or just upgrade to a newer version of Ubuntu if you aren't running the latest. This being a home box and not a production server, your change control should be much more lenient :)

HTH,
Peter

---

### Post by laluz on 2009-10-06
> **Xianath said:**
> 
You're not using EcoGreen/GreenPower disks, are you?
 
Does your array has an internal bitmap? 

The kernel 'garbage' you've posted is very worrying. 
HTH,
Peter
Peter, great advice! This is exactly type of input I am seeking. I believe my disks are indeed Green, this might really explain my troubles. 
Let me check out the issues along your post and I will report my experience then.

---

### Post by laluz on 2009-10-11
[http://linux-raid.osdl.org/index.php/Bitmap](http://linux-raid.osdl.org/index.php/Bitmap)

---

### Post by fjgaude on 2009-10-11
Well, anything to report as to your progress? Thanks!

---

### Post by CharlesA on 2009-10-11
> **brettg said:**
> If this is a production server in a commercial environment then get a linux compatible RAID adapter from 3Ware or Adaptec. Warning, these are NOT cheap.

If this is a home server and money is a concern then take a look [here]("http://tuxnetworks.blogspot.com/search?q=raid")

Second this. I've got a RAID-5 array running on my home media server. I ended up using a Highpoint Technologies RocketRAID 2640x1 to run it. Granted, it cannot do RAID6, it's a fairly decent card that isn't as expensive as some of the 3WARE or Adeptec cards.

---

### Post by laluz on 2009-10-12
> **fjgaude said:**
> Well, anything to report as to your progress? Thanks!

Until now I only have a better understanding of a problem :-)
Yesterday out of sloppiness I have struck the PC case and imeddiately the ATA bus driver (or whichever it was) started reporting problems. Following that RAID kicked all but one drive out. 
After forced reassembling all was OK again. 
I have also just installed an UPS to sort out the power fail factor. BTW a 650Wt case with Athlon 2.6GHz and six HDD consumes only up to 120Wt, 70Wt idle. 
Following the advice I have also added an internal bitmap. Will see what difference it makes.
Next step - deaktivating power safe features of the drives and installing a different kernel.

---

### Post by fjgaude on 2009-10-12
Thanks for the update report... interesting... each of us learn day-by-day, eh?

---

### Post by laluz on 2009-10-13
[http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php)

---

### Post by laluz on 2009-10-13
> **laluz said:**
>  BTW a 650Wt case with Athlon 2.6GHz and six HDD consumes only up to 120Wt, 70Wt idle. 

with 7 HDDs and a samsung syncmaster 305T 30" monitor 110Wt idle, 130 typical web-browsing, 240 peak. 30 minutes reported runtime on APC Back-UPS RS 1200 fresh battery.
I was looking for this type of information and could not find it. So I think this would be of use for others.

---

### Post by laluz on 2009-10-22
tick.
Since I have installed an UPS (so no manual shutdowns in fear of powerloss) and restrained from hitting the case with my mighty feet, the array just keeps running.

---

### Post by fjgaude on 2009-10-22
Wonderful... things get better the more we learn how things work. <smile>

---

### Post by sloggerkhan on 2009-10-22
> **laluz said:**
> In case anybody involved with RAID in Ubuntu reads this topic I would like to have your opinion on my problem. I would like to know whether this might be related to Ubuntu specifics or it is proper to go to mdadm author? 
Until now I have received a general advice along the line "drop the mdadm and get a hardware card". At the same time people say mdadm is rock solid. This is a bit confusing.

People who spend hundreds or thousands of dollars on fancy raid cards need to feel good about their wasted cash, so they try to convince everyone there's a real significant advantage to proprietary hardware raid and that the hardware raid they could have used for free sucks.

However, the truth is that hardware raid only makes sense for certain non-consumer applications.

---

### Post by laluz on 2009-11-23
So a month is gone and I have no problem with the array anymore. I have seen two power mains failure, a crash of my box due to a software problem and some manual reboots in this time. No problem what so ever with the array, even when another singular disc with the same jfs needed an fsck.
Thanks all and especially Peter aka Xianath!

---

