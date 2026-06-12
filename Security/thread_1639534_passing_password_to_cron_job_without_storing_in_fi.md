---
title: "passing password to cron job without storing in file"
date: 2010-12-06
forum: Security
---

### Post by timotheus2 on 2010-12-06
I run Ubuntu Server 10.10.

I have an application (Duplicity) that takes an environment variable on the command line to specify the password/passphrase to use for running.

In a Bash shell, I can do the following to manually run the application one time without revealing the password via 'ps' or storing the password in a file:

```
# unset HISTFILE; \
PASSPHRASE=mypass duplicity --encrypt-key="XXXXXXXX" /etc ssh://backuphost/backups; \
exit;

```My question is: what tool or method can I use to run duplicity as a cron job such that the password is never stored anywhere except in memory; including, not in a shell script?

Ideally, I would have the cron job look like:

1 12 * * * root tell_env -run duplicity --encrypt-key="XXXXXXXX" /etc ssh://backuphost/backups

And on the command line, as root, I would run at my own convenience:
# unset HISTFILE; \
PASSPHRASE=mypass tell_env -daemon;
exit;

It seems that I will have to write my own C program; and that tell_env would have to check the UID and GID at startup to prevent one user from accessing another user's environment. Is there a tool in the Ubuntu repository that does exactly this?

I read somewhere on-line that if you use UNIX, OS Authentication is the method for this.

Thank you for any suggestions, including pointing me to a different mailing list or forum.

---

