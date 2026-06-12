---
title: "Ubuntu single application sudo password bypass"
date: 2009-10-29
forum: Security
---

### Post by mewrei on 2009-10-29
I just installed some security monitoring software that I'd like to have run in a screenlet, but I'm trying to figure out the best way to add my user account to the sudoers file so I can sudo one command without entering my credentials, but still have to authenticate for everything else.

---

### Post by Lars Noodén on 2009-10-30
You'll have to find the exact name of the application with it's full path and if it is being launched by kdesu, gksu, gksudo or something similar.  

The entry in sudoers will look vaguely like this, substitute the group adm for another group if you wish:

%adm ALL=(ALL) NOPASSWD: /bin/sh -c /usr/bin/zenmap ""


But be careful.  Keep a window open to the editor working on sudoers until you have verified that there are no errors in it.  Also be careful that you do not grant, accidentalyl, a backdoor into your system.  For example, allowing an arbitrary shell or allowing packages to be installed gives 100% access. :(

You can get hints about what to put in the sudoers by having a window or tab open in terminal and watching the output from .xsession-errors and auth.log while you try to use that application to test your sudoers configuration.

[INDENT][FONT="Courier New"]tail -f ~/.xsession-errors
sudo tail -f  /var/log/auth.log
[/FONT][/INDENT]

---

