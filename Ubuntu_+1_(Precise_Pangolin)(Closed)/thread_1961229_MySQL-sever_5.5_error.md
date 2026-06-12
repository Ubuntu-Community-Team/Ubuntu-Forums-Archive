---
title: "MySQL-sever 5.5 error"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fady_fod on 2012-04-18
I upgraded to Ubuntu 12.04 months ago . Every thing went OK !
Ubuntu 12.04 was working perfectly !

Suddenly after some update this Week MySQL gave these errors :

> Setting up mysql-server-5.5 (5.5.22-0ubuntu1) ...
120419  3:34:44 [Note] Plugin 'FEDERATED' is disabled.
120419  3:34:44 InnoDB: The InnoDB memory heap is disabled
120419  3:34:44 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120419  3:34:44 InnoDB: Compressed tables use zlib 1.2.3.4
120419  3:34:44 InnoDB: Initializing buffer pool, size = 128.0M
120419  3:34:44 InnoDB: Completed initialization of buffer pool
120419  3:34:44 InnoDB: highest supported file format is Barracuda.
120419  3:34:44  InnoDB: Waiting for the background threads to start
120419  3:34:45 InnoDB: 1.1.8 started; log sequence number 1616050
ERROR: 130  Incorrect file format 'user'
120419  3:34:45 [ERROR] Aborting

120419  3:34:45  InnoDB: Starting shutdown...
120419  3:34:46  InnoDB: Shutdown completed; log sequence number 1616050
120419  3:34:46 [Note] /usr/sbin/mysqld: Shutdown complete

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
 Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
I tried to purge mysql-server ,mysql-common ,mysql-server-5.5 and reinstall . But the same errors 

Error.log (/var/log/mysql/)
> 

120224 11:38:24 [Note] Plugin 'FEDERATED' is disabled.
120224 11:38:24  InnoDB: Initializing buffer pool, size = 8.0M
120224 11:38:24  InnoDB: Completed initialization of buffer pool
120224 11:38:24  InnoDB: Started; log sequence number 0 44233
120224 11:38:24 [Note] Event Scheduler: Loaded 0 events
120224 11:38:24 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.58-1ubuntu1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
120224 11:38:48 [Note] /usr/sbin/mysqld: Normal shutdown

120224 11:38:48 [Note] Event Scheduler: Purging the queue. 0 events
120224 11:38:48  InnoDB: Starting shutdown...
120224 11:38:49  InnoDB: Shutdown completed; log sequence number 0 44233
120224 11:38:49 [Note] /usr/sbin/mysqld: Shutdown complete


:confused:

Any help will be appreciated !

---

### Post by radiofranky on 2012-04-25
I'm also getting this error message and my mysql shuts down every 1 min or so.


120407  0:01:01 [Note] Event Scheduler: Purging the queue. 0 events
120407  0:01:01  InnoDB: Starting shutdown...
120407  0:01:03  InnoDB: Shutdown completed; log sequence number 1 2001721234
120407  0:01:03 [Note] /usr/sbin/mysqld: Shutdown complete

120407  0:01:03 [Note] Plugin 'FEDERATED' is disabled.
120407  0:01:03  InnoDB: Initializing buffer pool, size = 8.0M
120407  0:01:03  InnoDB: Completed initialization of buffer pool
120407  0:01:03  InnoDB: Started; log sequence number 1 2001721234
120407  0:01:03 [Note] Event Scheduler: Loaded 0 events
120407  0:01:03 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.54-1ubuntu4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
120407  0:02:01 [Note] /usr/sbin/mysqld: Normal shutdown

120407  0:02:01 [Note] Event Scheduler: Purging the queue. 0 events
120407  0:02:01  InnoDB: Starting shutdown...
120407  0:02:03  InnoDB: Shutdown completed; log sequence number 1 2001725205
120407  0:02:03 [Note] /usr/sbin/mysqld: Shutdown complete

120407  0:02:03 [Note] Plugin 'FEDERATED' is disabled.
120407  0:02:03  InnoDB: Initializing buffer pool, size = 8.0M
120407  0:02:03  InnoDB: Completed initialization of buffer pool
120407  0:02:03  InnoDB: Started; log sequence number 1 2001725205
120407  0:02:03 [Note] Event Scheduler: Loaded 0 events
120407  0:02:03 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.54-1ubuntu4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
120407  0:03:01 [Note] /usr/sbin/mysqld: Normal shutdown

120407  0:03:01 [Note] Event Scheduler: Purging the queue. 0 events
120407  0:03:01  InnoDB: Starting shutdown...
120407  0:03:03  InnoDB: Shutdown completed; log sequence number 1 2001731489
120407  0:03:03 [Note] /usr/sbin/mysqld: Shutdown complete

---

### Post by Milos_SD on 2012-04-25
Try this.

```
sudo gedit /etc/mysql/my.cnf
```

even if there is something in there, replace it with this: [http://paste.ubuntu.com/928346/](http://paste.ubuntu.com/928346/)

Save the file and then do:

```
sudo dpkg --reconfigure -a
```

---

