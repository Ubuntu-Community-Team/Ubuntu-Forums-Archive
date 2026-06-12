---
title: "Encryption tools &gt; What to use ?"
date: 2017-03-12
forum: Security
---

### Post by GeordieJedi on 2017-03-12
Hi there guys.

I've got an external HDD and I want to encrypt it.

What are the best (and possibly easiest) tools to do this please ?
preferably something with a GUI.

I've heard that TrueCrypt has been discontinued.
Is there anything else in the same vein ?

TIA for any help and advice.

---

### Post by TheFu on 2017-03-12
"Best" is highly subjective.  I'd use LUKS.  Don't know of any GUI for it, however.  Some file managers understand existing LUKS encrypted partitions and will offer to decrypt them.  Caja does this. Can't speak for any other file manager. I tend to script things, since GUIs don't work on servers 2,000 miles away.

I suppose people might use VeraCrypt (the replacement to truecrypt). The issue with veracrypt is a licensing problem. People need to decide for themselves if wrongly using truecrypt as a base is legally/morally allowed.

---

### Post by kevdog on 2017-03-12
Veracrypt is multiplatform (Windows, Mac, Linux) and has a GUI.  I don't have any knowlege about the licensing issues.  It's pretty easy to use. You need to make a decision about the type of encryption you want -- file level, directory level, partition level or whole disc level.  Once you kind of figure out what is best for you, then search for the appropriate tools.

---

### Post by HermanAB on 2017-03-13
+10 for LUKS.

---

