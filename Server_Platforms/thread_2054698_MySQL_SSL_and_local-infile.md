---
title: "MySQL SSL and local-infile"
date: 2012-09-07
forum: Server Platforms
---

### Post by tuxraiderpen on 2012-09-07
I have a setup a server via taskel | LAMP Server, and added phpadmin... all works great except two things.

1) MySQL SSL support

I have edited /etc/mysql/my.cnf to add

local-infile or
local-infile = 1

under [mysqld]

I need to load a file via phpmyadmin using import and the CSV LOAD DATA.

I get the #1148 used command not allowed.... message, which the above should correct.

I've edited and restarted mysql, rebooted, and still nothing will change this response.

BUT

doing it via:

:~$ mysql -umyuser -pmypass --local-infile=1 mydb

Works... what is not getting set in my.cnf to allow the this for the server and phpmyadmin and possibly other php scripts? ? 

2) SSL

I've followed two examples to enable SSL support, with no joy...

[https://mifosforge.jira.com/wiki/display/MIFOS/How+to+enable+MySQL+SSL+on+Ubuntu](https://mifosforge.jira.com/wiki/display/MIFOS/How+to+enable+MySQL+SSL+on+Ubuntu)

[http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-debian-squeeze](http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-debian-squeeze)

And yet SSL still shows "DISABLED"

Any ideas on correcting these issues?

KUbunutu 12.04 - full updates

MySQL, php, Apache, phpmyadmin added via packages from repos
via tasksel for LAMP, and apt-get for phpmyadmin

---

### Post by SeijiSensei on 2012-09-10
I can't answer your question, but it is really all that necessary to have SSL support in MySQL?  Most web applications talk to the database server over the localhost interface.  There's no need to encrypt that at all.

If you are connecting to the server from a remote workstation over the Internet, I'd use a VPN.  For a point-to-point connection, I find [shared-key OpenVPN solutions]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") a piece of cake to configure.

---

### Post by tuxraiderpen on 2012-09-10
> **SeijiSensei said:**
> I can't answer your question, but it is really all that necessary to have SSL support in MySQL?  Most web applications talk to the database server over the localhost interface.  There's no need to encrypt that at all.


MySQL supports SSL connections for clients and replication. We use this currently, on a different distro.

We want and use this on other servers. If we can't configure such a basic option on ubuntu based servers we will have to continue to use the other distro which takes this setup with out issue.

---

### Post by SeijiSensei on 2012-09-10
I use CentOS on servers.  Is there some reason you need to change distros?  "If it ain't broke, ..."

---

### Post by tuxraiderpen on 2012-09-10
> **SeijiSensei said:**
> I use CentOS on servers.  Is there some reason you need to change distros?  "If it ain't broke, ..."

Yes, we want a single distro solution desktop to laptop to server thus cutting down on support issues. We want to move away from RH/CentOS as they don't want desktop users for one. We have several others.

This is starting to veer off into a debate that doesn't really resolve my issue(s). Thanks.

---

### Post by SeijiSensei on 2012-09-10
I wasn't trying to debate, you, really.  I was just curious why you would switch.   

Also the vast majority of people who post here are not using things like SQL server replication.  That was the reason for my initial response about using SSL.  You're probably one of a very small number of people on this forum who would even have a plausible rationale for using that.  Oftentimes I see less experienced users than you who try to implement advanced solutions because they think those methods will enhance security in cases where there is no vulnerability to fix.

So, please don't take offense, and good luck!

---

### Post by Wim Sturkenboom on 2012-09-11
> 
:~$ mysql -umyuser -pmypass --local-infile=1 mydb

Works... what is not getting set in my.cnf to allow the this for the server and phpmyadmin and possibly other php scripts? ? 

Seeing that you use the mysql command, shouldn't your '*local-infile = 1*' directive not be in the [mysql] section instead of the [mysqld] section?

---

