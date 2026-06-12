---
title: "Help me migrate this Windows pseudo-server to Ubuntu"
date: 2012-07-30
forum: Server Platforms
---

### Post by JoeSabido on 2012-07-30
I have a Windows 7 computer running the following services, and I'm wondering if I could migrate this reasonably "easy" to Ubuntu Server. The reason I'm considering the migration is for the potential performance gains.

- 18 instances of MySQL (Running as independent services, they're slaves to remote databases)
- WAMP (Ubuntu Server comes with LAMP out of the box I believe, so no problem there)
- OpenVPN (Available through apt-get I'm pretty sure)
- Openfire
- FTP Server (Available through apt-get?)

My two main issues here are the MySQL instances and the Openfire server, which is java based. I've been trying for several hours to get multiple instances of MySQL working but I can't get it to work after following at least 6 different tutorials, some using musql_multi and some using complete separate instances, but no luck so far, and in the mean time now I have left over files all over the place.

On Windows I would copy the mysql directory and paste it with a different name, modify the my.ini inside it, remove the databases (except the default ones), and add the service with a single instruction in a command window. And that's it.

What would be the "equivalent" process here? I would do it on a clean install (Ubuntu Server 12).

---

### Post by TheFu on 2012-07-30
"Easy" is relative to your skills.  I don't think it would be "easy" for me.

All of these are possible under a single server, but mixing FTP and VPN and SQL on the same logical server is definitely **not** a best practice.

I'd install KVM on the hostOS with little else, definitely no GUI libraries which can negatively impact server stability. Then I'd build a heavy MySQL VM, another OpenVPN VM, another FTP Server VM (be certain to LOCK THIS DOWN HARD), and finally the last VM for your apache, php/perl/python, and openfire needs.  See how the different security risk levels are grouped logically?

Managing your KVM DomUs from a different desktop machine running virt-manager or virsh is probably best. Be certain to setup ssh keys between the systems.

It won't be a "migration", rather it will be fresh installs of everything.  If you are new to Ubuntu, you are probably taking on more than you are read for, I must say.

You'll need to migrate your users and data for each application manually. For mysql, that should be easy.  I'd strongly recommend using an LDAP user-auth setup to centralize user and group management.

And is it called Ubuntu Server 12.04 (April) .... 12.10 will be released in October, but if you are running a production server, stay on 12.04 which is an LTS release.  The release numbers are YY.MM format and often extremely different. These aren't like 12.01.01 and 12.01.02 releases that other software versions have.

For a large number of large MySQL DBs, you'll want to follow a MySQL best practices guide to get the best performance for your situation and needs. Unix works different and scaling best practices are different from Windows. 
Just found this [http://mysqlsandbox.net/](http://mysqlsandbox.net/) GPL software. Don't know anyhting about it.  I always run a single instance with many DBs myself.  

You really want different configuration files and to share the same executables and libraries so memory use is more efficient - different DS and heap for each instance, but the same CS for all.

Interesting problem. I wish you well.

---

### Post by JoeSabido on 2012-07-30
Well, when I said "migration" I meant the data, like moving my PHP files and dumping my DBs and importing them in the new server.

Anyway, you're probably right. I'll stick to Windows.

Thanks

---

### Post by CharlesA on 2012-07-30
I really wouldn't have FTP and SQL servers on the same box.

LAMP and openfire and openvpn, maybe, but not something as insecure as FTP.

Also +1 to KVM, if you decide to go that route.

---

### Post by TheFu on 2012-07-31
**I hope he sees this warning about FTP.  **

It applies to all platforms, including Windows.  The vast majority of people running FTP servers shouldn't.  There are better ways to transfer and share files, unless you really want everyone in the world to have access and only allow anonymous access.

Not to mention the issues that FTP causes with network firewalls - which ports do you need? Huh?

FTP needs to go away like telnet, though it took a decade longer to remove telnet than it should have.

Of course, there are very specific uses where FTP is perfect. Very specific purposes that 99% of the world don't have.

---

### Post by CharlesA on 2012-07-31
> **TheFu said:**
> **I hope he sees this warning about FTP.  **

It applies to all platforms, including Windows.  The vast majority of people running FTP servers shouldn't.  There are better ways to transfer and share files, unless you really want everyone in the world to have access and only allow anonymous access.

Not to mention the issues that FTP causes with network firewalls - which ports do you need? Huh?

FTP needs to go away like telnet, though it took a decade longer to remove telnet than it should have.

Of course, there are very specific uses where FTP is perfect. Very specific purposes that 99% of the world don't have.

Indeed. I don't even use FTP to transfer files to my web host. sftp/rsync over ssh wins hands down. I am not even sure what someone would use ftp for unless it was at a company sending patches and whatnot to customers, but it would be better to use something that is secure.

EDIT: Ports 21 and 20 for normal FTP, 990 for ftps and 22 for sftp. I should know cuz I dealt with firewall problems at work with their stupid "secure ftp" server. Yuck!

---

### Post by SeijiSensei on 2012-07-31
> **JoeSabido said:**
> I've been trying for several hours to get multiple instances of MySQL working but I can't get it to work after following at least 6 different tutorials, some using musql_multi and some using complete separate instances, but no luck so far, and in the mean time now I have left over files all over the place.

I don't understand the motivation for this arrangement at all, since MySQL like most SQL servers, is perfectly happy running as a single instance supporting multiple databases.

Still, if you're committed to running eighteen separate MySQL instances, they have to each be bound to a separate TCP port.  You'll need eighteen versions of my.cnf with different ports specified in each.  There's no way multiple instances of the server can all listen on a single port.  I don't know how that would happen in Windows, either.

---

### Post by rubylaser on 2012-07-31
> **SeijiSensei said:**
> I don't understand the motivation for this arrangement at all, since MySQL like most SQL servers, is perfectly happy running as a single instance supporting multiple databases.

Still, if you're committed to running eighteen separate MySQL instances, they have to each be bound to a separate TCP port.  You'll need eighteen versions of my.cnf with different ports specified in each.  There's no way multiple instances of the server can all listen on a single port.  I don't know how that would happen in Windows, either.

+1.  With the ability to assign users and permissions, I can't think of an example where I'd want multiple MySQL processes running.  Besides the extra overhead and management to maintain 18+ separate MySQL instances.

---

### Post by CharlesA on 2012-07-31
> **SeijiSensei said:**
> I don't understand the motivation for this arrangement at all, since MySQL like most SQL servers, is perfectly happy running as a single instance supporting multiple databases.

I don't understand it either. Granted I only have 2 dbs running on the same SQL server, I know they can handle a lot more.

> **rubylaser said:**
> +1.  With the ability to assign users and permissions, I can't think of an example where I'd want multiple MySQL processes running.  Besides the extra overhead and management to maintain 18+ separate MySQL instances.

+1.

---

### Post by JoeSabido on 2012-07-31
The reason why I need the separate instances is explained in my original post.

I have 18 remote databases that need slaves, all the databases have the same name, and I need to be able to shut down one of the slaves at any given moment without affecting the others.

Of course, they would all listen on a different TCP port.

I already have this working very well under Windows, and I was considering doing it under Linux instead but I seriously lack the time to keep experimenting with it just to make it work (at all) and it's all so confusing and unnecessarily convoluted, so I'm going to stick with what I have.

---

### Post by rubylaser on 2012-07-31
> **JoeSabido said:**
> The reason why I need the separate instances is explained in my original post.

I have 18 remote databases that need slaves, all the databases have the same name, and I need to be able to shut down one of the slaves at any given moment without affecting the others.

Of course, they would all listen on a different TCP port.

I already have this working very well under Windows, and I was considering doing it under Linux instead but I seriously lack the time to keep experimenting with it just to make it work (at all) and it's all so confusing and unnecessarily convoluted, so I'm going to stick with what I have.

Sounds good.  In IT, if it isn't broke don't fix it is always a good mantra to hold to :)

---

### Post by TheFu on 2012-07-31
> **JoeSabido said:**
> The reason why I need the separate instances is explained in my original post.

I have 18 remote databases that need slaves, all the databases have the same name, and I need to be able to shut down one of the slaves at any given moment without affecting the others.

Of course, they would all listen on a different TCP port.

I already have this working very well under Windows, and I was considering doing it under Linux instead but I seriously lack the time to keep experimenting with it just to make it work (at all) and it's all so confusing and unnecessarily convoluted, so I'm going to stick with what I have.

There's always a reason to do odd things and you have a good one for mysql instances.  There are others just a valid for doing that, but sometimes we all think the way we are doing things is the best way and lose track that other methods can also be better.

Confusing to you seems elegant to others. It is a matter of perspective.  I get frustrated when my UNIX skills don't transfer to Windows in a similar way.  In Linux there are usually 100 different ways to accomplish the same or very similar things. Often there is a "best practice" too, but nobody is going to force that on anyone.  That flexibility is part of the power to UNIX OSes.

UNIX taught me that just because you **can** do something, that doesn't mean you **should** do it. Many things that work are bad ideas for other, subtle reasons.

Actually, looking at that link [http://mysqlsandbox.net/](http://mysqlsandbox.net/) for managing mysql instances, that appears to be the easy part of your needs, IMHO.  OTOH, if you are new to Linux, 80% of your existing MS-Windows skills do not transfer when you work on "server" installs. There is a steep learning curve since there aren't any GUIs at the OS level.

Personally, I wouldn't use Apache. It is extremely complex and there are better ways to run a web-app that provides a load balanced front-ends, higher security, much greater performance, a reverse proxy and an easier server configuration.  But we'll assume your reasons for Apache are completely sound and not "because that's how we've always done it."

---

