---
title: "Permissions for multiple users editing websites"
date: 2011-07-09
forum: Security
---

### Post by archigos on 2011-07-09
I'm looking to figure out the best way to set permissions for multiple users to edit websites.  These websites do not belong to any specific user.  I'm looking to break it down into three categories that certain users may or may not have permission to access.
[LIST]
[*]Internal - These are internal-facing websites.
[*]External - These are external-facing websites.
[*]Client - These are client's websites.  This is where it gets tricky because they're websites that we develop and host but, on occasion, a client will want to have access to their specific website as well.
[/LIST]

How can I go about categorizing these with permissions so that one of our staff may have access to only certain of these directories?  Furthermore, how can I then allow certain users to access only certain subdirectories of the client directory?

Or, am I going about this all wrong?  How would you organize these to be able to break access down in the manner I'm referring?

---

### Post by bodhi.zazen on 2011-07-10
Well, your permissions are going to get complicated fast as it sounds as if you have a large number of users with diverse access needs.

IMO the easiest is going to be to have the most restrictive group owned by root.

The second group of pages should be owned by another user, sat staff.

The client pages should be owned by the clients.

The group of all pages should be www-data (apache) .

Initial permissions of directories / files will be 
directories 750
files 640

Then use ACL to allow various staff to access various things.

[http://www.ghacks.net/2010/01/28/further-control-of-linux-files-with-acl/](http://www.ghacks.net/2010/01/28/further-control-of-linux-files-with-acl/)

That should at least get you started ;)

---

### Post by archigos on 2011-07-10
Thank you!  ACL looks to be -exactly- what the doctor ordered.  I'll have to do some reading up about defaults for directories and such so that new files get the right permissions by default, but it looks like its the answer.
I figure I'll set up user accounts for clients and place our own sites in /var/www, then perhaps symlink to client sites for ease of access.

---

### Post by archigos on 2011-07-10
Hmm... there's something I'm not quite getting.

```
jrokeach@rino:~$ groups jrokeach
jrokeach : jrokeach admin external-www internal-www client-www
jrokeach@rino:~$ getfacl /var/www
getfacl: Removing leading '/' from absolute path names
# file: var/www
# owner: root
# group: www-data
user::rwx
group::r-x
group:external-www:r--
group:internal-www:r--
group:client-www:r--
mask::r-x
other::---

jrokeach@rino:~$ cd /var/www
-bash: cd: /var/www: Permission denied
jrokeach@rino:~$ ls -al /var/www
ls: cannot access /var/www/..: Permission denied
ls: cannot access /var/www/.: Permission denied
ls: cannot access /var/www/index.html: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
-????????? ? ? ? ?                ? index.html
```

Shouldn't I be able to cd into that directory given those permissions?

---

### Post by bodhi.zazen on 2011-07-10
My guess is you need to change your primary group, try newgrp (this will start a new shell).

see man newgrp ;)

---

### Post by archigos on 2011-07-10
I found the problem: I happen to be an idiot.
I figured that +r access to a directory was sufficient; I needed to add +x.  Once I did so, it worked perfectly.

---

### Post by bodhi.zazen on 2011-07-10
> **archigos said:**
> I found the problem: I happen to be an idiot.
I figured that +r access to a directory was sufficient; I needed to add +x.  Once I did so, it worked perfectly.

Fantastic =)

Keep in mind, if you add a user to a group, the effect does not take place until a new shell is started.

As you have multiple sites, I typically use virtual hosts with Apache, with organization of 

/var/www/site_1
/var/www/site_2

Depending on the complexity of the sites you may wish

/var/www/site_1/html -> html pages
/var/www/site_1/php -> php scrpits
/var/www/site_1/css -> css 
/var/www/site_1/js -> java script

well, you get the idea, the more complex a site the more it helps to keep separate directories.

As it sounds s if your sites may be quite complex, initial planning goes a long ways.

---

