---
title: "import public PGP Key which is my secret Key"
date: 2010-10-18
forum: Security
---

### Post by ka3sem on 2010-10-18
Hi,

I have an encrypted document (with my key) which I should decrypt.
After the generation of my key, my computer is formated and new reinstalled.

Now GnuPG find my key public and I can't use it for decryption!

Do you have a solution for me please? It's very important !!!


thanks for help

---

### Post by FuturePilot on 2010-10-18
Are you saying you did a reinstall and you didn't backup your key? If that's the case there's really nothing you can do unless you have a backup of it somewhere.

---

### Post by Agent ME on 2010-10-18
You need your private key to decrypt.

---

### Post by rookcifer on 2010-10-18
> **ka3sem said:**
> Hi,

I have an encrypted document (with my key) which I should decrypt.
After the generation of my key, my computer is formated and new reinstalled.

Now GnuPG find my key public and I can't use it for decryption!

Where did it find it?  If you didn't backup your entire key (the .gnupg folder) then you are out of luck.

---

### Post by ka3sem on 2010-10-19
I have saved my key in my email before the reinstall and I know its password.
Now, this key have 2 IDs; one is for a public key an the other is for the subkey which is secret.
The document which I have is encrypted with the subkey.
When I try a decryption, I receive: "gpg: secret key not available" :confused:

---

### Post by ka3sem on 2010-10-19
my key is now like an imported key from an other system. How can I import my own secret key?

What's a keyring please?

---

### Post by anomie on 2010-10-20
gpg(1) uses the --import option for both public and private keys, e.g.: 
```
$ gpg --import key_file_here
```

Note that it's a fairly bad idea to send your private key over (clear text) email and/or keep a copy of it on a mail server (!).

---

### Post by rookcifer on 2010-10-21
> **anomie said:**
> gpg(1) uses the --import option for both public and private keys, e.g.: 
```
$ gpg --import key_file_here
```

Note that it's a fairly bad idea to send your private key over (clear text) email and/or keep a copy of it on a mail server (!).

Well the private key is usually itself encrypted so that shouldn't be an issue.

---

### Post by anomie on 2010-10-21
[QUOTE=rookcifer]Well the private key is usually itself encrypted so that shouldn't be an issue.[/QUOTE]

I think we've disagreed on a similar point before. ;) 

With respect to OP, the calibre of his posts leads me to (perhaps unfairly) suspect that his private key passphrase may be less than stellar. Seems like an unnecessary risk to be shipping the private key around clear text.

---

### Post by rookcifer on 2010-10-22
> **anomie said:**
> I think we've disagreed on a similar point before. ;) 

Well, it is encrypted.  That's what the passphrase to unlock the key is for -- it decrypts the key itself.  (The default cipher used to encrypt the key is CAST5, according to the GPG documentation).  It's the same with SSH keys.  However, with SSH you can choose not to use a passphrase, which means you have to be very careful not to let an adversary have at the private key since it will be trivial to use it to decrypt everything encrypted with the public key.

---

### Post by anomie on 2010-10-22
Agree completely that it's encrypted. Disagree that it's a non-issue to pass around the private key clear text (particularly when many apps - GnuPG included - do not enforce passphrase strength). 

I just don't want OP to look at this thread and get the impression that a private key does not need to be safeguarded. The reality - IMO - is that not everyone uses a suitably strong passphrase like you do (rookcifer).

---

