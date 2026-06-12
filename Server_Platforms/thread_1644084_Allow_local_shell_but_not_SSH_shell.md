---
title: "Allow local shell but not SSH shell"
date: 2010-12-12
forum: Server Platforms
---

### Post by SRTS on 2010-12-12
SFTPD is available for certain allowed users, except they don't get a shell, so far so good.
Now the side effect is, that SSHD must be running for SFTPD to work. Now all (non-SFTPD) users could potentially login via SSH instead of just locally in front of the machine.
How can I prevent SSH remote login for everyone (except for the SFTPD users), so they can only login when they are in fact in front of the PC?

Oh also is it "PermitRootLogin no" or "AllowRootLogin no"? Seems different websites use one or the other.

Meanwhile I found out more:
in sshd_config, typical for linux, various things just do not work as many internet sites claim:
DenyGroups does not work with a '!' to negate, for example
DenyGroups !somegroup
DenyUsers does not work with komma. You need 1 line for each user.
DenyUsers someone,someonelse  <- will NOT work!
AllowUsers similarly doesn't work in that way.
I'm using openssh v5.xxx

So, I solved the problem by just adding a DenyUsers line for everyone. thx

---

### Post by papibe on 2010-12-13
Check this out: [How to restrict users to SFTP only instead of SSH]("http://www.debian-administration.org/articles/94").

---

### Post by SRTS on 2010-12-13
> **papibe said:**
> Check this out: [How to restrict users to SFTP only instead of SSH]("http://www.debian-administration.org/articles/94").

Um thanks, but won't this actually also prevent all local login too if I remove their shells, so they cant login at ALL anymore?

---

### Post by papibe on 2010-12-15
> **SRTS said:**
> ... so they cant login at ALL anymore?

They can't. It seems the best solution would be a compromise. Like removing all ssh access to the users, and creating special users that can only sftp to the server. This article explains it in detail:

[How do I allow a user to use scp or sftp, but not allow regular ssh.]("http://www.snailbook.com/faq/restricted-scp.auto.html")

I hope it helps.

---

