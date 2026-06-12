---
title: "cbc(aes) algo missing from /proc/crypto on 18.04"
date: 2020-12-18
forum: Security
---

### Post by Serban_Maerean on 2020-12-18
Looking at the /proc/crypto file on a Ubuntu 18.04 machine, I don't see the cbc(aes) algo.  I see the xts(aes) algo with type skcipher and I expected to see cbc(aes) algo w/same type as well.

[COLOR=#000000][FONT=Menlo]# uname -a[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Linux hs22n64 4.15.0-88-generic #88~16.04.1-Ubuntu SMP Wed Feb 12 04:19:15 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# whichos[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]OS: Debian Linux: Ubuntu 18.04 LTS  =>  Kernel: 4.15.0-88-generic on x86_64[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]# grep "xts(aes)" /proc/crypto[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]name         : xts(aes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# grep "cbc(aes)" /proc/crypto[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#
[/FONT][/COLOR]

These are the 2 aes algos I see in /proc/crypto:

[COLOR=#000000][FONT=Menlo]name         : xts(aes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]driver       : xts(ecb(aes-asm))[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]module       : kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]priority     : 200[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]refcnt       : 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]selftest     : passed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]internal     : no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]type         : skcipher[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]async        : no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]blocksize    : 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]min keysize  : 32[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]max keysize  : 64[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ivsize       : 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]chunksize    : 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]walksize     : 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]name         : ecb(aes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]driver       : ecb(aes-asm)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]module       : kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]priority     : 200[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]refcnt       : 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]selftest     : passed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]internal     : no[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]type         : blkcipher[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]blocksize    : 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]min keysize  : 16[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]max keysize  : 32[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ivsize       : 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]geniv        : <default>[/FONT][/COLOR]

Is it expected?

Thanks so much.

---

