---
title: "Apache Server file security"
date: 2011-01-10
forum: Server Platforms
---

### Post by TTGRULES on 2011-01-10
Hi, im hosting a website that does database reports, and I have the data stored in my own format. I wanted to allow for direct data uploads. To do that, I have to chown the upload folder to www-data.. is this secure? I don't allow for anyone to upload unless they have an encrypted key that can only be gained by logging in.
Thanks!

---

### Post by rubylaser on 2011-01-10
The www-data user is the user that Apache uses by default.  So as long as your permissions are setup properly on your files/folders, you'll be just fine.

---

