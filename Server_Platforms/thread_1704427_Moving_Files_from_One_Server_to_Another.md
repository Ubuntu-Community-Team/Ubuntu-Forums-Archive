---
title: "Moving Files from One Server to Another"
date: 2011-03-10
forum: Server Platforms
---

### Post by thunderclap on 2011-03-10
I'm moving my site to a new VPS and need to learn how to move the files from my current server to the new one.  I'd rather not download everything to my computer and then re-upload everything... seems like a lot of wasted time.  There has to be a way to copy between the two servers, but how?  I have heard someone mention rsync... is that a program I could use?  If so, how?

I appreciated any help in this matter.

---

### Post by arrrghhh on 2011-03-10
rsync would probably be the best method.

Assuming you can scp between the boxes, you can rsync between the boxes.

---

### Post by CharlesA on 2011-03-10
+1 to rsync.

---

### Post by thunderclap on 2011-03-10
What would be the best command line to use for this?

---

### Post by arrrghhh on 2011-03-10
> **thunderclap said:**
> What would be the best command line to use for this?

rsync is the command...

```
man rsync
```          
     ^^ if you want to learn more about it.

---

### Post by BkkBonanza on 2011-03-10
Here's an example,

assuming you have ssh access to both server's, oldsrv.com being the old one,
and the username is the same on both servers
and the file tree to copy is /var/www
login to the new one,

rsync -av [email]user@oldsrv.com[/email]:/var/www/*  /var/www/

It will login to oldsrv.com and prompt for auth, then build a file list and copy the content to the target on the current server.

---

### Post by Lars Noodén on 2011-03-11
> **BkkBonanza said:**
> Here's an example,

assuming you have ssh access to both server's, oldsrv.com being the old one,
and the username is the same on both servers
and the file tree to copy is /var/www
login to the new one,

rsync -av [email]user@oldsrv.com[/email]:/var/www/*  /var/www/

It will login to oldsrv.com and prompt for auth, then build a file list and copy the content to the target on the current server.

+1 for rsync

Be sure to encrypt the rsync connection, though.

```

rsync **-e ssh** -av [email]user@oldsrv.com[/email]:/var/www/*  /var/www

```

---

### Post by thunderclap on 2011-03-11
I appreciate all the input.  Everything moved quickly and easily.  Thank you!

---

### Post by BkkBonanza on 2011-03-11
Actually the **-e** option is only needed if you're using a different shell than ssh (which is the default) or if you need to specify non-default options like a non-standard port (22). rsync will use ssh by default which is always encrypted.

---

