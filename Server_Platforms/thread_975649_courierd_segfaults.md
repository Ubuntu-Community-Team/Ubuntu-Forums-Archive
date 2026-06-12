---
title: "courierd segfaults"
date: 2008-11-08
forum: Server Platforms
---

### Post by rkleemann on 2008-11-08
Hi,

I'm running a pretty busy email server with courier-mta.

I've been seeing a LOT of segfault messages, like this:

Nov  8 12:39:30 email1 kernel: [1186221.637015] courierd[19725]: segfault at 190000000038 rip 410bd5 rsp 7fff17537800 error 4
Nov  8 12:40:42 email1 kernel: [1186293.238148] courierd[20106] general protection rip:410bd5 rsp:7fff17537a20 error:0
Nov  8 12:42:43 email1 kernel: [1186414.070214] courierd[20548]: segfault at 2f3731366a rip 410bd5 rsp 7fff17537a20 error 4
Nov  8 12:44:44 email1 kernel: [1186535.017948] courierd[21361]: segfault at 38 rip 410bd5 rsp 7fff17537a20 error 4
Nov  8 12:46:00 email1 kernel: [1186610.660123] courierd[22477]: segfault at 6da7 rip 410bd5 rsp 7fff17537800 error 4
Nov  8 12:47:07 email1 kernel: [1186676.891922] courierd[23174] general protection rip:410bd5 rsp:7fff17537a20 error:0
Nov  8 12:48:17 email1 kernel: [1186746.925591] courierd[23479] general protection rip:410bd5 rsp:7fff175374d0 error:0
Nov  8 12:49:50 email1 kernel: [1186839.813743] courierd[23843] general protection rip:410bd5 rsp:7fff175376f0 error:0
Nov  8 12:51:21 email1 kernel: [1186930.328673] courierd[24285]: segfault at 6da7 rip 410bd5 rsp 7fff17537a20 error 4
Nov  8 12:53:10 email1 kernel: [1187038.990709] courierd[24812]: segfault at 3871 rip 410bd5 rsp 7fff17537a20 error 4

The server isn't out of memory, here's the result of free:

$ free
             total       used       free     shared    buffers     cached
Mem:       1509436    1385140     124296          0     148816     727448
-/+ buffers/cache:     508876    1000560
Swap:      1124508     133388     991120

What could be causing these segfaults?

Thanks
Ricardo

---

