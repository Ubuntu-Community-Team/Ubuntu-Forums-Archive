---
title: "LTSP, rdesktop &amp; dialog boxes"
date: 2011-06-01
forum: Server Platforms
---

### Post by JoeyB63 on 2011-06-01
I'm currently running Ubuntu 10.04 LTSP server.

When running an rdesktop session on the clients, I've got XINITRC_PROMPT_ON_EXIT set to "True".  Within xinitrc I've got ldm-dialog --message "message text".  When rdesktop ends, the dialog box displays ok, but there's like a screenshot of the last thing on the screen behind it.  

This hasn't really been an issue (although it doesn't look very nice) but when using iTalc to lock the screen then unlock it, it still has a big padlock behind the message, so it looks like it's still locked.  Is there any way to blank the screen behind the dialog window?  I've tried using zenity instead of ldm-dialog but it has the same problem.  Does anyone know a solution to this?

Many thanks.

PS  I'm relatively new to this so please go easy on me O:)

---

