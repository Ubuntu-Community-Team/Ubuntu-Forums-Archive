---
title: "Problem with Version 3.0.0 of Windows Client"
date: 2012-04-17
forum: Ubuntu One (CLOSED)
---

### Post by Dreigo42 on 2012-04-17
I just updated my Ubuntu One Windows Client to the new version and upon starting it, it says "Sorry, an error has occurred and Ubuntu One needs to close" with "---------------------------
Ubuntu One experienced an error
---------------------------
Sorry, an error has occurred and Ubuntu One needs to close.
---------------------------
Close   Hide Details...   
---------------------------
"Copied from the details.

Has anybody else had this problem? While I'm at it, the only reason I use the Windows Client is that my schoolwork requires specific software and I use it to keep a backup but now it isn't backing up.

---

### Post by ianp5a on 2012-04-19
I just upgraded my Windows UO client when prompted, a few days ago. No error messages. And now it will not start. Windows 7 64bit

---

### Post by ianp5a on 2012-04-19
An uninstall followed by a clean install solved my problem.
I should have known. I'd forgotten that was the usual solution on Windows.

Anyway, my tip is to first panic, and post the problem here, before trying out all the alternatives.

---

### Post by rabbitoid on 2012-04-20
I have a similar problem, clean install didn't help.
- I have Windows (yuck) xp
- had installed: ubuntu one, 2.0.3
- I could enter my login, but it never synced because of the firewall, so I uninstalled it. 
- removed any files containing "ubuntu" from the system

- tried to install 3.0.0. it installs (without asking) in C:\Program Files\ubuntuone. Then - nothing. No sign-in window. The window task manager has no ubuntu tasks, nothing in the system tray.

- reboot: now I have the "U" in the tray, I have 3 processes: 
  ubuntuone-control-panel-qt.exe
  ubuntuone-syncdaemon.exe
  ubuntu-sso-login.exe

still no sign of an IHM. right click on the "U" has only "restore" which has no effect and "quit". Not very helpful :(

try to launch any of the execs in C:\Program Files\ubuntuone\dist: nothing, exits at once

Help please?

---

### Post by berksted on 2012-04-26
Any solutions so far? I've found a few bug reports on the errors I have been getting but so far I've got the same problem.

I tried uninstalling and installing a few times but it's not connecting still. Right now just getting a python dll error on start up.

Perhaps it might be best to go back to the previous version as that one seemed to have worked.

---

