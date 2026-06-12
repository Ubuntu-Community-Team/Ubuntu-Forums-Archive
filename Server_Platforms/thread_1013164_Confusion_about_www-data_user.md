---
title: "Confusion about www-data user"
date: 2008-12-16
forum: Server Platforms
---

### Post by kook44 on 2008-12-16
Hi-
I've installed apache on 8.10.  Everything is working fine.  I see that apache is running three processes as user www-data as always.  I checked the list of users and there's no www-data user.
How is this possible?

---

### Post by doobiest on 2008-12-16
How are you checking users?  are you just issuing 'users' from the command line?

If you are you will only see real users there, not www-data because apache is a daemon running under the user www-data

fyi you can cat /etc/shadow and that is a grimmy way if listing all valid users.

---

### Post by jpeddicord on 2008-12-16
www-data is a user/group set created specifically for web servers. It should be listed in /etc/passwd as a user, and can be configured to run as another user in /etc/apache2/apache2.conf.

Basically, it's just a user with stripped permissions so if someone managed to find a security hole in one of your web applications they wouldn't be able to do much. Without a lower-user like www-data set, apache2 would run as root, which would be a Bad Thing® since it would be able to do anything and everything to your system.

---

### Post by kook44 on 2008-12-16
> **doobiest said:**
> How are you checking users?  are you just issuing 'users' from the command line?

If you are you will only see real users there, not www-data because apache is a daemon running under the user www-data

fyi you can cat /etc/shadow and that is a grimmy way if listing all valid users.

> **jacobmp92 said:**
> www-data is a user/group set created specifically for web servers. It should be listed in /etc/passwd as a user, and can be configured to run as another user in /etc/apache2/apache2.conf.

Basically, it's just a user with stripped permissions so if someone managed to find a security hole in one of your web applications they wouldn't be able to do much. Without a lower-user like www-data set, apache2 would run as root, which would be a Bad Thing® since it would be able to do anything and everything to your system.

Ah, yes.  I was using users.  So, technically, what makes www-data not a "real" user? I'm going to want to also set up tomcat to run as a daemon under a user "tomcat".  How would I set one of my own up from scratch?  I was planning on just creating a user w/ useradd.  I'm thinking that isn't the right way to do it...

---

### Post by jpeddicord on 2008-12-16
> **kook44 said:**
> Ah, yes.  I was using users.  So, technically, what makes www-data not a "real" user? I'm going to want to also set up tomcat to run as a daemon under a user "tomcat".  How would I set one of my own up from scratch?  I was planning on just creating a user w/ useradd.  I'm thinking that isn't the right way to do it...

It's a real user in the sense that it can be used and operated on, but it's a system user that cannot be logged in to (unless you add a password to it, which isn't a great idea).

As for Tomcat, I don't really know, other than that one of the tomcat packages might create and set up the user automatically.

---

### Post by doobiest on 2008-12-16
well put it this way www-data is a real user, you can su www-data but I never would want to.  The point more so is that services/daemons are running under the www-data user not applications.  so if you su'd to www-data it would invoke an instance of bash for the www-data, at that point it would show up in the users list.  User only shows active users that have application level processes running under them, if that helps describe it better.

RE: tomcat i'd assume upon installing tomcat it would create it's own user or use an existing one. I'd stick with that.

But some things you might want to look into is useradd userdel usermod, groupadd, groupdel, groupmod.. Just for fun, but be careful.

---

### Post by doobiest on 2008-12-16
> **jacobmp92 said:**
> It's a real user in the sense that it can be used and operated on, but it's a system user that cannot be logged in to (unless you add a password to it, which isn't a great idea).

As for Tomcat, I don't really know, other than that one of the tomcat packages might create and set up the user automatically.


You can su to www-data without changing the password. 

Example sudo su www-data would go from you > root user > www-data

in actuality there is always a password for a user you just might not know it.

---

### Post by jpeddicord on 2008-12-16
> **doobiest said:**
> You can su to www-data without changing the password. 

Example sudo su www-data would go from you > root user > www-data
Yes, you can su to any user defined in /etc/passwd, but that doesn't enable direct logins on the account.

> 
in actuality there is always a password for a user you just might not know it.No, system users have an invalid password set (listed as * or ! in /etc/passwd) that prevents them from being signed in to (using su to access an account does not qualify as signing in either. ;))

---

### Post by doobiest on 2008-12-16
Hey if I can run bash as that user I would consider that logged in enough for me

---

### Post by Stephen-I-M on 2009-01-09
I have no problem assigning group ownership to www-data, but under Users Settings->Group Settings, www-data does not appear.

My goal is to add myself to the www-data group.

StephenB

---

### Post by mbeach on 2009-01-09
if you use the configuration editor (gconf-editor) there is a setting at:
"/apps/gnome-system-tools/users/showall" 
Enable that to show all users.  Launch your "users and groups" again and you'll see www-data.

---

### Post by mbeach on 2009-01-09
you may also want to read the description in the man file for adduser.
```
man adduser
```
specifically the part about adding a system account.

also, a read of:
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2.2](http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2.2)
will outline the differences between system users and 'real users'.

---

### Post by Stephen-I-M on 2009-01-19
Thank you mbeach.

StephenB

---

### Post by Blario on 2012-02-13
> **jpeddicord said:**
> Yes, you can su to any user defined in /etc/passwd, but that doesn't enable direct logins on the account.

No, system users have an invalid password set (listed as * or ! in /etc/passwd) that prevents them from being signed in to (using su to access an account does not qualify as signing in either. ;))

old thread, but i found this at the top of google.  this post helped me, but its not /etc/passwd.  it's the second field of /etc/shadow.  worked like a charm.  yayy for security.

---

