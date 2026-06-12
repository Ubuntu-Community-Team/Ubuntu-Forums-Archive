---
title: "Gaim save passwords in plain text"
date: 2007-01-12
forum: Server Platforms
---

### Post by DuckMan on 2007-01-12
/home/USERNAME/.gaim/accounts.xml

gaim is saving passwords in plain text?! :| WTF?!

---

### Post by BitTorrentBuddha on 2007-01-12
Most files in your home file that need to be kept private usually are set so only the owner (you) and the superuser (root) can view them.

---

### Post by PetePete on 2007-01-12
even so, its still not very good practise to store passwords in plain text 

glad i dont use gaim :D

---

### Post by pstewart on 2007-01-12
You can always choose not to save the password if you like.

Gaim writes to the accounts.xml file every so often while it's running, so encryption would be a real pain. You should be the only user (other than root) with access to the file. If other users can access your files and you don't trust them, you shouldn't be storing sensitive information there anyway.

There's a better explanation [here]("http://gaim.sourceforge.net/plaintextpasswords.php").

---

