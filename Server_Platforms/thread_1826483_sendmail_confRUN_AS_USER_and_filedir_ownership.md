---
title: "sendmail confRUN_AS_USER and file/dir ownership"
date: 2011-08-16
forum: Server Platforms
---

### Post by cconstantine on 2011-08-16
I'm working with Sendmail and Cyrus (for the local delivery agent). I quickly ran into a problem with Sendmail refusing to hand incoming messages off to the LDA (cyrusv2 via LMTP). Sendmail insisted it didn't like the ownership on the Unix-domain socket that the Cyrus master process created.

I ended up changing Sendmail's confRUN_AS_USER setting in the sendmail.mc figuring I could just make Sendmail (the daemon instance serving as the MTA) run as the same user as Cyrus (the "cyrus" user.) Worked fine, and local mail delivery works.

But I now realize that the /etc/mail/Makefile file has built-in commands about lots of things being owned by the user "smmta". So when I "make" in /etc/mail files or directories change their ownership to "smmta".

So I'm trying to figure out how to properly (by which I mean, not futz my system to the point where I can't do updates of the Sendmail package) reconfigure the Sendmail MTA process to run as "cyrus". I looked at the shell scripts in /usr/share/sendmail and I was thinking maybe I could set DAEMON_UID in the /etc/mail/sendmail.conf but I'm out of my depth wrt the Ubuntu/Debian package and setup/config scripts.

Can anyone shed light? ...or even just asking me questions might help me dig deeper.

---

