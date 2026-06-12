---
title: "Postfix local server sends bulk (spam) messages ?"
date: 2006-06-15
forum: Server Platforms
---

### Post by xpmaniac4ever on 2006-06-15
Hi. Today I installed Postfix mail server on my server and when I use it to send mails to any Yahoo account, they appear in the Bulk folder of the destination, where spam resides. Why does this happen and how can I prevent it ?

---

### Post by MJN on 2006-06-16
You really need to be asking Yahoo that - as it is they that have determined your messages are likely spam... but on what basis?
 
Not being familiar with Yahoo, does it not tell you *why* a particular message has been deemed suspect? Perhaps it adds an additional header to each message saying why/how it failed analysis? (try getting it to show you the full headers - perhaps another Yahoo user can tell you how if you're not sure).
 
Perhaps it's based on where the mail was sent from, e.g. a known dialup/broadband dynamic IP range... Are you? If so, try using your ISPs mail server as a relay using the Postix directive **relayhost = [***address.of.your.ISPs.mail.server***]**
 
Mathew

---

