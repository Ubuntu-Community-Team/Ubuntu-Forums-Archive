---
title: "Wine error message?"
date: 2010-11-14
forum: Wine
---

### Post by phantomswordsmen on 2010-11-14
I'm trying to run a program called ti connect. When I try to run it in Wine I get this message. 

The file '/home/wil/TI Calculator/ticonnect_eng.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Ubuntu says that they do this to prevent me from security risks. Is there anyway to bypass this?

---

### Post by Soulcage on 2010-11-14
cd /home/wil/TI Calculator/ && wine ticonnect_eng.exe
or you can right click any .exe click properties then permission tab and click the check box.

---

