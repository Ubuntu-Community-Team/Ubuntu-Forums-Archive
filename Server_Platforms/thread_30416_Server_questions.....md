---
title: "Server questions...."
date: 2005-04-28
forum: Server Platforms
---

### Post by s0c0 on 2005-04-28
I am doing some network consulting for a small company of under 10 employees.  They would like a website capable of taking online orders, a database for inventory, an email server, and file server.  They are looking to save money on this server so Linux appears to be the best solution.  I've been thinking about using a Ubuntu box.  What specs do you think I will need to run: Apache 1.3, Samba, an Access database, and an email server(have not decided on which one I will use).

I was thinking something like a 3+ Ghz Athlon w/ 800 FSB, and 1mb L2 cache.  A 80gb hard drive (possibly two for software RAID 1).  1024mb of RAM and everything else being fairly generic.  Would a computer like this be able to handle moderate usage on ths small network?  Do I need something with a bit more beef for scalability? (fyi, we have already setup a T1 connection).

---

### Post by DJ_Max on 2005-04-28
[QUOTE=s0c0]I am doing some network consulting for a small company of under 10 employees.  They would like a website capable of taking online orders, a database for inventory, an email server, and file server.  They are looking to save money on this server so Linux appears to be the best solution.  I've been thinking about using a Ubuntu box.  What specs do you think I will need to run: Apache 1.3, Samba, an Access database, and an email server(have not decided on which one I will use).

I was thinking something like a 3+ Ghz Athlon w/ 800 FSB, and 1mb L2 cache.  A 80gb hard drive (possibly two for software RAID 1).  1024mb of RAM and everything else being fairly generic.  Would a computer like this be able to handle moderate usage on ths small network?  Do I need something with a bit more beef for scalability? (fyi, we have already setup a T1 connection).[/QUOTE]
 A nice P4 or Athlon XP will handle your needs just fine. As long as you know how to manage a server correctly, you won't have any problems.

For email you should use Postfix, it's lighweight and secure(I use it on my box.)

---

### Post by philipacamaniac on 2005-04-28
Access? If you're going to be running Linux, you'll have to choose something like MySQL or PostGre. Also, for mail, Postfix and Cyrus are good.

---

### Post by az on 2005-04-28
Ubuntu supports apache2, with apache1.3 being in univers and not recieving security updates.  Other desirable server packages are also only in universe (php-mysql)


"Would a computer like this be able to handle moderate usage on ths small network?"

For a ten user network, I think this server could be a lot less powerful and still do the job.

---

### Post by DJ_Max on 2005-04-28
[QUOTE=philipacamaniac]Access? If you're going to be running Linux, you'll have to choose something like MySQL or PostGre. Also, for mail, Postfix and Cyrus are good.[/QUOTE]
 Yeah, didn't catch that. There are quite a few good open source DB's.
MySQL for basic stuff
PostrgeSQL for advanced stuff
mSQL, SQLite are lightweight. There's also Firebird.

---

### Post by s0c0 on 2005-04-28
I will be developing a GUI interface for this using Visual Basic so access appears to be the best solution as a database engine and linux shouldn't have any problems with this.  THanks for the input guys.

---

### Post by s0c0 on 2005-04-28
Okay this is what I came up with:

CPU - AMD Athlon64 2800/400mhz FSB
RAM - 512mb ddr
Hard Drive - 80gb 7200 rpm
Power - 450w supply

Everything else is bare minimum and yes the motherboard ofcourse supports the CPU.  This pretty much one of the cheapest setups I could find without getting crappy parts.  Total cost (hardware only) is under $600, but knock off another $100 if they go with a KVM switch.  I thin this will suit their needs, any disagreements?

---

### Post by az on 2005-04-28
[QUOTE=s0c0]I will be developing a GUI interface for this using Visual Basic so access appears to be the best solution as a database engine and linux shouldn't have any problems with this.  THanks for the input guys.[/QUOTE]


You will be missing out on so much by doing this.

---

### Post by wfx on 2005-04-29
You can use mysql via MS Access:
[http://www.washington.edu/computing/web/publishing/mysql-access.html](http://www.washington.edu/computing/web/publishing/mysql-access.html)

---

### Post by tncmmngs on 2005-04-29
[QUOTE=philipacamaniac]Access? If you're going to be running Linux, you'll have to choose something like MySQL or PostGre. Also, for mail, Postfix and Cyrus are good.[/QUOTE]

Unless Access 2003 has changed significantly from earlier versions, putting it on a server is doing nothing more than putting a file on a file server. Each client, whether VB or a standard Acess install, has to download the entire db to the client. If the db is big, that could generate a lot of unnecessary traffic. 

If you want to do that, you'll have the tools with Samba. And it may be a satisfactory solution if the db is small. But since you're putting together a web server, why not use MySql and build a web interface with PHP? Tastes great, less filling, and you won't have to install and maintain a clunky VB client on 10 PCs.

---

### Post by az on 2005-04-29
...And that does not close the door to the office's next workstations from being linux-based.  

You said the company wanted to same some money on licencing, right?  Out of the ten seats, do any of them do more than web, text, email and printing?

Instead of writing a VB client to all this, you could make a cross-platform web based tool.  Or even one written in Python using cross-platform tools.

---

### Post by s0c0 on 2005-05-01
Looks like these guys aren't comfortable with Linux and so the client is calling the shot on setting up a Windows 2003 Small Business Server *arggghhh*.  Meh, maybe when they go to buy the $500-$700 MS cd/license they will change their mind.  On the flip-side I've convinced them to have me build a custom linux (or freebsd) firewall box.  Thank for the responses.

P.s. Never used MySQL or PHP.  Are there some progs out there that make this kind of thing simple or at least some good resources?

---

### Post by dataw0lf on 2005-05-02
[QUOTE=s0c0]Looks like these guys aren't comfortable with Linux and so the client is calling the shot on setting up a Windows 2003 Small Business Server *arggghhh*.  Meh, maybe when they go to buy the $500-$700 MS cd/license they will change their mind.  On the flip-side I've convinced them to have me build a custom linux (or freebsd) firewall box.  Thank for the responses.

P.s. Never used MySQL or PHP.  Are there some progs out there that make this kind of thing simple or at least some good resources?[/QUOTE]


php.net

[http://www.freewebmasterhelp.com/tutorials/phpmysql](http://www.freewebmasterhelp.com/tutorials/phpmysql)

FYI -- php.net is generally considered to be one of the greatest programming references ever, bar none.  

Also, since you're from Utah, try joining #uphpu on the FreeNode IRC servers.  It's the PHP user group around here, and has some friendly people that will be more than willing to help you.

---

### Post by s0c0 on 2005-05-02
[QUOTE=dataw0lf]php.net

[http://www.freewebmasterhelp.com/tutorials/phpmysql](http://www.freewebmasterhelp.com/tutorials/phpmysql)

FYI -- php.net is generally considered to be one of the greatest programming references ever, bar none.  

Also, since you're from Utah, try joining #uphpu on the FreeNode IRC servers.  It's the PHP user group around here, and has some friendly people that will be more than willing to help you.[/QUOTE]

You're the network admin with black shoulder length hair at Areo Graphics, right? I went for an interview there a month or so back.  I guess you guys didn't hire me.   [-X  Meh, oh well.   ;-)  Interesting seeing you here.  Anyways thanks for the links!  :)

---

### Post by jdonnell on 2005-05-02
I do php, python, and asp/vbscript at work and there are a lot more resources on the net for php than the rest. Same with mysql compared to all others. You can pick up php in a day or two if you know how to code already. It's unfortunate that your customer wants sql server. We were bitten by ms lock in and have used php/linux for everything since. We only have one site left that is asp on win2k. That will be on linux in the next 5 years. 

One question, is this application only for internal use? If not then a dedicated server (provided by a host) might be a better solution. I can give you some advice on these if you go this route

---

### Post by s0c0 on 2005-05-02
[QUOTE=jdonnell]I do php, python, and asp/vbscript at work and there are a lot more resources on the net for php than the rest. Same with mysql compared to all others. You can pick up php in a day or two if you know how to code already. It's unfortunate that your customer wants sql server. We were bitten by ms lock in and have used php/linux for everything since. We only have one site left that is asp on win2k. That will be on linux in the next 5 years. 

One question, is this application only for internal use? If not then a dedicated server (provided by a host) might be a better solution. I can give you some advice on these if you go this route[/QUOTE]


This is internal, but a vpn will be setup a few months down the road after the company establishes itself.

---

### Post by Gandalf on 2005-05-02
install VHCS it will install everything for you, it use apache2, postfix, php4 and proftpd
[HOWTO: install VHCS on ubuntu (SERVER)](http://ubuntuforums.org/showthread.php?t=25722)

---

### Post by dataw0lf on 2005-05-02
[QUOTE=Gandalf]install VHCS it will install everything for you, it use apache2, postfix, php4 and proftpd
[HOWTO: install VHCS on ubuntu (SERVER)](http://ubuntuforums.org/showthread.php?t=25722)[/QUOTE]
I'm not a proponent for these type of solutions for server application.  'Wizards' or 'Easy fixes' or 'prepackaged deals' or whatever you want to call them usually do more harm than good, for one major reason:  the system administrator installing them with these 'quick and dirty' package deals is supposedly supposed to, y'know, 'administer' them.  If you go the short route, you'll pay in the end, because the knowledge that you could've earned setting them up the 'hard way' was all bundled up in a bunch of scripts.  For personal application(s), this is fine.  However, for a business orientated setup, I strongly disagree with anything of this nature, unless you're an experienced system administrator and know exactly what the application(s) in question are doing.

---

### Post by Gandalf on 2005-05-02
[QUOTE=dataw0lf]I'm not a proponent for these type of solutions for server application.  'Wizards' or 'Easy fixes' or 'prepackaged deals' or whatever you want to call them usually do more harm than good, for one major reason:  the system administrator installing them with these 'quick and dirty' package deals is supposedly supposed to, y'know, 'administer' them.  If you go the short route, you'll pay in the end, because the knowledge that you could've earned setting them up the 'hard way' was all bundled up in a bunch of scripts.  For personal application(s), this is fine.  However, for a business orientated setup, I strongly disagree with anything of this nature, unless you're an experienced system administrator and know exactly what the application(s) in question are doing.[/QUOTE]
 well i don't know what to say man lol but almost all servers that desire an Open sources Virtual Hosting Control Panel recommand this because there IS NO changes to the system except to proftpd
apache will work with it's default values with an include line in /etc/apache2/httpd.conf to include /etc/apache2/sites-enables/vhcs2.conf, same to bind to include /var/cache/bind/*.db, and it's more than secure because each domain gets it's own user and group there's no way to include other customer file since it's not in his php_opendir values, the files will be chmodded to vu20XX:www-data where XX is a number strating by 01 till ..... do the math...

it's not like you mentioned an easy fix or a patch, read the tuto see how the install goes you will understand then, you will apt-get packages manually, and of course you can customize apache2.conf and php4.ini to your needs manually

i've been using VHCS to host (for now) 3 sites never had a problem like crashing (except the damn day where my HDD had a FULL bad sectors!!!! 4gb were left out of 40), it really work smooth, mail/FTP and domains creating are no easier than that, two mouse click and you're up....

one last thing to mention, VHCS do daily backup of all the sites available (by default at 23h40) i also made a patch (since it's an open source project and the patch is on VHCS site) to backup domain databases as well... just try it and let me know if you encounter some as you said "do more harm" which i disagree!!!!

---

### Post by s0c0 on 2005-05-02
[QUOTE=Gandalf]install VHCS it will install everything for you, it use apache2, postfix, php4 and proftpd
[HOWTO: install VHCS on ubuntu (SERVER)](http://ubuntuforums.org/showthread.php?t=25722)[/QUOTE]

I'll have to slap this on one of my testing boxes.

---

### Post by Gandalf on 2005-05-03
[QUOTE=s0c0]I'll have to slap this on one of my testing boxes.[/QUOTE]
 if you need help just contact me ok?

---

### Post by jobertel on 2005-05-05
I run SBS 2003 and can tell you that it requires far more resources (hardware) than a LAMP install. Your client should plan on spending around $5000 on a brand name box, maybe a little less on a home build. The problem is that if you want to use Exchange, Active Directory, MS SQL, etc. a desktop type PC will choke.

The only reason I didn't use Linux is that I'm still really a newb and there is no organized local support for a full time production network running Linux....yet.

I hope this helps.

John B.

---

### Post by jvzsys on 2005-05-28
Use FireBird
[http://www.firebirdsql.org](http://www.firebirdsql.org)
Much better than MySQL
Greertings
 :razz:

---

### Post by LordHunter317 on 2005-05-28
[QUOTE=tncmmngs] has to download the entire db to the client. If the db is big, that could generate a lot of unnecessary traffic. [/quote]Access has never, and will never work like that.

>  But since you're putting together a web server, why not use MySql and build a web interface with PHP? Tastes great, less filling, and you won't have to install and maintain a clunky VB client on 10 PCs.Because the time to develop is longer?  Because it's likely to be less secure?  Because it's harder to extend?  Because MySQL's only advantage to Access is it's faster?

[quote=dataw0lf]FYI -- php.net is generally considered to be one of the greatest programming references ever, bar none. [/quote]Besides for all the incredibly important details they choose to leave out.  Their documentation would be useless if it wasn't for the user-contributed commentary, which half of is usually wrong... *sigh*

[quote=Gandalf]well i don't know what to say man lol but almost all servers that desire an Open sources Virtual Hosting Control Panel[/quote]**Most,** nay, nearly all, servers do **NOT** desire, need, or want this.  It's only desirable to web-hosting providers who need to give end-users limited administrative control over their site.

>  recommand this because there IS NO changes to the system except to proftpd
apache will work with it's default values with an include line in /etc/apache2/httpd.conf No, it really won't.  Apache isn't setup to be production OOB on any distribution, and with damn good cause.  There's just some stuff that's site-specific no matter what.  Debian (and Ubuntu in turn) have done a good job of minimizing that, but the default Apache2 installation is not start and go.  Neither would be the VHCS setup unless they fill in the proper blanks.  If they do, great.  But I somehow suspect you still have the same initial per-site configuration to do, you just have a more dressed-up interface for it.

>  and it's more than secure because each domain gets it's own user and group there's no way to include other customer file since it's not in his php_opendir values, the files will be chmodded to vu20XX:www-data where XX is a number strating by 01 till ..... do the math...There's more to it than just file permissions.  And under that scheme, I can still read any other customer's scripts.  The manner is obvious to anyone properly experienced with PHP administration.

PHP isn't secure unless you're using PHP as a CGI script and Apache/suExec.  And if VHCS is doing that, their permissions are wrong on the files.  Whoops.  

[quote=jvzsys]Use FireBird[/quote]FireBird is a massive overkill solution for 10 people.  It's almost akin to recommending an elephant gun to kill a house fly.

**To the OP:**
If they want SBS, give them SBS.  Your hardware is budgeted OK for that, though they're planning on using Exchange, I would require a RAID-1 array for the OS, a RAID-5 array for the Exchange datastores, and at least 1GB of RAM.  More RAM is always better. 

I want a take a second and note that the fact you were considering, not requiring, at least RAID-1 for the OS makes you an amateur in my book.  Real Sysadmins don't skimp on disk redundancy.  It's the most commonly failed component.

Like it or not, they're probably better off buying a Dell or HP.  They'll get better service and response time, and a better deal in the long run.  This is just the reality of the industry: low/mid-range servers are commidity objects.  Custom-building is rarely viable, especially when you consider support on the darn thing.

For the DB, if you're doing SBS, you should have SQL Server.  I would recommend using that for storing the data, and use an Access front-end.  This gives them the ability to create new reports and queries, but limits the chances of having data eaten by the mental retardation that is Access.

---

### Post by tncmmngs on 2005-05-30
> **LordHunter317]Access has never, and will never work like that.

Do you have some references you can point to? I based my comment on:

1. Microsoft (not a Microsoft partner or other consulting firm with Microsoft ties) analysis  of traffic utilization on our network and resulting recommendations. 

2. Microsoft documentation. See MS KB article [URL=http://support.microsoft.com/default.aspx?scid=KB said:**
> 303519[/URL] . Here's a snip:
[QUOTE]Microsoft Jet is a file-sharing database system. A file-sharing database is one in which all the processing of the file takes place at the client. When a file-sharing database, such as Microsoft Jet, is used in a multiuser environment, multiple client processes are using file read, write, and locking operations on the same shared file across a network. If, for any reason, a process cannot be completed, the file can be left in an incomplete or a corrupted state. Two examples of when a process may not be completed is when a client is terminated unexpectedly or when a network connection to a server is dropped.

If the processing takes place on the client, the client has to have the data.  The Access/Jet db and Foxpro engines work the same way. 

3. Internal network traffic analysis on a production network.

I'm pretty confident Access does work as I've described, but if you can point to some other authoritative documentation, I'm willing to learn.

I would agree that Access allows faster development (I've taught Access use and programming since 2.0), but would caution that I've seen **many** Access databases become unmanageable because of the ad hoc nature of the development Access encourages.

In the end, I would agree with your final comment in that if the client demands  a particular solution, give it to him. I offered my suggestions as alternatives he might propose.

---

### Post by LordHunter317 on 2005-05-30
[QUOTE=LordHunter317]
Do you have some references you can point to?[/quote]Yeah.  I don't see 50MB (or whatever the size of the DB is) of traffic everytime I open a remote Access database. It streams the bits it needs off of the fileserver as necessary.

> If the processing takes place on the client, the client has to have the data.  The Access/Jet db and Foxpro engines work the same way. Yes, but it doesn't have to have the entire DB, just the relevant portions.

It makes no logical sense when you consider the multi-user case anyway.  You have to write to the server copy, so why would Access read the entire thing locally anyway?
Nevermind the fact SMB simply doesn't work like that.  It allows it to treat it as a local file and access specific blocks as necessary.  A complete local copy isn't needed, nor is ever made.

[edit]Moreoever, think of it this way:  If Access really had ever required all of a 50MB database to be copied down from a network share, big corporations would have screamed for that to be changed ages ago.  That kind of load simply to open the database isn't acceptable.

---

### Post by tncmmngs on 2005-05-31
Those references?

> Yes, but it doesn't have to have the entire DB, just the relevant portions.

Right. Not the file. The data in the file. The data is processed by the client. For instance, If you asked your All Cars db to show you only red convertibles, the db engine on your PC still has to process the entire universe of data (the tables or queries used to build your question). All of the data, not just the result, moves over the network.

A client/server db, like MySql, sends only the question to the server, the server returns the answer. Here's another reference that may explain better than I can:

[http://www.expresstechnology.com/TechBulletins/SQLCompare.htm](http://www.expresstechnology.com/TechBulletins/SQLCompare.htm)

> Nevermind the fact SMB simply doesn't work like that. 

This is not a SMB-specific issue. It is a a file-sharing db model issue.

[edit]Moreoever, think of it this way:  If Access really had ever required all of a 50MB database to be copied down from a network share, big corporations would have screamed for that to be changed ages ago.  That kind of load simply to open the database isn't acceptable.[/QUOTE]

I know at least one that already has. Another MS recommendation was to use a terminal services-type solution, or an ASP solution. This would keep the data traffic concentrated on the server VLAN. We are phasing out use of Access db's stored on network servers.

---

### Post by LordHunter317 on 2005-06-01
[QUOTE=tncmmngs]
Right. Not the file. The data in the file. The data is processed by the client. For instance, If you asked your All Cars db to show you only red convertibles, the db engine on your PC still has to process the entire universe of data (the tables or queries used to build your question). All of the data, not just the result, moves over the network.[/quote]That's still not **all** the data in the database.  And no, it probably wouldn't even require the whole table.  It would require the index and the appropriate rows looked up from the index.

Yes, the network load will be higher in an Access database.  But it doesn't require the entire contents to be transferred necessarily.  It's still a **situation dependent** thing.  It might require all the data being transferred.  It might require an index and two rows being transferred.  It might require nothing.  You don't know.  You can't make any assumptions without knowing the data, how it's structured, and how it's being queried.

---

