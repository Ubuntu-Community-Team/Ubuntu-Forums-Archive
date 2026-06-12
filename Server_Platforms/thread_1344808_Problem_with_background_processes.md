---
title: "Problem with background processes"
date: 2009-12-03
forum: Server Platforms
---

### Post by guessswh0 on 2009-12-03
So I seem to be having a weird issue.  I have a ubuntu 9.04 server setup.  I am trying to setup a bnc (IRC Bouncer) within the user account's shell.  It complied fine, and everything is good.  I can get it to execute no problem.

WHat will happen is it will run for maybe 5 seconds, then when i type "ps" to make sure it is running, it isn't.

The program is designed to run in the background, and will specifically say it was launched with XXX as the pid in the background.  If I do a "ps" immediately after launching it, I will see it in the background, but if I wait 5 seconds and do it again, it is no longer in the background.

Any suggestions, or some setting I might need to have set on the server?

Thanks for the help

---

