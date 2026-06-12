---
title: "[SOLVED] Samba sharing out Apache htdocs - permissions"
date: 2008-10-14
forum: Server Platforms
---

### Post by batfastad on 2008-10-14
Hi everyone
I've recently added Apache PHP5 and MySQL5 to Ubuntu server. Mainly that box is a NAS, but we need to buy a new machine so for a short while this box will be performing both duties. It's got more than enough grunt though.

I'm looking to add a share in Samba to share out our www docs folder, so that I can edit the intranet source files over the network.

Just wondering what permissions files / folders that Apache shares out should be given?
The only file in my /var/www folder is the index.html that gets created at installation.
I've made some mods to httpd.conf and apache2.conf but nothing that changes anything drastic.

The permissions on that default index.html are:
```
-rw-r--r-- root root
```
That equals 644 when I do stat -c "%a" /var/www/index.html


The permissions on the /var/www directory are:
```
drwxr-xr-x root root
```
Which equals 755 when I do stat -c "%a" /var/www/


When I view processes it appears httpd runs under it's own user account, www-data
Should the files I place in my Apache docs also have owner/group as www-data?
Or is leaving it as root ok?
Just wondering what the standard Apache admin practice should be?

Here's the code I've got in my intranet Samba share:
```
[intranet]
path = /var/www
browseable = yes
public = yes
writeable = yes
read only = no
guest only = yes
guest ok = yes
create mask = 2660
directory mask = 2770
force group = sambaaccess
```

sambaaccess is the group name of a group I set up specifically for Samba sharing. The above Samba permissions are set so that anyone can access/edit/delete files from the share - that is how I intend it whilst I'm developing. Then I'll make it readonly

Are the create mask, directory mask, force group all set ok for this?
Or should I change force group to root or www-data?
And change create mask to 644 (like current index.html permissions)?
And directory mask to 755 (like current /var/www directory permissions)?

I'm guessing I should change the smb.conf so it sets the permissions to match what the Apache installation default has given me
Thought I better check and get it right from the beginning!

Any advice/suggestions?

Thanks, Ben

---

### Post by mbeach on 2008-10-14
edit: bad suggestion from me removed.

---

### Post by lykwydchykyn on 2008-10-15
You do *not* want www-data owning the web data.  www-data should have read and execute permissions only.

I usually create a group called "webadmins" and make sure all files belong to webadmins, and all permissions are 775.  Owner of the files can be root or some other user, doesn't really matter (just not www-data).

Then in samba use "force group = webadmins" and use the "force create mode" and "force directory mode" directives to make sure permissions stay at 775.

---

### Post by batfastad on 2008-10-16
Ok sorted!
Just wanted to make sure I was getting it correct.

Thanks, Ben

---

