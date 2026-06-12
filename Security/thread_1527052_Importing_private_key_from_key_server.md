---
title: "Importing private key from key server"
date: 2010-07-08
forum: Security
---

### Post by ManiDhillon on 2010-07-08
Greetings friends!
I have this issue with which I want your help.
Recently I installed Ubuntu Lucid Lynx 10.04 x64 on my laptop and as usual copied my .gnupg folder from my backup hard disk to my home directory.
All my key configuration was back. Then I created a new key for my another email address and synced with key servers.
I, then had to re-install Ubuntu again and alas! I forget to backup my updated .gnupg folder.
Now my new key is on key servers and I want to import it but every time I import it, it is imported in public keys section.
Is there any way that I can import that key to my private keys?

P.S: I've posted this on gnuPG mailing list a month ago and got no response.

---

### Post by rookcifer on 2010-07-08
Key servers only store public keys for obvious reasons.  So, no, unless you made a backup of your entire keyring, you cannot get the private key back.  You will have to generate a new key.

This is why the GnuPG manual stresses the importance of backups.

---

### Post by ManiDhillon on 2010-07-08
Well that's a problem. Because then I'll have double keys on the keyservers. I think I should waie for the key to expire. It's just 7 month's wait. :)

---

### Post by anomie on 2010-07-09
Take it as a important lesson for the future: your encryption keys are *just as valuable* as your (encrypted) data. Without one, the other is useless. 

At least you were thoughtful enough to put an expiration date on your key pair.

---

### Post by ratcheer on 2010-07-09
Here is an excellent article I found on how to manage your keys:

[http://blogs.koolwal.net/2009/04/01/gpgpgp-part-5-backing-up-restoring-revoking-and-deleting-your-gpgpgp-keys-in-debian/](http://blogs.koolwal.net/2009/04/01/gpgpgp-part-5-backing-up-restoring-revoking-and-deleting-your-gpgpgp-keys-in-debian/)

Tim

---

### Post by ManiDhillon on 2010-07-09
> **anomie said:**
> Take it as a important lesson for the future: your encryption keys are *just as valuable* as your (encrypted) data. Without one, the other is useless. 

At least you were thoughtful enough to put an expiration date on your key pair.

I usually back up my gnupg folder after each week, but this time I forgot. Anyway thanks for your help and quick replies guys.

---

