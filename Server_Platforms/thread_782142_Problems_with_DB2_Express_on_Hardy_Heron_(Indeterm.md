---
title: "Problems with DB2 Express on Hardy Heron (Indeterminable operating system)"
date: 2008-05-04
forum: Server Platforms
---

### Post by tPelleplut on 2008-05-04
Hello,

I upgraded to Hardy Heron this weekend and I can nog longer run DB2 on my laptop. Looking into the db2diag.log I can find:

2008-05-05-00.14.19.668767+120 I62153E1641         LEVEL: Event
PID     : 10239                TID  : 140162244224736PROC : db2start
INSTANCE: omeins1              NODE : 000
FUNCTION: DB2 UDB, base sys utilities, sqleStartStopSingleNode, probe:1130
DATA #1 : String, 38 bytes
/ardome/db/omeins1/sqllib/adm/db2star2
DATA #2 : Hexdump, 256 bytes
0x00007FFF18D9DCF0 : 2F61 7264 6F6D 652F 6462 2F6F 6D65 696E    /ardome/db/omein
0x00007FFF18D9DD00 : 7331 2F73 716C 6C69 622F 6164 6D2F 6462    s1/sqllib/adm/db
0x00007FFF18D9DD10 : 3273 7461 7232 0000 0000 0000 0000 0000    2star2..........
0x00007FFF18D9DD20 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD30 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD40 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD50 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD60 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD70 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD80 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DD90 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DDA0 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DDB0 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DDC0 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DDD0 : 0000 0000 0000 0000 0000 0000 0000 0000    ................
0x00007FFF18D9DDE0 : 0000 0000 0000 0000 0000 0000 0000 0000    ................

2008-05-05-00.14.20.133882+120 E63795E837          LEVEL: Severe
PID     : 10246                TID  : 140205440595680PROC : db2star2
INSTANCE: omeins1              NODE : 000
FUNCTION: DB2 UDB, oper system services, sqloKADetermineKernelIntegrity, probe:30
DATA #1 : <preformatted>
Indeterminable operating system.
CALLSTCK: 
  [0] 0x00007F841BEEB5BE sqloKADetermineKernelIntegrity + 0x54C
  [1] 0x00007F841BEEA0C0 sqloKAAnalyze + 0x74
  [2] 0x000000000040CF10 /ardome/db/omeins1/sqllib/adm/db2star2 + 0xCF10
  [3] 0x0000000000408069 DB2StartMain + 0x29DD
  [4] 0x000000000040567F main + 0x37
  [5] 0x00007F8417C801C4 __libc_start_main + 0xF4
  [6] 0x00000000004055AA /ardome/db/omeins1/sqllib/adm/db2star2 + 0x55AA
  [7] 0x0000000000000000 ?unknown + 0x0
  [8] 0x0000000000000000 ?unknown + 0x0
  [9] 0x0000000000000000 ?unknown + 0x0

2008-05-05-00.14.20.197476+120 E64633E271          LEVEL: Severe
PID     : 10246                TID  : 140205440595680PROC : db2star2
INSTANCE: omeins1              NODE : 000
FUNCTION: DB2 UDB, oper system services, sqloKAAnalyze, probe:10
DATA #1 : Codepath, 8 bytes
5

I had the error on my DB2 Express 9.2 and got the same thing once upgraded to 9.5 (thought that would solve it...). Running x86_64 version of Ubuntu. Anyone else seen this?

---

### Post by windependence on 2008-05-05
I'm thinking you may have to reinstall DB2 as it does not recognize the new kernel. Just a guess though, I'm not a database expert.

-Tim

---

### Post by tPelleplut on 2008-05-05
That I did, and suffered from the same problem both before and after the reinstallation of DB2.

---

### Post by haba7 on 2009-02-04
Hi tPelleplut! Did you manage to get it working? I have the same problem in Intrepid with DB2 9.5.2 beta.

---

### Post by tPelleplut on 2009-02-04
> **haba7 said:**
> Hi tPelleplut! Did you manage to get it working? I have the same problem in Intrepid with DB2 9.5.2 beta.

No, I switched focus and did not try again afterwards. Sorry.

---

