---
title: "vsftpd won't delete user"
date: 2013-06-30
forum: Server Platforms
---

### Post by Snitz on 2013-06-30
I've installed vsftpd on my machine to ease up the process of transfering files.

I have added a new user called Snitz and gave it permission to /home/Snitz/
All is good for now.

But I originally intended to gain access to /home/mycode/
because that's where my site's files are stored.

So I tried added a new user named "mycode" but it kept saying user already exists and I do not know what the password is.
So I tried deleting the user: ```
sudo userdel mycode
```
but it kept saying user is currently logged in.
I tried disconnecting: ```
logout mycode
```
but I got logged out of my root username.

---

### Post by chrisguk on 2013-06-30
Have you tried 

sudo passwd mycode

?

Also check the file /etc/passwd to see is the user is present.  There is more information about this file here:  [http://manpages.ubuntu.com/manpages/hardy/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/passwd.5.html)

---

### Post by Snitz on 2013-06-30
EDIT: it worked.

---

