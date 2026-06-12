---
title: "GPG - Gnome keyring cleartexts passphrase"
date: 2009-02-11
forum: Security
---

### Post by ushills on 2009-02-11
I use the gnome keyring manager to cache and unlock my gpg passphrase on login.  However, when looking under passwords and encryption > passwords > show password this password is shown in cleartext.

Can anyone confirm if it is stored in cleartext or how I can either hash this password so that it isn't so clearly available.

---

### Post by meho_r on 2009-02-11
I'd like to know that too. It seems that large part of security in Ubuntu rely on user login password and if it get compromised, the user is "compromised" too :) All passwords are visible, content of Private folder is accessible too. I'm not sure if it's a good idea that so much depends on user login pass.

Of course, one can change password in Seahorse to access other passwords and that they're not unlocked upon login but after entering that new pass. Still, it's pretty inconvenient.

---

### Post by lfaraone on 2010-02-26
> **ushills said:**
> I use the gnome keyring manager to cache and unlock my gpg passphrase on login.  However, when looking under passwords and encryption > passwords > show password this password is shown in cleartext.

Can anyone confirm if it is stored in cleartext or how I can either hash this password so that it isn't so clearly available.


See [http://live.gnome.org/GnomeKeyring/SecurityPhilosophy](http://live.gnome.org/GnomeKeyring/SecurityPhilosophy)

It is not stored in the clear, but it is displayed in the clear when you are authenticated.

---

### Post by Agent ME on 2010-02-27
If the password in your keyring was hashed, then it would be useless.

The point of a password keyring is to remember your passwords so that they can be used by other programs once you've logged in. This means that it's possible to read your passwords from your keyring (if you've logged in already with your own password) - that's the whole point of the keyring.

---

