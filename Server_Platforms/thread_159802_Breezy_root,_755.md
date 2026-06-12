---
title: "Breezy: /root, 755?"
date: 2006-04-13
forum: Server Platforms
---

### Post by Teo on 2006-04-13
Ubuntu Breezy 5.10.
Just after installation on a clean partition: permissions to folder /root are set to 755 :o.

It's root's folder, it should have 750!

---

### Post by Derek Djons on 2006-04-13
I think that's correct. If you take a look in the properties you'll see that the **OWNER** has the 775 permissons. Since the owner is ROOT every other user and even group related user won't be able to **Write**, only read and execute.

---

### Post by Teo on 2006-04-13
[QUOTE=Derek Djons]I think that's correct. If you take a look in the properties you'll see that the **OWNER** has the 775 permissons. Since the owner is ROOT every other user and even group related user won't be able to **Write**, only read and execute.[/QUOTE]
That's correct users can't write to /root - but users **should not** be allowed to read /root either.

It's not so importnant for a desktop system, but for server or multi-user workstation is essential.

ps. FC5 for example - 750 for /root.

---

### Post by ubernoob on 2006-04-14
I agree with teo. And I have been thinking of the same myself. I don't see any reason that users should have read access to /root as default. It seems like debian/ubuntu is the only distribution with 755 as default.

---

