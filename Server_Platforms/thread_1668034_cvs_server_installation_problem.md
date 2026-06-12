---
title: "cvs server installation problem"
date: 2011-01-15
forum: Server Platforms
---

### Post by ozz0 on 2011-01-15
I installed the the ubuntu 10.10 recently. I have problem installing the cvspserver. 

I followed the steps specified in 
[https://help.ubuntu.com/10.10/server...vs-server.html]("https://help.ubuntu.com/10.10/serverguide/C/cvs-server.html")

I followed every and each steps many times but it just doesn't work when I go to step: 
**sudo netstat -tap | grep cvs**

there is no cvs server process. if I telnet to port 2401, which the cvspserver listens to, I still can't. 

Please help.

---

### Post by gordintoronto on 2011-01-15
Sometimes it can help if you reboot the computer.

When you run top, does cvs show up?

---

### Post by gmargo on 2011-01-16
I followed that CVS server procedure on a stock 10.10 Maverick server installation, and had no problems.  The cvspserver shows up under 'netstat'.

Perhaps you copied the /etc/xinetd.d/cvspserver file incorrectly?  Or failed to restart xinetd? Any error messages?

In any case, there is a bug in the documentation:  Instead of **/var/lib/cvs**, the default repository root is under **/srv/cvs/** so make the appropriate change. (But that directory change is not the cause of your problem.)

---

### Post by FranciscoLopez on 2011-11-23
I have the same problem in a new 11.10 server image. followed the procedure in the serverguide pdf, installed cvs, but I noticed cvs had not made a cvsroot..... so I made the cvsroot in the standard /srv/cvs using the init command, then I installed xinetd and when I searched for it there was no cvspserver file, no problem I thought i will just make one and append the stuff in the pdf......so I did, and still nothing. I tried restarting xinetd and the server several times but nothing has worked should i uninstall xinetd and cvs and try again?

---

### Post by gmargo on 2011-11-23
To test the latest installation procedure, I created a new virtual
machine image installed from the 11.10 Oneiric server ISO.

I followed this procedure in the Oneiric server installation guide:
[https://help.ubuntu.com/11.10/serverguide/C/cvs-server.html](https://help.ubuntu.com/11.10/serverguide/C/cvs-server.html)

I concur that the /srv/cvs directory is not created automatically,
so must be created manually with "mkdir /srv/cvs".

The /etc/xinetd.d/cvspserver file is one you have to create; it is not
from any package install.  The instructions don't make that clear.

So I created /etc/xinetd.d/cvspserver with the parameters given,
and restarted the xinetd server.

(Here I didn't quite follow the instructions - since xinetd
has been convertd to an Upstart job, you can use the
"service", "stop", and "start" commands.)

```

vim /etc/xinetd.d/cvspserver       # or use preferred editor

service xinetd stop
service xinetd start

# NOTE: "service xinetd restart" did not work for me.
# So better to use stop + start.

```Now check that the server is listening on default port 2401:
```

netstat -tlnup

# should show a line like:
tcp        0      0 0.0.0.0:2401            0.0.0.0:*               LISTEN      1903/xinetd

```Or omit the -n flag to get names instead of numerics:
```

netstat -tlup

# should show a line like:
tcp        0      0 *:cvspserver            *:*                     LISTEN      1903/xinetd

```So the xinetd daemon is now listening on behalf of the cvs server.

Can you get to this point?

---

### Post by FranciscoLopez on 2011-11-23
> **gmargo said:**
> To test the latest installation procedure, I created a new virtual
machine image installed from the 11.10 Oneiric server ISO.

I followed this procedure in the Oneiric server installation guide:
[https://help.ubuntu.com/11.10/serverguide/C/cvs-server.html](https://help.ubuntu.com/11.10/serverguide/C/cvs-server.html)

I concur that the /srv/cvs directory is not created automatically,
so must be created manually with "mkdir /srv/cvs".

The /etc/xinetd.d/cvspserver file is one you have to create; it is not
from any package install.  The instructions don't make that clear.

So I created /etc/xinetd.d/cvspserver with the parameters given,
and restarted the xinetd server.

(Here I didn't quite follow the instructions - since xinetd
has been convertd to an Upstart job, you can use the
"service", "stop", and "start" commands.)

```

vim /etc/xinetd.d/cvspserver       # or use preferred editor

service xinetd stop
service xinetd start

# NOTE: "service xinetd restart" did not work for me.
# So better to use stop + start.

```Now check that the server is listening on default port 2401:
```

netstat -tlnup

# should show a line like:
tcp        0      0 0.0.0.0:2401            0.0.0.0:*               LISTEN      1903/xinetd

```Or omit the -n flag to get names instead of numerics:
```

netstat -tlup

# should show a line like:
tcp        0      0 *:cvspserver            *:*                     LISTEN      1903/xinetd

```So the xinetd daemon is now listening on behalf of the cvs server.

Can you get to this point?

:D

you sir are an amazing fellow, you have my very heartfelt thanks, 
and I confirm the procedure worked. my cvs server is up and running and I have a project ready for code to work in. 
the main stumbling block appears to be the need for  stop + start of xinetd instead of restart.

I propose that the server guide be amended and you are given full credit for the contribution.

---

