---
title: "Live cd H/w detection"
date: 2004-12-28
forum: The Cafe
---

### Post by eldrich_rebello on 2004-12-28
Hi,how do I find out if the live cd has detected my modem?Also how do I connect to the net from the live cd?Will these results determine if the same will happen if I install ubuntu to my hard disk?It's a morphix live cd actually.Rite?

---

### Post by nemin on 2004-12-28
[QUOTE=eldrich_rebello]Hi,how do I find out if the live cd has detected my modem?[/QUOTE]
I think you first have to tell us what kind of modem you're talking about.. A DSL modem or a phone modem? USB or PCI? Without that info no one can help you.
[QUOTE=eldrich_rebello]
Also how do I connect to the net from the live cd?[/QUOTE]
Completely depends on your kind of internet connection.
[QUOTE=eldrich_rebello]
Will these results determine if the same will happen if I install ubuntu to my hard disk?[/QUOTE]
Usually it's almost the same.
[QUOTE=eldrich_rebello]
It's a morphix live cd actually.Rite?[/QUOTE]
As far as I know, it's only *based* on Morphix..

---

### Post by eldrich_rebello on 2004-12-28
MODEMS:CXT
PCI Slot 3 (PCI bus 1, device 10, function 0)
from the win xp device manager.PCI it is then.

12-29-2004 00:30:38.750 - File: C:\WINDOWS\system32\tapisrv.dll, Version 5.1.2600   
12-29-2004 00:30:38.750 - File: C:\WINDOWS\system32\unimdm.tsp, Version 5.1.2600   
12-29-2004 00:30:38.750 - File: C:\WINDOWS\system32\unimdmat.dll, Version 5.1.2600   
12-29-2004 00:30:38.750 - File: C:\WINDOWS\system32\uniplat.dll, Version 5.1.2600   
12-29-2004 00:30:38.765 - File: C:\WINDOWS\system32\drivers\modem.sys, Version 5.1.2600   
12-29-2004 00:30:38.765 - File: C:\WINDOWS\system32\modemui.dll, Version 5.1.2600   
12-29-2004 00:30:38.781 - File: C:\WINDOWS\system32\mdminst.dll, Version 5.1.2600   
12-29-2004 00:30:38.781 - Modem type: SoftV92 Data Fax Modem
12-29-2004 00:30:38.781 - Modem inf path: mdmcxsf2.inf
12-29-2004 00:30:38.781 - Modem inf section: ModemCH
12-29-2004 00:30:38.781 - Matching hardware ID: pci\ven_14f1&dev_2f00
12-29-2004 00:30:39.109 - 115200,8,N,1, ctsfl=1, rtsctl=2
12-29-2004 00:30:39.109 - Initializing modem.
12-29-2004 00:30:39.109 - DSR is low while initializing the modem. Verify modem is turned on.
12-29-2004 00:30:39.125 - Send: AT<cr>
12-29-2004 00:30:39.125 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.125 - Interpreted response: OK
12-29-2004 00:30:39.140 - Send: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2<cr>
12-29-2004 00:30:39.281 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.281 - Interpreted response: OK
12-29-2004 00:30:39.296 - Send: ATS7=65M1+ES=3,0,2;+DS=3;+IFC=2,2;X3<cr>
12-29-2004 00:30:39.312 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.312 - Interpreted response: OK
12-29-2004 00:30:39.312 - Waiting for a call.
12-29-2004 00:30:39.328 - Send: at+vcid=1<cr>
12-29-2004 00:30:39.343 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.343 - Interpreted response: OK
12-29-2004 00:30:39.359 - Send: ATS0=0<cr>
12-29-2004 00:30:39.375 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.375 - Interpreted response: OK
12-29-2004 00:30:39.375 - 921600,8,N,1, ctsfl=1, rtsctl=2
12-29-2004 00:30:39.375 - Initializing modem.
12-29-2004 00:30:39.375 - DSR is low while initializing the modem. Verify modem is turned on.
12-29-2004 00:30:39.390 - Send: AT<cr>
12-29-2004 00:30:39.406 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.406 - Interpreted response: OK
12-29-2004 00:30:39.421 - Send: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2<cr>
12-29-2004 00:30:39.578 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.578 - Interpreted response: OK
12-29-2004 00:30:39.593 - Send: ATS7=65M0+ES=3,0,2;+DS=3;+IFC=2,2;X3<cr>
12-29-2004 00:30:39.609 - Recv: <cr><lf>OK<cr><lf>
12-29-2004 00:30:39.609 - Interpreted response: OK
12-29-2004 00:30:39.609 - Dialing.
12-29-2004 00:30:39.625 - Send: ATDT########<cr>
12-29-2004 00:31:18.578 - Recv: <cr><lf>+MCR: V34<cr><lf>
12-29-2004 00:31:18.578 - Interpreted response: Informative
12-29-2004 00:31:18.578 - Recv: <cr><lf>+MRR: 33600<cr><lf>
12-29-2004 00:31:18.578 - Interpreted response: Informative
12-29-2004 00:31:19.343 - Recv: <cr><lf>+ER: LAPM<cr><lf>
12-29-2004 00:31:19.343 - Interpreted response: Informative
12-29-2004 00:31:19.343 - Recv: <cr><lf>+DR: V42B<cr><lf>
12-29-2004 00:31:19.343 - Interpreted response: Informative
12-29-2004 00:31:19.343 - Recv: <cr><lf>CONNECT 33600<cr><lf>
12-29-2004 00:31:19.343 - Interpreted response: Connect
12-29-2004 00:31:19.343 - Connection established at 33600bps.
12-29-2004 00:31:19.343 - Error-control on.
12-29-2004 00:31:19.343 - Data compression on.
12-29-2004 00:31:49.343 - Read: Total: 8379, Per/Sec: 276, Written: Total: 4366, Per/Sec: 142
12-29-2004 00:33:49.343 - Read: Total: 102770, Per/Sec: 786, Written: Total: 77281, Per/Sec: 607

from a log file.makes no sens to me!PCI\VEN_14F1&DEV_2F00&SUBSYS_200414F1&REV_01\4&1A671D0C&0&50F0

---

