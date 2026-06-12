---
title: "Samba share with root access"
date: 2008-08-24
forum: Server Platforms
---

### Post by MoClvland on 2008-08-24
Hi, I am trying to setup a samba share to my /var/www directory so that I can easily upload my web files from dreamweaver. But I can't seem to get the share to work, I can't logon to the share from my XP machine.  I can logon to a non root share just not the root share.  


I've searched the internet and what I found was this:

```
[config]
        comment = Admin Config Share  - Whatever
        path = /var/www
        valid users = george
        force user = root
        force group = root
        admin users = george  
        writeable = Yes
```

But it doesnt seem to work.  

Any help would be appreciated, thanks.

---

### Post by Iowan on 2008-08-24
There MUST be a better way to access the files than opening them as root, but...
The default **/etc/samba/smb.conf** file has a line:```
   invalid users = root
```Did you take that out?

---

### Post by MoClvland on 2008-08-24
Thanks, I did remove that line.  

Actually I'm not sure if there is a better way.  

I've been running a web site with apache on windows for several years and I'm just now switching to linux.  Of course with windows this is not a problem.  

Should the web site files (html, php) have root permissions or should they be something different?  I kept them as root because the /var/www/ directory is root.  How do most people handle that?

---

### Post by bab1 on 2008-08-24
There is no need for the files to be owned by root.  I believe this is poor practice.  Who do you want to be the owner of the files in /var/www ?  Who is the owner of the directory?  You can force the ownership of the subdirectories and files with the use of "sticky bits" in Linux.  You can can use "force user" and "force group" to change the authenticated user to the forced user and group in Samba.

This is how I use it for my backups:```
[Backup]
        comment = Domain Backups
        path = /smb/backup
;       guest ok = no
        valid users = bruce +smbusers
        force group = smbusers
; Valid users "bruce" is the backup admin
; valid users that are groups use the "+" sign
        writable = yes
        create mask = 0770
        directory mask = 3770

```

---

### Post by MoClvland on 2008-08-24
Ok, that helps.  

So just to be clear, the files for the website (usually located in /var/www ) can be owned by another user and group, other than root.

That actually makes sense, and I'm guessing thats not a security risk?

Thanks again.

---

### Post by bab1 on 2008-08-24
> **MoClvland said:**
> ...

So just to be clear, the files for the website (usually located in /var/www ) can be owned by another user and group, other than root.

That actually makes sense, and I'm guessing thats not a security risk?

Thanks again.

No it's not a security risk.  When the browser ask for the file, Apache is responding to the request.

if you notice, I use /smb for all my windows share files.  I do this for neatness.  You could symlink the dirctory to the wwwroot.

---

