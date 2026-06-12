---
title: "I cant connect ssh localhost please help"
date: 2017-03-26
forum: Server Platforms
---

### Post by brendan1789 on 2017-03-26
Hi so when I try the $ ssh root@127.0.1.1 command i get the output: 
ssh: connect to host 127.0.1.1 port 22: Connection refused
also my user is not a sudoer what can I do?
(I am trying to give myself sudoer privileges to install sublime text)

---

### Post by wildmanne39 on 2017-03-26
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-03-26
The root user is disabled by default in ubuntu. You won't be able to ssh with it.

Also, why are you trying to ssh to localhost? ssh is for remote access, not after you have already logged in.

To give sudo rights to any user you need to know the password of an existing user that has sudo rights. Only in that case you can use one admin user to give admin rights to another user. Do you know the password for one current admin user?

---

### Post by brendan1789 on 2017-03-27
yeah the admin password is same as my password how would i go about giving myself sudo rights?

---

### Post by darkod on 2017-03-27
But the user is different, even if the password is the same right?

---

### Post by nightfalls on 2017-03-27
You need to edit the file [COLOR=#111111][FONT=Consolas]/etc/ssh/sshd_config [/FONT][/COLOR] and edit the line [COLOR=#111111][FONT=Consolas]PermitRootLogin[/FONT][/COLOR] put yes before it, if you want to connect with root.

---

### Post by TheFu on 2017-03-28
If you aren't in the sudoers group, ask the admin to install the package for you or get the source for it, compile it yourself and install somewhere under your HOME.  All users can do this. 

If you know the root password, use **su - **. On Ubuntu, root doesn't have a password, so unless someone did something against ubuntu methods and advice, this won't work.

---

### Post by brendan1789 on 2017-03-29
I searched ol and found that i could edit the sudo file with visudo and add myself in, thanks for the help though

---

### Post by TheFu on 2017-03-29
Since you were using ssh, I didn't think visudo wasn't known.  We all have gaps in our knowledge. No big deal, but filling those gaps in an organized way now will save hours, days, weeks, months of frustration.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - read the first 140-ish pages to get some background, then skim the rest of the book quickly flipping pages to see what's possible.

There are also "Ubuntu Server Guide" and "Ubuntu Desktop Guide" which might be useful.

There are lots of little tools like visudo in the Linux world.  There's vipw, vigr, gpasswd, passwd, usermod, chage, sudoedit ... There are also manpages about most config file formats.  *man sudoers* or *man fstab* for example.  With a little practice, all the shell utilities can be used together to make really impressive tools.  The glue tools to allow all the shell tools to work together are usually covered in a Unix 101 class.

Sorry if you knew all this already.  Just don't want to leave out too many details which can be confusing instead of helpful.

---

