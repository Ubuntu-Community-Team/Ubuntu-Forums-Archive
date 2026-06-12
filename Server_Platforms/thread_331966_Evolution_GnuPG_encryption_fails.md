---
title: "Evolution GnuPG encryption fails"
date: 2007-01-05
forum: Server Platforms
---

### Post by Aleksandersen on 2007-01-05
Hi,

I get this error everytime I try and encrypt a e-mail message via Evolution with GnuPG.

> Could not create message.

Because "can't connect to `/home/aleksandersen/.gnome2/seahorse-PhWKvL/S.gpg-agent': Connection refused
gpg: can't connect to `/home/aleksandersen/.gnome2/seahorse-PhWKvL/S.gpg-agent': connect failed
gpg: writing to `-'
gpg: DSA/SHA1 signature from: "REMOVED-FROM-FORUM-POST Daniel Aleksandersen <REMOVED-FROM-FORUM-POST>"
", you may need to select different mail options.

---

### Post by pipes on 2007-02-12
Hi there, 

This occurs when the seahorse-daemon isn't loading correctly. You need to verify this is running....

pipes@sloane:~$ pgrep -fl seahorse
10133 /usr/bin/seahorse-daemon -d

If it isn't. loading the applications -> accessories -> encryption keys will restart the daemon.

---

### Post by Aleksandersen on 2007-02-12
It is running, because it works fine from KMail.

---

