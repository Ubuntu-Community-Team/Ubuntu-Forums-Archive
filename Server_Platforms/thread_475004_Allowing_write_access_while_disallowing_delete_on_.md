---
title: "Allowing write access while disallowing delete on FTP"
date: 2007-06-15
forum: Server Platforms
---

### Post by zakusage on 2007-06-15
I've set up an FTP server in my basement with a directory that I've shared across multiple accounts by mounting /var/ftp/shared to ~/shared in each newly made account. Right now it's being used as sort of a collaborative place to store things, and I would like everyone with an account to be able to add things. What I wouldn't like, however, is if someone abused these powers and deleted most if not all the things in there. I'm really only allowing access to people I trust, but still I've learned better than to trust in people. 

Is there any way to allow write access but disallow the ability to delete things?

---

### Post by craigp84 on 2007-06-15
Hi zakusage,

> Is there any way to allow write access but disallow the ability to delete things?

There certainly is. Create your incoming directory as normal, allow your users write access (doesn't matter if they're all anonymous sharing the same id or authenitcated users with their own accounts) as you normally would.

The trick is to create an extra account, say ftp_ro, and have your ftpd chown files to the ftp_ro user and chmod 644 the files. This way everyone can still read, but noone can delete.

So for vsftpd, the configuration lines are:

```
chown_uploads=YES
chown_username=ftp_ro
```

Hope this helps,

-c

---

