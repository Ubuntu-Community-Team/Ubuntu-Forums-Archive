---
title: "Secure Deletion"
date: 2009-07-04
forum: Security
---

### Post by SoftwareExplorer on 2009-07-04
Is running ```
cat /dev/urandom > bigfiledeletemewhenurunoutofroom
``` a way to securely delete files without haveing to destroy all the data on a hard disk?

---

### Post by HermanAB on 2009-07-05
The only way to securely delete files, is to encrypt the disk drive with LUKS AES256 and when you want to delete it, forget the key.

---

### Post by Agent ME on 2009-07-05
> **HermanAB said:**
> The only way to securely delete files, is to encrypt the disk drive with LUKS AES256 and when you want to delete it, forget the key.
This is wrong.
There are ways to overwrite files, such as with the shred command.

Back to SoftwareExplorer's question on how to erase the "empty" space, I think that method would work. I've seen utilities I can't remember the name of that are built to erase empty space, but they essentially did the same thing.

You could also read from "/dev/zero" instead of "/dev/urandom" if using urandom goes too slow. (Chances are the chokepoint will be your HD access speed and not your cpu.)

---

### Post by Trebaruna on 2009-07-05
Please do not forget to take your filesystem into account. If yours does journalling, chances are it is very difficult/impossible to properly remove all traces of a file. I'm not quite sure at which point this becomes an issue; certainly modes where the blocks to be written to disk are first committed to the journal will cause problems.

---

### Post by HermanAB on 2009-07-05
It depends on your threat level.

If your threat is your little kid sister, then by all means use shred or similar.

---

