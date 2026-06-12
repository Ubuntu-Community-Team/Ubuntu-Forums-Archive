---
title: "Oversight in firmware?"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-03-23
This morning I've noticed that kernel is complaining about being unable to load amd-ucode/microcode_amd.bin.
I've checked and folder *amd-ucode* under */lib/firmware* is missing and two files from it: microcode_amd.bin microcode_amd_fam15h.bin.
Remedy is easy: from *[http://www.amd64.org/support/microcode.html](http://www.amd64.org/support/microcode.html)* get [http://www.amd64.org/index.php?id=50&file=amd-ucode-latest.tar](http://www.amd64.org/index.php?id=50&file=amd-ucode-latest.tar), create folder *amd-ucode* in */lib/firmware*, extract two aforementioned files and that is it. If You want You could (not to restart machine) do ```
modprobe -r microcode
modprobe microcode
```Every bug is an opportunity to learn something new... ;)

---

### Post by dino99 on 2012-03-23
dont have *.bin about my intel microcode, but lot of things found by nautilus. Why do you think it should use that path ? (lib/firmware)

---

### Post by zika on 2012-03-23
> **dino99 said:**
> dont have *.bin about my intel microcode, but lot of things found by nautilus. Why do you think it should use that path ? (lib/firmware)From several pieces of documentation. Also, it corrected message (that gave hint about the path that file should be located) that surfaced in dmsg this morning.
So:
1. it is in accordance with documentation (read it in archive mentioned above, for example...) ...
2. it works...
```
:~$ dmesg|grep microcode
[   14.993985] microcode: CPU0: patch_level=0x01000083
[   15.778263] microcode: CPU1: patch_level=0x01000083
[   15.779979] microcode: CPU2: patch_level=0x01000083
[   15.781662] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba

```

---

### Post by dino99 on 2012-03-23
> **zika said:**
> From several pieces of documentation. Also, it corrected message (that gave hint about the path that file should be located) that surfaced in dmsg this morning.
So:
1. it is in accordance with documentation (read it in archive mentioned above, for example...) ...
2. it works...

so  have you reported it ?

---

### Post by zika on 2012-03-23
> **dino99 said:**
> so  have you reported it ?No.

Update: I found some spare time to explain this laconic answer: I have mainline daily kernel and (first) I have to check if a message that I received was due to 999 or it would be reproduced also in 3.2-ubuntu-generic... Before that it is un-opportune to file a bug... Just short while ago update for linux-firmware came (without microcode for amd...) so...

---

