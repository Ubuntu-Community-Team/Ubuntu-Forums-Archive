---
title: "Ubuntu 10.04 Web Server Running Joomla, With “File Unwritable Problem”"
date: 2010-11-13
forum: Server Platforms
---

### Post by bloodhacker2 on 2010-11-13
Ubuntu 10.04 Web Server Running Joomla, With “File Unwritable Problem”
Ok guys, this is my problem.
I’m running ubuntu 10.04 desktop as a web server using joomla 1.5.22. The problem is every time I try to make changes in the backend of joomal, joomal comes back and tells me the files are unwritable. 
So I took a look at the Directory Permissions and ever one of them is marked “Unwritable”.
I figured this was an ubuntu permission problem.
So how do I make my ubuntu file writeable?

---

### Post by bloodhacker2 on 2010-11-13
Ubuntu 10.04 Web Server Running Joomla, With “File Unwritable Problem”


Ok guys, this is my problem.

I’m running ubuntu 10.04 desktop as a web server using joomla 1.5.22. The problem is every time I try to make changes in the backend of joomal, joomal comes back and tells me the files are unwritable. 

So I took a look at the Directory Permissions and ever one of them is marked “Unwritable”.

I figured this was an ubuntu permission problem.

So how do I make my ubuntu file writeable?

---

### Post by James78 on 2010-11-13
Default permissions for Joomla are 644 for files, 755 for directories.

This will recursively set permissions.
```
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
```

If that does not work, then you need to give us more information!

What are your directory/file permissions set to, and what user/group owns them?

---

### Post by cariboo on 2010-11-13
Please don't create multiple threads on the same subject, I have merged your two threads.

---

