---
title: "ColdFusion / Apache help..."
date: 2006-08-30
forum: Server Platforms
---

### Post by hawk6773 on 2006-08-30
Ok, so I'm pretty new to Ubuntu and Linux in general. I've managed to get one of my old PCs up and running with no problem.

I've installed and setup Apache, PHP, and MySQL and have verified that they're working.

My next task is to get ColdFusion MX 7 up and running. I attempted to do this once, but when I would start coldfusion, I'd get an error saying that the apache connector didn't work properly, but that coldfusion was up and running. Not the case, didn't get a coldfusion page, but a bunch of garbage instead.

So, in uninstalled and re-installed coldfusion using the server configuration . No problem worked fine.

What I want to do configure Coldfusion to run off Apache and not itself. I tried to do this using the Macromedia instructions, but got the following error:

```

root@skywalker:/opt/coldfusionmx7/bin# /opt/coldfusionmx7/runtime/bin/wsconfig -server coldfusion -ws Apache -dir /etc/apache2/ -coldfusion -v
Found JRun server coldfusion at 127.0.0.1:2920
Could not find file /etc/bin/httpd
Could not find file /usr/sbin/httpd
Could not find file /usr/local/apache/bin/httpd
Could not find file /usr/apache/bin/httpd
Could not find file /etc/bin/httpd
Could not find file /usr/sbin/httpd
Could not find file /usr/local/apache/bin/httpd
Could not find file /usr/apache/bin/httpd
Using Apache binary {0}

```](*,) 

I guess I need to know what the apache binary is, where it's at, and what the configuration file is and where it's at.

Any help would be great!

Thanks.

---

### Post by hawk6773 on 2006-08-30
Ok, so I'm not sure what I did, but it's working under localhost:8500.

Anyway it can be changed to just localhost?

---

### Post by ethan@xmlstandards.org on 2006-09-14
Let me know if you still need to know how to do this.

I have successfully setup ColdFusion MX 7.02 on Ubuntu Server 6.06.1 LTS release several times now against Apache 2 without any issues.

The key is to perform most of the steps manually so you'll understand better how ColdFusion MX and Apache work with each other.

Mostly with regard to the web connectors. Going forwards I would never use the wsconfig.jar to connect Apache to ColdFusion. Far better to setup this up manually. You will however probably need the most up to date wsconfig.jar that contains the mod_jrun2.so library for Apache. See the Adobe website for details about that.

Anyway, let me know and I will post a detailed walkthrough. Please note that it will be quite detailed so only get back if you really need this.

Ethan Cane
Web Developer

---

### Post by medw1974 on 2006-09-26
Ethan,

A detailed walkthrough would be very helpful to myself as I am just about to attempt installing coldfusion on ubuntu for the first time.

Regards
Michael

---

### Post by pete on 2006-09-26
fwiw, I was able to get CF up and running pretty easily through Apache following (roughly) the steps outlined here:

[http://www.howtoforge.com/coldfusion_installation_debian_sarge](http://www.howtoforge.com/coldfusion_installation_debian_sarge)

Don't know if it's exactly what you're looking for, but I thought I'd throw it out there just in case.

---

### Post by Vevmesteren on 2006-11-21
[http://www.daveshuck.com/blog/index.cfm/2006/6/12/Installing-CFMX7--Apache222-on-Ubuntu-606](http://www.daveshuck.com/blog/index.cfm/2006/6/12/Installing-CFMX7--Apache222-on-Ubuntu-606)

---

