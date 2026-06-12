---
title: "Steam is not working (64bit Jaunty)"
date: 2009-04-21
forum: Wine
---

### Post by Peter09 on 2009-04-21
Steam was working and suddenly stopped. Now when I attempt to start it I get a blue screen.

The last message logged to a terminal is to do with deleting a lock file.

Any Suggestions?

---

### Post by Kareeser on 2009-04-21
Paste the error here

---

### Post by Peter09 on 2009-04-21
Here it is

> fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: Fetching server list from CSDS. . .
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 171 servers.
CellID: Connecting to 196.38.180.3:27031. . .
CellID: Connect to 196.38.180.3:27031 took 575 MS
CellID: Nothing beat our old best time of 74 MS
err:ntdll:RtlpWaitForCriticalSection section 0x89724c "?" wait timed out in thread 0023, blocked by 0024, retrying (60 sec)
Terminated
[email]game@Mesh:~/.wine[/email]/drive_c/Program Files/Steam$ Deleting active MRSW lock (0x1122bc), expect failure

---

### Post by NightMKoder on 2009-04-21
Do you have moblock/ipblock installed? Steam doesn't like not receiving the first message it sends.

---

### Post by Peter09 on 2009-04-21
Not to my knowledge, I have never explicitly installed them.

---

