---
title: "Test GPG passphrases?"
date: 2018-03-19
forum: Security
---

### Post by PDA1 on 2018-03-19
How can I test the gpg passphrases associated with various email addresses I have?  Such as, encrypt and then decrypt a file using command line that prompts me for the passphrase.

I *thought* I forgot all of my gpg passphrases but then remembered them.  Phew....

Thanks,

PDA1

---

### Post by TheFu on 2018-03-19
gpg isn't email-specific.  There are CLI tools that can be run in a shell against the gpg certs.   gpg, gpgv2, and gpg2. These tools let you query the cert for information, encrypt and decrypt files ... which is what email messages are.

---

### Post by PDA1 on 2018-03-19
Seahorse lists all of the passphrases relative to the email addresses I have.  I'd like to check them in some dynamic way.

---

### Post by TheFu on 2018-03-19
> **PDA1 said:**
> Seahorse lists all of the passphrases relative to the email addresses I have.  I'd like to check them in some dynamic way.

Sorry. I don't use seahorse.

---

