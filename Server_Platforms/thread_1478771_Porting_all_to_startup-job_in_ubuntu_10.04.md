---
title: "Porting all to startup-job in ubuntu 10.04"
date: 2010-05-10
forum: Server Platforms
---

### Post by quesy on 2010-05-10
Hi all,

Im trying to find some good information about the new init system. I want to start all my services through this with no luck. I have tried to import the usual init.d scripts into a formatted /etc/init/???.conf with no luck.

The documentation and examples to do this are bad, maby you guys can point me in the right direction.

The main services i want to port is, apache2, postfix, courier, tomcat, mysql, samba.


Anyone ?

---

### Post by Kljuka on 2010-05-10
In the past, SysV INIT was responsible for starting services at startup.

Now, Upstart does the job. Config files of upstart are in            /etc/event.d/
To list all services, use:
```
initctl list
```To start a service, type:
```
initctl start <service_name>
```...

There seem to be many tutorials. One of them:
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by quesy on 2010-05-10
10.04 is using /etc/init now it seems. But my question was how to port /etc/init.d/apache2 script to eg. /etc/init/apache2.conf. ive tried so much now and it will not work.

The startup script for apache2 is huge, so i tried to include it in 

script
......
end script

with no success.

---

