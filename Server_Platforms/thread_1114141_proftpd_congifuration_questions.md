---
title: "proftpd congifuration questions"
date: 2009-04-02
forum: Server Platforms
---

### Post by edpatterson on 2009-04-02
I need to restrict access to a single users home directory. I found the:
# Use this to jail all users in their homes
DefaultRoot     ~
setting but this affects all users. I only need to restrict one. There are only three accounts on the box, root, mine and the person (developer) I need to restrict.

I have to fall back to ftp until I can get rsync functioning across multiple boxes.

Thanks for any and all help
Ed

---

