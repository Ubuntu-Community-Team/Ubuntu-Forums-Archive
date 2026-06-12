---
title: "Keyrings in Hardy not using /etc/shadow"
date: 2008-05-08
forum: Security
---

### Post by ilrudie on 2008-05-08
This is not a critical problem but rather a curious behavior I found under Hardy.

Encryption and Keyrings does not use my user's /etc/shadow password to unlock my keyring.  Is this a known problem with Keyrings in Hardy, a problem with my settings or is this how it is supposed to work?

The problem started when I changed my users password to match my active directory credentials which I am required to change monthly.  I first used the GUI under System>Administration>Users and Groups.  I noticed that my new password would not unlock my keyrings.  I then used 'sudo passwd <username>' to change my password from the command line.  Keyrings still uses my old password to unlock.  I am able to change it manually from the keyrings screen but I wanted to know if this was intentional or not.

Thanks

---

### Post by antikristian on 2009-04-27
Unfortunately I belive it's intentional, so the easiest way to circumvent it is to disable the keyring password (not a great solution) 

I recommend filing a bug report about it, because it is a usability issue.

I think the best way to implement this would be to use PAM to unlock the keyring (with either the users password, fingerprint, or other pam module) or getting a dialog to change the keyring password once the users password gets changed.

The current implementation is probably a bit safer than using /etc/shadow though, for instance if you store personal passwords in the keyring on a shared machine at school or work, the administrator would not be able to change your password and read your stored passwords.

---

