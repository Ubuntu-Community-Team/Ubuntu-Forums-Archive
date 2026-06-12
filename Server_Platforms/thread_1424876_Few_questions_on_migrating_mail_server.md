---
title: "Few questions on migrating mail server"
date: 2010-03-08
forum: Server Platforms
---

### Post by kameleon25 on 2010-03-08
Hello,

     At my work we have a Fedora machine that does all of our mail currently and I need to migrate it off to a separate machine in the coming weeks. I am more familiar with ubuntu so I am looking to migrate it to an ubuntu xen VM. 

Here is what I have currently:
Fedora Core 11
Postfix
Dovecot w/ procmail
using LDAP for authentication
mbox format mail boxes
Majordomo

Would like to migrate to:
Ubuntu 8.04 (or wait till 10.04 comes out for the longer LTS)
Postfix
Dovecot w/ sieve
Must use existing LDAP (may actually move this to a separate machine also)
Maildir format mailboxes
Mailman

The reason for the move is due to several reasons. Mainly my predecessor thought it was a good idea to pile as many services on one box that is humanly possible. Also I need to migrate to the Maildir format so that my backuppc backups won't take as long since each message will be a separate file. And since Majordomo is no longer updated, I am looking at moving to Mailman or similar.

My main question is this: what would be the best way to migrate from the old mail server to the new one without losing any mail (we are a state agency and cannot delete any emails). We have about 160+ users across the state. All authenticate against our openLDAP service on the current mail server.

Thanks in advance for the help.

---

### Post by volkswagner on 2010-03-08
If you are currently using IMAP, bookmark this.  It has great tools for the migration when you are ready.

[http://www.athensfbc.com/imap_tools/](http://www.athensfbc.com/imap_tools/)

---

### Post by kameleon25 on 2010-03-08
Thanks for that link. Should that work if I don't know the users password though? That is the kicker. I could default everyones password but then they would have to change it adding a step. 

The biggest thing right now would be to move from the mbox to Maildir format.

---

