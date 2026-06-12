---
title: "GPG always caches passphrase"
date: 2008-12-03
forum: Security
---

### Post by dethadol on 2008-12-03
I am using 8.04.

I have succesfully imported my  GPG keys, but when I decrypy a file GPG always caches the passphrase even though I have st the preferences to "never remember passphrases".

How can I prevent GPG from caching the passphrase?

---

### Post by kevdog on 2008-12-04
Can you give more details on this and where you modified your preferences?  I am unfamiliar with the option you are talking about.

---

### Post by dethadol on 2008-12-09
Kevdog, thanks for the interest.

I have always used Kgpg in another distro (mandriva) so when I came to Ubuntu I imported my public and private keys into Seahorse. This works fine and I can decrypt all the stuff I had previously encrypted in Mandriva and also encrypt and decrypt new stuff.

However, when I decrypt something Seahorse caches my passphrase in memory and will subsequently decrypt anything without me entering the passphrase, I would prefer not to have my passphrase available like this as I see it as a security risk.

Under Seahorse > Edit > Preferences > Passwords and Encryption keys there is an option - Never remember passphrase, I have this selected but it appearsc not to work. I would like to find a way to disable remembering passphrase.

---

### Post by tubbygweilo on 2008-12-09
System > Preferences > Encryption and Keyrings > PGP PassPhrase may be another way to achieve the result you are seeking.

---

### Post by kevdog on 2008-12-09
That sounds like a option specific to seahorse.  I don't use seahorse but rather gpg on command line or through the firegpg interface.

---

### Post by dethadol on 2008-12-09
Tubbygweilo

I'm afraid that didn't work either

Kevdog

Bavk to the command line as you suggested.


Thanks to both of you

---

### Post by 54de4vg on 2009-01-14
I'm using seahorse, and I've got the same problem.  I've gone to the system > preferences > encryption and keyrings settings area.  I have always used the "never remember passphrases option, but once I enter the passphrase, it is remembered for as long as I am booted up.  I'm about to try the setting which says, "remember passphrases for [x] minutes" with x=1 minute.  Hopefully that will at least limit the passphrase being cached.  This is a real bug that needs a solution.

---

### Post by sanximb on 2009-03-12
Go to System -> Preferences -> Encryption and Keyrings and check the option at the bottom that says "Show icon in status area . . .". That way when you enter the password an icon shows up that you can right-click and clear the cache with.

---

