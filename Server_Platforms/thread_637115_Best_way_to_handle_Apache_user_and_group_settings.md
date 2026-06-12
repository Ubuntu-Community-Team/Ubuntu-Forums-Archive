---
title: "Best way to handle Apache user and group settings"
date: 2007-12-10
forum: Server Platforms
---

### Post by coquimbo on 2007-12-10
I'd like some clarification on a point.  

Apache2's default configuration is to run as www-data:www-data.  That's for security reasons, and should never be set to your user account.   However, it's really annoying to have to use sudo to create a file in the /var/www directory every time, or to copy files over.  Would it be a security risk to add my user account to the www-data group?  Or should I just set the owner of /var/www to my user account?  

What has been the best way you have set up your apache server and files without sacrificing security?

---

### Post by Portable_Jim on 2007-12-10
I do not think it would compromise security. It would allow you to access & modify more files, but the server cannot access more files.

---

