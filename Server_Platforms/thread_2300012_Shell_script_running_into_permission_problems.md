---
title: "Shell script running into permission problems ?"
date: 2015-10-23
forum: Server Platforms
---

### Post by jaesun on 2015-10-23
[B]Edit: Stupid me, mispelled something in my script. Ran into another error, but unrelated to permissions
[/B]
OS: Ubuntu 14.04 LTS Server

I am trying to execute a shell script (script located here: [https://wiki.postgresql.org/wiki/Automated_Backup_on_Linux](https://wiki.postgresql.org/wiki/Automated_Backup_on_Linux) )

Username when I log into the server: jaesun (also verified by running whoami)

Directory I am in: /home/jaesun

Directory permissions as by running "ls -l /home/":
```
drwxr-xr-x 8 jaesun jaesun 4096 Oct 22 18:30 jaesun
```

Directory permissions as by running "ls -l /home/jaesun/":
```
drwxrwxr-x 2 jaesun jaesun      4096 Oct 22 18:15 backups
-rw-rw-r-- 1 jaesun jaesun      1407 Oct 22 18:30 pg_backup.config
-rwxrwxr-x 1 jaesun jaesun      4878 Oct 22 18:17 pg_backup_rotated.sh
-rwxrwxr-x 1 jaesun jaesun      3992 Oct 22 18:16 pg_backup.sh

```

script is located here: /home/jaesun/pg_backup.sh with 775 permissions (I did chmod +x pg_backup.sh)

the script is trying to create the following directories within the home directory:
/home/jaesun/backups
/home/jaesun/backups/2015-10-22/

I run the script (presumably as me): 

```
jaesun@dc-jira01:~$ ./pg_backup.sh
```

But I get the following errors:

```
jaesun@dc-jira01:~$ ./pg_backup.sh
Making backup directory in /home/jaesun/backups/2015-10-22/
mkdir: cannot create directory â/home/jaesunâ: Permission denied
Cannot create backup directory in /home/jaesun/backups/2015-10-22/. Go and fix it!
```

if I run the command it is trying to run:

mkdir -p /home/jaesun/backups/2015-10-22/

it runs fine.

I updated the script to output the user it is running as, and it shows jaesun as the user. 

echo $(id -un);
whoami;

results in:
jaesun
jaesun

Not sure what I am doing wrong? it should have permissions to create the directory. not sure if I am missing a step here? I'm logged in as jaesun, and I am trying to let it create a folder, in a folder owned by me with 775 permissions, so I would think it should be fine.

---

