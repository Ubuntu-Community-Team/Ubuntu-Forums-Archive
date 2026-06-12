---
title: "fetchmail via ssh"
date: 2016-09-12
forum: Server Platforms
---

### Post by marchello_lippi2 on 2016-09-12
Hi all, 

I'm about to receive mail from my remote dovecot imap server using fetchmail via ssh. 

My .fetchmailrc file: 

```

poll hostname protocol imap: 
plugin "ssh %h /usr/sbin/dovecot"
     username "user1" password "pass1" mda "/usr/lib/dovecot/deliver -d user1" keep;

```

fetchmail command line output: 

```

$ fetchmail --fetchmailrc ~/.fetchmailm2 --fetchlimit 100 --nosyslog --nodetach -vvv
Old UID list from hostname: <empty>
Scratch list of UIDs: <empty>
fetchmail: 6.3.26 querying hostname (protocol IMAP) at Mon Sep 12 09:07:21 2016: poll started
fetchmail: running ssh %h /usr/sbin/dovecot (host hostname service imap)
**Fatal: open(/var/run/dovecot/master.pid) failed: Permission denied**
fetchmail: socket error while fetching from user1@hostname
fetchmail: 6.3.26 querying hostname (protocol IMAP) at Mon Sep 12 09:07:24 2016: poll completed
Merged UID list from hostname: <empty>
fetchmail: Query status=2 (SOCKET)
fetchmail: normal termination, status 2

```

Please advise. 
Thanks ahead.

---

### Post by howefield on 2016-09-12
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by marchello_lippi2 on 2016-09-20
It was my bad configuring of dovecot. Now it is resolved using this link 
[https://www.server-world.info/en/note?os=Ubuntu_14.04&p=mail&f=2](https://www.server-world.info/en/note?os=Ubuntu_14.04&p=mail&f=2)

---

