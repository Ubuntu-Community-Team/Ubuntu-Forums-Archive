---
title: "Mysql server not starting"
date: 2018-08-02
forum: Server Platforms
---

### Post by thompsonavc on 2018-08-02
Hi, I am still newish to Ubuntu and getting the below error when attempting to start

[….] Starting mysql (via systemctl): mysql.servicejob for mariadb.service failed because  control process exited with error code.
See “systemctl status mariadb.service” and “journalctl -xe” for details.

Any advice would be much appreciated

---

### Post by thompsonavc on 2018-08-02
systemctl status mariadb.service output [https://ibb.co/g0TZMK](https://ibb.co/g0TZMK)

---

### Post by thompsonavc on 2018-08-02
&#9679; mariadb.service - MariaDB database server
   Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2018-08-02 12:53:17 BST; 25min ago
  Process: 13154 ExecStart=/usr/sbin/mysqld $MYSQLD_OPTS $_WSREP_NEW_CLUSTER $_WSREP_START_POSITION (code=exited, status=1/FAILURE)
  Process: 13055 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR= ||   VAR=`/usr/bin/galera_recovery`; [ $? -eq 0 ]   && systemctl set-environment _WSREP_START_POSITION=$VA
  Process: 13053 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (code=exited, status=0/SUCCESS)
  Process: 13052 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var/run/mysqld (code=exited, status=0/SUCCESS)
 Main PID: 13154 (code=exited, status=1/FAILURE)
   Status: "MariaDB server is down"


Aug 02 12:53:13 TGWOLV-LMS01 systemd[1]: Starting MariaDB database server...
Aug 02 12:53:14 TGWOLV-LMS01 mysqld[13154]: 2018-08-02 12:53:14 140256223329408 [Note] /usr/sbin/mysqld (mysqld 10.1.29-MariaDB-6) starting as process 13154 ...
Aug 02 12:53:17 TGWOLV-LMS01 systemd[1]: mariadb.service: Main process exited, code=exited, status=1/FAILURE
Aug 02 12:53:17 TGWOLV-LMS01 systemd[1]: mariadb.service: Failed with result 'exit-code'.
Aug 02 12:53:17 TGWOLV-LMS01 systemd[1]: Failed to start MariaDB database server.

---

### Post by SeijiSensei on 2018-08-02
Are you using sudo?

```
sudo systemctl start mysql
```

You cannot start most daemons as an ordinary user. Only root can do that.

---

### Post by LHammonds on 2018-08-03
@SeijiSensei, in his screenshot, I can see he is the root user issuing those commands.  Had to rotate the image and zoom in, but its there. :-)

@thompsonavc, let's see the output of your file system:

```
df -h
```

Was this the server that ran out of space and filled up the root partition (which everything is in root)?  Is that the source of when the database service stopped working?

**EDIT:** Based on the timing of [your prior thread](https://ubuntuforums.org/showthread.php?t=2397637) and the start of this one, seems like this is the Moodle/MariaDB server that had its file system filled up and partition switched to read-only mode.  So I guess the boot CD worked and you cleared off enough space to boot the system.

Here are some places to look (but keep in mind that this is not a config issue since it was running before the crash)

[https://mariadb.com/kb/en/library/what-to-do-if-mariadb-doesnt-start/](https://mariadb.com/kb/en/library/what-to-do-if-mariadb-doesnt-start/)

LHammonds

---

### Post by thompsonavc on 2018-08-03
Needed to clear space in ./cache directory in order to fix mariadb issues. Ken from the Moodle forum has been very helpful with all this. Starting to gain more knowledge in Ubuntu and linux in general. Hope to continue my knowledge journey.

---

