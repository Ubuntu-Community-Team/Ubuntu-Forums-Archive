---
title: "How secure is gnome-keyring?"
date: 2008-04-26
forum: Security
---

### Post by crash369 on 2008-04-26
Hello all.  I have a couple of questions about gnome-keyring.

The data on my laptop are pretty unimportant, and as such, if someone were to gain access to it and peruse my system, I would be annoyed, but not threatened.  The only sensitive information that is stored on the laptop are my RSA private key as well as various passwords, which give me access to other machines.  These other machines DO contain sensitive information.

The private key is encrypted with a passphrase, which, from what I understand makes it secure and useless without said passphrase (please, please correct me if I am wrong).  This passphrase, along with other passwords (wpa-psks, etc) are kept by gnome-keyring.

So my questions are:
1. How secure is the gnome-keyring data if someone gains access to my laptop?
2. Can this data be copied and decrypted (to get plain-text passwords)?
3. Can it be copied and used in conjunction with my encrypted private key to gain access to the remote machines?
4. Would it matter if the attacker only had temporary access to my laptop (i.e. I went to the bathroom and left it unlocked) or actually had my ubuntu login password?

Any help would be appreciated.

---

### Post by Oldsoldier2003 on 2008-04-27
With physical access to your machine your entire key can be exported. However they would have to crack your passphrase in order to use it. This is a very good reason to never ever use a blank or weak passphrase for your keys.


Edit: I am assuming you are talking about your pgp key. Bottom line is use a good passphrase and you should be safe.

---

### Post by crash369 on 2008-04-27
So that's my question, if they have access to gnome-keyring data, do then need to crack my passphrase, or will the keyring give it to them?

p.s. - it's an SSH private key... don't know if that makes a difference.

---

### Post by Dr Small on 2008-04-27
Whether it is a OpenPGP key or a SSH key, the private key for both should require a password for added security. As OldSoldier stated, if they have physical access to your system, and your private key is weak or passwordless, then they can access it.

I am pretty sure that the keyring basically just organizes stuff. If they had access to the data, they would still have to crack the passphrases on the private keys to use them.

Dr Small

---

### Post by crash369 on 2008-04-27
I think there is confusion.  The issue is not whether to use a passphrase to encrypt a private key -- I have already encrypted it.  The issue is whether I should worry about gnome-keyring storing that passphrase.

---

### Post by jakupl on 2008-04-27
No. You will never find your passphrase on a text document anywhere.

---

