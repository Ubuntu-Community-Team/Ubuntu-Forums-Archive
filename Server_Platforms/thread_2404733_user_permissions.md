---
title: "user permissions"
date: 2018-10-27
forum: Server Platforms
---

### Post by albertocastillo2001 on 2018-10-27
Hello

I setup a VPS with Ubuntu Server 16.04. Created a few users and surprisingly, users can see eachother documents. I checked the file permissions for any newly created file:
[LIST]
[*]groups have rw
[*]others have r
[/LIST]

How come others can have read permissions? It's a server. How come users can see eachother. Is Ubuntu Server set up as this on purpose?

Thanks

---

### Post by TheFu on 2018-10-28
User permissions can be set to be anything the user wants.
An admin can override the initial settings or make the defaults at account creating be something else.
This stuff is usually covered in the first few classes for a beginning Linux admin course.
Different VPS images can be configured in any way the person/organization who created the image wants.

I wouldn't assume that all installed versions of Ubuntu Server have the same defaults unless the exact same source is used.  VPS providers often tweak the setups.

On a "server", generally, it is desirable to have users working together, so the userids might be put into the same group, then r-x permissions setup by default for the group.  

If you are going to run a Unix server (and Linux is Unix-like), then you'll want to fully understand the cornerstone of all Unix security. That is file and directory permissions.  There are tutorials - any of them for Unix would apply for end-users.  Unix permissions are Unix permissions around the world - doesn't matter if the system runs Ubuntu, Redhat, AIX, Solaris, HP-UX, iOS, MacOS, Android, ... all same-same in how they work, though the defaults and setups can be different.

For configuring the defaults you'd like, you'll need to stick with Ubuntu/Debian specific guides.  You can find free Admin books here: 
[https://www.lpi.org/how-to-get-certified/free-training-materials](https://www.lpi.org/how-to-get-certified/free-training-materials) . Of course, you can buy an Ubuntu Admin book, if you prefer, but when you do that, you'll be getting an Ubuntu-slanted book and not gaining the extra knowledge for how the different Linux distros change things slightly from each other.

For end-users, Linux and Unix are 90% the same.  For Systems Administration, the remaining 10%, the changes are much more important across Unix-like systems.

BTW, if you want direct help, please post **ls -l** output along with 'id' output for the involved userids. We know permissions stuff extremely well here. If you do, please, please, use code tags so it lines up and is readable. Here's an example.
```

$ ll
total 52
drwxrwxrwt 12 root    root   4096 Oct 28 20:07 ./
drwxr-xr-x 31 root    root   4096 Oct 27 12:43 ../
-rw-------  1 thefu   thefu    0 Oct 28 19:05 config-err-uHaRPy
```
Seeing that output is much easier than trying to read and parse a textual description.

---

### Post by albertocastillo2001 on 2018-11-07
Hi!

Thanks for your reply.
Yes, I am aware of how the security is managed and know how the permissions work. However it was quite surprising for me to see that by default, users could see file contents of other users, the "other" permissions are set to read by default.

Thanks!

---

