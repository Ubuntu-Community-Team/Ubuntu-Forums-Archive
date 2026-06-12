---
title: "User homepages"
date: 2009-01-04
forum: Server Platforms
---

### Post by gypsumwolf on 2009-01-04
I am using Ubutnu Server Edition. How do I make it so each user has a 'www' folder in their home directory so they can build their own websites and host them from there?

---

### Post by cb951303 on 2009-01-04
type "sudo a2enmod userdir"
by default it enables "public_html" directory on every user's home directory but you can change it to www if you like.

After moving your files to /home/user/public_html, go to [http://localhost/~user](http://localhost/~user) and voila!

---

### Post by gypsumwolf on 2009-01-04
Thanks, that is exactly what I was looking for.

---

