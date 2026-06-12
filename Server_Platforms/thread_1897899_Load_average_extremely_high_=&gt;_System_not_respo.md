---
title: "Load average extremely high =&gt; System not responding"
date: 2011-12-20
forum: Server Platforms
---

### Post by tincup on 2011-12-20
Hi.

We have an Ubuntu Server System, where users logon an interactively start some number crunching processes. Sometimes, if users don't "behave", the load average can get so high that the system is not responding anymore.

I do realize that it might be time for a more sophisticated job management (e.g. a grid engine). But for now, is there any way of controlling the load average and, especially, always leaving some free time slots for system processes like networking?

Thanks in advance,
 Tin

---

### Post by Lars Noodén on 2011-12-20
Just two guesses: You could try [nice](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nice.1.html) when they log on.  Or you could install [cpulimit](http://ubuntuforums.org/showthread.php?t=992706) and try that.

---

### Post by SeijiSensei on 2011-12-20
It looks like you can control quite a few aspects of the user's environment via PAM, specifically in the /etc/security/limits.conf file.  The "priority" and "nice" directives appear especially relevant.  See
 
[http://www.linuxtopia.org/online_books/linux_administrators_security_guide/16_Linux_Limiting_and_Monitoring_Users.html#PAM](http://www.linuxtopia.org/online_books/linux_administrators_security_guide/16_Linux_Limiting_and_Monitoring_Users.html#PAM)

and 

[http://ss64.com/bash/limits.conf.html](http://ss64.com/bash/limits.conf.html)

---

