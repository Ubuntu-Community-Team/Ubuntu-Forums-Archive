---
title: "GPG passphrase store on keyring"
date: 2009-02-08
forum: Security
---

### Post by ushills on 2009-02-08
Is there a way to have my GPG secret key passphrase unlocked on logging in as a user.  There is no option currently to remember the passphrase and add it to my gnome keyring.

I use this for enigmail, however, not all users can be bothered to enter another password to sign email.  I do not want a password free signing key however.  I would be willing to accept the same passphrase as my login passphrase.

---

### Post by argie on 2009-02-08
I don't know if this works under 7.10, but I'll tell you what works under 8.04, it may help. 

1. Go to System » Preferences » Encryption and Keyrings (the program is seahorse-preferences, I recall that Seahorse is installable under 7.04)
2. Go to the PGP Passphrases tab.
3. Select 'Always remember passphrases whenever logged in'
4. Deselect 'Ask me before using a cached passphrase'.

You will have to enter your passphrase one time (the first time you try to decipher a PGP message or file) and on subsequent logins and attempts to use the key you will not be prompted.

---

### Post by ushills on 2009-02-08
i tried this but it didn't appear to work between logins. Should it?

---

### Post by argie on 2009-02-12
It should. On my Ubuntu 8.04.2 system, I have been able to take the keys out (I store them on a USB drive), shut down the computer, put it on many days later with the keys on the drive and I will still be able to use the cached passphrase (I simply have to click 'Authorize' because I have that setting marked).

Perhaps you should report this as a bug.

---

