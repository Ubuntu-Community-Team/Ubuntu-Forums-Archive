---
title: "Terminal Emulator Control File"
date: 2010-09-17
forum: Server Platforms
---

### Post by wdtice on 2010-09-17
Hi All, I have gotten my project ubuntu server 10.04 up and running and logged in remotely with a terminal emulator program called AccuTerm  that I use from work. It has multiple control files and want to know which file works best with ubuntu server. My reason for asking is some of the manual pages do not display correctly and keyboard functions seem to function incorrectly via VT100 and I have eighteen to choose from? Any ideas with out me checking all of them.

---

### Post by Bachstelze on 2010-09-18
Hard to say which one to try without knowing which ones you have. ;) Try VT220 if you have it, it should be good enough.

Also don't forget to set the TERM environment variable to whatever you use, like

```
export TERM=vt220
```

---

### Post by wdtice on 2010-09-18
Thank you

---

