---
title: "Squid cache directory not been initialized"
date: 2012-04-29
forum: Server Platforms
---

### Post by Silenti-Ambulo on 2012-04-29
Dear Ubuntu Support and fellow users,

I'm trying to set up a proxy using Squid3 on a remote Server.
I've been trying whole day to get Squid to work.
Late this afternoon I found a post saying it was easier to configure with Webmin.
So completely removed Squid3 and all programs associated.

After I installed Webmin and Squid3 from console, I setup the config file from squid3.

/etc/webmin/squid/config
```
squidclient=squidclient
cache_dir=/var/spool/squid3
log_dir=/var/log/squid3
pid_file=/var/run/squid3.pid
squid_path=squid3
squid_conf=/etc/squid3/squid.conf
cachemgr_path=/usr/lib/cgi-bin/cachemgr3.cgi
squid_restart=squid3 -k reconfigure
squid_start=service squid3 start
squid_stop=service squid3 stop
```

Then I tried to start it up inside Webmin, it didn't want to create a cach directory under Root (I know I'm a n00b) so I created an new user for it. I pressed it and it ran without an error.
So I went back to the squit main page and I keep getting this error.
```
Your Squid cache directory /var/spool/squid3 has not been initialized.This must be done before Squid can be run.
```

When I say it should start squid3 from console it says it started.
When I look at the proceslist it just states [ ? ]

I have no clue weather it's running or not.

Anybody got any idea?

Thanks in advanced.

---

### Post by SeijiSensei on 2012-04-29
Try running "sudo squid -z".  That should create the initial cache directories.  Then run "sudo service squid3 restart".

---

### Post by elico on 2012-04-29
it's so simple to manage squid using only conf file.
also latest squid webmin config was out of sync to the syntax of the file.
try the squid -z first.
and what version of squid + ubuntu are you using?

---

### Post by Silenti-Ambulo on 2012-04-30
I'm using Squid3 and ubuntu 12.04

I started over from scratch this morning.
I installed webmin and Squid3.

When I tried "Sudo Squid3 -z" it told me squid3 was running.
So I stopped the service and did the command again.
And restarted squid3 service afterwards.

I'm still getting the error in Webmin: ```
Your Squid cache directory /var/spool/squid3 has not been initialized.This must be done before Squid can be run.
```
Also initialize Cache as Unix User.

Last time I used Root, but got an error saying it shouldn't be run as Root.
Any advice?

---

### Post by SeijiSensei on 2012-04-30
I just installed squid3 from the Precise repositories.  The initial setup created /var/spool/squid3 and set its ownership to proxy:proxy.  Do you have that directory with those permissions?  Did you install from the repositories?

---

### Post by ashleydrees on 2012-05-01
i too have now been through this, it seems in squid3 you need to un-comment the cache line in the config file... 

# Uncomment and adjust the following to add a disk cache directory.
# cache_dir ufs /var/spool/squid3 100 16 256

to 

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid3 100 16 256

i did all sorts of stuff before i found that... which thankfully, i took notes of so could undo all the workarounds...

---

### Post by EmmEight on 2013-03-28
@ashleydrees

Good work!

Worked like a charm!

Also good to mention it can be found on line 2245... the squid.conf isn't very small :P

---

### Post by DieEier on 2013-10-30
Thanks everyone for sharing. Had the same problem. This helped solve it.

---

