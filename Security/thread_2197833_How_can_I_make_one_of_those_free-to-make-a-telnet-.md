---
title: "How can I make one of those free-to-make-a-telnet-account servers?"
date: 2014-01-05
forum: Security
---

### Post by tobias-richards on 2014-01-05
[COLOR=#000000][FONT=verdana]I've come across many telnet servers where I can type in the username, "new", and it walks me through the steps of creating a restricted account. How can I make my Ubuntu server do that? I can't figure out how to write a script that allows username "new" to create an account without exposing the "new" account to insecure privileges such that the user could CTRL+C out of new's logon script, and gain control of the system.

Surely there is a solution that I can apt-get, or at least download and build the tarball from source. The problem is that I can't find it.[/FONT][/COLOR]

---

### Post by houstonbofh on 2014-01-11
Make the "new" account have almost no privileges, and make the scripts suid root.  Also, make them executable but not readable...

However, this is still hackable, so monitor it carefully, and keep the logs on a different server.

---

