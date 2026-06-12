---
title: "dovecot failing in mbox-sync.c"
date: 2006-07-06
forum: Server Platforms
---

### Post by MoonWyrd on 2006-07-06
I'm seeing this error in the log when I try to check my email via imap:
> 
dovecot: imap-login: Login: user=<USER>, method=PLAIN, rip=#.#.#.#, lip=#.#.#.#, TLS
dovecot: imap(USER): file mbox-sync.c: line 1243 (mbox_sync_handle_eof_updates): assertion failed: (trailer_size <= 2)
dovecot: child 8301 (imap) killed with signal 6

Has anyone else come across this?  Any suggestions for a solution?

---

### Post by Glut on 2006-07-06
Your best bet may be the dovecot forums, although the debian(ubuntu) stable version is no longer the recommended version - so there may no be much support forthcoming.

---

### Post by MoonWyrd on 2006-07-08
going to answer my own question.  Turned out to be a file locking issue between dovecot and postfix.  The former was using dotlock and the latter flock.  This caused a small bit of corruption of a mail box which was the cause of the error.  Changing dovecot to flock and fixing up the corrupted file resolved the problem.

---

