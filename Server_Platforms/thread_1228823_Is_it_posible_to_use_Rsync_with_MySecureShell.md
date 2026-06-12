---
title: "Is it posible to use Rsync with MySecureShell?"
date: 2009-08-01
forum: Server Platforms
---

### Post by Traumadog on 2009-08-01
Hello!

I tried asking this question on the Security Forum without success, and I thought I'd try it over here to see if anyone had any ideas.

I'm currently using "MySecureShell" to limit user access to their home directories.

Question: Is is possible for users bound by "MySecureShell" to use "Rsync" to backup and/or synchronize their files from remote systems. To date, none of the attempts to do this have been successful. (Please note: "Rsync" works fine if the user is not bound by "MySecureShell")

Any help as to how to do this would be greatly appreciated.

Thanks in advance!

Traumadog

---

### Post by jwooton on 2009-08-22
I would love to know the answer to this also.

---

### Post by jwooton on 2009-11-27
FYI Traumadog... after searching a bit I discovered this isn't possible.

---

### Post by HermanAB on 2009-11-27
I have no idea what MySecureShell is...  The usual way to secure rsync is with ssh.  Read the rsync man page, it is all in there.

---

