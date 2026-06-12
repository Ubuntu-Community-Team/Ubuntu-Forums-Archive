---
title: "mysqldump where to save password?"
date: 2011-08-14
forum: Server Platforms
---

### Post by durus on 2011-08-14
I have to servers setup [Server-production] and [Server-backup] and I am using rdiff-backup to connect from [Server-backup] to [Server-production] in order to take a backup of the content from [Server-production] to [Server-backup] using ssh keys to connect.

Now I want to setup backup for my databases but need help to figure out where and how I should save the sql password in order to keep it safe from potential hackers.

Can I save the password on [Server-backup] and remotely through SSH trigger mysqldump to dump the file before I run rdiff-backup? Can I save the password in a way that only root on [Server-production] can read the password but other users can execute it?

Where would you save the password and why?

---

### Post by evarie on 2011-08-14
Why you make it so difficult?

You can just make a folder in a secret place.
Tell only people how must know it where it is.
Or, You can make a folder in 
/home or /var or /temp 
and give it
the ownership root and gave it a new group so
that you can make members of those people
you want to gave access to that folder.
Give the password tekst file the extension pw.txt
So, name it "mysql.pw.txt"
The url will be for example /home/mysql/mysql.pw.txt

And change chmod to 710. But then you must read more about the command chmod and chown.

If you are paranoid. Maybe use the folder .private or use truecript.

Is this wat you need to know?

---

### Post by hakermania on 2011-08-14
I would save the password to an unexpected place with unexpected name.
Also, I would use md5sum to save it and then convert the given password to md5sum and compare it with the saved one.
So, the actual password string won't exist in your system!

---

### Post by rubylaser on 2011-08-14
Just write it to a file and give that 600 permissions, something like [this]("http://www.techiecorner.com/1619/how-to-setup-mysqldump-without-password-in-cronjob/").. This would require the root user's credentials to even read the file.  If the hacker had the root password to be able to read the file, your whole system would be compromised anyways, so they could just start mysql and skip the grant tables to make a new password.

Anything else is a waste of time, and really won't give you any extra protection imho.

---

### Post by Wim Sturkenboom on 2011-08-15
> **durus said:**
> ...
Now I want to setup backup for my databases but need help to figure out where and how I should save the sql password in order to keep it safe from potential hackers.
...
Where would you save the password and why?
I don't use a password for backups. So where to store it? Nowhere. And why? Because I don't have one.

:D :D :D :D

Just create a passwordless user with *_select_* and *_lock tables_* privileges; as far as I'm aware, that's all the privileges that that user needs.

Use that user in your script. Problem solved and you can mark the thread as such ;)

---

### Post by Wim Sturkenboom on 2011-08-15
I just realise that you probably also don't have dedicated mysql users for access to the databases. I strongly advise that you create them with the minimal privileges that they need. E.g. no database user needs *_grant_* privileges and visitors to a website don't need *_drop table_* or *_drop database_*.

---

