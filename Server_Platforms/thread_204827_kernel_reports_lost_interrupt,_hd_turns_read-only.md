---
title: "kernel reports lost interrupt, hd turns read-only"
date: 2006-06-27
forum: Server Platforms
---

### Post by rpsenicnik on 2006-06-27
Hello,

I've been running Ubuntu 6.06 as a LAMP server for few weeks, and kernel repeatedly turns hard drive into read-only mode after server is working for 4-5 days. I've checked the hard drive for bad sectors and did fsck, but the problem still happens. Load on the server is minimal, and I'm using G3 iBook.

If the hardware is the problem, I'll probably get something more sturdy. Any recommendations?

Here's the kernel log when the change occurs:

Jun 27 06:25:01 sango-cub /USR/SBIN/CRON[10666]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily)
Jun 27 06:25:26 sango-cub kernel: [422769.705068] ide-pmac lost interrupt, dma status: 8400
Jun 27 06:25:26 sango-cub kernel: [422769.710608] hda: lost interrupt
Jun 27 06:25:26 sango-cub kernel: [422769.710628] hda: dma_intr: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 27 06:25:26 sango-cub kernel: [422769.710645] ide: failed opcode was: unknown
Jun 27 06:25:26 sango-cub kernel: [422769.804589] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 27 06:25:26 sango-cub kernel: [422769.804602] ide: failed opcode was: unknown
Jun 27 06:25:26 sango-cub kernel: [422769.804613] hda: drive not ready for command
Jun 27 06:25:26 sango-cub kernel: [422769.810057] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 27 06:25:26 sango-cub kernel: [422769.810070] ide: failed opcode was: unknown
Jun 27 06:25:26 sango-cub kernel: [422769.810080] hda: drive not ready for command
Jun 27 06:25:26 sango-cub kernel: [422769.815444] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jun 27 06:25:26 sango-cub kernel: [422769.815457] ide: failed opcode was: unknown
Jun 27 06:25:26 sango-cub kernel: [422769.815471] hda: DMA disabled
Jun 27 06:25:26 sango-cub kernel: [422769.815482] hdb: DMA disabled
Jun 27 06:25:26 sango-cub kernel: [422769.815517] hda: drive not ready for command
Jun 27 06:25:28 sango-cub kernel: [422772.213050] ide0: reset: success
Jun 27 06:25:42 sango-cub kernel: [422785.773066] hda: irq timeout: status=0xd0 { Busy }
Jun 27 06:25:42 sango-cub kernel: [422785.773104] ide: failed opcode was: unknown
Jun 27 06:25:49 sango-cub kernel: [422793.213046] ide0: reset: success
Jun 27 06:26:44 sango-cub exiting on signal 15

---

### Post by lamego on 2006-06-27
The fsck only checks for the filesystem structure it doesn't perform a surface scan. From your log you seem to have data read/write errors.
Use the badblocks command to check for bad blocks.

---

### Post by MJN on 2006-06-27
Your drive could be on its way out? I'm afraid I don't know the meaning of the specific errors however it can't hurt to rule out physical errors.

Install **smartmontools** from the repositories and try (as root):

smartctl -s on -o on -S on /dev/hda
smartctl -a /dev/hda

Any errors? Might also be worth running it on /dev/hdb too as I see that's mentioned too.

You can run various tests too - try man smartctl for details.

This might be stabbing in the dark, but do you have a spare IDE cable you can try?

Mathew

[EDIT: Could be a red herring but it looks like you're not the only one hence the above may not apply. See [http://groups.google.co.uk/group/linux.debian.ports.powerpc/browse_frm/thread/f12646d58f5f7b23/cfae90a4cc189071%23cfae90a4cc189071]](http://groups.google.co.uk/group/linux.debian.ports.powerpc/browse_frm/thread/f12646d58f5f7b23/cfae90a4cc189071%23cfae90a4cc189071])

---

### Post by rpsenicnik on 2006-06-27
Thank you for the google group link, that seems to be the same problem.

Both SMART and badblock check report no problems.

I'll google about disabling CD drive, that might help (and I'm not using it anyways).

In case my iBook is stuck with this, is there a way to:

-automatically return the hard-drive into read-write state
-or restart the system when it happens
-or disable the switch to read-only state?

Thanks for the help, really appreciate it,

Rudi

---

### Post by LordHunter317 on 2006-06-27
Your disk is dying or you have a bad IDE controller or ribbon.  It's imperative you check the health of the disk in another system.

---

### Post by MJN on 2006-06-28
Indeed - you really need to fix the cause rather than the symptom.

(For info, the remount as read-only is configured in /etc/fstab with the **errors=remount-ro **optionhowever as mentioned this isn't the way to 'solve' this one)

Mathew

---

### Post by rpsenicnik on 2006-06-28
Thanks for the info.

Since this is an ancient iBook laptop, getting to the HD is far beyond my capabilities  :) It's all good, though, since this is my learning machine - I've just wanted to get my feet wet before jumping into the ubuntu server waters.

---

