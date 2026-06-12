---
title: "Upgrade or reinstall or fix issue? Version 12.04 Server"
date: 2014-04-03
forum: Server Platforms
---

### Post by Eric_Snyder on 2014-04-03
Ok...
I have 12.04 server running. I use the following:

GUI
Samba
Webmin
MySQL
Tomcat server

I do have some logical volumes with critical data.

I have been having issues with the GUI. If I let it sit for more than a day the the mouse clicking becomes unresponsive. Currently when I reboot most of the time I get a black screen after the process. I can ping and get all services off the server I just can't use the machine through the keyboard/mouse screen.

My question...Do I:

1) fix the issue?
2) Reinstall 12.04
3) Upgrade to a newer version?

Thoughts, opinions?

---

### Post by Catalys on 2014-04-03
At this state, upgrading will probably break more stuff. Before you do any of those, make a snapshot/backup of your data. You should try to fix the issue, and if you are 100% unable to fix it: Doing a clean install is probably your only option.

---

### Post by nerdtron on 2014-04-03
The mouse becomes unresponsive after a day doesn't necessarily mean you should reinstall.
Are there any processes that is taking up the server resources? Does the server use any swap?
You should investigate the services running on it like the sql or tomcat if there are any memory leaks.

---

