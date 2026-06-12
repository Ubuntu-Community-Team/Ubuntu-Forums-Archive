---
title: "folder / file permission /var/www"
date: 2012-03-27
forum: Ubuntu Dev Link Forum
---

### Post by idavid on 2012-03-27
i can't found any good tutorial on how to do this. i'm working on my computer no in a server i know i need to use sudo chown ?? /var/www
how ever non of those have work for me, what i need is every time i create a folder or move a folder into www not having to issue sudo chown o sudo chmod o+rwx -R /var/www
the last one it's the one that im using.

What i need it's to doit just once and forget about doing it.

---

### Post by ijumpship on 2012-03-27
Why would you want to do that?
This would increase your risk of someone who had access to your web-root folder being able to place whatever they want to in that folder,hence compromising your security

I have seen people change the ownership of /var/www from root to www-data.I would not even do that and most people would not even recommend it.

If You are using a CMS most instruct you how to make particular folders such as /themes/files writeable. but I do think anyone will instruct you how to make the web root have expanded permisssions or mode

---

### Post by idavid on 2012-03-27
It's my personal machine not an ubuntu server. i use it only for development!

---

### Post by julioneander on 2012-03-28
In my Development environments, I usually create separate directories for each project and change the ownership of them to my username.
This way, I can develop from the /var/www directory without the need of root privileges.
If by some reason a directory must be writable by Apache, I give www-data write privileges ONLY to that directory.

Note that this is only recommended for Development environments.

To change ownership of files or directories, see chown

```
man chown
```To change what users can do with your files (privileges), see chmod

```
man chmod
```Regards.

---

### Post by shubham1 on 2012-03-31
> **idavid said:**
> i can't found any good tutorial on how to do this. i'm working on my computer no in a server i know i need to use sudo chown ?? /var/www
how ever non of those have work for me, what i need is every time i create a folder or move a folder into www not having to issue sudo chown o sudo chmod o+rwx -R /var/www
the last one it's the one that im using.

What i need it's to doit just once and forget about doing it.
try this thread:
[http://ubuntuforums.org/showthread.php?p=11583282](http://ubuntuforums.org/showthread.php?p=11583282)
and see the other ways too.
this thread contains some very common problems

---

