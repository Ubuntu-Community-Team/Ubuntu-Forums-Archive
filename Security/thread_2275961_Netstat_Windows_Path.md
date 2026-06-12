---
title: "Netstat Windows Path"
date: 2015-04-29
forum: Security
---

### Post by stephen69 on 2015-04-29
On running netstat I got the follownig back.   Why would a windows path be mapped, given that I dont connect to any windows box?

unix  3      [ ]         STREAM     CONNECTED     236308   3764/C:\windows\sys


/tmp/dbus-JeRAuqa2qg
unix  3      [ ]         STREAM     CONNECTED     230799   2704/unity-scope-ho 
unix  3      [ ]         STREAM     CONNECTED     29193    2873/deja-dup-monit 
unix  3      [ ]         STREAM     CONNECTED     26952    2704/unity-scope-ho 
unix  3      [ ]         STREAM     CONNECTED     236308   3764/C:\windows\sys 
unix  3      [ ]         STREAM     CONNECTED     25841    2622/telepathy-indi

---

### Post by Habitual on 2015-04-29
Do you have a Windows partition mounted?
Or did you?

---

### Post by stephen69 on 2015-04-29
No window partion mounted current or past.  Could the system have being compromised?

---

### Post by cariboo on 2015-04-29
Have you got wine installed?

---

### Post by The Cog on 2015-04-29
**sudo lsof | less**
should at least tell you which program has it open.

---

### Post by stephen69 on 2015-04-30
Thanks all,  I didnt realize wine mapped a virtual drive.  Explains why after apt removed wine the mapping was not reproducable.

---

### Post by Habitual on 2015-05-11
Glad *that* worked out!

---

