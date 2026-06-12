---
title: "How do you handle your webroot permissions when uploading?"
date: 2011-07-29
forum: Server Platforms
---

### Post by volkswagner on 2011-07-29
OK,

I have been plagued by this for some time.  

How many times do you need to run chown -R user:www-data or similar to your webroot directory.

I have been searching via Google and this forum.  I have yet to find a definite answer to handle uploading and creating new files usable by apache2.

Scenarios can vary.  Some folks put there webroot inside a /home directory.  Some users leave the default location as /var/www.

I have  a two part question.

1.  Why do I often read "Apache runs as user=www-data, therefore files need to be readable by such (www-data)", but the default install in Ubuntu includes an index.html with the following?

```
ls -l /var/www
total 4
-rw-r--r-- 1 root root 177 2011-07-28 21:52 index.html

```

Perhaps I can answer my own question here: "because the index.html file is readable by anyone?".  Does this mean than any file with permissions "-rw-r--r--" should run without incident in Apache2?  I assume there are some files that need the execute bit, which files would those be?

2. The more important question for me is, how do Admins handle uploaded files to there Apache2 root directory?  If you use FTP, SFTP, SSH/rsync or even create files directly on the server, how do you maintain the file permissions/owner/group?

I have been overwhelmed with things like umask, stickybit, and the like, but have yet to find a common way to have users upload files to a directory while maintaining the parent directories permission structure.

I see the "Apache file permission" thread arrive on this forum nearly daily, yet no common answer.  I understand each user may have unique requirements, but is seems the topic is grossly common but not well understood.

---

### Post by Wim Sturkenboom on 2011-07-30
1)
Because it is world readable ;)
2)
I think you answered your own question in another thread; don't use /var/wwww but use the user's home directory / directories. That way the user(s) can directly upload into their home directory and it's easy to jail them in there. The only issue is that apache itseldf can't write in that directory; therefore I have a dedicated directory 'files' that is writable by apache. You can either change the ownership and permissions of the file directories (chown youruser:var-www, chmod 774) or use acl (that's what  use)

Below my setup as used in an intranet environment. I'm the developer, database and system administrator etc. 

```

/home/wim
  |
  +-- site 1
  |     +-- inc
  |     +-- web        --> document root; apache can read
  |          +-- files --> apache can write here
  |          +-- index.php
  |
  +-- site 2
  |     +-- inc
  |     +-- web        --> document root; apache can read
  |          +-- files --> apache can write here
  |          +-- index.php
  |

```
The document root for each site is 'web'. 'inc' is the directory where I place common stuff and stuff that should not be revealed (e.g. mysql connection functions that contain usernames and passwords); apache can read it but as it's outside the document root, visitors can't get it.

PS 1)
I use the index.html in /var/www as a catch all page in case somebody ends up there by accident.
PS 2)
I don't use Ubuntu servers as don't understand them; Slackware seems more transparent to me but that might be because I grew up with it.

---

### Post by Wim Sturkenboom on 2011-07-30
I have never really understood why there is a /var/www ; or better, why people keep on trying to place their websites in there.

/var is basically for semi temporary stuff like log files, spool files etc. Something permanent like a website does not belong in there in my opinion.

On the other hand, it's probably the only sensible place to place the 'it works' index.html

The same can be said for the mysql databases. I've created a separate directory /home/databases (to replace /var/lib) for it (in my home setup) and a separate /database partition (in my intranet setup).

---

