---
title: "cups not starting"
date: 2011-02-23
forum: Server Platforms
---

### Post by expatCM on 2011-02-23
cups does not start with the server.  When I  try to start from the terminal I get the error message

cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting! 
cupsd: Child exited with status 1!

The log files show nothing.  cupsd.conf exists.  It is user - root and group - root with permissions set at 0644.

My interpretation of this is that the program is not launching from either boot or terminal for a fundamental reason.  I do not quite see what that reason is ..

What did I not do correctly this time?  Any suggestions welcome.

---

### Post by expatCM on 2011-02-24
I have now run dpkg -s cupsys and the output says that everything is fine.  Could this problem be something to do with groups?  But why can the cupsd.conf file not be read... ?

---

### Post by expatCM on 2011-02-25
I made a typo that was hard to spot but good enough to stop the show.

---

