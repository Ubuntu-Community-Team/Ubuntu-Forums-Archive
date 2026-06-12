---
title: "Ubuntu 8.10: IBM LTO4 SAS drive / Adaptec ASC-3805 won't read LTO2 tape nor write to"
date: 2008-12-23
forum: Server Platforms
---

### Post by KewlEugene on 2008-12-23
Hi,

Issue:

Ubuntu 8.10: IBM LTO4 SAS drive / Adaptec ASC-3805 won't read LTO2 tape nor write to LTO3 tape.

I have an Ubuntu 8.10 desktop. I tried an IBM LTO4 SAS drive with an Adaptec ASC-3805 SAS, and it won't read an LTO2 tape, and it will not write to an LTO3 tape.

these commands work fine:
..........................
mt -f /dev/nst0 rewind
mt -f /dev/nst0 eject
mt -f /dev/nst0 status
.........................

if i place an LTO2 tape into the IBM LTO4 drive. (the tape was  written on the same ubuntu 8.10 PC, with HP 448 LTO2 drive / Adaptec LP29160LP SCSI card) and then type 

mt -f /dev/nst0 setblk 65536

.............................
/dev/nst0: Input output error
.............................

So my question is, does Ubuntu 8.10 server work with the IBM LTO4 SAS and Adaptec ASC-3805 ? Which driver or version of mt works ?

Thanks

---

### Post by KewlEugene on 2008-12-24
opps, I meant Adaptec 3085 and not 3805.

On the IBM LTO4 SAS drive, I just tied writing an LTO3 tape with

dd of=/dev/nst0 if=data.tar

and it just hung. i tried to kill -9 and it wouldn't go away. had to reboot.

does the adaptec-3085 require any special config ?

---

