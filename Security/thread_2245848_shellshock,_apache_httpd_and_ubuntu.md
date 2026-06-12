---
title: "shellshock, apache httpd and ubuntu"
date: 2014-09-26
forum: Security
---

### Post by Erik_Persson on 2014-09-26
Ubuntu (as well as Debian 7) symlinks /bin/sh to /bin/dash, not /bin/bash, as standard. Dash is not vulnerable to shellshock.
Thus, apache on ubuntu should not be vulnarable to shellshock (unless cgi explicitly use bash etc). 

However, I can not verify this since I have patched all my ubuntu and debian machines.
Anyone else who can verify it?

/erik

---

### Post by John_Ten on 2014-09-30
The executable is mentioned at the start of the script, e.g. #!/bin/bash, that is the executable that will run when the script is executed. If you change that it will be ok with the condition that /bin/bash won't be called specifically inside the script.

---

