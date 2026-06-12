---
title: "SFTP between OS X 10.5 and Ubuntu Server 8.10"
date: 2009-03-12
forum: Server Platforms
---

### Post by mobbbx on 2009-03-12
Hi,

I am currently using Mac OS X 10.5 (Leopard) so i ssh to the ubuntu server via its Mac terminal.

I am trying to send files from local OS X to remote ubuntu server. The file is stored locally (Mac OS X) under Documents folder. But i can't seem to be able to do it. Please see the following code:

```
sftp> put /usr/local/Documents/<Directory>
stat /usr/local/Documents/<Directory>: No such file or directory

sftp> put /Macintosh HD/Users/Rudy/Documents/Interests
stat /Macintosh: No such file or directory
```

I'm sure there's something wrong with the path i typed in. 

Help anyone?

---

### Post by BkkBonanza on 2009-03-12
I'm not an OS X user but it looks like it's not liking the spaces. You probably just need to put quotes around the path so it knows the spaces are part of it.

---

### Post by pytheas22 on 2009-03-12
I'm guessing you need to escape the spaces in directory names with a \, e.g.:
```

put /Macintosh**\** HD/Users/Rudy/Documents/Interests
```

Note the backslash between 'Macintosh' and 'HD'.

---

