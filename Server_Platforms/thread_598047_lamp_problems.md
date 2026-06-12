---
title: "lamp problems"
date: 2007-10-31
forum: Server Platforms
---

### Post by mondoman89 on 2007-10-31
I'm having trouble getting a lamp installed. apache seems to be working, I can see the apache2-default page that says "it works". The problem I'm having is with phpmyadmin. at first it wasn't showing phpmyadmin in the directory. I linked phpmyadmin using 
>  sudo ln -s /usr/share/phpmyadmin /mountpoint/path/to/document_root 
I now see it in the directory but when i click phpmyadmin firefox wants to download a file or something. I'm still learning how to use linux, please help me.

---

### Post by ruibernardo on 2007-10-31
To access phpmyadmin try [http://localhost/phpmyadmin](http://localhost/phpmyadmin). The link shouldn't be necessary, remove it.

---

### Post by mondoman89 on 2007-10-31
i tried just typing in the address, but when i do that this download window pops up. for some reason firefox wants to download somethin. see attached pic.

---

