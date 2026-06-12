---
title: "Do not have access to admin rights"
date: 2009-05-11
forum: Security
---

### Post by e4xit on 2009-05-11
i know this question may sound like a repeat (but i have searched the forums resonably thoroughly and most threads seem to relate to older ubuntu distributions (i have jaunty i think), and get solved in updates.

Well my problem is that when i try to access System->Admin->Networking/users & groups there is a small button "Unlock" whihc you need to press to unlock the settings, when i press this it says: "Could Not Authenticate, an unexpected error has returned"

i see some threads say this may mean my user is not an admin, so i checked in console with ```
$ groups
```and it says i am in admin (amongst others)

```
will@elvyn-250-174:~$ groups
will adm dialout cdrom audio plugdev lpadmin admin sambashare
will@elvyn-250-174:~$ sudo adduser will admin
[sudo] password for will: 
The user `will' is already a member of `admin'.
```any help appreciated....i am pretty new to linux so be nice! ;) (Basically i have just spend 5 days reading solid forums, that is the extent of my knowledge!)

also why can i not read/write/save files in /usr/local directories, i could before i reinstalled (should have been same as before!!!?!?!) am not bothered by security if that changes anything, just want to be ABLE to access everything on my comp as admin!

Thanks in advance...

Will

---

### Post by cdenley on 2009-05-11
Post the output from this command.
```

sudo grep ^[^#]. /etc/sudoers

```

Have you upgraded recently? If so, have you rebooted since?

---

### Post by shadowlemon on 2009-05-18
strange... sounds like %admin isn't configured in /etc/sudoers

---

