---
title: "Remove Service Controlled by Upstart From Boot in 10.04"
date: 2010-06-04
forum: Server Platforms
---

### Post by andylawrence on 2010-06-04
How do I go about preventing a service that is controlled by Upstart from starting when the machine is booted.  I'm trying to prevent Mysql from starting on boot and in Lucid it's controlled by Upstart which means I can no longer use update-rc.d to remove it from the boot.  I've read elsewhere to rename the /etc/init/mysql.conf file to mysql.conf-disabled, but renaming the file makes the "service mysql start" command stop working because Upstart uses that file if I want to manually start the service.

---

### Post by andylawrence on 2010-06-05
Bump.

---

### Post by richardjh on 2010-06-05
I have recently been stumped by this too, so your question finally made me sit down and look into upstart.

Most solutions I have found won't work properly, because they suggest making changes that will cause the service to fail to start. 
This is not what you want because you still want the service to start when called manually.
 

I have come to the conclusion that  you can't use upstart like sysvinit. You have to think event based.


So what you want to do is cause MySQL to not try to start on any change to run level, or specifically run level 2, which is the run level Ubuntu runs in (by default although apart from 0 and 6 they all now appear to be the same).

The configuration (what used to be called an init script) is now /etc/init/mysql.conf and not /etc/init.d/mysql

The bit that starts the service is
```
start on (net-device-up
          and local-filesystems)
```

In other words, when the network devices start and the disks are mounted, start MySQL. 
Okay, so that is always. 

You need to comment out those lines, otherwise MySQL will always start on boot.

However you do still need a "start on" section so use this instead:

start on runlevel [!0123456]

That is ( in words), start MySQL when the run level is not 0,1,2,3,4,5 or 6. 
Okay so that is never.

You now are in the situation when MySQL will never start automatically by upstart, and you have not had to rename any configurations or in any other way break MySQL as a service and you can still start MySQL manually using

```
service mysql start
```

The documentation on this is scarce, so any feedback would be appreciated.

Thanks to : [http://old.nabble.com/Start-stop-services-controlled-by-upstart-on-karmic-td26272954.html](http://old.nabble.com/Start-stop-services-controlled-by-upstart-on-karmic-td26272954.html)

---

### Post by andylawrence on 2010-06-06
> **richardjh said:**
> I have recently been stumped by this too, so your question finally made me sit down and look into upstart.

Most solutions I have found won't work properly, because they suggest making changes that will cause the service to fail to start. 
This is not what you want because you still want the service to start when called manually.
 

I have come to the conclusion that  you can't use upstart like sysvinit. You have to think event based.


So what you want to do is cause MySQL to not try to start on any change to run level, or specifically run level 2, which is the run level Ubuntu runs in (by default although apart from 0 and 6 they all now appear to be the same).

The configuration (what used to be called an init script) is now /etc/init/mysql.conf and not /etc/init.d/mysql

The bit that starts the service is
```
start on (net-device-up
          and local-filesystems)
```

In other words, when the network devices start and the disks are mounted, start MySQL. 
Okay, so that is always. 

You need to comment out those lines, otherwise MySQL will always start on boot.

However you do still need a "start on" section so use this instead:

start on runlevel [!0123456]

That is ( in words), start MySQL when the run level is not 0,1,2,3,4,5 or 6. 
Okay so that is never.

You now are in the situation when MySQL will never start automatically by upstart, and you have not had to rename any configurations or in any other way break MySQL as a service and you can still start MySQL manually using

```
service mysql start
```

The documentation on this is scarce, so any feedback would be appreciated.

Thanks to : [http://old.nabble.com/Start-stop-services-controlled-by-upstart-on-karmic-td26272954.html](http://old.nabble.com/Start-stop-services-controlled-by-upstart-on-karmic-td26272954.html)
I changed the start on line in /etc/init/mysql.conf to 

start on runlevel [!0123456]

like you suggested and it worked great.  Thanks for your help.

---

### Post by scotty64 on 2010-06-09
Richards suggestion solved my problem as well: I often need an FTP server (vsftpd), but for security reasons I dislike having it running all the time (upstart).
I think this suggestion should make it into a HowTo, sticky post etc. because I guess many people have this problem.
thanks !

---

### Post by idallen on 2013-03-06
"man 5 init" says you can create /etc/init/mysql.override to over-ride mysql.conf, so you don't have to edit mysql.conf at all.

---

### Post by koenn on 2013-03-06
AFAIK, you can also rename de .conf filies in /etc/init, eg to something like /etc/init/mysql.conf.DISABLED  to prevent upstart (init) from seeing/processing them

---

### Post by GordThompson on 2013-03-06
> **koenn said:**
> AFAIK, you can also rename de .conf filies in /etc/init, eg to something like /etc/init/mysql.conf.DISABLED  to prevent upstart (init) from seeing/processing them
Yes, but the OP said they didn't like that approach because it also breaks

```
service mysql start
```
idallen's suggestion of creating a 'mysql.override' file does seem to work, however. I just did...

```
cp /etc/init/mysql.conf /etc/init/mysql.override
```
...and then changed the line in 'mysql.override' from...

```
start on runlevel [2345]
```
...to...

```
start on runlevel [!0123456]
```
MySQL does not start on boot, but it can still be started manually with `service mysql start`.

---

### Post by koenn on 2013-03-06
good to know.

I also just noticed this thread is over two years old :-)

---

