---
title: "ubuntu server user accounts"
date: 2006-06-17
forum: Server Platforms
---

### Post by levi_v on 2006-06-17
Is it possible to have more than two user accounts for the server version? Right now I get a message when i try and add more, "Only one or two names allowed."

---

### Post by LordHunter317 on 2006-06-17
POsting the command you're trying to run is helpful.

---

### Post by levi_v on 2006-06-19
[QUOTE=LordHunter317]POsting the command you're trying to run is helpful.[/QUOTE]

adduser

---

### Post by mssever on 2006-06-19
It's possible to have as many user accounts as you want (within reason). If you post the entire command line (usernames and passwords obfuscated) along with the exact error message, it will be easier to figure out why you're having problems.

Edit: You should also have a look at ```
man adduser
```

---

### Post by Randomskk on 2006-06-19
adduser is to add a username to a group.
useradd is to create a new username.

Easy to confuse.

---

### Post by mssever on 2006-06-19
[quote=Randomskk]adduser is to add a username to a group.
useradd is to create a new username.

Easy to confuse.[/quote] 
Actually, either one will work for creating a new username (I just used adduser to create a new username), but the syntax of useradd is a litle easer and the man page is a whole lot cleaner.

---

### Post by Randomskk on 2006-06-19
Ah, ok, I just stuck to useradd for adding users and adduser to adding users to groups :P

---

### Post by LordHunter317 on 2006-06-19
adduser is traditionally meant for add users interactively.  It varies from distro to distro (and UNIX to UNIX).  useradd is standardized and more suitable for scripting.

---

