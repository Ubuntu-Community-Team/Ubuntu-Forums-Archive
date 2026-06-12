---
title: "how to not change file owner and group permissions when someone uploads a file?"
date: 2011-07-17
forum: Server Platforms
---

### Post by jcab on 2011-07-17
In my /var/www directory, I have everything set up with:

user: www-data
group: developers

directories: chmod 570
files: chmod 460


Everything seems fine. Users from the developers group can edit files and all, but now we began using the Git repository, and whenever a user edits a file (ie. Joe who is a developer,) file permissions get screwed again. Now they're:

user: Joe
group: Joe

directories: chmod 755
files: chmod 644

How can I fix this so permissions remain the same?

---

### Post by jcab on 2011-07-17
Anyone?:( Thought someone would know

---

### Post by capscrew on 2011-07-18
> **jcab said:**
> In my /var/www directory, I have everything set up with:

user: www-data
group: developers

directories: chmod 570
files: chmod 460


Everything seems fine. Users from the developers group can edit files and all, but now we began using the Git repository, and whenever a user edits a file (ie. Joe who is a developer,) file permissions get screwed again. Now they're:

user: Joe
group: Joe

directories: chmod 755
files: chmod 644

How can I fix this so permissions remain the same?

What specifically do you want to remain the same?  The UID/GID or the rights permissions.  

Why do you have the permissions set at 570 for directories and 460 for files?   The system wide file/directory permissions are controlled by the umask.  But why would you want such a strange set of permissions?

Either way let us know which "permissions" you are talking about.

[**_This_**]("http://www.zzee.com/solutions/unix-permissions.shtml") should be of some help.

---

