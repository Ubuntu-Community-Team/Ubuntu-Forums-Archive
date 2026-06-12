---
title: "Planning Samba Permissions"
date: 2011-01-27
forum: Server Platforms
---

### Post by Kljuka on 2011-01-27
I have a directory with 2 subdirectories that I want to share with other Windows computers:
```

/var/store/
/var/store/restricted
/var/store/public
```2 users will access this directory. They need to have the following permissions:
```
userplus:
rwx /var/store (so read and write permissions on the whole directory tree)

user2:
rwx /var/store/public (everything on directory public)
r-x /var/store/restricted (only read access to directory restricted)
```This needs to work even with newly created files and dirs:

[LIST]
[*] if userplus creates files (and dirs) in /var/store/restricted, they need to be only readable by user2
[/LIST]

[LIST]
[*] if userplus creates files (and dirs) in /var/store/public, they need to be writable by user2
[/LIST]
 

Can this be done? In reality, there will be more directories (not only public and restricted), but following the same concept. Thank you for your help.

---

### Post by datamove on 2011-01-27
So called "Sticky bit" on directory (chmod g+s or chmod u+s ) should help here. Read the man page for chmod or search the topic on internet.

---

### Post by Kljuka on 2011-01-27
Thank you datamove. That solved the problem.

In case someone wants to know how I did it:

I created 2 groups (in linux): everyone and privileged. I put privileged users in both groups, non privileged (the ones with only read access to restricted dir) in everyone.

Then managed restricted directory (for users in privileged group):
```
chmod 775 /var/store/restricted
chmod g+s /var/store/restricted
chown whatever:privileged /var/store/restricted
```And for public directory (for everyone):
```
chmod 775 /var/store/public
chown whatever:everyone /var/store/public
```And then Samba magic :D
added in /etc/samba/smb.conf
```
[store]
        comment = Storage
        path = /var/store/
        write list = +userplus +user2
        valid users = @everyone
        readonly = yes
        public = no
        create mask = 0774
        directory mask = 0775
        force group = everyone
```That's it. If I made some mistake (or security hole), please correct me.

---

