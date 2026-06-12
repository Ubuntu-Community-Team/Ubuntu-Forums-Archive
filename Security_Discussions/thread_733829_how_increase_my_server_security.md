---
title: "how increase my server security"
date: 2008-03-24
forum: Security Discussions
---

### Post by etusha on 2008-03-24
hi all 
im new in linux
i need to increase my server security
i have ubuntu server 6.06 dapper + plesk

---

### Post by insineratehymn on 2008-03-24
That depends on what services your server is offering.

If you are using Apache you can set it up so some folders are out of the scope of the actual Apache server.

If you are using cross network traffic, you can encrypt your packets with SSH, even inside your home.

If you are having alot of people uploading/downloading, you can set up disk-quotas so each user has a limit on traffic.

If you are using MySQL you can restrict users to their own tables.

If people are SSH'ing in to your box you can limit them to their own directories and do the quota thing.

The security possibilities which each service are almost endless.

Give us an idea of what you are running and we will try to give you a condusive answer.

---

### Post by etusha on 2008-03-24
apache ftp mysql ssh (download/upoad)
its hosting server

---

### Post by insineratehymn on 2008-03-24
Ok, I guess Ill start at the beginning:

Apache:

Here is a quick how-to that you can install some quick patches that will make Apache2 more secure:
[http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security](http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security)

FTP:

Don't use FTP, you have an SSH server already running, use SFTP.

MySQL:

I don't think there are going to be any quick patches, just make sure that each user can only access their own tables and such. Proper database normalization and user management will help you avoid any holes that may appear.

SSH:

Use your SSH configuration files to make it more secure.
[http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/](http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/)

Here is a quick how-to that should show you how to edit your SSHd configuration files so people can only access their own stuff.

Have fun, and try to break in to your own boxes. If you know of any nerds, or 133t hax0rz give them your IP and get them to break in, at least some people with good intentions at least.

---

### Post by Dr Small on 2008-03-24
> 
Have fun, and try to break in to your own boxes. If you know of any nerds, or 133t hax0rz give them your IP and get them to break in, at least some people with good intentions at least.

Like me? ;)

---

### Post by insineratehymn on 2008-03-25
Haha, so which one are you?

A nerd or a 133t hax0rz?

---

### Post by hyper_ch on 2008-03-25
Unplug the box and move it to your bank's tresor vault (but don't connect it again to the net there) ;)

---

### Post by Dr Small on 2008-03-25
> **insineratehymn said:**
> Haha, so which one are you?

A nerd or a 133t hax0rz?
Both :D

---

### Post by etusha on 2008-03-25
stop joke 
im speaking seriously

mod please close this post

---

