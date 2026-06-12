---
title: "Umask for Directory permissions"
date: 2009-08-26
forum: Server Platforms
---

### Post by Ben Leedham on 2009-08-26
Hi,

 I am running a webapp in tomcat. Several OS users use this webapp and they are all members of the same group, the webapps home directory has permissions drwxrwxr-- which is what I want, the problem I am having is that when the webapp creates directories or files they don't have the group write permission set ( drwxr-xr-- ).

I have tried recursively setting the GUID bit on the webapps home directory, and tried setting the system wide default umask to 027 ( this is overridden in all user profiles apart from the user who is running tomcat ).

None of it worked.

I was hoping someone would be able to shed come light on this for me?

---

### Post by Ben Leedham on 2009-08-27
I should have been setting the umask to 002.

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

