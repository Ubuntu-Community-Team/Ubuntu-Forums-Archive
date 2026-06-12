---
title: "&quot;Invalid Signature&quot; from my own PGP key in Evolution"
date: 2009-08-03
forum: Security
---

### Post by marshmallow1304 on 2009-08-03
I've been recently sending emails back and forth between my addresses to try to figure out some settings issues with one of my accounts.  In doing so, I noticed that when I receive one of my own emails in Evolution, it informs me that the email is signed with an "Invalid Signature".

When I look for more info, I get
> The signature of this message cannot be verified, it may have been altered in transit.
followed by
> gpg: armor header: Version: GnuPG v1.4.9 (GNU/Linux)
gpg: Signature made Mon 03 Aug 2009 12:56:57 AM EDT using DSA key ID 12345678
gpg: using PGP trust model
gpg: BAD signature from "My Name <my@email.com>"
gpg: binary signature, digest algorithm SHA1

I read somewhere that this can happen when the public key isn't in the keyring, but of course my own is.  Any ideas?


Edit:  When sending from one address to the sending address (itself) and to another address, the email received by the sending address shows a valid signature, but the email received by the other account shows an invalid signature.

---

### Post by sasho_zl on 2009-08-03
Maybe it's an issue with the way the account processes the message. Also check how the trust of your key is set with "**gpg --edit-key** name".

---

### Post by kevdog on 2009-08-03
If you verify or decrypt the file from the command line, do you get this error -- I'm just trying to see if its pgp/gpg or evolution throwing this error.

---

### Post by marshmallow1304 on 2009-08-03
> **sasho_zl said:**
> Maybe it's an issue with the way the account processes the message.
I wondered about that.  It's a school server and it has a more than a few things wrong with it (expired certificates and such).

> **sasho_zl said:**
> Also check how the trust of your key is set with "**gpg --edit-key** name".
trust: ultimate

---

### Post by sasho_zl on 2009-08-03
Probably the server is handling the mail in a way that is changing the hash.

---

