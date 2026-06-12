---
title: "Auto mount group shares /w samba PDC"
date: 2010-03-02
forum: Server Platforms
---

### Post by benign on 2010-03-02
I've a few group shares setup with samba and a PDC (using windows 7 clients) and the home directory for each user gets mounted automatically. I've configured group shares and only members of the respective group have access to them, but my question is how do I tell samba to automount group shares based on the user group?

---

### Post by benign on 2010-03-05
Any ideas? I've tried creating a login script, but it can't resolve any share names until the system has been up for ~40 seconds.

---

