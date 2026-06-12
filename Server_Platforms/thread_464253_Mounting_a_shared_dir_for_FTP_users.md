---
title: "Mounting a shared dir for FTP users?"
date: 2007-06-04
forum: Server Platforms
---

### Post by hagen00 on 2007-06-04
Hello

I've searched and experimented and tried, but to no avail. 

I'm trying to set up a shared FTP folder, but haven't had much luck. Basically, I'm doing this:

```
mount --bind /var/ftp/user/shared /var/ftp/user/client/shared
```

My problem is, is that it creates a duplicate directory. Everything else works, but the duplicate directory is annoying. What I mean is that after I run the above comand, I have the following directories

/var/ftp/user/shared/shared
/var/ftp/user/client/shared/shared

i.e. it's duplicated the directory. Why would it do that?

Help appreciated. 

H

---

### Post by hagen00 on 2007-06-04
I clearly don't understand how to use mount properly. 

Do I first create the directories, and then mount them with the above command? Or do I just create /var/ftp/user/shared and not the directory /var/ftp/user/client/shared?

---

### Post by hagen00 on 2007-06-05
Bump...no one??

---

### Post by Mr. C. on 2007-06-07
Use: 

```
mount --bind /var/ftp/user/shared /var/ftp/user/client
```

MrC

---

