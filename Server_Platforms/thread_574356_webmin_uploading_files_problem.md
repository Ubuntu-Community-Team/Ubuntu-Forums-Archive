---
title: "webmin uploading files problem"
date: 2007-10-12
forum: Server Platforms
---

### Post by rbprogrammer on 2007-10-12
ok, so i log into my server with webmin.  the user that i log in with is part of the group [FONT="Courier New"]admin[/FONT].  and the folder i am uploading to has these permissions:
[INDENT]drwxrwxr-x 9 root admin 4096 2007-10-12 18:04 www[/INDENT]
so clearly i have write permissions with the user that i log in with.  but for some reason, ever file i try to upload, i get this error:
[INDENT]
Failed to upload files : Failed to write to /path/to/server/www/file.ext : Bad file descriptor
[/INDENT]
now, if i were to log onto the server as [FONT="Courier New"]root[/FONT], i can upload the file to that location without a problem.  what could be causing this problem??  it's quite annoying and i dont want to log in as [FONT="Courier New"]root[/FONT] every time i need to upload a file

---

### Post by rbprogrammer on 2007-10-18
bump..

please help. this problem is so incredibly annoying..... :confused:

---

