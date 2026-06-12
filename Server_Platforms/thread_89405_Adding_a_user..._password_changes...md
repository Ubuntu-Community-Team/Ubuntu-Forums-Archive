---
title: "Adding a user... password changes.."
date: 2005-11-12
forum: Server Platforms
---

### Post by Aven on 2005-11-12
Ok, everytime I add a user.. the password always changes.. it's really frustrating because I've been trying to setup an FTP server.. and when it's setup.. passwords never work.

I've tried the following:

- switching to a different FTP daemon
- went on System > Administration > User and groups and manually added.
- used 'useradd' in the command line

The user gets created but always "Wrong Password"

can someone please help me?


thanks

---

### Post by LordHunter317 on 2005-11-12
What's the useradd command you're running?

---

### Post by Juippisi on 2005-11-12
Try something like this:

useradd test
passwd test
<some password>
<again>

and try to log on.

---

