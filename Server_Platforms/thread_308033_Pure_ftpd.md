---
title: "Pure ftpd"
date: 2006-11-27
forum: Server Platforms
---

### Post by Compact on 2006-11-27
I'm using pure ftp with mysql. Every user has a folder with subfolders. I want users to share some of this subfolders among other users. How can i do it? I have tried to use a symlink, but I it doesn't work, maybe I have to configure something of pure ftp?

Thank you!

---

### Post by golfing22 on 2006-11-27
You could always use Directory Alias, which I think pureftpd supports

---

### Post by Compact on 2006-11-28
Thank you for your reply. With directory alias I will allowevery user to access the folder and I only one some users to share the same folder. I have tryied to use symbolic links, but then I cannot active chroot averyone option, so every user will be able to go around the server. Any idea?

Thank you!

---

