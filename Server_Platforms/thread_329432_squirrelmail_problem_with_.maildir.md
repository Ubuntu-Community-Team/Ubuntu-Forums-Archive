---
title: "squirrelmail problem with .maildir"
date: 2007-01-01
forum: Server Platforms
---

### Post by mcmanus on 2007-01-01
Hey y'all,

I've got another slight problem.  I've been migrating all the services from my old Gentoo box to my new Ubuntu dapper 6.06.1 server box, and I've hit a little snag with squirrelmail.

My old server has postfix & courier-imap setup to use ~/.maildir as the maildir folder.  It seems like no matter what I do, I can't get squirrelmail on the new server to use ~/.maildir, it insists on using ~/Maildir.  While simply recreating symlinks for every user isn't hard to do, is there a more elegant fix for this in squirrelmail?  I looked at /usr/share/docs/squirrelmail/presets.txt.gz for all the different options, but I didn't see anything related.  Any ideas/tips would be greatly appreciated!  Thanks!!

---

### Post by linuchsan on 2007-01-01
Look at the Default IMAP folder prefix section in your squirrelmail config file.

---

### Post by MJN on 2007-01-01
Run conf.pl in {squirrelmail directory}/config/ and set the prefix under **Folder Defaults **>** Default Folder Prefix**.

Mathew

---

### Post by mcmanus on 2007-01-01
No go, still doesn't work.  /var/log/mail.log still shows:

```
Jan  1 19:07:58 lothlorien imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jan  1 19:07:58 lothlorien imaplogin: chdir Maildir: No such file or directory
```

When I put my symlink back in, it can't access the folder list..  I get this error:

```
ERROR: Could not complete request.
Query: CREATE ".maildir/INBOX.Sent"
Reason Given: Invalid mailbox name.
```

---

### Post by MJN on 2007-01-02
What did you set the Default Folder Prefix to? (even better post the contents of {squirrelmail folder}/config/config.php)
 
Can you access your mailboxes okay with another e-mail client? (always a good idea to determine whether it's the IMAP server or client that's to blame). I assume you have told Courier to use ~/.maildir? (have you proved this to be working?)
 
Mathew

---

### Post by mcmanus on 2007-01-03
Currently, default folder prefix is set to '' and I've got Maildir symlinked to .maildir.  I've got postfix and courier-imap(-ssl) both pointing to ~/.maildir, and my fat clients can connect no problem (mutt, Mail.app, and Thunderbird).  squirrelmail works too, if I simply have the symlink in place.  I'll do a once-over on my config.php and paste it up here when I get a chance.

Thanks!

---

### Post by MJN on 2007-01-03
Okay, so definitely a SM issue then.
 
Any joy with setting the prefix to **~/.maildir/**   ?
 
Mathew

---

