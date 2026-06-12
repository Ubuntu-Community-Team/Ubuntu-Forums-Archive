---
title: "Installing OpenNMS on Ubuntu"
date: 2008-11-18
forum: Server Platforms
---

### Post by dannym978 on 2008-11-18
Hi , i am trying to get open nms installed on hardy heron. I have followed the instructions in the post below but when i try to browse onto the GUI i get connection denied.

Does anyone have a idea why this may be the case?

[http://ubuntuforums.org/archive/index.php/t-883854.html](http://ubuntuforums.org/archive/index.php/t-883854.html)

Thanks

---

### Post by cariboo on 2008-11-18
Are there nay logs that you can check for error messages? They usually are locatede in /var/log.

Jim

---

### Post by dannym978 on 2008-11-23
Hi, no there arent any logs available.

Has anyone documented the opennms install on ubuntu, the various guides i have found dont work for varying reasons.

---

### Post by wirelessmonkey on 2008-11-23
Are you getting the permission denied error when trying to connect to opennms via browser on the local machine, or somewhere else?
Did you get any errors durning the installation?

Check and see if opennms is running... in a terminal type:

ps aux | grep nms


Did the command return anything?

You may need to start over from the beginning, so we can see if there are errors during installation.

Post back, and I'll help if I can.

---

### Post by Mach1US on 2009-11-03
I just tried the install of openNMS and encunered few problems.
It finishes with
```
- checking if iplike is usable... YES
- checking for stale eventtime.so references... OK

Installer completed successfully!
```
but before that i see this
```
INFO: Marking ChangeSet: 1.7.4/changelog.xml::1.7.4-categories-fix-missing-data::rangerrick::(MD5Sum: a01ad7492f6cae9e4085cc7f843d3ef8) ran due to precondition failure: 
          SQL Precondition failed.  Expected '0' got '6'
```
also this
```
INFO: Marking ChangeSet: 1.6.0/tables/quartz.xml::qrtz_locks-data::rangerrick::(MD5Sum: ef1165f6f8d76148669ab40b7f3975b) ran due to precondition failure: 
          SQL Precondition failed.  Expected '0' got '1'
```
```
INFO: Marking ChangeSet: 1.6.0/tables/atinterface.xml::1.6.0-recreate-hash-index::rangerrick::(MD5Sum: cda8ae7c6c1efacb5f55b9a5b4876cc1) ran due to precondition failure: 
          Index atinterface_nodeid_idx does not exist
```
```
INFO: Marking ChangeSet: 1.6.0/tables/distPoller.xml::1.6.0-distPoller-data::rangerrick::(MD5Sum: d74620928ab0522fd23a96c387e954c) ran due to precondition failure: 
          SQL Precondition failed.  Expected '0' got '1'
```
```
Configures PostgreSQL tables, users, and other miscellaneous settings.

- searching for jicmp:
  - trying to load /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/server/libjicmp.so: NO
  - trying to load /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libjicmp.so: NO
  - trying to load /usr/lib/jvm/java-6-sun-1.6.0.16/jre/../lib/amd64/libjicmp.so: NO
  - trying to load /libjicmp.so: NO
  - trying to load /usr/share/opennms/lib/libjicmp.so: NO
  - trying to load /usr/share/opennms/lib/linux32/libjicmp.so: NO
  - trying to load /usr/java/packages/lib/amd64/libjicmp.so: NO
  - trying to load /lib/libjicmp.so: NO
  - trying to load /usr/lib/libjicmp.so: NO
  - trying to load /usr/lib/jni/libjicmp.so: OK
- searching for jrrd:
  - trying to load /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/server/libjrrd.so: NO
  - trying to load /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libjrrd.so: NO
  - trying to load /usr/lib/jvm/java-6-sun-1.6.0.16/jre/../lib/amd64/libjrrd.so: NO
  - trying to load /libjrrd.so: NO
  - trying to load /usr/share/opennms/lib/libjrrd.so: NO
  - trying to load /usr/share/opennms/lib/linux32/libjrrd.so: NO
  - trying to load /usr/java/packages/lib/amd64/libjrrd.so: NO
  - trying to load /lib/libjrrd.so: NO
  - trying to load /usr/lib/libjrrd.so: NO
  - trying to load /usr/lib/jni/libjrrd.so: NO
  - trying to load /usr/lib/libjrrd.so: NO
  - trying to load /usr/local/lib/libjrrd.so: NO
  - trying to load /opt/NMSjicmp/lib/32/libjrrd.so: NO
  - trying to load /opt/NMSjicmp/lib/64/libjrrd.so: NO
- Failed to load the optional jrrd library.
  - This error is not fatal, since jrrd is only required for optional features.
```

Any advice greatly appreciated.

---

### Post by p-brane on 2009-11-03
Those are INFO only messages and not worry.  Should probably be suppressed by the installer.  The JRRD library is only need if you want to create RRDTool compatible files instead of the default Java based JRobin files.  As the message states, optional.

---

### Post by Mach1US on 2009-11-03
Thanks, that helps, i wasn't sure.
Still when run ps aux | grep nms it doesn't appear to be running . 
I have edited file /etc/postgresql/8.2/main/pg_hba.conf with line 
```
# IPv4 local connections:
host all all 176.16.0.1/24 trust
``` to allow me access from local machines(original install of OpenNMS on 8.04 server,no browser) through
[http://172.16.0.1:8980/opennms/](http://172.16.0.1:8980/opennms/) .
What do i need to do to start (or restart this server) and is this additional line will let me connect to it from local machines ?

---

### Post by p-brane on 2009-11-04
If the pg_hba.conf wasn't correct, the install script you ran wouldn't have completed.  You should start OpenNMS with either the init scripts or directly with:

```
/usr/share/opennms/bin/opennms start
```

---

### Post by Mach1US on 2009-11-04
Thanks a Million,that did the trick, it finally works \\:D/
.

---

### Post by Rbacon on 2012-11-27
I am running into a problem when attempting to set up the database. using the directions I found here... [http://www.opennms.org/index.php/QuickStart#Initialize_OpenNMS_and_the_Database](http://www.opennms.org/index.php/QuickStart#Initialize_OpenNMS_and_the_Database) I dont't understand why non of those work for me... If I try to run 
/usr/share/opennms/bin/opennms start
I get
You need to run the installer to set up the database
I try to run what it recommends but a few errors and one that sticks out is
Caused by: org.postgresql.util.PSQLException: FATAL: password authentication failed for user "postgres"

If anyone has a very good guide to go with please let me know. If you need more information I can do my best to give it to you.

---

### Post by howefield on 2012-11-27
Old thread back to sleep.

Feel free to start a fresh thread.

---

