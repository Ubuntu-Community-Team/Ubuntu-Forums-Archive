---
title: "simple file encryption"
date: 2007-01-22
forum: Server Platforms
---

### Post by Sniper99 on 2007-01-22
hi, im sort of new at linux, but i do have enough experience to understand basically wut is going on....i have this really nice file encryption engine on my windows, its called like Piccrypt, and it works by encrypting files into bitmap images using blowfish encryption, so first off, i was wondering, what are my options for a free file encrypter, maybe even one just like the one that i have, second, wut is a fairly high encryption......i dont know if its different on ubuntu 6.06, just a question

---

### Post by jtc on 2007-01-22
I'd recommended gpg (gnupg), which is more or less almost some kind of standard in the Linuxworld. It won't generate any bitmaps, but the encryption is good. It is most commonly used as asymmetric encryption (public keys, etc), but you can also use it with symmetric encryption and a password.

If you want a GUI to it I'd recommend kgpg in kde and seahorse in gnome.

---

### Post by PurplePenguin on 2007-01-22
There's also a program called steghide (I believe) that will hide messages in photos.  I played around with it a year or so ago... pretty cool, although not the kind of thing that you'd find yourself using very often. 

Unless you're in some really cool line of work. ;)

---

