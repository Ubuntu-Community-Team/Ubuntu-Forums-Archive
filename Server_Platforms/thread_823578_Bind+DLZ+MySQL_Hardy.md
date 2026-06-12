---
title: "Bind+DLZ+MySQL Hardy"
date: 2008-06-09
forum: Server Platforms
---

### Post by cycloptivity on 2008-06-09
Hi Guys,

Im not sure if its a run of bad luck on my part but try as i might finding doco on how to get DLZ running with a MySQL backend on hardy is impossible - Is anyone able to give me a hand to get this setup and running on a hardy server?

Cheers,

Kahn

---

### Post by cycloptivity on 2008-06-10
I take it this is either a, exceptionally easy and im being a blind halfwit or well you know the rest :P

I would be most gratefull for any assistance in this

Kahn.

---

### Post by cycloptivity on 2008-06-10
Nobody at all? Perhaps I posted this in the wrong place =\

---

### Post by cycloptivity on 2008-06-12
Bump bump - I take it no one has had to configure this on a ubuntu host?

---

### Post by drmoocow on 2008-08-27
I got this up and running yesterday. It requires rebuilding the bind9 package.

Make a temporary holding directory - I use /usr/local/src for this. From that directory, download the source for the bind9 package. Also, make sure the fakeroot and bison packages are installed.

```
mkdir -p /usr/local/src/bind9
cd /usr/local/src/bind9
apt-get install fakeroot bison
apt-get source bind9
```

This will bring the bind9 source into the bind9-9.4.2 directory. Inside there, edit the debian/rules file.

```
vi bind9.9.4.2/debian/rules
```

Look for the section starting with "configure-stamp:". You'll be adding a flag to the commandline - I added a backslash to the last option, and added --with-dlz-mysql on the next line.

```
    ./configure --prefix=/usr \
        --mandir=\$${prefix}/share/man \
        --infodir=\$${prefix}/share/info \
        --sysconfdir=/etc/bind \
        --localstatedir=/var/run/bind \
        --enable-threads \
        --with-libtool \
        --enable-shared \
        --enable-static \
        --with-openssl=/usr \
        --with-gnu-ld \
        --enable-ipv6 \
        --with-dlz-mysql

```

Save and exit the file.

Now you'll need to build the new package. From the bind9-9.4.2 directory, run the dpkg-buildpackage command:

```
dpkg-buildpackage -rfakeroot -b
```

Once it finishes compiling (it'll take around 5 minutes or so), you can install the packages. Back up one directory and run ls. You'll see a bunch of packages there ending in .deb.

Install all these packages to install your new bind9:

```
dpkg -i *.deb
```

Now you're set with bind9 installed. Now you can configure it to use DLZ.

cd into /etc/bind9. Edit your named.conf.options file and put your upstream provider's DNS servers into the forwarders section:

```
    forwarders {
        1.2.3.4;
        5.6.7.8;
    };

```

You can add as many DNS servers in there as you need, but two should suffice. Save and exit the file, then edit the named.conf.local file. Add this to the bottom:

```
dlz "Mysql zone" {
   database "mysql
   {host=127.0.0.1 dbname=db_name user=db_user pass=db_pass}
   {select zone from dns_records where zone = '%zone%'}
   {select ttl, type, mx_priority, case when lower(type)='txt' then concat('\"', data, '\"') when lower(type) = 'soa' then concat_ws(' ', data, resp_person, serial, refresh, retry, expire, minimum) else data end from dns_records where zone = '%zone%' and host = '%record%'}";
};
```

Change the information on the third line to match that of the MySQL database, username and password you'll be using. Save and exit this file.

Log in to MySQL and create the database and user you want to use.

```
create database db_name;
grant all privileges on db_name.* to db_user@localhost identified by 'db_pass';

```

Create the table you'll need for the DNS records. Change the resp_person default to the email address of the person responsible for the DNS server (probably you) in the format of username.domain.com - the @ becomes a period. Change the primary_ns to the name of your nameserver, ie. ns1.yourdomain.com.

```
 CREATE TABLE `dns_records` (
  `id` int(11) NOT NULL auto_increment,
  `zone` varchar(64) default NULL,
  `host` varchar(64) default NULL,
  `type` varchar(8) default NULL,
  `data` varchar(64) default NULL,
  `ttl` int(11) NOT NULL default '3600',
  `mx_priority` int(11) default NULL,
  `refresh` int(11) NOT NULL default '3600',
  `retry` int(11) NOT NULL default '3600',
  `expire` int(11) NOT NULL default '86400',
  `minimum` int(11) NOT NULL default '3600',
  `serial` bigint(20) NOT NULL default '2008082700',
  `resp_person` varchar(64) NOT NULL default 'resp.person.email',
  `primary_ns` varchar(64) NOT NULL default 'ns1.yourdns.here',
  `data_count` int(11) NOT NULL default '0',
  PRIMARY KEY  (`id`),
  KEY `host` (`host`),
  KEY `zone` (`zone`),
  KEY `type` (`type`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1
```

That's about it. Now all you need to do is enter records into the table.

```
// for www.domain.com to resolve to 1.2.3.4
insert into dns_records (zone, host, type, data, mx_priority) values ('domain.com', 'www', 'A', '1.2.3.4', null)

// for domain.com to resolve to 1.2.3.4
insert into dns_records (zone, host, type, data, mx_priority) values ('domain.com', '@', 'A', '1.2.3.4', null)

// for www2.domain.com to alias to www.domain.com
// note the trailing period in the data field
insert into dns_records (zone, host, type, data, mx_priority) values ('domain.com', 'www2', 'CNAME', 'www.domain.com.', null)

// for mail for domain.com to go to domain.com
// note the trailing period in the data field
insert into dns_records (zone, host, type, data, mx_priority) values ('domain.com', '@', 'MX', 'domain.com.', '0')

```

I won't go into too much detail about DNS, unless you need help with it. Just remember that any records that have a name in the data field - MX, CNAME, etc - need a trailing period. Also, MX records MUST have a name in the data field, not an IP, otherwise it won't work properly.

Let me know if you need any more assistance.

---

### Post by cycloptivity on 2008-09-23
lol at googling my own thread; Thanks for your reply mate - I will have a crack at it again tonight and see how i go!

Cheers,

Kahn

---

### Post by drmoocow on 2008-09-23
Anytime. Glad to be of service. :D

---

### Post by cycloptivity on 2008-09-24
OK finally i have a working version! I have written up a howto which you can find at [http://svn.the-mesh.org/trac.cgi/wiki/HardyBindDlzHowto](http://svn.the-mesh.org/trac.cgi/wiki/HardyBindDlzHowto) there was some additional steps needed for a vanilla Hardy Server install but I got there in the end. Many thanks moocow :D

---

### Post by kunstman on 2008-11-08
Hello,

I tried to setup a bind deamon with mysql backend descriped as above. But when i try to run the deamon with /etc/init.d/bind9 start i get an [fail] when i look in my /var/log/syslog file the following lines are showed:

Nov  8 20:33:04 mainserver named[30624]: Loading 'Mysql zone' using driver mysql^M
Nov  8 20:33:04 mainserver named[30624]: unsupported DLZ database driver 'mysql^M'.  Mysql zone not loaded.
Nov  8 20:33:04 mainserver named[30624]: loading configuration: not found
Nov  8 20:33:04 mainserver named[30624]: exiting (due to fatal error)

Does anybody know how this could be?

Thanks.

---

### Post by drmoocow on 2008-11-10
The ^M means that there's an extra linefeed in the config file that it wasn't expecting... this is usually caused by editing the file on a Windows box and copying it over. Windows and Unix don't use the same linefeed codes.

You can fix it by editing the named.conf.local file with your favorite editor (nano, vi, emacs, whatever). At the end of one or more of the lines (probably all of them) you'll see an ^M there. Delete that from each line and save the file and try again, you should be fine then.

Let me know.

---

### Post by cycloptivity on 2009-03-02
Since our SVN server isn't really know for its stability; Sorry for the bad formatting :)


Compile and run Bind9 (9.4.2) on Hardy Heron Server 8.04.1

For some time I have been looking for howto's on this topic however have come up empty; A Post (I also borrowed some of drmoocows examples in this text) on the ubuntu forums lead me to getting started on my attempts again. So after a few hours here is the howto for a working DNS server.

Get the sources

apt-get install dpkg-dev
mkdir -p /usr/local/src/bind9
cd /usr/local/src/bind9
apt-get source bind9
mkdir -p /usr/local/src/mysql
cd /usr/local/src/mysql
apt-get source mysql-server 


Get the build essentials

apt-get update
apt-get install mysql-common libncurses5-dev libwrap0-dev libreadline5-dev chrpath automake1.9 doxygen texlive-latex-base gs dpatch gawk fakeroot bison libtool libssl-dev build-essential debhelper gcc

You may also want to install something to administer the MySQL server which is my preferred method which you can do by adding phpmyadmin to the apt-get install list.
Build MySQL & Install

dpkg-buildpackage -rfakeroot -b
cd ..
dpkg -i *.deb


Build Bind9 & Install

cd /usr/local/src/bind9/bind9-9.4.2/
vim debian/rules

Look for the section starting with "configure-stamp:". You'll be adding a flag to the commandline - I added a backslash to the last option, and added --with-dlz-mysql on the next line, also consider --disable-threads \ as they dont work any on a Linux system according to the doco at [http://bind-dlz.sourceforge.net/mysql_driver.html](http://bind-dlz.sourceforge.net/mysql_driver.html)

dpkg-buildpackage -rfakeroot -b
cd ..
dpkg -i *.deb

Now you should have both MySQL and Bind compiled and installed and even running with any luck its time to configure Bind


Configuration /etc/bind/named.conf.local

dlz "Mysql zone" {
   database "mysql
   {host=127.0.0.1 dbname=changeme port=3306 user=changeme pass=changeme}
   {select zone from dns_records where zone = '%zone%'}
   {select ttl, type, mx_priority, case when lower(type)='txt' then concat('\"', data, '\"')
        else data end from dns_records where zone = '%zone%' and host = '%record%'
        and not (type = 'SOA' or type = 'NS')}
   {select ttl, type, mx_priority, data, resp_person, serial, refresh, retry, expire, minimum
        from dns_records where zone = '%zone%' and (type = 'SOA' or type='NS')}
   {select ttl, type, host, mx_priority, data, resp_person, serial, refresh, retry, expire,
        minimum from dns_records where zone = '%zone%' and not (type = 'SOA' or type = 'NS')}
   {select zone from xfr_table where zone = '%zone%' and client = '%client%'}
   {update data_count set count = count + 1 where zone ='%zone%'}";
};

You may also want to add forwarders in BIND if you plan to use the server for Internet address lookups.


SQL Here is some test DNS data for you to use

-- phpMyAdmin SQL Dump
-- version 2.11.3deb1ubuntu1.1
-- [http://www.phpmyadmin.net](http://www.phpmyadmin.net)
--
-- Host: localhost
-- Generation Time: Sep 24, 2008 at 07:19 PM
-- Server version: 5.0.51
-- PHP Version: 5.2.4-2ubuntu5.3

SET SQL_MODE="NO_AUTO_VALUE_ON_ZERO";

--
-- Database: `bind`
--
CREATE DATABASE `bind` DEFAULT CHARACTER SET latin1 COLLATE latin1_swedish_ci;
USE `bind`;

-- --------------------------------------------------------

--
-- Table structure for table `dns_records`
--

CREATE TABLE IF NOT EXISTS `dns_records` (
  `id` int(11) NOT NULL auto_increment,
  `zone` varchar(64) default NULL,
  `host` varchar(64) default NULL,
  `type` varchar(8) default NULL,
  `data` varchar(64) default NULL,
  `ttl` int(11) NOT NULL default '3600',
  `mx_priority` int(11) default NULL,
  `refresh` int(11) NOT NULL default '3600',
  `retry` int(11) NOT NULL default '3600',
  `expire` int(11) NOT NULL default '86400',
  `minimum` int(11) NOT NULL default '3600',
  `serial` bigint(20) NOT NULL default '2008082700',
  `resp_person` varchar(64) NOT NULL default 'resp.person.email',
  `primary_ns` varchar(64) NOT NULL default 'ns1.yourdns.here',
  `data_count` int(11) NOT NULL default '0',
  PRIMARY KEY  (`id`),
  KEY `host` (`host`),
  KEY `zone` (`zone`),
  KEY `type` (`type`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=9 ;

--
-- Dumping data for table `dns_records`
--

INSERT INTO `dns_records` (`id`, `zone`, `host`, `type`, `data`, `ttl`, `mx_priority`, `refresh`, `retry`, `expire`, `minimum`, `serial`, `resp_person`, `primary_ns`, `data_count`) VALUES
(7, 'domain.com', 'www2', 'CNAME', 'www.domain.com.', 3600, NULL, 3600, 3600, 86400, 3600, 2008082700, 'resp.person.email', 'ns1.yourdns.here', 0),
(6, 'domain.com', '@', 'A', '1.2.3.4', 3600, NULL, 3600, 3600, 86400, 3600, 2008082700, 'resp.person.email', 'ns1.yourdns.here', 0),
(5, 'domain.com', 'www', 'A', '1.2.3.4', 3600, NULL, 3600, 3600, 86400, 3600, 2008082700, 'resp.person.email', 'ns1.yourdns.here', 0),
(8, 'domain.com', '@', 'MX', 'domain.com.', 3600, 0, 3600, 3600, 86400, 3600, 2008082700, 'resp.person.email', 'ns1.yourdns.here', 0);


Testing You should now be able to use your DNS server if you dont get something like below go back over the steps and feel free to contact Kahn in IRC at irc://dm1.irc.the-mesh.org:6667 #themesh

root@ns1:/usr/local/src/bind9# dig [www.domain.com](www.domain.com) @127.0.0.1

; <<>> DiG 9.4.2-P1 <<>> [www.domain.com](www.domain.com) @127.0.0.1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3212
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.domain.com](www.domain.com).			IN	A

;; ANSWER SECTION:
[www.domain.com](www.domain.com).		3600	IN	A	1.2.3.4

;; Query time: 13 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Sep 24 19:52:11 2008
;; MSG SIZE  rcvd: 48

root@ns1:/usr/local/src/bind9#

---

### Post by stevenjgarner on 2009-05-21
Many thanks for this.  Just successfully deployed BIND+DLZ+MySQL using this on a Xen virtual machine running on LTS Hardy Heron.  At first my installation was failing all DNS tests (dig, etc).  Turning on the debug severity of logging for BIND ([http://www.ludd.luth.se/~kavli/BIND8/logging.html](http://www.ludd.luth.se/~kavli/BIND8/logging.html)), the surprise was that the installation was working fine, but the zone data with which the SQL table was being populated was all wrong. Fortunately the "Bind with DLZ, MySQL and replication" tutorial at [http://en.gentoo-wiki.com/wiki/Setup_Bind_with_DLZ,_MySQL_and_replication#Sample](http://en.gentoo-wiki.com/wiki/Setup_Bind_with_DLZ,_MySQL_and_replication#Sample), includes data for a sample zone file.  After tweaking their suggestions a bit (e.g. you do not want NULL for data in the SOA record), we now have a database-driven BIND as our name server.

Here is the required format of the data for a typical zone:

INSERT INTO `dns_records` (`id`, `zone`, `host`, `type`, `data`, `ttl`, `mx_priority`, `refresh`, `retry`, `expire`, `minimum`, `serial`, `resp_person`, `primary_ns`, `data_count`) VALUES
('', 'domain.com', '@', 'SOA', 'ns1.yourdns.here.', 3600, NULL, 3600, 3600, 86400, 3600, 2008082700, 'resp.person.email.', 'ns1.yourdns.here.', 0),
('', 'domain.com', '@', 'NS', 'ns1.yourdns.here.', 3600, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL, 0),
('', 'domain.com', '@', 'NS', 'ns2.yourdns.here.', 3600, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL, 0),
('', 'domain.com', '@', 'A', '1.2.3.4', 3600, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL, 0),
('', 'domain.com', 'www', 'CNAME', 'domain.com.', 3600, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL, 0),
('', 'domain.com', '@', 'MX', 'mail.domain.com.', 3600, 10, NULL, NULL, NULL, NULL, NULL, NULL, NULL, 0),
('', 'domain.com', 'mail', 'A', '1.2.3.5', 3600, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL, 0);

... note the many instances of NULL; note the FQDN's (fully-qualified-domain-name's, with a period at the end).  I was interested to read in [http://bind-dlz.sourceforge.net/mysql_driver.html](http://bind-dlz.sourceforge.net/mysql_driver.html) that the MySQL DLZ driver is single threaded, which could be a performance issue with some name servers.  You might want to look at the Postgres driver which is threaded.

About secondary name servers.  The standard recommendation is to use MySQL replication so the same database information is driving BIND DLZ on both the primary and secondary name server.  We want to have all our database information clustered using DRBD on more than one server, so we're looking into an SSH tunnel from BIND DLZ through to the MySQL DRBD cluster.

My next step to optimize this a bit (before I load up on squillions of zone records) is to normalize the SQL table into 3 tables - one for the domain, one for the SOA information, and one for the zone records.  Should make things a lot cleaner when I attempt to create a web-interface.  Should be okay, as we can edit the DLZ configuration in named.conf.local with the necessary SQL joins.

Many thanks also to Raphael Burnes, who pointed much of this out to me. You won't stay anonymous forever!

---

### Post by Disty on 2010-04-22
Sorry to drag this thread back up- and this time it's on Karmic too, but I'm getting very poor stability of BIND with mysql/dlz.

Here are some error messages from /var/log/syslog:

```
Apr 22 21:12:17 dnsdebug named[6613]: mysql driver unable to return result set for lookup query
Apr 22 21:12:17 dnsdebug kernel: [285552.573949] type=1503 audit(1271963537.759:53): operation="open" pid=6618 parent=1 profile="/usr/sbin/named" requested_mask="::rw" denied_mask="::rw" fsuid=107 ouid=0 name="/dev/tty"
Apr 22 21:12:17 dnsdebug named[6613]: mysql driver unable to return result set for lookup query
Apr 22 21:13:17 dnsdebug named[6613]: last message repeated 7 times
```

Any ideas what could be causing this or how I could fix it? I constantly have to restart BIND!

---

### Post by chaseleightone on 2011-08-11
I got stuck installing on Ubuntu 10.04.3 LTS (Lucid Lynx) at the step:

Build MySQL & Install step, here's what I did:

cd mysql-dfsg-5.1-5.1.41
./configure --prefix=/usr/local/mysql

... and towards the end of the config I ran into a snag with:

config.status: error: cannot find input file: Docs/Makefile.in

not really adept at fixing compiling errors, I am reaching out for any advice on how to proceed with this. I'm also writing this up as a blog post on:

[http://fanaticaltenacity.blogspot.co...-dns-name.html](http://fanaticaltenacity.blogspot.co...-dns-name.html)

---

### Post by capsula4 on 2011-09-17
Very nice tutorial, this really helped me a lot!!

The only thing I cannot get to work are the dns records with "@" as host

In the examples given on this post, "www MX" and "www2 CNAME" worked great for me, but none of the "host=@" records worked.

Any idea?

Thanks!

---

### Post by wazza75 on 2012-11-24
Thanks for the article. I just have one query, since you are not specially configuring mysql in any way, is it really necessary to build mysql from source? Can you just install mysql from the repositories and install bind9 from source?

Warwick

---

### Post by Andruk Tatum on 2013-01-07
I had to add this to debian/rules to get it to successfully compile with any DLZ option:

the line was:

```
export CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE $(DEBUG) $(OPT)
```

is now:

```
export CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE $(DEBUG) $(OPT) -DDLZ
```

This fixes linking issues with the contrib/dlz/drivers/sdlz_helper.c file.



The named daemon was also failing to start, so I checked syslog to see what was going on. I had to run the following commands to get the named daemon to successfully start (make sure there is a "bind" user in /etc/passwd):

```
sudo touch /var/log/query.log
sudo chown bind /var/log/query.log
sudo chgrp bind /var/log/query.log
```

---

### Post by Andruk Tatum on 2013-01-12
You can create a read-only Postgres user (I called mine "bind9_dlz_readonly") by executing the following SQL:

```

--
-- Create the bind9_dlz_readonly user, 
-- without privileges to create databases, 
-- without privileges to create users, 
-- and with an encrypted password.
--
CREATE USER bind9_dlz_readonly NOCREATEDB NOCREATEUSER WITH ENCRYPTED PASSWORD '<password>';

--
-- Revoke all permissions on the bind9_dlz database (that's 
-- what I called mine) from the user we just created.
--
-- Note that you have to do this on every database you don't 
-- want the bind9_dlz_readonly user to be able to connect to.
--
REVOKE ALL ON DATABASE bind9_dlz FROM bind9_dlz_readonly;

--
-- Grant connection privileges to the bind9_dlz_readonly user.
--
GRANT CONNECT TO DATABASE bind9_dlz TO bind9_dlz_readonly;

--
-- Grant selection (read) privileges to the bind9_dlz_readonly 
-- user on the bind9_dlz and dns_xfr tables.
--
GRANT SELECT ON dns_record, dns_xfr TO bind9_dlz_readonly;

```

If you are using psql, you can check the privileges on all databases by using the 
[FONT="Courier New"]\list[/FONT]
command.

It returns a table that looks like 
```

   Name    |  Owner   | Encoding |   Collate   |    Ctype    |       Access privileges       
-----------+----------+----------+-------------+-------------+-------------------------------
 bind9_dlz | postgres | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =Tc/postgres                 +
           |          |          |             |             | postgres=CTc/postgres        +
           |          |          |             |             | bind9_dlz_readonly=c/postgres
           .          .          .             .             .                               
           .          .          .             .             .                               
           .          .          .             .             .                               

```

Where the access privileges is of the format
<(username>=<permissions/<user who granted permissions>

And access privileges are indicated by:

[LIST]
[*][FONT="Courier New"]r[/FONT] -- SELECT
[*][FONT="Courier New"]w[/FONT] -- UPDATE
[*][FONT="Courier New"]a[/FONT] -- INSERT
[*][FONT="Courier New"]d[/FONT] -- DELETE
[*][FONT="Courier New"]D[/FONT] -- TRUNCATE
[*][FONT="Courier New"]x[/FONT] -- REFERENCES
[*][FONT="Courier New"]t[/FONT] -- TRIGGER
[*][FONT="Courier New"]X[/FONT] -- EXECUTE
[*][FONT="Courier New"]U[/FONT] -- USAGE
[*][FONT="Courier New"]C[/FONT] -- CREATE
[*][FONT="Courier New"]c[/FONT] -- CONNECT
[*][FONT="Courier New"]T[/FONT] -- TEMPORARY
[*][FONT="Courier New"]arwdDxt[/FONT] -- all table privileges (differs for other types of objects)
[/LIST]

So the lines in the table above would be read as:
[LIST]
[*]Any user (PUBLIC) has been granted TEMPORARY (T) and CONNECT (c) privileges by the postgres user.
[*]The postgres user has been granted CREATE DATABASE (C), TEMPORARY (T), and CONNECT (c) privileges by the postgres user.
[*]The bind9_dlz_readonly user has been granted CONNECT (c) privileges by the postgres user.
[/LIST]

The postgres user granting privileges to itself makes sense because it is the owner of the database.

To list the table access privileges, you can use the 
[FONT="Courier New"]\dp[/FONT]
command.

It returns a table that looks like
```

                                        Access privileges
 Schema |       Name        |   Type   |       Access privileges       | Column access privileges 
--------+-------------------+----------+-------------------------------+--------------------------
 public | dns_record        | table    | postgres=arwdDxt/postgres    +| 
        |                   |          | bind9_dlz_readonly=r/postgres | 
 public | dns_record_id_seq | sequence |                               | 
 public | dns_xfr           | table    | postgres=arwdDxt/postgres    +| 
        |                   |          | bind9_dlz_readonly=r/postgres | 

```

So the lines in the above table would be read as:
[LIST]
[*]The postgres user has been granted all table privileges (INSERT, SELECT, UPDATE, DELETE, TRUNCATE, REFERENCE, and TRIGGER) by the postgres user on the dns_record table.
[*]The bind9_dlz_readonly user has been granted SELECT privileges by the postgres user on the dns_record table.
[*]The postgres user has been granted all table privileges (INSERT, SELECT, UPDATE, DELETE, TRUNCATE, REFERENCE, and TRIGGER) by the postgres user on the dns_xfr table.
[*]The bind9_dlz_readonly user has been granted SELECT privileges by the postgres user on the dns_xfr table.
[/LIST]

References:
[http://stackoverflow.com/questions/5717611/postgresql-view-database-connect-permissions]("http://stackoverflow.com/questions/5717611/postgresql-view-database-connect-permissions")

---

