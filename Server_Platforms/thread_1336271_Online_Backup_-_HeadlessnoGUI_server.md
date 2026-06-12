---
title: "Online Backup - Headless/noGUI server"
date: 2009-11-24
forum: Server Platforms
---

### Post by TheGameAh on 2009-11-24
Hey guys.

Running a simple Samba box, CentOS based.  Was going to setup a spare machine with BackupPC to host backups, but wanted to lean more towards something that would do the same but offsite.  I know of some the services, Jungledisk, iBackup (expensive).  Are there any recommendations for a server with no gui for online backup?

---

### Post by Denbert on 2009-11-24
> **TheGameAh said:**
>  Are there any recommendations for a server with no gui for online backup?

Install webmin on the server you want to backup.

Setup another server called server2 and add a user  e.g. backupghost :D

Go to your webmin page on server you want to backup and choose the Filesystem Backup module:

[IMG]http://hegnstoften.net/pictures/webmin-backup/file-system-backup.png[/IMG]

Choose dir to backup:

[IMG]http://hegnstoften.net/pictures/webmin-backup/file-system-backup_step_01.png[/IMG]

Setup where your backup goes: here shown to server2, with username and file - note the extension gz.tar - tar was set earlier, gz compression is set in next step:

[IMG]http://hegnstoften.net/pictures/webmin-backup/file-system-backup_step_02.png[/IMG]

Set backup option - Here i only set Backup Label and compression mode:

[IMG]http://hegnstoften.net/pictures/webmin-backup/file-system-backup_step_03.png[/IMG]

Here you schedule your backup - I've showed the simple weekly setting below - can be set very flexible:

[IMG]http://hegnstoften.net/pictures/webmin-backup/file-system-backup_step_04.png[/IMG]

If you hit Create and Backup now button, you will proably see an error - this is due to the missing SSH key. As this is made over ssh you need to connect to the destination server via ssh in order to receive ssh key and accept the key:

```
#su backupuser
# ssh 192.168.9.253
The authenticity of host '192.168.9.253 (192.168.9.253)' can't be established.
RSA key fingerprint is e1:17:14:36:bc:70:c3:47:03:01:6b:40:01:ca:67:85.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.9.253' (RSA) to the list of known hosts.

```

And now you have a fast and secure backup solution, which runs rock steady over LAN and WAN :guitar:

---

