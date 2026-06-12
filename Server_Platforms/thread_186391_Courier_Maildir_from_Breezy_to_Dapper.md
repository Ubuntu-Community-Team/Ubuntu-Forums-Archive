---
title: "Courier Maildir from Breezy to Dapper"
date: 2006-06-01
forum: Server Platforms
---

### Post by jfdill_2 on 2006-06-01
I restored a Courier Maildir directory from a backup of a system that was running Breezy to a system that is running Dapper, but there seem to be changes in the handling of ACLs between the versions of Courier in Breezy vs. Dapper.  The folders show up in Thunderbird and are "subscribed" but when I try to access a folder I get:

```
Jun  1 22:20:10 localhost imaplogin: Error reading ACLs for INBOX.CARB.02Carb: No such file or directory
```

MAILDIR="Maildir" and MAILDIRPATH="Maildir" I have hashed and rehashed and that is definitely not the problem.  Has anyone else encountered this problem and found a workaround?  Or perhaps some tool to convert Courier Maildir to some other format that doesn't care about ACLs?

Edit: I just found this courier2dovecot script that might work:

[http://bendiken.net/2005/11/03/courier-imap-to-dovecot-migration-script](http://bendiken.net/2005/11/03/courier-imap-to-dovecot-migration-script)

Ultimately, I am probably just going to use Evolution and add it as a regular Maildir folder as it's basically old archived mail.

Update:  Yay it worked!  Here's the drill:

1. run courier2dovecot to convert Maildir to dovecot format
2. apt-get --purge courier-base
3. apt-get install dovecot-imap
4. add protocols = imap to /etc/dovecot/dovecot.conf
5. /etc/init.d/dovecot start
6. now I can read my old e-mails again!

---

