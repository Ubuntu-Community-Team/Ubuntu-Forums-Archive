---
title: "Manually Editing the Users File"
date: 2006-11-13
forum: Server Platforms
---

### Post by ericbarch on 2006-11-13
Just a quick question I'm hoping someone can answer. I'm currently using the desktop version of Ubuntu on my server because it was easier to admin, but I'd like to switch to the server edition. I just need to know how to edit the user privileges of a user account without using the GUI. In which file is this information stored? Thanks. -Eric

---

### Post by r0ydster on 2006-11-14
Not sure about what exactly your looking for, but you might want to look at the man pages for adduser and useradd.

adduser is the tool to add users to a server with no gui, after the initial install.

The 2 main files are /etc/passwd and /etc/group - be careful if you manually edit these files, if you make a mistake, it will cause problems.

Hope this helps,

Mike

---

### Post by ericbarch on 2006-11-14
I need to make a user that can use the serial port. I'm fairly sure all I need to do is add the new user to the 'dialout' group. -Eric

---

### Post by AgenT on 2006-11-14
```
man useradd
man userdel
man usermod
```

---

