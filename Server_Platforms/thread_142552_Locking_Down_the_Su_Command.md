---
title: "Locking Down the Su Command"
date: 2006-03-10
forum: Server Platforms
---

### Post by Eternal Blade on 2006-03-10
Hello, I've been trying to get it so only one group of users can su into root; the rest should not be able to.  I've read online that I have to edit /etc/pam.d/su and edit the setting in there.  I followed their directions and have attempted to lock down su, but failed.  After I do this the users can no longer get into Networking, Synaptic, and other services on the GUI even with the right password, but they are still able to go to a terminal and su into root.  Am I doing something wrong or does Ubuntu have things set up differently?

Thank you!

---

### Post by Zelut on 2006-03-10
Ubuntu uses the sudo command and it should be fairly easy to limit specific users access to super user access.

you can edit the 'sudo'ers using 'visudo' at the prompt.  Only users listed in that file will have access to use the sudo command (or you can limit users access to only certain commands when using sudo).  Hope that answers your question.  Let me know if you need more..

---

