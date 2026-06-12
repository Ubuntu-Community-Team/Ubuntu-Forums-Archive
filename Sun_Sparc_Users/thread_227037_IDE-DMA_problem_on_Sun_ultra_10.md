---
title: "IDE-DMA problem on Sun ultra 10"
date: 2006-08-01
forum: Sun Sparc Users
---

### Post by puiwa on 2006-08-01
Hello,

I installed 6.06 on a ultra10, everyting was fine except there were errors on IDE-DMA setting. Any hint to solve the problem?


[    9.634098] hda: dma_timer_expiry: dma status == 0x60
[    9.634127] hda: DMA timeout retry
[    9.634138] hda: timeout waiting for DMA
[    9.680372] hda: status error: status=0x58 { DriveReady SeekComplete DataRequ
[    9.680394] ide: failed opcode was: unknown
[    9.680411] hda: drive not ready for command
[   14.734094] hda: status timeout: status=0xd0 { Busy }
[   14.734108] ide: failed opcode was: unknown
[   14.734126] hdb: DMA disabled
[   14.734161] hda: drive not ready for command
[   15.310094] ide0: reset: success
[    5.289376] hda: dma_timer_expiry: dma status == 0x20
[    5.289402] hda: DMA timeout retry
[    5.289413] hda: timeout waiting for DMA
[    5.335634] hda: status error: status=0x58 { DriveReady SeekComplete DataRequ
[    5.335655] ide: failed opcode was: unknown
[    5.335672] hda: drive not ready for command
[   10.389364] hda: status timeout: status=0xd0 { Busy }
[   10.389378] ide: failed opcode was: unknown
[   10.389419] hda: drive not ready for command
[   10.965365] ide0: reset: success

---

