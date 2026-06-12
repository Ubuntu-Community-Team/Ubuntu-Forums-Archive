---
title: "Backup MySQL without starting MySQL"
date: 2009-02-22
forum: Server Platforms
---

### Post by meoblast001 on 2009-02-22
:( Well... I'm having a bad day. My server crashed. It now wants to think it's harddrive is full although it is not. I need to backup all my files so that i can reinstall Ubuntu. I cannot start MySQL because it requires it to write to the disk and I can't use any tools that need to write to the disk. What must I do to backup my MySQL databases? This is urgent.



I guess this is Ubuntu's birthday present to me considering my birthday is in 2 days.

---

### Post by konqueror7 on 2009-02-22
mmm...using mysql administrator would also fail since it would need mysql server to run,,,have you tried copying the 'Program Files\MySQL\MySQL Server 5.0\data' folder? there seems to be where mysql stores it as files...i haven't tried it though, but as of now, its the only thing i can think of...you might try this first with another mysql installation and see if it work, make sure you backup first...

---

### Post by cariboo on 2009-02-22
> Program Files\MySQL\MySQL Server 5.0\data

@konqueror7

You may have noticed this is an Ubuntu forum, there is no Program Files directory in the Linux file tree. :) Your systax is all wrong too, the path should be /Program\Files/MySQL/MySQL\Server\5.0/data. The linux files sytem doesn't deal well with spaces so you have to use "\" as a delimiter

@meoblast001

All the mysql database files are located in /var/lib/mysql

Jim

---

### Post by E_K on 2009-02-22
possible to try the drive in another computer and just copy every thing over?

What happens if you delete some stuff on the drive still say full?

---

### Post by konqueror7 on 2009-02-22
oh, i forgot! i copied it from my winxp,,,haha (so dumb of me)
the answer is already above...

@cariboo907
about my directory, this how i install my mysql, so maybe its different from yours...;)

---

### Post by koenn on 2009-02-22
> **cariboo907 said:**
> the path should be /Program\Files/MySQL/MySQL\Server\5.0/data. The linux files system doesn't deal well with spaces so you have to use "\" as a delimiter

not that it matters much to this thread, but this is not quite accurate.

The Linux filesystem deals quite well with spaces in paths and file names, but the shell interprets them as a delimiter between words (parameters, command line arguments, ...), and that's why paths with spaces are misinterpreted when used in a command line, unless
- you quote the string, or
- you 'escape' the spaces. the \ character is an escape character that informs the shell to *not* treat the following space as a delimiter. Consequently, a path with spaces would look like 
```
 .../Program\ Files/MySQL/MySQL\ Server\ ... 
```
Bash will try to do this automatically if you use tab for command completion.

---

### Post by koenn on 2009-02-22
> **meoblast001 said:**
> :( Well... I'm having a bad day. My server crashed. It now wants to think it's harddrive is full although it is not. I need to backup all my files so that i can reinstall Ubuntu. I cannot start MySQL because it requires it to write to the disk and I can't use any tools that need to write to the disk. What must I do to backup my MySQL databases? 


You could try to add some additional storage, like an external disk, or mount an nfs share of an other machine, then copy the mysql data dir or use mysql dump to dump the databases to files that you can use to rebuild the databases once you have an mysql server up and running again.
I'm not sure Mysqldump will work if mysql server isn't running, but copying the datadir might work if you're using ISAM, which i think is the default. 

> **meoblast001 said:**
> :
This is urgent.

I guess this is Ubuntu's birthday present to me considering my birthday is in 2 days.
or it's a reminder that you should anticipate situations like this by making backups and preparing restore procedures.

---

