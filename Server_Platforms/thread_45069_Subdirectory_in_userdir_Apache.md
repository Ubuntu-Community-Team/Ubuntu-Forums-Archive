---
title: "Subdirectory in userdir Apache"
date: 2005-06-28
forum: Server Platforms
---

### Post by gdboling on 2005-06-28
I have userdir working in apache at [http://localhost/~gdboling/](http://localhost/~gdboling/) but when I try and access a subdirectory as in [http://localhost/~gdboling/foo/](http://localhost/~gdboling/foo/) I get an access denied from Apache.  How can I configure it so I can access subfolders in the userdir?

Thanks.

---

### Post by LordHunter317 on 2005-06-28
The apache user (www-data) needs at least access permission ('1) on the directory (and all above it) to be able to access files inside.  To be able to read it to do like a directory index, it needs the read permission as well ('1'+'4' = '5').

---

### Post by gdboling on 2005-07-05
[QUOTE=LordHunter317]The apache user (www-data) needs at least access permission ('1) on the directory (and all above it) to be able to access files inside.  To be able to read it to do like a directory index, it needs the read permission as well ('1'+'4' = '5').[/QUOTE]

Sorry for the late response.  Thanks for the information.  So what would be the command(s) to get this to work.  I tried using chmod and chown but neither are giving me the appearnt access I need to get this to work.

---

### Post by LordHunter317 on 2005-07-05
On a directory, you'd likely say: ```
chmod o=rx
``` to give apache read and access permissions.  This allows it to do directory indexes (**NB:** all other users get these permissions too.  But who really cares if the data's web accessible)  If you don't want that:```
chmod o=x
``` allows it to read files, but not do an index.  On a file:```
chmod o=r
``` is sufficent.

---

