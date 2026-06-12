---
title: "Hide a database from the root user"
date: 2011-06-05
forum: Server Platforms
---

### Post by nss11 on 2011-06-05
Hi,

Does anybody know if it is possible to hide certain databases from the root user in MySQL?

It may *sound *stupid, since the root is the root and all that, and it may feel strange but it kind of adds a level of abstraction which I want to give the "root user", and I want to avoid going down the route of creating a new mysql instance on the server.

I had wondered if there is some kind of 'hide' parameter for a database or whether it is possible to change the root username to something else (e.g. 'realroot') and then create a new user 'root' with all the same privileges (except those on the hidden databases).

Just mulling around with some ideas, I hope my question makes sense. :)

Thanks in advance for any help or guidance.

---

### Post by SeijiSensei on 2011-06-05
Which "root" user are you talking about, the OS root user, or the MySQL root user?

I don't think you can stop the MySQL root user from seeing everything in the database.  After all, a simple "mysqldump -U root -p rootpassword dbname" will create a text file containing all the information in "dbname".  It might be possible to keep the OS root user from seeing the information by using a strong password on the MySQL root user's account.  OS root will still be able to see the contents of /var/lib/mysql and might be able to tease out some information from the binary database images stored there.

If you want to protect the information from prying eyes, encrypt it before storing it in the database.

---

### Post by 3xp10r3r|X13 on 2011-06-05
You could just create an encrypted volume, using truecrypt. That way, the root user could see that there is some file, but he wouldn't be able to view or access any files within this encrypted container.

[http://www.truecrypt.org/](http://www.truecrypt.org/)

edit: sry, I thought, when you were talking about a database, you meant just some docs or videos etc...

---

### Post by nss11 on 2011-06-05
Thanks for the replies.

Yes, I meant the MySQL 'root' account - sorry. Basically all I want to do is have a database for my software but for the mysql "root" user to not be able to see or edit it.

So I thought, if I could rename the mysql "root" username to be "realroot", and then create a second user with all privileges called "root", is there a way for it to have all privileges on everything except my software's database?

Sorry if I'm having trouble putting my question across.

---

### Post by brettg on 2011-06-05
I'd be extremely surprised if you could block the root user from a database, it sort of defeats the whole point of having a root user.

What I am really interested in is why you want to do this in the first place.

---

### Post by jtarin on 2011-06-05
> **brettg said:**
> I'd be extremely surprised if you could block the root user from a database, it sort of defeats the whole point of having a root user.

What I am really interested in is why you want to do this in the first place.He wants to hide something from his...boss, wife...OK?  Sheesh!!!:p

---

### Post by SeijiSensei on 2011-06-06
It sounds to me like you don't have root access, in the OS sense, but if you do, you could run a second instance of MySQL on a different port from 3306.  Give that instance a different root password.  You'd need to have it write to another directory as well.

I've done this with PostgreSQL when I've been experimenting with a new release.  If you compile PostgreSQL from source, it installs under /usr/local, so you can have the standard version on one port, writing to /var/lib/pgsql, and a second version on a different port writing to /usr/local/pgsql.

---

### Post by nss11 on 2011-06-06
I know it kind of seems stupid with it being the 'root' user, but it's for some software I wanted to keep the database hidden to avoid 'tinkering' easily.

I've experimented and changed the root user to something different and then created a second account called 'root' but I'm stumbling on global permissions - seems I can't find a way to apply the global permissions, but not apply them for a certain database.

So I'm thinking of going down SeijiSensei's advice by installing another instance of mysql, which I had hoped of avoiding, but kind of makes sense I suppose, especially since global permissions should be 'global' on the one database.

Thanks for the help guys, very much appreciated. :)

---

