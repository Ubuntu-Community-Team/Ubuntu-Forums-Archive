---
title: "Best encryption with GUI?"
date: 2014-02-01
forum: Security
---

### Post by grier-devon on 2014-02-01
So I want to encrypt a file or two in my cloud service and I am curious what is the best tool for creating a passphrase and encrypting a file? I don't mind command line if there is a good guide but would prefer something with a GUI. Thanks for any input.

---

### Post by TheFu on 2014-02-01
The list of CLI tools is nearly endless and "best" is highly, highly subjective.
Stay with tools that use well-know crypto methods. 
Avoid tools claiming _secrets_ ... or FIPS compliance.

You can encrypt with these - a few ideas to get started:
* gpg
* openssl (use *list-cipher-algorithms* option to see which cyphers are compiled in)
** AES in openssl
** Blowfish in openssl 
* Most password managers - keepassx uses AES - password managers aren't just for passwords.
* ZIP - brute force attacks against ZIP files is highly efficient, so extremely long passwords are required.
* gpg-zip - 
* Truecrypt - just setup the "container" to be the size you like.  Perhaps 650MB (CDROM-sized) for long-term cloud storage.

I would go with gpg, since it can be used with smart-cards and keys stored only on a smart-card. Don't have the card, the file cannot be encrypted.

Anyway, look for GUIs for those tools, if you must .... or easily create your own with Zenity.

---

### Post by grier-devon on 2014-02-02
Thanks so much for the information, that information is helping me find a good option.

---

