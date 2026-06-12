---
title: "Never ending permission issues between apache, vsftpd and ssh."
date: 2011-02-13
forum: Server Platforms
---

### Post by iarp on 2011-02-13
Apache, vsftpd and my own doings via ssh access are in a never ending permissions battle.

My DocumentRoot is set to /home/iarp/projects/.

Everything i upload via ftp:
```
-rw-r--r-- 1 iarp www-data 108942 2011-02-13 00:37 CoolBlue10.zip
```

Everything via ssh:
```
drwxr-xr-x 3 iarp iarp   4096 2010-03-13 12:30 CoolBlue10
```

In order to allow web applications to do anything to their own files or folders requires i run the code below:
```

chgrp -R www-data folder/
chmod -R 775 folder/
```

I've got to figure out someway of letting www-data access to these things without me constantly having to do chgrp/chmod all the time. Everytime i upload something via php script i have to rerun the chmod/chgrp and it's quite annoying.

The reason it's located in my home directory is because i do a TON of editing via ftp, and the only ftp server I've found was easy to setup was vsftpd which requires it to be in my home directory.

So i'm at a loss of what to do to fix this issue.

---

