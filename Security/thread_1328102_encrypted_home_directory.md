---
title: "encrypted home directory"
date: 2009-11-16
forum: Security
---

### Post by spirosdenaxas on 2009-11-16
Hello,

during setup (9.10 server), I chose to have the home directory of the main user encrypted. Truly, this does happen as i can see it when running mount that the fs is ecryptfs. 

However I am getting increasingly worried as I don't recall choosing a password and I am unsure what passphrase is used for encryption. I would like to be able to know what is used so I can back it up safely. I have tried reading the documentation and most of it refers on making a new directory encrypted and now during the main setup.

any help would be much appreciated.

thanks
S.


-- EDIT --

passphrase can be retrieved using ecryptfs-unwrap-passphrase

---

### Post by HermanAB on 2009-11-16
The password is not saved anywhere.  What is saved is a hash of the password.  Therefore the password cannot be retrieved.

Soooooo, you need to back-up your data since you will lose it on a reboot!

Next time, write it down and keep it in your wallet.

---

### Post by spirosdenaxas on 2009-12-06
> **HermanAB said:**
> 
Next time, write it down and keep it in your wallet.

Write one down? As I mentioned, it was not mentioned anywhere.

Spiros

---

### Post by paradigm2 on 2009-12-06
The documentation for the encryption is confusing because it is hard to know what is for 8.10, 9.04, or 9.10.  They all have significant differences.  It would be nice to get a updated set of docs for 9.10 only.  Does anyone have a link to this?

---

### Post by Penguinsunite on 2009-12-08
there is another way. since the password is stored as a hash value, you can google a program to recieve the hash values and therefore retrieve your password.

---

### Post by Dr Small on 2009-12-10
Probably, most likely, the passphrase for your encrypted home is the same as your account password, since you did not have to enter a specificly different password to decrypt your home.

---

