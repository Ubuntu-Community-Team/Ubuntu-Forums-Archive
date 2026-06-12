---
title: "Unable to install openaudit unable to connect to mysql"
date: 2021-02-21
forum: Server Platforms
---

### Post by deepakdeshp on 2021-02-21
Using Ubuntu 20.04  virtual server. I had already set up mysql server and php applications like phpmyadmin and Moodle etc. I tried installing Open audit by running OAE-Linux-x86_64-release_4.0.2-2.run. While running it mysql and mariadb cannot be connected.** How do I recover mysql?  [B]I have various databases installed for mysql.**[/B]

```
[COLOR=#333333][FONT=&amp]sudo service mysql restart[/FONT][/COLOR][sudo] password for uma: 
Job for mariadb.service failed because the control process exited with error code.
See "systemctl status mariadb.service" and "journalctl -xe" for details.
uma@ubuntu:/var/www/html$ systemctl status mariadb.service
&#9679; mariadb.service - MariaDB 10.3.25 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor prese>
     Active: failed (Result: exit-code) since Sun 2021-02-21 13:56:52 UTC; 20s >
       Docs: man:mysqld(8)
             https://mariadb.com/kb/en/library/systemd/
    Process: 3132 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var>
    Process: 3140 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_ST>
    Process: 3146 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && >
    Process: 3193 ExecStart=/usr/sbin/mysqld $MYSQLD_OPTS $_WSREP_NEW_CLUSTER $>
   Main PID: 3193 (code=exited, status=1/FAILURE)

Feb 21 13:56:51 ubuntu systemd[1]: Starting MariaDB 10.3.25 database server...
Feb 21 13:56:51 ubuntu mysqld[3193]: 2021-02-21 13:56:51 0 [Note] /usr/sbin/mys>
Feb 21 13:56:51 ubuntu mysqld[3193]: 2021-02-21 13:56:51 0 [Warning] Could not >
Feb 21 13:56:52 ubuntu systemd[1]: mariadb.service: Main process exited, code=e>
Feb 21 13:56:52 ubuntu systemd[1]: mariadb.service: Failed with result 'exit-co>
Feb 21 13:56:52 ubuntu systemd[1]: Failed to start MariaDB 10.3.25 database ser>

mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


sudo apt purge mysql-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 default-mysql-client : Depends: mysql-client-8.0 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


  
```

---

### Post by TheFu on 2021-02-21
First, the post above has cut off important parts of the errors. Use a wider terminal or redirect the log output to a file then use a viewer/editor that supports line wrapping.

Second, please clarify - do you want mysql or do you want mariadb?  The interfaces and clients are compatible, but I think the DB files are not binary compatible anymore.

Third, take the last error message, cleans it of any local specific stuff, drop it into google search and see what gets returned.  Most of the time you'll see 10 possible answers.  TRY  THOSE.  If those don't work, include each, exactly as you entered it, back here.  If you aren't clear, we don't know.  It is 100% fine to say things you don't really understand.  Nobody knows everything.

For example, the top answer I see is that someone didn't actually install the DBMS server on their system. They only installed the client.  It is the top answer because everybody does it.

Package dependency issues can usually be traced back to not being consistent with patching.  Patch weekly. Fix any issues immediately.  The longer we wait to fix an APT issue, the worse it gets.  Eventually, a reinstall will be needed.  Manually installed .deb files can cause havoc with APT and dependencies. Often, 1 manually installed .deb file will require specific versions of packages (or claim to) and hold back a number of other packages. Over time, as the dependencies aren't updated, patching becomes harder and harder, until it breaks. This usually takes 3-6 months, so most of us would think it was something new, when it was something we did 6 months ago.

Might be worth noting that about 5 yrs ago, Ubuntu switched from mysql as the default to mariaDB being the default for that type of DBMS.  Package dependencies these days should be smart enough to accept either.  In the beginning, it wasn't that way.  Had a project management web-app decide that MariaDB was NOT a valid DBMS and during a weekly updated decided to remove it and install mysql instead.  Took me much longer than I'd like to admit to figure that issue out. Had about 4 hrs of downtime. I don't allow automatic, unattended, patching by Canonical since then.  Sure, my patching is automatic, but I have to kick it off and always look over the packages to be updated/installed on each system manually.

So, my first question is - did you actually install the "mysql-server" package?

---

### Post by deepakdeshp on 2021-02-22
Thank you for your reply.
The programs I installed use mysql , but open audit which I am trying to install uses MariaDB. 
I did try Google search but I couldnt get any good clue which would solve my problem.
I had installed mysql server but it broke as I tried installing openaudit. The programs like wordpress, wordpress,Joomla, Moodle which are installed are using mysql DB, till it was broken.

---

### Post by TheFu on 2021-02-22
> **deepakdeshp said:**
> Thank you for your reply.
The programs I installed use mysql , but open audit which I am trying to install uses MariaDB. 
I did try Google search but I couldnt get any good clue which would solve my problem.
I had installed mysql server but it broke as I tried installing openaudit. The programs like wordpress, wordpress,Joomla, Moodle which are installed are using mysql DB, till it was broken.

This is why people use VMs and Containers - so conflicting dependencies don't ... er ... conflict.  Plus, you are using a bunch of highly hackable systems there. Hopefully, you'll not put this onto the internet and only allow access through a VPN.  Making something work is relatively easy.  Making something secure is 100x harder.

If it was me, I'd not deploy any of those tools, but you have different needs, I suppose.
Setup a separate DBMS container or VM (depending on your skillz) and have all the clients connect into that instance. Obviously, the DBMS will need multiple databases, multiple logins, and shouldn't allow any connections from the outside world. Only the 3 web-app systems (assuming you go with VMs) should be allowed to talk to that MariaDB instance.  Since the clients for both mysql and mariaDB are the same, it won't matter what each project uses.  You will have more troubles with having specific php versions and non-conflicting versions of php modules. I'd use a separate container/VM for each to make life easier.

BTW, you might find that some only support mySQL clients in the 7.x line and some support only mySQL clients in the 8.x line. It gets ugly.  Separation via containerization is the least overhead method, but you'll need to learn to rebuild the systems weekly and redeploy. That's how patching of containers is done.  A little more CPU+RAM overhead (10x) would be to use separate VMs for each.  Treat each VM just like another server.

Systems architecture is where security begins.  Starting out with systems that can never be patched is a recipe for failure and being hacked.

Good luck with whatever you decide.

---

### Post by LHammonds on 2021-02-22
FYI - I do not think you can install both MySQL and MariaDB on the same server...and I am not sure if you were trying to do so based on what has been said so far.  Even though the client libraries tend to work for either database system, the databases themselves are no longer binary compatible...meaning, you cannot run MySQL, then uninstall MySQL, install MariaDB and expect MariaDB to make use of the database files from MySQL.  You "can" export the data from either one into .SQL backup files and import into the other system but as said before, they are not binary compatible anymore and there are differences in structure which may or may not affect you...such as how each implement "roles" for security....similar concepts but very different implementations which cannot be imported/exported between the different DBMS.

If you have one application that requires MariaDB and all others will work with MySQL "or" MariaDB, then you need to stick with MariaDB for your database back-end server if you intend on one DBMS hosting all the various application databases.  Would certainly make it easier to manage even if you separate the databases on different servers.

But to more directly address your current issue, you need to purge MySQL and MariaDB off the server completely before attempting to install MariaDB (server).

When asking for help about such issues, make it absolutely clear what you are trying to use by using the exact name (and preferably the version number) to avoid confusion on your part and ours.  Stating Ubuntu 20.04 was great and the output shows MariaDB 10.3.25 which is about 3 stable branches behind and released on Oct 7th, 2020.  Even though the command-line to invoke the database console is called "mysql" for compatibility reasons, be careful when asking for help and describing the database as "MySQL" if it is actually "MariaDB"

When installing MariaDB, you can pick which branch to use (10.3, 10.4, 10.5).  10.5 is the current stable branch.  The others are considered "old" and not recommended to use unless you have a specific need.  [https://downloads.mariadb.org/mariadb/repositories/#mirror=jaleco](https://downloads.mariadb.org/mariadb/repositories/#mirror=jaleco)

Here is an article I wrote describing how I installed 10.4 on Ubuntu Server 20.04 when it came out.  This setup is for a dedicated database server intended to be used by various other application servers (no local web server at all).  Seeing how others install a system might be helpful in how you do yours...or not...depending on your needs.  [https://hammondslegacy.com/forum/viewtopic.php?f=40&t=279](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=279)

**EDIT:** I also would not recommend installing myphpadmin on your database server or any web server accessing it.  But if you do, make sure it CANNOT be accessed from the Internet.  myphpadmin is a bit bloated.  I would recommend a lighter utility if you absolutely must use a web interface such as [adminer](https://www.adminer.org/).  But I REALLY recommend just using SSH and the command-line.  Repetitive tasks such as backup/restore can be automated using shell scripts.  But I understand if you need to "design" databases/tables using a GUI but still recommend NOT using it against a production server.  Use it on a development server and take the .SQL file exports and run those on the production server via command-line.

LHammonds

---

### Post by deepakdeshp on 2021-02-23
> **TheFu said:**
> This is why people use VMs and Containers - so conflicting dependencies don't ... er ... conflict.  Plus, you are using a bunch of highly hackable systems there. Hopefully, you'll not put this onto the internet and only allow access through a VPN.  Making something work is relatively easy.  Making something secure is 100x harder.

If it was me, I'd not deploy any of those tools, but you have different needs, I suppose.
Setup a separate DBMS container or VM (depending on your skillz) and have all the clients connect into that instance. Obviously, the DBMS will need multiple databases, multiple logins, and shouldn't allow any connections from the outside world. Only the 3 web-app systems (assuming you go with VMs) should be allowed to talk to that MariaDB instance.  Since the clients for both mysql and mariaDB are the same, it won't matter what each project uses.  You will have more troubles with having specific php versions and non-conflicting versions of php modules. I'd use a separate container/VM for each to make life easier.

BTW, you might find that some only support mySQL clients in the 7.x line and some support only mySQL clients in the 8.x line. It gets ugly.  Separation via containerization is the least overhead method, but you'll need to learn to rebuild the systems weekly and redeploy. That's how patching of containers is done.  A little more CPU+RAM overhead (10x) would be to use separate VMs for each.  Treat each VM just like another server.

Systems architecture is where security begins.  Starting out with systems that can never be patched is a recipe for failure and being hacked.

Good luck with whatever you decide.
That is nicely written. Systems have to be always patched to the latest patches, very true. You say that my system is very hackable, why would you say that? I thought that Linux systems are much more secure. I have put all the applications and their databases in a single vm. The server will not be exposed to the internet only accessible on the LAN by me. The idea here is to learn about applications with hands on experience like wordpress , drupal,joomla,dolibarr,alfresco and magento.

---

### Post by deepakdeshp on 2021-02-23
> **LHammonds said:**
> FYI - I do not think you can install both MySQL and MariaDB on the same server...and I am not sure if you were trying to do so based on what has been said so far.  Even though the client libraries tend to work for either database system, the databases themselves are no longer binary compatible...meaning, you cannot run MySQL, then uninstall MySQL, install MariaDB and expect MariaDB to make use of the database files from MySQL.  You "can" export the data from either one into .SQL backup files and import into the other system but as said before, they are not binary compatible anymore and there are differences in structure which may or may not affect you...such as how each implement "roles" for security....similar concepts but very different implementations which cannot be imported/exported between the different DBMS.

If you have one application that requires MariaDB and all others will work with MySQL "or" MariaDB, then you need to stick with MariaDB for your database back-end server if you intend on one DBMS hosting all the various application databases.  Would certainly make it easier to manage even if you separate the databases on different servers.

But to more directly address your current issue, you need to purge MySQL and MariaDB off the server completely before attempting to install MariaDB (server).

When asking for help about such issues, make it absolutely clear what you are trying to use by using the exact name (and preferably the version number) to avoid confusion on your part and ours.  Stating Ubuntu 20.04 was great and the output shows MariaDB 10.3.25 which is about 3 stable branches behind and released on Oct 7th, 2020.  Even though the command-line to invoke the database console is called "mysql" for compatibility reasons, be careful when asking for help and describing the database as "MySQL" if it is actually "MariaDB"

When installing MariaDB, you can pick which branch to use (10.3, 10.4, 10.5).  10.5 is the current stable branch.  The others are considered "old" and not recommended to use unless you have a specific need.  [https://downloads.mariadb.org/mariadb/repositories/#mirror=jaleco](https://downloads.mariadb.org/mariadb/repositories/#mirror=jaleco)

Here is an article I wrote describing how I installed 10.4 on Ubuntu Server 20.04 when it came out.  This setup is for a dedicated database server intended to be used by various other application servers (no local web server at all).  Seeing how others install a system might be helpful in how you do yours...or not...depending on your needs.  [https://hammondslegacy.com/forum/viewtopic.php?f=40&t=279](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=279)

**EDIT:** I also would not recommend installing myphpadmin on your database server or any web server accessing it.  But if you do, make sure it CANNOT be accessed from the Internet.  myphpadmin is a bit bloated.  I would recommend a lighter utility if you absolutely must use a web interface such as [adminer]("https://www.adminer.org/").  But I REALLY recommend just using SSH and the command-line.  Repetitive tasks such as backup/restore can be automated using shell scripts.  But I understand if you need to "design" databases/tables using a GUI but still recommend NOT using it against a production server.  Use it on a development server and take the .SQL file exports and run those one idea is to  the production server via command-line.

LHammonds
Thank you. Openaudit which I was trying to install has an installable executible. After running it it broke mysql and there were prompts for installing Mariadb. I was trying to install [https://opmantek.com/network-dist](https://opmantek.com/network-dist) is only covery-inventory-software/ This isnt a production server. I have installed all applications like [COLOR=#000000]wordpress , drupal,joomla,dolibarr,alfresco and magento on a single virtual server. The idea is to get hands on experience on these application. It is only for learning purpose and there is no access to the server from the internet. Only I access the server from the LAN[/COLOR]

---

### Post by TheFu on 2021-02-23
Let's unpack this.

> **deepakdeshp said:**
> That is nicely written. Systems have to be always patched to the latest patches, very true. You say that my system is very hackable, why would you say that? 
Based on the way you planned to put multiple high-risk webapps onto a single system.  Systems architecture says a bunch about the team running the systems and their ability to secure it.  I was a guess based on that which demonstrated less than expert level skills.

> **deepakdeshp said:**
> I thought that Linux systems are much more secure. 
A poorly deployed application stack will still end up with a non-secure system regardless of the OS.

> **deepakdeshp said:**
> I have put all the applications and their databases in a single vm. 
Exactly. THIS choice isn't the way that a professional admin and professional application support team would do it for an enterprise with a separate security team.  It is fine for deploying cat video servers, but I wouldn't all my enterprise data on a system setup that way.

> **deepakdeshp said:**
> The server will not be exposed to the internet only accessible on the LAN by me. 
Well, that *could* drastically reduce the attack vectors. Hard to say, since we don't know anything about how your LAN is secured ... or not secured.  Typical home users have routers that haven't been patched in years, with UPnP enabled, and don't think twice before clicking a URL shortened link in any email they get. There's no way to actually knwo where that link will send them - could be jumping from link to link to link to link for 5 minutes. Racking up ad views for the original guys.  Software programmers are almost always just as guilty of these faults too.  When I was a programmer, constantly solving challenges, security on the internet wasn't really much of a concern ... until I got hacked the first time.  It can happen to anyone on their desktop, their phone and on their servers.  A WAN firewall isn't the end of security considerations and if someone wants to get in, wordpress that isn't locked down will probably be the easiest method.  Though Joomla, Dupal, and other CMS systems have problems too.  Just assume that 2M wordpress sites are compromised right now. Most of the owners don't know or don't care.

If you get any emails with phishing links ... setup a secured environment that you are willing to have hacked and clink on the links. See what happens. Follow the reasonable things to be done, assuming that you trusted just the first link.

And never trust AV software completely.  Assume those are about 50% useful. Nothing can replace an informed end-user clicking the mouse and typing things into the browser. AV doesn't mean we get to be stupid.

> **deepakdeshp said:**
> The idea here is to learn about applications with hands on experience like wordpress , drupal,joomla,dolibarr,alfresco and magento.

Alfresco used to be a bear to upgrade.  Our security guys won't allow php web-apps to be on the internet. To access those, a VPN must be used.  Magento had some big security failure in the last few years. Be certain you read up about that.  Actually, OWASP has a Top-10 List for most programming languages that every admin and security conscious admin should know how to exploit, test, and mitigate.

Getting stuff to work usually isn't all that hard.  Keeping it up, maintained, current, patch, backed up, and testing the recovery for each at least annually is what professionals do.  Backups that haven't been validated by direct test restores can't be called backups.  They are prayers and hope.  Until you actually restore a system, there's no way to know you have what you need to recover and save a business that was hacked ... let's say 2 weeks to 13 weeks ago.  My #1 security technique is to have automatic, daily, versioned, backups with at least 60 days of versions for low-risk systems. Higher risk systems have over 6 months of backup versions.

Securing all that stuff is very hard.

---

### Post by LHammonds on 2021-02-23
> **deepakdeshp said:**
> Openaudit which I was trying to install has an installable executible.yuck, I try to avoid pre-compiled installers.

> **deepakdeshp said:**
> After running it it broke mysql and there were prompts for installing Mariadb.And this is why.

> **deepakdeshp said:**
> [COLOR=#000000]The idea is to get hands on experience on these application. It is only for learning purpose and there is no access to the server from the internet. Only I access the server from the LAN[/COLOR]Learning in a safe environment awesome.  However, be wary of learning how things work when you install them in a manner unlike production.  For example, a developer might install a database and 2 or 3 web servers on the same machine.  If they configure things to work this way, they might be learning bad habits or at the very least, incorrect/insecure ways of configuring the system that do not apply to a production system.  The user credential setup / design for web users accessing a local database is NOT the same for web users on a separate web server accessing a separate / dedicated database server.  ([Reference Example](https://hammondslegacy.com/forum/viewtopic.php?p=909#p909))  Also, testing an application that is also running on the database server completely by-passes any firewall rules that would be in place in a production environment.  A web application server would need to connect to the database server and pass through the firewall rules. ([Reference Example](https://hammondslegacy.com/forum/viewtopic.php?p=858#p858)).  Another potential issue would be a web developer creating links referencing another site via hard-coded local values or server-side paths that only exist "if" both app servers are on the same machine but then breaks later when the sites need to be separated onto different web servers for better performance.  I have seen WordPress admins make this mistake all the time requiring me to scrub the code and database for problem links and correct them (and then caching of those bad links can cause even more headaches).

[Open-AudIT Requirements](https://community.opmantek.com/display/OA/Server+Requirements) states that it uses MySQL, not MariaDB.  This does not match what you are experiencing.  Looking at the [Dependencies page](https://community.opmantek.com/pages/viewpage.action?pageId=25299095), it shows "mysql-server" in most operating systems but in the very latest (such as Ubuntu 20.04), it switches to mariadb-server.  I REALLY do not like applications that try to pack it all (database, web server, CGI, etc.) regardless of what you already have installed because it tends to create "silo" systems which I try to avoid if at all possible.  There is a paradigm shift happening with containers in this regard but to me, the tech is still not mature enough for my adoption.

If you find that you need to increase the performance of Open-AudIT, would this package allow for flexibility such as a dedicated database and 3 or 4 Open-AudIT web servers?  Would you be able to use reverse-proxy servers to help facilitate load balancing?  ([Reference Example](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260)).   If this application cannot scale to accommodate growth, you should attach this risk as part of the analysis of this package.  I have used Nagios and a single server can handle a great many devices but as the device count increases and the diversity of locations become problematic (e.g. world-wide), I have the option to roll out additional servers to extend the monitoring capacity.

Wall of text has come to an end as I go home for the day (lucky you. hehehe)

LHammonds

---

### Post by deepakdeshp on 2021-02-24
It is always a privilege to get the opinions of advanced and expert Ubuntu users like you. Thank you for your time, especially for finding about OA(Open Audit) and giving your opinion.Actually I am retired and will not be configuring any production servers at all. I was associated with computers one way or the other throughout my career so I find this as the way to keep in touch and marvel at the open source tools and the facilities they offer.
True that the single package offered by OA is a bad idea, it offers all in the package like database etc. and tends to break things as i found out myself. Providing Docker image for OA would have  been better. I had dabbled a bit in Nagios, I think Nagios xi is much better with the added features, easy to configure and use.

---

### Post by LHammonds on 2021-02-24
Advanced in age maybe, certainly not what I'd call an expert.  I would need Linux certifications before being considered an expert.  Nagios is just what I know because I researched it way back in the day and that is what I utilize for my needs.

Have fun with Ubuntu.  I know I have.

LHammonds

---

### Post by deepakdeshp on 2021-02-25
> **LHammonds said:**
> Advanced in age maybe, certainly not what I'd call an expert.  I would need Linux certifications before being considered an expert.  Nagios is just what I know because I researched it way back in the day and that is what I utilize for my needs.

Have fun with Ubuntu.  I know I have.

LHammonds
Certification doesnt make an all wise man IMO. They are no doubt important, but many times the real world fire  and experience makes the man an expert.

---

