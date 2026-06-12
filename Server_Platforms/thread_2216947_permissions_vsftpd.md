---
title: "permissions vsftpd"
date: 2014-04-14
forum: Server Platforms
---

### Post by cristian7 on 2014-04-14
¿How i prevent a user replace files?

Sorry for my bad English. Not my native language

---

### Post by nerdtron on 2014-04-14
If you don't want the user to replace/edit the file, remove the write permission of the user for that file.
Can you post the "ls -la" of the vsftpd directory?

---

### Post by cristian7 on 2014-04-14
The problem is that is not a single file, i need to the user can upload files but not replace them

what do you mean with ''ls -la''?

---

### Post by nerdtron on 2014-04-15
In the terminal go to the vsftpd folder and type "ls -la". Post the output here so that we can see the permission of the folder.
What you want is bit complicated. Are there many user accounts that would upload to that folder?

---

### Post by steeldriver on 2014-04-15
It depends exactly what you want to do, but a couple of possibilities are

1. set the [sticky bit]("http://en.wikipedia.org/wiki/Sticky_bit") on the directory: this would allow each user to replace their own files, but not replace another user's files (like the default permissions on the /tmp system directory)

2. if the directory is on an ext2/3/4 filesystem you may be able to use [extended file attributes]("http://en.wikipedia.org/wiki/Extended_file_attributes#Linux"), in particular if you set the **append** attribute (chattr -a) on the directory iirc that will prevent users from removing (or renaming) even their own files

---

### Post by cristian7 on 2014-04-15
Just one user,

root@mscan:/var/www/mscan# ls -la
total 76
drwxrwxrwx 19 mscan root    4096 Apr 14 22:58 .
drwxrwsrwx 11 mscan root    4096 Apr 14 18:48 ..
drwxrwxrwx  3 mscan nogroup 4096 Mar 13 12:58 aqaa
drwxrwxrwx  3 mscan nogroup 4096 Apr 13 16:48 asd
drwxrwxrwx  4 mscan nogroup 4096 Mar 15 12:14 ipeear
drwxrwxrwx  3 mscan nogroup 4096 Apr 13 19:13 nzvspog
drwxrwxrwx  3 mscan nogroup 4096 Apr 13 19:18 nzvspog2
drwxrwxrwx  3 mscan nogroup 4096 Apr 13 21:38 nzvswaw
drwx------  3 mscan nogroup 4096 Apr 14 22:58 nzvswaw2241
drwxrwxrwx  3 mscan nogroup 4096 Mar 16 22:56 nzvswaw2352
drwxrwxrwx  3 mscan nogroup 4096 Mar 27 13:36 pruebillamadafaca
drwxrwxrwx  3 mscan nogroup 4096 Mar 13 15:15 test1
drwxrwxrwx  3 mscan nogroup 4096 Mar 15 11:37 testipear
drwxrwxrwx  4 mscan nogroup 4096 Mar 15 12:21 testipeear
drwxrwxrwx  3 mscan nogroup 4096 Mar 15 11:43 testipeer
drwxrwxrwx  3 mscan nogroup 4096 Mar 15 11:42 testiper
drwx------  3 mscan nogroup 4096 Apr 14 18:34 tstxml
drwxrwxrwx  3 mscan nogroup 4096 Apr  5 21:13 wawvs
drwxrwxrwx  3 mscan nogroup 4096 Apr  5 21:21 wawvstow

---

### Post by cristian7 on 2014-04-15
Thank you steel, the second option is what i need, i dont know how to do it, but at least its possible. i gonna keep looking

---

