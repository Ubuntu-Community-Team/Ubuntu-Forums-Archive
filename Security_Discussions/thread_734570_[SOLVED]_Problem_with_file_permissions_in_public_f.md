---
title: "[SOLVED] Problem with file permissions in public folder"
date: 2008-03-24
forum: Security Discussions
---

### Post by samona on 2008-03-24
hi all,

I have a permissions problem.  I have a folder that has the permissions set to the following: 
[B]
drwxr-xr-x 3 mike mike 4096 2008-03-24 17:41 public_html[/B]

Everytime I FTP to this account and drop a file into the folder, the file's permissions are automatically set to:

**-rw------- **

I don't want to have to change the permissions of every file I store in this folder one at a time, is there a way I can make it so every file dropped into the public_html folder becomes readable by everyone?

Thanks in advance.

---

### Post by newtonfn on 2008-03-24
That's depends on the ftp server. What FTP server are you using?

---

### Post by samona on 2008-03-24
Vsftp

---

### Post by newtonfn on 2008-03-24
Sorry.. you hit the one I do not know how to use. (I know proftpd, but I do not recommend to change, because proftpd have some securities issues)

---

### Post by samona on 2008-03-24
No, its ok.  You helped me figure out that it was the server configuration.  Thanks!

---

