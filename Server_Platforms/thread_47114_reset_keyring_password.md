---
title: "reset keyring password?"
date: 2005-07-07
forum: Server Platforms
---

### Post by roots on 2005-07-07
hi....

something really silly happened just a few minutes ago: i tried to connect to some smb shares on a remote pc, i was asked for the smb password and if i want to store it  in the keyring file. i decided to do so, then i was asked to set a keyring password.
then it happened...i started typing the password, made a typo but at the same time i accidentally hit the touchpad and "managed" to confirm this incomplete and wrong password. very funny i thought, and up to now i tried quite a few combinations to find the "wrong password" but without success.

can anyone tell me where/how to set or reset the keyring password? i got root access so this shouldn't be the trouble...
um by the way...i'm using ubuntu 5.04.

thanks in advance!
.roots

p.s. a GREAT forum, many answers already found and very good howtos! keep it up!    ;-)

---

### Post by hp99 on 2006-02-03
hi,

open a shell and delete the file "default.keyring" in $HOME/.gnome2/keyrings/
you'll loose all the passwords but can set a new defaul.keyring password next time nautilus is asking you.
cheers,
gregor

---

