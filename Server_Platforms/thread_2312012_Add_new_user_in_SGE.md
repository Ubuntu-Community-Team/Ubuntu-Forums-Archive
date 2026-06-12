---
title: "Add new user in SGE"
date: 2016-02-01
forum: Server Platforms
---

### Post by jason-cordero on 2016-02-01
Hi, 

I'm a newbie in SGE cluster management, and I need to add a new user to the cluster. I've done it successfully with adducer <newuser>. Then I have to open QMON as root user to add that <newuser>  to a userset and to a project. After this, I do [FONT=Menlo]qlogin -P myproject [/FONT]but it tells me:

[FONT=Menlo]local configuration COLONIAL not defined - using global configuration[/FONT]
[FONT=Menlo]Your job 14077 ("QLOGIN") has been submitted[/FONT]
[FONT=Menlo]waiting for interactive job to be scheduled ...timeout (3 s) expired while waiting on socket fd 4[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Could not start interactive job.[/FONT]

[SIZE=2]Do you know why this may happen?

It also tells me whenever I do ssh login:
[/SIZE][FONT=Menlo]/usr/bin/xauth:  file /home/juan/.Xauthority does not exist[/FONT]

---

### Post by MAFoElffen on 2016-02-01
What version of what OS (platform details) do you have Sun Grid Cluster installed into? That installs onto AIX, BSD, FreeBSD, NetBSD, OpenBSD, HP-UX, IRIX, Linux, Mac OS X, Solaris, SUPER-UX, Tru64, Windows via Microsoft Windows Services for UNIX, andZ/OS. 

What you look like you are getting in an .Xauthority error. QMON is an X based application. Root don't not have an Xauthority file there fore connot use X. Root cannot run X, only users can. 

Primary-- To start X, which QMON is an X-based utility, as a root privileged user, does not work. Root does not have a home directory, so has no .Xauthority file. You cannot start an X session as Root. So if you need to start an X session or anything requiring X X <> with administrative prevelges, then that user needs to do that as a member of the wheel. (sudoers) group (sudo or su), thereby using that users .Xauthority file... 

Secondary-- If on Solaris, there are switches you use to create a User with a Home directory (creates that directory and binds the user to it) with the useradd command (their default without switches does not). The above assumes that user was created with a home directory, and it contains an .Xauthority file with the correct permissions and ownership. ([Solaris Admin Tasks: Add User]("https://docs.oracle.com/cd/E23824_01/html/821-1451/gkhqx.html")) Note that the user's home directory noted in the admin manual, is a written there as a network shared directory, in a domain environment. That way, wherever, those user settings and files are found... which in your case are not being found.

Then to refer to Admin accounts in Oracle's SGE manual:
> 
To enable the use of a privileged port and the ability to execute jobs as other users, the Oracle GridEngine daemons must be started as the root user. It is actually possible to install and run a cluster as anon-root user, but then only that user will be able to run jobs in the cluster. To limit the securityimpact of the daemons running as root, they instead switch to a non-root user immediately after startup.That non-root user can be specified during installation, and is by convention chosen to besgeadmin. If the cluster is configured to use a non-root user in this way, it is important that the userchosen have an account on the master machine and every execution host

So it warns at starting jobs in the cluster as a local user, not as root. But if you did that as that new user, there is a problem with that user, his rights and privileges.

---

