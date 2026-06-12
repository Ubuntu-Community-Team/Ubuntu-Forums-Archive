---
title: "OSSEC realtime FILE Monitoring!!"
date: 2010-10-15
forum: Security
---

### Post by CyberAngel on 2010-10-15
Hello,

I am striving to setup OSSEC to monitor some specific files for realtime changes! Is this possible?
I can't really find a lot of info from their Documentation :(

Some Examples:
/etc/myfile.txt is deleted. I need this to be reported.
/etc/myfile.txt is created again so I need this to be reported again!
This has to happen instantly though, because the file might be deleted and created again many times in a short period of time.. 


Another one...
/etc/passwd is touched (accessed) even if there is no changes! Can this be reported as well?

Thank you!

---

### Post by CharlesA on 2010-10-15
*Moved to **Security Discussions**.*

---

### Post by OpSecShellshock on 2010-10-15
Strikes me as more of a tripwire job.

---

