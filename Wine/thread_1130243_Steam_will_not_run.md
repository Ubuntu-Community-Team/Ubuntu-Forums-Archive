---
title: "Steam will not run"
date: 2009-04-19
forum: Wine
---

### Post by eilios on 2009-04-19
I installed to Jaunty recently, and am enjoying it so far. The only problem is now steam refuses to run. I reinstalled WINE and everything EXCEPT steam runs perfectly. Help?

---

### Post by eilios on 2009-04-19
Update: I ran it with the terminal and got this error.
CellID: Fetching server list from CSDS. . .
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 164 servers.
CellID: Connecting to 87.248.196.197:27031. . .
CellID: Connect to 87.248.196.197:27031 took 171 MS
CellID: Nothing beat our old best time of 49 MS
err:ntdll:RtlpWaitForCriticalSection section 0xc271e4 "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)

---

### Post by NightMKoder on 2009-04-19
Wine version? I have it running fine on latest wine (1.1.19).

---

### Post by eilios on 2009-04-19
> **NightMKoder said:**
> Wine version? I have it running fine on latest wine (1.1.19).
That's what i'm using, which is what is weird.

---

### Post by NightMKoder on 2009-04-19
Do you have any other apps installed on the same prefix? I installed steam on a clean prefix (`export WINEPREFIX=~/.wine_steam`) so it doesn't conflict with any other app.

---

### Post by eilios on 2009-04-19
> **NightMKoder said:**
> Do you have any other apps installed on the same prefix? I installed steam on a clean prefix (`export WINEPREFIX=~/.wine_steam`) so it doesn't conflict with any other app.
That worked. Thanks.

---

