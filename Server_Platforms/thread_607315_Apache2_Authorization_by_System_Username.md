---
title: "Apache2 Authorization by System Username"
date: 2007-11-08
forum: Server Platforms
---

### Post by MasterXandrex on 2007-11-08
All,

I need to find a way to authorize users to view web directories by system username and password. I am fine with juggling users between groups if that's what is takes.

Please let me know,

Xan

---

### Post by bunker on 2007-11-09
Not 100% on what you mean, but you can set up different virtualhosts to run as different system users with the User and Group directives.  If you wanted to do something where the permissions of a remote user are determined by file system permissions, you would need to look into scripting something.  I'm not sure if it would be particularly secure to sync with /etc/passwd though, plus I think it could end up being fairly easy to break out of the limited permissions.  Have you considered just setting up an ssh server, or encrypted ftp?

---

### Post by MasterXandrex on 2007-11-09
Both of these I have, the sftp and ssh servers. However, I need something that can be accessed from a web browser over port 80 -- don't ask why, suffice it to say, some people are anal about such things. 

Also, I don't need to control user access based on file system permissions, I rather would simply like to make sure that in order for a person to access a directorythey have a valid username to my system and belong to a give user group.

Xan

---

### Post by MJN on 2007-11-09
You need the libapache2-mod-auth-pam package/module - I've got no experience of it but it sounds like exactly what you want.
 
([http://pam.sourceforge.net/mod_auth_pam/](http://pam.sourceforge.net/mod_auth_pam/) is the project homepage however looking at the page it sounds like [mod_authnz_external]("http://mod_authnz_external") is what you need for using /etc/shadow which your system likely uses)
 
Mathew

---

