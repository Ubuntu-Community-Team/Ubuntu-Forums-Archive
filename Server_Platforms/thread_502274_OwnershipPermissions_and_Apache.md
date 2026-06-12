---
title: "Ownership/Permissions and Apache"
date: 2007-07-16
forum: Server Platforms
---

### Post by igknighted on 2007-07-16
I have an Ubuntu server running, and I do all my web design on a windows box using Dreamweaver.  Dreamweaver lets me edit the files directly on the server via FTP, but I am having all sorts of permissions issues.  For php/mysql to be happy I need to have the files owned by www-data.  But I cannot log in to FTP as www-data and so the permissions are 777 so that Dreamweaver can read and write via its FTP properly.  Everything is working OK now, but I am worried about leaving the permissions at 777 and any security risks that would cause.  Right now it is not an issue because the site is still under development and the server is only accessible from the local network, but once it goes live what should the permissions be?  Note that I will still need Dreamweaver to have access to the page as some of the users editing content will have no linux (or in some cases even real web design) knowledge.

---

### Post by Mr. C. on 2007-07-16
Which ftp server ?  How is it configured ?

You'll want to use group permissions to help this situation.

What user do you log in as via DreamWeaver ?

MrC

---

### Post by igknighted on 2007-07-17
> **Mr. C. said:**
> Which ftp server ?  How is it configured ?

You'll want to use group permissions to help this situation.

What user do you log in as via DreamWeaver ?

MrC

I am using vsftpd, and I am using my normal user to log in.  I really didn't do much configuration, never really played all that much with ftp before.

---

### Post by Mr. C. on 2007-07-17
I'm not at my system right now; can you or someone show me the output of :

```
egrep 'www|sql'  /etc/group
```

I believe you can own the files, and you can change their group to www-data, with permissions 644.  This allows you to write, apache/php/everyone else can read them.

You don't need to make *files* have the execute bit (eg. 644 vs 755, or 666 vs. 777).  Only directories need the examine bit (755).

Only you need to be able to write the files, since you log in as your self, a local user.

You will want to configure vsftpd.conf to set the local_umask to 022.  Add the following to /etc/vsftpd.conf:

```
local_umask=022
```

and restart vsftpd:

```
/etc/init.d/vsftpd restart
```

This will create new files so that you can read/write, and group/others can read.

The 777 permissions whlie excessive are not of major importance, as your allowing the world to read them via your website; the only concerns are local users logging onto your system writing your web files.  If there are no other users, this isn't that big a deal.

MrC

---

### Post by igknighted on 2007-07-18
> **Mr. C. said:**
> I'm not at my system right now; can you or someone show me the output of :

```
egrep 'www|sql'  /etc/group
```

I believe you can own the files, and you can change their group to www-data, with permissions 644.  This allows you to write, apache/php/everyone else can read them.

You don't need to make *files* have the execute bit (eg. 644 vs 755, or 666 vs. 777).  Only directories need the examine bit (755).

Only you need to be able to write the files, since you log in as your self, a local user.

You will want to configure vsftpd.conf to set the local_umask to 022.  Add the following to /etc/vsftpd.conf:

```
local_umask=022
```

and restart vsftpd:

```
/etc/init.d/vsftpd restart
```

This will create new files so that you can read/write, and group/others can read.

The 777 permissions whlie excessive are not of major importance, as your allowing the world to read them via your website; the only concerns are local users logging onto your system writing your web files.  If there are no other users, this isn't that big a deal.

MrC

Yes, this account is the only one used.  The server has the LAMP stack and an email server which is remotely admin'ed (scalix).  If there isn't an issue with excessive permissions I may just leave it.

FWIW, here is the output of the command you requested: ```
mysql:x:27
```

---

### Post by Mr. C. on 2007-07-18
Ok.

Since mysql is in one group, apache/php in another, and you are the owner, the only way to remove the other's write permissions would be to either create a new group, and place both apache/php and mysql in that group, and change the group ownership of the files to that new group, or place mysql in the www-data group, and make all files group www-data.  This would allow 644 permissions.

MrC

---

