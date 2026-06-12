---
title: "encrypted file server with read-write multiple acces at the same time"
date: 2009-09-14
forum: Security
---

### Post by nlz on 2009-09-14
I work for a media development NGO. Currently our shared network drive holds all our documents. Quite some of them are sensitive and in my opinion the drive should be encrypted. The only problem is that when I would encrypt it with truecrypt, only one person can access it with read and write acces and the other only with read-only.

The server is hosted by a ICT firm which shouldn't be able to see the content.

What do you think would be a good solution? (and don't say: host our own fileserver)

---

### Post by fargle on 2009-11-10
I would look at using dm-crypt encryption instead - you can mount it once the system starts up using a passphrase, and then it's just a partition like any other, so I don't see what issues there would be with multiple users accessing the files.

An article like [[COLOR="Blue"]this[/COLOR]]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu") should get you started on the commands you'd need.

---

