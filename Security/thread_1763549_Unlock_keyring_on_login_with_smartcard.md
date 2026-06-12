---
title: "Unlock keyring on login with smartcard?"
date: 2011-05-20
forum: Security
---

### Post by bpeyser on 2011-05-20
I have managed to get smartcard authentication working on my 64b Ubuntu Maverick installation. What I would like to do is log in with my smartcard, and have my keyring unlocked without also entering my password.

Currently, I can log in using my smartcard (or username/password if I don't have it, for now), but then I have to enter my password to unlock the keyring. Is there some way to get the keyring unlocked at login when using a smartcard? I have pam_pkcs11.so listed in /etc/pam.d/common.auth and it seems to work well, except for the keyring.

Does anyone know how I can set this up?

---

### Post by bpeyser on 2011-05-24
I think this is planned for gnome-keyring but not yet available:

[http://live.gnome.org/GnomeKeyring/Goals#Goal:_Common_Storage_of_Passwords](http://live.gnome.org/GnomeKeyring/Goals#Goal:_Common_Storage_of_Passwords)

If anyone knows a hack to make this work would be great, but looks like I will still have to use a crummy password.

---

