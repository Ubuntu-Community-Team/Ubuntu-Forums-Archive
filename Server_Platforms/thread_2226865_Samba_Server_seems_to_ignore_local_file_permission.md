---
title: "Samba Server seems to ignore local file permissions"
date: 2014-05-29
forum: Server Platforms
---

### Post by Leegaert on 2014-05-29
Hi.

I'm running Ubuntu Server 12.04 and I'm experiencing a problem with my Samba setup.

I've created some groups to easily grant permissions on my samba shares. Some shares have two groups as valid users. A read only group and a group with read write permissions on the files and directories. The read write group has full access as you can see below.
Now, the problem is that the members of the mediausers-ro group still have write access through Samba although they only have the "other" permissions, i.e. read and execute on directories.

How can I fix this?

```

drwxrwsr-x 20 monco mediausers-rw 4096 Apr  5 16:54 ./
drwxrwsr-x  4 monco mediausers-rw 4096 Mar 23 17:54 ../
drwxrwsr-x  8 monco mediausers-rw 4096 Mar 23 17:55 10cc/
drwxrwsr-x 18 monco mediausers-rw 4096 Apr  6 12:41 AC DC/
drwxrwsr-x  3 monco mediausers-rw 4096 Mar 23 22:07 Deep Purple/
drwxrwsr-x  8 monco mediausers-rw 4096 Mar 23 22:48 Dire Straits/
drwxrwsr-x  7 monco mediausers-rw 4096 Apr  6 11:00 The Police/
...

```

This is my samba config.
```

#======================= Global Settings =======================

[global]
   workgroup = WORKGROUP
   server string = Samba %v on (%L)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   invalid users = root bin daemon adm sync shutdown \
                        halt mail news uucp operator monco


# CUSTOM GLOBAL
   hide dot files = yes
   hide unreadable = yes
   guest ok = no
   read only = no
   browsable = no
   force user = monco
   create mask = 0664
   force directory mode = 2775
   follow symlinks = yes
   wide links = yes
   unix extensions = no


#======================= Share Definitions =======================
[backup]
   comment = Backup disk
   path = /srv/backup
   valid users = @mgmtusers

[download]
   comment = Download disk
   path = /srv/download
   valid users = @dwnldusers

[documents]
   comment = Documents share
   path = /srv/documents
   valid users = @docusers
   browsable = yes

[pictures]
   comment = Pictures share
   path = /srv/pictures
   valid users = @pictusers-rw @pictusers-ro
   browsable = yes

[series]
   comment = Series share
   path = /srv/series
   valid users = @mediausers-rw @mediausers-ro 
   browsable = yes

[music]
   comment = Music share
   path = /srv/music
   valid users = @mediausers-rw @mediausers-ro
   browsable = yes

[movies]
   comment = First movies disk
   path = /srv/movies
   valid users = @mediausers-rw @mediausers-ro
   browsable = yes

```

---

### Post by Leegaert on 2014-06-02
Does anybody have any idea?

I discovered something else:
In one of the shared folders, there is a folder lost+found:
```

drwxrwsr-x  2 root  root       16384 Dec 20 20:00 lost+found/

```

When I access that share with a user that is not part of the root group, I can still access that folder and modify it. Normally the folder should be hidden because of this smb.conf line:
```

hide unreadable = yes

```

I'm clearly missing something here but I have no idea what...

---

### Post by sweekly44 on 2014-06-02
Try adding the line "read only = yes"  and "write list = +(name of group with read/write privileges)" to the music group. Although I'm not sure this would let the group with read privileges also execute files.

---

### Post by Morbius1 on 2014-06-02
> Now, the problem is that the members of the mediausers-ro group still  have write access through Samba although they only have the "other"  permissions,
"Valid users" will restrict who gains access to the share but once they are allowed in everyone on every share you defined is converted to "monco" because of this line in the [global] section of your smb.conf:
> force user = monco
After the connection is made everyone is monco so they will be able to do whatever monco can do.

---

### Post by Leegaert on 2014-06-02
@Morbius1,

Thanks a bunch! That was it, how stupid of me :)
I was under the impression that it would force the owner on newly created files.

I'll mark this thread as solved!

---

