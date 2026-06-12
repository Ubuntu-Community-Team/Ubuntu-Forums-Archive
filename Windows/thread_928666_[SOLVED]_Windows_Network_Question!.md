---
title: "[SOLVED] Windows Network Question!"
date: 2008-09-24
forum: Windows
---

### Post by Rytron on 2008-09-24
Hi,
I have set up an xp pc to join a domain via a server 2003 machine.
However the xp pc is now no longer connected to the server 2003 pc. How can I remove the log on to network1 domain that was set via server 2003?
Thanks.

---

### Post by Battie on 2008-09-24
Right click on My Computer and go to Properties, then to the Computer Name tab.  Click Change and select Workgroup instead of Domain.  It doesn't matter what you put in the Workgroup field unless you actually are trying to create one.  It will request a username and password to join but you don't need one.  Reboot when asked and you're good to go.

Just remember that you won't be able to log into any network account that you'd previously used on that computer.

---

