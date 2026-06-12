---
title: "Problem with thunderbird and GNUPG / OpenPGP decryption"
date: 2009-09-13
forum: Security
---

### Post by T.lancer on 2009-09-13
hi, I have recently migrated a PC from SUSE to Ubuntu and I am having some difficulty with decrypting emails in thunderbird using OpenPGP / GNUPG

first I had some permission problems with the config file.  But that seems to be working now.

I have the list of keys and that's all correct as well.


Now when I try to decrypt an email I get the following error message:

```
gpg command line and output:
/usr/bin/gpg --charset utf8  --batch --no-tty --status-fd 2 --keyserver-options auto-key-retrieve --keyserver pool.sks-keyservers.net, subkeys.pgp.net, pgp.mit.edu, ldap://certserver.pgp.com -d --use-agent 
usage: gpg [options] [filename]
```

anyone got any idea what the problem is?



ok, I removed the keyservers and tried to decrypt an email and it worked!

Problem solved.

---

