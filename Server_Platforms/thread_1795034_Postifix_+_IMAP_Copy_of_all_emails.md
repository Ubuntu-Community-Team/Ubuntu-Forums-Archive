---
title: "Postifix + IMAP: Copy of all emails"
date: 2011-07-01
forum: Server Platforms
---

### Post by msavard on 2011-07-01
Hi all,

I have a server running Ubuntu 10.04 + Postfix + Webmin and I need to be able to make a copy of every mail received or sent from every account  before the owner of the account delete it.

Is there a way to do this ? 

Thanks

Marc

---

### Post by HermanAB on 2011-07-02
Postfix has an Always BCC feature.  

Go to postfix.org and read a bit.

---

### Post by SeijiSensei on 2011-07-02
For inbound messages, you could install [procmail]("http://www.procmail.org/") and create a file named "/home/user/.procmailrc" (note the leading dot) with the following "recipe":

```

:0c
/path/to/archive/folder

```

This places a copy of every delivered message in the file /path/to/archive/folder.  The user must have write permissions to the file.

If you want to archive every message for all users as they arrive, create a file called /etc/procmailrc instead with the same recipe.  Procmail processes that file (with root permissions) before it processes the .procmailrc files in the users' home directory.

(Why isn't procmail installed by default in Ubuntu?  What other mail delivery agent could possibly be preferred to the incredibly powerful procmail?)

Outbound is more difficult, though the "Always BCC" option Herman mentions sounds useful.

---

