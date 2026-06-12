---
title: "ejabberd stopped working"
date: 2006-08-26
forum: Server Platforms
---

### Post by henrrrik on 2006-08-26
My ejabberd installation stopped working sometime after the 16th of August. 
The node doesn't start properly, but it doesn't log anything so I can't tell what's broken. 
Anyone else have problems?

---

### Post by Woei on 2006-08-26
> **henrrrik said:**
> My ejabberd installation stopped working sometime after the 16th of August. 
The node doesn't start properly, but it doesn't log anything so I can't tell what's broken. 
Anyone else have problems?

I don't run a jabber server, but I'd be very surprised a daemon like that doesn't hold logs somewhere in /var/log or wherever it's configured to log things. Check the configuration files for a stanza about logging. If all else fails, start the program manually, prepending it with 'strace'. Strace is a utility that will print all the system calls a program makes. If it's hanging on something, paste it here, so we'll have a better chance of finding what's wrong with ejabberd all of sudden.

---

### Post by henrrrik on 2006-08-27
> **Woei said:**
> I don't run a jabber server, but I'd be very surprised a daemon like that doesn't hold logs somewhere in /var/log or wherever it's configured to log things. Check the configuration files for a stanza about logging. If all else fails, start the program manually, prepending it with 'strace'. Strace is a utility that will print all the system calls a program makes. If it's hanging on something, paste it here, so we'll have a better chance of finding what's wrong with ejabberd all of sudden.

I messed around with it a bit and apparently there was a problem with /etc/init.d/ejabberd. Starting /usr/sbin/ejabberd manually worked fine. 
I had some stuff added to it to support federation with Google Talk, perhaps that was causing the problem.
I ended up backing up my config files and purged and re-installed it. Works now.

---

