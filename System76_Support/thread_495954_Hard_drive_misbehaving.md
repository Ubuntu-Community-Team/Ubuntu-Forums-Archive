---
title: "Hard drive misbehaving?"
date: 2007-07-08
forum: System76 Support
---

### Post by beuno on 2007-07-08
Hello again  :D
I've been using my Darter for over a week now, and it's just perfect.
I haven't had any problems, but I have noticed a LOT of these in my /var/logs/kern.log
```

Jul  8 15:18:11 ubuntu kernel: [218005.088000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218005.088000] end_request: I/O error, dev hda, sector 89174336
Jul  8 15:18:11 ubuntu kernel: [218009.460000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218009.460000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174344
Jul  8 15:18:11 ubuntu kernel: [218009.460000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218009.460000] end_request: I/O error, dev hda, sector 89174344
Jul  8 15:18:11 ubuntu kernel: [218013.756000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218013.756000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174352
Jul  8 15:18:11 ubuntu kernel: [218013.756000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218013.756000] end_request: I/O error, dev hda, sector 89174352
Jul  8 15:18:11 ubuntu kernel: [218017.884000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218017.884000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174360
Jul  8 15:18:11 ubuntu kernel: [218017.884000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218017.884000] end_request: I/O error, dev hda, sector 89174360
Jul  8 15:18:11 ubuntu kernel: [218021.976000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218021.976000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174368
Jul  8 15:18:11 ubuntu kernel: [218021.976000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218021.976000] end_request: I/O error, dev hda, sector 89174368
Jul  8 15:18:11 ubuntu kernel: [218026.092000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218026.092000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174376
Jul  8 15:18:11 ubuntu kernel: [218026.092000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218026.092000] end_request: I/O error, dev hda, sector 89174376
Jul  8 15:18:11 ubuntu kernel: [218030.176000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218030.176000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174384
Jul  8 15:18:11 ubuntu kernel: [218030.176000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218030.176000] end_request: I/O error, dev hda, sector 89174384
Jul  8 15:18:11 ubuntu kernel: [218034.324000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218034.324000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174392
Jul  8 15:18:11 ubuntu kernel: [218034.324000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218034.324000] end_request: I/O error, dev hda, sector 89174392
Jul  8 15:18:11 ubuntu kernel: [218038.708000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218038.708000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174400
Jul  8 15:18:11 ubuntu kernel: [218038.708000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218038.708000] end_request: I/O error, dev hda, sector 89174400
Jul  8 15:18:11 ubuntu kernel: [218042.792000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218042.792000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174408
Jul  8 15:18:11 ubuntu kernel: [218042.792000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218042.792000] end_request: I/O error, dev hda, sector 89174408
Jul  8 15:18:11 ubuntu kernel: [218046.984000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218046.984000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174416
Jul  8 15:18:11 ubuntu kernel: [218046.984000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218046.984000] end_request: I/O error, dev hda, sector 89174416
Jul  8 15:18:11 ubuntu kernel: [218051.100000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218051.100000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174424
Jul  8 15:18:11 ubuntu kernel: [218051.100000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218051.100000] end_request: I/O error, dev hda, sector 89174424
Jul  8 15:18:11 ubuntu kernel: [218055.240000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218055.240000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174432
Jul  8 15:18:11 ubuntu kernel: [218055.240000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218055.240000] end_request: I/O error, dev hda, sector 89174432
Jul  8 15:18:11 ubuntu kernel: [218059.456000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:11 ubuntu kernel: [218059.456000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174440
Jul  8 15:18:11 ubuntu kernel: [218059.456000] ide: failed opcode was: unknown
Jul  8 15:18:11 ubuntu kernel: [218059.456000] end_request: I/O error, dev hda, sector 89174440
Jul  8 15:18:24 ubuntu kernel: [218066.664000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:24 ubuntu kernel: [218066.664000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174440
Jul  8 15:18:24 ubuntu kernel: [218066.664000] ide: failed opcode was: unknown
Jul  8 15:18:24 ubuntu kernel: [218066.664000] end_request: I/O error, dev hda, sector 89174440
Jul  8 15:18:24 ubuntu kernel: [218071.592000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jul  8 15:18:24 ubuntu kernel: [218071.592000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=89174440, high=5, low=5288360, sector=89174440
Jul  8 15:18:24 ubuntu kernel: [218071.592000] ide: failed opcode was: unknown
Jul  8 15:18:24 ubuntu kernel: [218071.592000] end_request: I/O error, dev hda, sector 89174440
Jul  8 21:23:28 ubuntu kernel: [239976.828000] set_level status: 0
Jul  8 21:23:28 ubuntu kernel: [239976.828000] set_level status: 0
Jul  8 21:23:28 ubuntu kernel: [239977.004000] set_level status: 0

```

Is the hard drive misbehaving?

I haven't had this before.

---

### Post by beuno on 2007-07-09
I'm being able to relate these errors with system hang ups.
The whole system just freezes for a few minutes and then continues working normally.
Then /var/log/syslog reports those disc errors for those minutes.

---

### Post by bigken on 2007-07-09
could be the drive has developed some bad sectors

---

### Post by beuno on 2007-07-09
It would look like it, but since it's brand new, I wouldn't want it to have  :D

---

### Post by palintheus on 2007-07-09
There have been several threads in this section about this, below is the first one I found on the second page.

[http://ubuntuforums.org/showthread.php?t=470403](http://ubuntuforums.org/showthread.php?t=470403)

---

### Post by beuno on 2007-07-09
> **palintheus said:**
> There have been several threads in this section about this, below is the first one I found on the second page.

[http://ubuntuforums.org/showthread.php?t=470403](http://ubuntuforums.org/showthread.php?t=470403)

Thanks for that, it does seem like a similar/same problem.

The thing is, I don't have a CD/DVD in my drive, and I have run the System76 drivers a few days ago.

Any more ideas?   :D

---

### Post by thomasaaron on 2007-07-09
I get the problem too on my Darter from time to time.
Something I'm doing it is triggering it, but I've not been able to put my finger on it yet.

It seems like it will run fine for a week or two and then I'll burn a CD and leave it in the drive too long, or something. Then, after rebooting, the problem will be gone for another week or two.

Right now, I'm focusing on a firmware update that should nip it in the bud once and for all. Almost there.

Best,
Tom

---

### Post by beuno on 2007-07-09
> **thomasaaron said:**
> I get the problem too on my Darter from time to time.
Something I'm doing it is triggering it, but I've not been able to put my finger on it yet.

It seems like it will run fine for a week or two and then I'll burn a CD and leave it in the drive too long, or something. Then, after rebooting, the problem will be gone for another week or two.

Right now, I'm focusing on a firmware update that should nip it in the bud once and for all. Almost there.

Best,
Tom

You guys rock :guitar:

---

### Post by bigken on 2007-07-09
> **beuno said:**
> It would look like it, but since it's brand new, I wouldn't want it to have  :D

the thing is just because its new does not make it a good drive :(

---

