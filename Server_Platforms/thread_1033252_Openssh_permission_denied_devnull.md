---
title: "Openssh permission denied /dev/null"
date: 2009-01-07
forum: Server Platforms
---

### Post by Stoneface on 2009-01-07
When I try to logon to my server using openssh I am refused access :```
-bash: /dev/null: Permission denied
```. It is stated there is an issue with /dev/null. When I logon as root I can access. When I type ```
ls -l /dev/null
``` I get ```
-rw-r--r-- 1 root 0 2009-01-07 18:39 /dev/null
```. How can I fix this?:confused:

---

### Post by Stoneface on 2009-01-07
Bump....

How can I make sure other users can use openssh as well...? How should I adjust that file?

---

### Post by cdenley on 2009-01-07
Did you set the user's home directory to /dev/null or something? What user are you trying to logon as? Post this output, substituting the correct username.
```

getent passwd myuser

```

---

### Post by Stoneface on 2009-01-07
getent passwd jasper: ```
jasper:x:1000:33:Jasper P,,,:/home/jasper:/bin/bash
```

---

### Post by cdenley on 2009-01-07
Try this
```

sudo rm /dev/null
sudo mknod /dev/null c 1 3
sudo chmod 666 /dev/null

```

---

### Post by Stoneface on 2009-01-07
Yes, that worked! I wonder how the problem occured in the first place...

---

