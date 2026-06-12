---
title: "Rsnapshot and Postgresql, permission issues."
date: 2010-12-08
forum: Server Platforms
---

### Post by draperdt on 2010-12-08
Hey Guys,

I have a server with a postgres database, apache and a custom java application.

I am trying to run rsnapshot to backup /home /etc and /var folders.  

But I am running into issues with rsnapshot and permissions. More specifically these kind of errors, 

```

rsync: send_files failed to open "/etc/postgresql/8.3/main/pg_hba.conf": Permission denied (13)
```

I look at the permissions on these files with ls -la, I get

```
-rw-r----- 1 postgres postgres 3617 2010-05-11 04:05 /etc/postgresql/8.3/main/pg_hba.conf 
-rw-------   1 root bin    77 2010-05-07 00:52 config

```

The owner of the files is root and postgres users. I am using passwordless login to connect to server as user XYZ. XYZ has root access to the server and to the database.

These files are all over the place. Some in /etc and some in /var/lib for instance.  How can I best copy these remaining  files. 

Or do you have any other suggestion? I just need to back up these important files somehow.

Thanks

---

### Post by SeijiSensei on 2010-12-09
It doesn't look like the remote user has root privileges.

I'd suggest using rsync in its daemon mode on the remote.  Run "sudo /usr/bin/rsync --daemon".  You'll need an /etc/rsyncd.conf file as well.  The simplest one will be something like

```

[backup]
path = /path/to/backup/directory
uid  = root
gid  = root

```

On the client make sure the rsync request looks like this:

```
cd /
rsync -av etc home var server::backup
```

Note the double colons.  "man rsync" for more details.

---

