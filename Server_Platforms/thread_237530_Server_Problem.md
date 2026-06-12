---
title: "Server Problem"
date: 2006-08-16
forum: Server Platforms
---

### Post by Sarunas on 2006-08-16
Hi,

I'm having some issues with the PE2900 running Ubuntu 6.0.

The server has crashed yesterday with I/O errors and megaraid
failure to reset, I don't have the exact errors from yesterday.

And a short while ago, it had another problem. In short:

[42964349.130000] sd 0:2:0:0: megasas: RESET -9743 cmd=2a
[42964349.130000] megasas: [ 0]waiting for 8 commands to complete
<SNIP>
[42964530.940000] sd 0:2:0:0: megasas: RESET -9743 cmd=2a
[42964530.940000] megasas: cannot recover from previous reset failures
[42964530.950000] sd 0:2:0:0: megasas: RESET -9743 cmd=2a
[42964530.950000] megasas: cannot recover from previous reset failures
[42964530.960000] sd 0:2:0:0: scsi: Device offlined - not ready after error recovery
<SNIP>
[42964530.960000] sd 0:2:0:0: SCSI error: return code = 0x6000000
[42964530.960000] end_request: I/O error, dev sda, sector 115180
[42964530.960000] sd 0:2:0:0: rejecting I/O to offline device
[42964530.960000] sd 0:2:0:0: rejecting I/O to offline device
[42964530.960000] sd 0:2:0:0: rejecting I/O to offline device
[42964530.960000] Buffer I/O error on device sda2, logical block 1589248
[42964530.960000] lost page write due to I/O error on sda2
<SNIP>

The full log can be found here: [http://www.redbrick.dcu.ie/~svan/sda_error](http://www.redbrick.dcu.ie/~svan/sda_error)

I ran all tests available for the hard drives on Dell' hardware
testing program, it found nothing wrong with the hardware. Its just 2
146 SAS hard drives on a PERC 5/i controller on RAID1.

Does anyone else experience this problem or even know why this is
happening or how to solve this?

The problem has happened yesterday with 2.6.15-23 kernel, the problem on monday was the 2.6.15-26 kernel.

Thanks,

---

