---
title: "WD Raptor horror story"
date: 2011-06-07
forum: Server Platforms
---

### Post by TheR on 2011-06-07
Ubuntu 10.04:

It looks I just don't have luck with WD Raptors, model WDC WD3000BLFS-0.

I am running iSCSI storage server with 4 of them in Linux RAID10 on LSI on board controller and 4 of them in HW LSI raid controller. I had already upgraded firmware because of the problem with LSI raid controller described here [http://forums.storagereview.com/index.php/topic/27303-velociraptor-premature-failure-rate-bad-drives-premature-to-market/page__st__50](http://forums.storagereview.com/index.php/topic/27303-velociraptor-premature-failure-rate-bad-drives-premature-to-market/page__st__50)

Then there is this problem [https://bugzilla.redhat.com/show_bug.cgi?id=512613](https://bugzilla.redhat.com/show_bug.cgi?id=512613) which is alive on 10.04 (althow I did't have the guts to try it for a year now).

Now after more than 200 days uptime, last night software raid failed on me. 

<Log>
Jun  6 20:24:54 ozssan kernel: [2279698.613730] mptbase: ioc0: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00)
Jun  6 20:24:54 ozssan kernel: [2279698.613918] mptbase: ioc0: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00)
Jun  6 20:24:54 ozssan kernel: [2279698.628061] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.628069] sd 8:0:6:0: [sdd] Unhandled error code
Jun  6 20:24:54 ozssan kernel: [2279698.628072] sd 8:0:6:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  6 20:24:54 ozssan kernel: [2279698.628076] sd 8:0:6:0: [sdd] CDB: Read(10): 28 00 18 ad 55 bf 00 00 08 00
Jun  6 20:24:54 ozssan kernel: [2279698.628085] end_request: I/O error, dev sdd, sector 414012863
Jun  6 20:24:54 ozssan kernel: [2279698.636488] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636493] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636498] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636502] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636507] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636511] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636516] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636520] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636525] mptbase: ioc0: LogInfo(0x30050000): Originator={IOP}, Code={Task Terminated}, SubCode(0x0000)
Jun  6 20:24:54 ozssan kernel: [2279698.636532] raid10: sdd1: rescheduling sector 828025600
Jun  6 20:24:54 ozssan kernel: [2279698.644896] sd 8:0:6:0: [sdd] Unhandled error code
Jun  6 20:24:54 ozssan kernel: [2279698.644898] sd 8:0:6:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  6 20:24:54 ozssan kernel: [2279698.644902] sd 8:0:6:0: [sdd] CDB: Read(10): 28 00 1c 9b 48 0f 00 00 30 00
Jun  6 20:24:54 ozssan kernel: [2279698.644910] end_request: I/O error, dev sdd, sector 479938575
Jun  6 20:24:54 ozssan kernel: [2279698.653200] raid10: sdd1: rescheduling sector 959876944
Jun  6 20:24:54 ozssan kernel: [2279698.661417] raid10: sdd1: rescheduling sector 959876952
Jun  6 20:24:54 ozssan kernel: [2279698.669461] raid10: sdd1: rescheduling sector 959876960
Jun  6 20:24:54 ozssan kernel: [2279698.677347] raid10: sdd1: rescheduling sector 959876968
Jun  6 20:24:54 ozssan kernel: [2279698.685027] raid10: sdd1: rescheduling sector 959876976
Jun  6 20:24:54 ozssan kernel: [2279698.692536] raid10: sdd1: rescheduling sector 959876984
Jun  6 20:24:54 ozssan kernel: [2279698.692540] sd 8:0:6:0: [sdd] Unhandled error code
Jun  6 20:24:54 ozssan kernel: [2279698.692542] sd 8:0:6:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun  6 20:24:54 ozssan kernel: [2279698.692545] sd 8:0:6:0: [sdd] CDB: Write(10): 2a 00 00 29 7b 37 00 00 08 00
Jun  6 20:24:54 ozssan kernel: [2279698.692550] end_request: I/O error, dev sdd, sector 2718519
Jun  6 20:24:54 ozssan kernel: [2279698.692553] raid10: Disk failure on sdd1, disabling device.
Jun  6 20:24:54 ozssan kernel: [2279698.692554] raid10: Operation continuing on 3 devices.
</log>

And after 8 seconds second disk failed and after another 20 seconds third disk failed too. Same log for all of drives. Pointless to say raid array was down.

Interesting point is that 4'th drive didn't fail. But this drive has been replaced two months ago and has been powered up for about 60 days.

Is there another ticking bomb in WD drives?


by
TheR

---

