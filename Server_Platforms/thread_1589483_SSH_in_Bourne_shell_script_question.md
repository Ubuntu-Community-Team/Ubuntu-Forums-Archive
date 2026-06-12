---
title: "SSH in Bourne shell script question"
date: 2010-10-06
forum: Server Platforms
---

### Post by guessswh0 on 2010-10-06
Hello all,

I have a question about using bourne for a shell script.

I have a script that at the moment performs a logical dump of my database, backups up the physical files of the database, and backs up everything within /var/www

I want to be able to copy the files over ssh to a remote server.  However, the only way I am able to find examples of doing this is when you exchange keys and do not need to provide a password.

How can you write a script that requires a password, not key exchange?  I was told I specifically have to do it this way.

Thanks for the help.

---

### Post by oregonbob on 2010-10-06
If you don't have a key installed, ssh asks for a password. So why not remove that key?

---

### Post by djurny on 2010-10-06
you could try the following;
```

ssh -o PubkeyAuthentication=No *remoteserver*

```
hth!

---

### Post by guessswh0 on 2010-10-06
thanks guys, I'll give it a shot

---

