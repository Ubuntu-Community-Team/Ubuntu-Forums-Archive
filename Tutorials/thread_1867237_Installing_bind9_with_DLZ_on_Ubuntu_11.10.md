---
title: "Installing bind9 with DLZ on Ubuntu 11.10"
date: 2011-10-22
forum: Tutorials
---

### Post by WitchCraft on 2011-10-22
When you think about installing a nameserver, then you theoretically could just install bind9 from the repositories.

This also works fine, if you work with file-based configuration.
But when you want to have a dynamic interface, e.g. your users can enter DNS names themselves, you don't want the dns server to be stopped and restarted at every entry, because this disrupts the service for everyone else.

So you want to use dynamic loadable zones (DLZ, [http://bind-dlz.sourceforge.net/](http://bind-dlz.sourceforge.net/)), which means bind9 uses a mysql/postgre/ODBC database as backend.
Then you can add n entries at your leisure, without having to restart the server.

But using bind9 with DLZ isn't that simple.
When you try, you'll find that it doesn't work.

Why that is, you see when you start the bind9 server **in debug mode**
```

named -g -d 9

```

You'll see this output
> 
22-Oct-2011 13:32:24.387 starting BIND 9.7.3 -g -d 9
22-Oct-2011 13:32:24.387 built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='


And you realize why it doesn't work.
Because bind9 in the ubuntu repositories has been compiled without DLZ support...

Of course, if bind9 doesn't load a SQL driver, it won't be able to access a SQL database...

So you have to recompile bind9.
And this is what this tutorial is about.

For this tutorial, for convenience, simplicity and ease of use, I will suppose you work as root.
However, this is not recommended for security reasons.
So if you don't, just add sudo in front of every apt-get directive.

```

apt-get install bind9
apt-get install bind9utils 
apt-get remove bind9
apt-get build-dep bind9
mkdir /home/yourusername/bind9
cd /home/yourusername/bind9
apt-get source bind9

```

The database dependencies (not included in build-dep bind9)
```

apt-get install libdb4.8-dev
apt-get install libpq-dev 
apt-get install libmysqlclient16-dev
apt-get install unixodbc unixodbc-dev

```

Install the databases themselves (you only need one of those)
```

apt-get install postgresql-9.1
apt-get install mysql-server mysql-client
apt-get install firebird2.5-superclassic 

```


cd /home/yourusername/sources/bind9/bind9-9.7.3.dfsg

```

./configure --prefix=/usr --sysconfdir=/etc/bind --localstatedir=/var \
--mandir=/usr/share/man --infodir=/usr/share/info \
--enable-threads --enable-largefile --with-libtool --enable-shared --enable-static \
--with-openssl=/usr --with-gssapi=/usr --with-gnu-ld \
--with-dlz-postgres=yes --with-dlz-mysql=yes --with-dlz-bdb=no \
--with-dlz-filesystem=yes --with-dlz-ldap=yes \
--with-dlz-stub=yes --with-geoip=/usr --enable-ipv6 

```

Now configure should run.

While configure is running, have a look at the configure statement, especially this argument:
```

--with-dlz-bdb=no

```

Note thatI have nothing against bdb (BerkeleyDB), as you see with "apt-get install libdb4.8-dev" but currently, configure doesn't like it:
> 
> checking for Berkeley DB DLZ driver... not found
> configure: error: could not find Berkeley DB include directory
> make: *** [configure-stamp] Error 1

([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=634533](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=634533))
So I just switched it off...


Now, if configure ran and didn't output an error message, initiate the make (compilation) process:
```

make

```
Otherwise, fix the error messages.

Now, while your system is compiling, we can create the database tables.

You can do this any way you like, I'll use pgamin3 for postgres, mysql-workbench for mysql, and flamerobin for firebird.
```

apt-get install pgadmin3
apt-get install flamerobin

```

For mysql-workbench, go to:
[http://dev.mysql.com/downloads/workbench/](http://dev.mysql.com/downloads/workbench/)

and download the most appropriate version of mysql-workbench   

Since I run Ubuntu 11.10 x64, and there is no such package, I downloaded mysql-workbench for ubuntu 11.04 x64.
[http://dev.mysql.com/downloads/workbench/5.2.html#downloads](http://dev.mysql.com/downloads/workbench/5.2.html#downloads)

Download it, then open a terminal, and change the current working directory to your download location.

There should be this file in that location:
> 
mysql-workbench-gpl-5.2.35-1ubu1104-amd64.deb



Now install it with
```

apt-get install libzip1 libgtkmm-2.4-1c2a python-paramiko python-pysqlite2 libctemplate0

dpkg -i mysql-workbench-gpl-5.2.35-1ubu1104-amd64.deb

```

Now start it (applications-->programming-->MySQL workbench in gnome-classic).


For those who use the 11.04 deb on 11.10, if your workbench freezes on the splash screen, just type alt+f4 and the workbench will show.

Now once arrived in mysql-workbench, click on connect (to localhost) and use  user root plus the password you set for user root during the mysql-installation.

Once you're connected (press alt+f4 if nothing happens)
go in menu Edit->Preferences->SQL Editor and
untick "Safe updates" (in order to be able to delete an entire table without where), then switch back to general (because you can't click OK here - bug) and then click OK. You may want to re-enable this options later on.


If SQL-workbench doesn't work, remove it with
```

apt-get remove mysql-workbench-gpl

```

and look out for another administration tool
like 
```

apt-get install mysql-admin 

```


Now, to connect to the postgres database, we first have to set the password:
```

su postgres
psql
ALTER USER postgres WITH ENCRYPTED PASSWORD 'your_password';
\q
exit

```


Now open pgamin3, and login to the database ON LOCALHOST (default port: 5432)


Now, enable remote access on your MySQL server:


In
```

/etc/mysql/my.cnf

```

change  
```

bind-address		= 127.0.0.1

```

to
```

#bind-address		= 127.0.0.1
bind-address		= 192.168.1.8

```
(with 192.168.1.8 being the server's internal IP address)

Add remote access:
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'your_password' WITH GRANT OPTION;


If you can't access mysql, you may have to change the mysql root user password:
```

open /usr/bin/mysqld_safe --skip-grant-tables

```

Start the mysql console:
```

mysql -u root -p mysql
update user set Password=PASSWORD('your_password') WHERE User='root';

```
then type exit to exit the mysql command line.




In order to enable postgresql remote access, do this:

Open 
```

/etc/postgresql/9.1/main/postgresql.conf

```
in a text editor.

Now change listen_addresses to your internal IP address, in this case 192.168.1.8
```

listen_addresses = 'localhost, 192.168.1.8'		# what IP address(es) to listen on;

```


Then, edit this file
```

/etc/postgresql/9.1/main/pg_hba.conf

```

and add
```
 
host    all             all             192.168.1.0/0           md5

``` 



Once you can connect to your databases, create the DLZ database:


MySQL
```

CREATE SCHEMA `bind9_dlz` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci ;

```


PostGreSQL
```


-- Database: "bind9_dlz"

-- DROP DATABASE "bind9_dlz";

CREATE DATABASE "bind9_dlz"
  WITH OWNER = postgres
       ENCODING = 'UTF8'
       TABLESPACE = pg_default
       LC_COLLATE = 'en_US.UTF-8'
       LC_CTYPE = 'en_US.UTF-8'
       CONNECTION LIMIT = -1;

```



Then, create the table-create scripts


MySQL:
```

-- MySQL dump 10.13  Distrib 5.1.58, for debian-linux-gnu (x86_64)
--
-- Host: localhost    Database: bind9_dlz
-- ------------------------------------------------------
-- Server version	5.1.58-1ubuntu1

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `dns_records`
--

DROP TABLE IF EXISTS `dns_records`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `dns_records` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `zone` varchar(255) NOT NULL,
  `host` varchar(255) NOT NULL DEFAULT '@',
  `type` varchar(255) NOT NULL,
  `data` text,
  `ttl` int(11) NOT NULL DEFAULT '86400',
  `mx_priority` int(11) DEFAULT NULL,
  `refresh` int(11) DEFAULT NULL,
  `retry` int(11) DEFAULT NULL,
  `expire` int(11) DEFAULT NULL,
  `minimum` int(11) DEFAULT NULL,
  `serial` bigint(20) DEFAULT NULL,
  `resp_person` varchar(255) DEFAULT NULL,
  `primary_ns` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `type` (`type`),
  KEY `host` (`host`),
  KEY `zone` (`zone`),
  KEY `zone_host_index` (`zone`(30),`host`(30)),
  KEY `type_index` (`type`(8))
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `dns_records`
--

LOCK TABLES `dns_records` WRITE;
/*!40000 ALTER TABLE `dns_records` DISABLE KEYS */;
/*!40000 ALTER TABLE `dns_records` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `xfr_table`
--

DROP TABLE IF EXISTS `xfr_table`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `xfr_table` (
  `zone` varchar(255) NOT NULL,
  `client` varchar(255) NOT NULL,
  KEY `zone` (`zone`),
  KEY `client` (`client`),
  KEY `zone_client_index` (`zone`(30),`client`(30))
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `xfr_table`
--

LOCK TABLES `xfr_table` WRITE;
/*!40000 ALTER TABLE `xfr_table` DISABLE KEYS */;
/*!40000 ALTER TABLE `xfr_table` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2011-10-19 23:04:01

```

PostGre:
```



--
-- PostgreSQL database dump
--

SET statement_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = off;
SET check_function_bodies = false;
SET client_min_messages = warning;
SET escape_string_warning = off;

SET search_path = public, pg_catalog;

SET default_tablespace = '';

SET default_with_oids = false;

--
-- Name: dns_record; Type: TABLE; Schema: public; Owner: postgres; Tablespace: 
--

CREATE TABLE dns_record (
    id integer NOT NULL,
    zone character varying(255) NOT NULL,
    ttl integer NOT NULL,
    type character varying(255) NOT NULL,
    host character varying(255) DEFAULT '@'::character varying NOT NULL,
    mx_priority integer,
    data text,
    primary_ns character varying(255),
    resp_contact character varying(255),
    serial bigint,
    refresh integer,
    retry integer,
    expire integer,
    minimum integer
);


ALTER TABLE public.dns_record OWNER TO postgres;

--
-- Name: dns_record_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE dns_record_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MAXVALUE
    NO MINVALUE
    CACHE 1;


ALTER TABLE public.dns_record_id_seq OWNER TO postgres;

--
-- Name: dns_record_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE dns_record_id_seq OWNED BY dns_record.id;


--
-- Name: dns_record_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('dns_record_id_seq', 1, false);


--
-- Name: dns_xfr; Type: TABLE; Schema: public; Owner: postgres; Tablespace: 
--

CREATE TABLE dns_xfr (
    zone character varying(255) NOT NULL,
    client character varying(255) NOT NULL
);


ALTER TABLE public.dns_xfr OWNER TO postgres;

--
-- Name: id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE dns_record ALTER COLUMN id SET DEFAULT nextval('dns_record_id_seq'::regclass);


--
-- Name: dns_record_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres; Tablespace: 
--

ALTER TABLE ONLY dns_record
    ADD CONSTRAINT dns_record_pkey PRIMARY KEY (id);


--
-- Name: dns_record_host_idx; Type: INDEX; Schema: public; Owner: postgres; Tablespace: 
--

CREATE INDEX dns_record_host_idx ON dns_record USING btree (host);


--
-- Name: dns_record_type_idx; Type: INDEX; Schema: public; Owner: postgres; Tablespace: 
--

CREATE INDEX dns_record_type_idx ON dns_record USING btree (type);


--
-- Name: dns_record_zone_idx; Type: INDEX; Schema: public; Owner: postgres; Tablespace: 
--

CREATE INDEX dns_record_zone_idx ON dns_record USING btree (zone);


--
-- Name: dns_xfr_client_idx; Type: INDEX; Schema: public; Owner: postgres; Tablespace: 
--

CREATE INDEX dns_xfr_client_idx ON dns_xfr USING btree (client);


--
-- Name: dns_xfr_zone_idx; Type: INDEX; Schema: public; Owner: postgres; Tablespace: 
--

CREATE INDEX dns_xfr_zone_idx ON dns_xfr USING btree (zone);


--
-- Name: public; Type: ACL; Schema: -; Owner: postgres
--

REVOKE ALL ON SCHEMA public FROM PUBLIC;
REVOKE ALL ON SCHEMA public FROM postgres;
GRANT ALL ON SCHEMA public TO postgres;
GRANT ALL ON SCHEMA public TO PUBLIC;

```


Then, insert the data

MySQL:
```


INSERT INTO `bind9_dlz`.`dns_records`
(`id`,`zone`,`host`,`type`,`data`,`ttl`,`mx_priority`,`refresh`,`retry`,`expire`,`minimum`,`serial`,`resp_person`,`primary_ns`)
VALUES
(1, 'example.com', '@', 'SOA', NULL, 180, NULL, 10800, 7200, 604800, 86400, 2011091101, 'admins.mail.hotmail.com', '77.84.21.84'), 
(2, 'example.com', '@', 'NS', '77.84.21.84', 180, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(3, 'example.com', '@', 'A', '77.84.21.84', 180, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(4, 'example.com', 'www', 'A', '77.84.21.84', 180, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(5, 'xn--unicode-example.com', '@', 'SOA', NULL, 180, NULL, 10800, 7200, 604800, 86400, 2011091101, 'admins.mail.hotmail.com', '77.84.21.84'), 
(6, 'xn--unicode-example.com', '@', 'NS', '77.84.21.84', 180, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(7, 'xn--unicode-example.com', '@', 'A', '77.84.21.84', 180, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(8, 'xn--unicode-example.com', 'www', 'A', '77.84.21.84', 180, NULL, NULL, NULL, NULL, NULL, NULL, NULL, NULL) 
;


```

PostGre:
```


insert into dns_record (id, zone, ttl, type, host, mx_priority, data, primary_ns, resp_contact, serial, refresh, retry, expire, minimum)
values
(1, 'example.com', 180, 'SOA', '@', NULL, NULL, '77.84.21.84', 'admins.mail.hotmail.com', 2011091101, 10800, 7200, 604800, 86400), 
(2, 'example.com', 180, 'NS', '@', NULL, '77.84.21.84', NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(3, 'example.com', 180, 'A', '@', NULL, '77.84.21.84', NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(4, 'example.com', 180, 'A', 'www', NULL, '77.84.21.84', NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(5, 'xn--unicode-example.ch', 180, 'SOA', '@', NULL, NULL, '77.84.21.84', 'admins.mail.hotmail.com', 2011091101, 10800, 7200, 604800, 86400), 
(6, 'xn--unicode-example.com', 180, 'NS', '@', NULL, '77.84.21.84', NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(7, 'xn--unicode-example.com', 180, 'A', '@', NULL, '77.84.21.84', NULL, NULL, NULL, NULL, NULL, NULL, NULL), 
(8, 'xn--unicode-example.com', 180, 'A', 'www', NULL, '77.84.21.84', NULL, NULL, NULL, NULL, NULL, NULL, NULL) 
;

```


Now comes the trickiest part:
Create the bind9 config file.

For MySQL (/etc/bind/named.conf):
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
#auskommentiert !!!
#include "/etc/bind/named.conf.options";
#include "/etc/bind/named.conf.local";
#include "/etc/bind/named.conf.default-zones";


key "rndc-key" {
            // how was key encoded
            algorithm hmac-md5;
            // what is the pass-phrase for the key
	        secret "4ptlffIBhVnZgfdT0CXIcLDZeONxA5bHUVT5W2NofC9O4FOfjps8FzghoQy4myXnJ0g9jrna9Sjl6uKt6c/22A==";
             };


#options {
#default-key "rndc-key";
#default-server 127.0.0.1;
#default-port 953;
#};

controls {
inet * port 953 allow { any; } keys { "rndc-key"; };
#inet * port 53 allow { any; } keys { "rndc-key"; };
};



logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity dynamic;
    };

    category queries { query.log; };
};





dlz "Mysql zone" {
   database "mysql
   {host=127.0.0.1 port=3306 dbname=bind9_dlz user=root password=your_password}
   {SELECT zone FROM dns_records WHERE zone = '$zone$'}
   {SELECT ttl, type, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data
    FROM dns_records
    WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT ttl, type, data, primary_ns, resp_person, serial, refresh, retry, expire, minimum
    FROM dns_records
    WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}
   {SELECT ttl, type, host, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data, resp_person, serial, refresh, retry, expire, minimum
    FROM dns_records
    WHERE zone = '$zone$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT zone FROM xfr_table where zone='$zone$' AND client = '$client$'}";
};

```


And PostgreSQL (/etc/bind/named.conf):
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
#auskommentiert !!!
#include "/etc/bind/named.conf.options";
#include "/etc/bind/named.conf.local";
#include "/etc/bind/named.conf.default-zones";


key "rndc-key" {
            // how was key encoded
            algorithm hmac-md5;
            // what is the pass-phrase for the key
	        secret "4ptlffIBhVnZgfdT0CXIcLDZeONxA5bHUVT5W2NofC9O4FOfjps8FzghoQy4myXnJ0g9jrna9Sjl6uKt6c/22A==";
             };


#options {
#default-key "rndc-key";
#default-server 127.0.0.1;
#default-port 953;
#};

controls {
inet * port 953 allow { any; } keys { "rndc-key"; };
#inet * port 53 allow { any; } keys { "rndc-key"; };
};



logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity dynamic;
    };

    category queries { query.log; };
};



dlz "Postgres Zone" {
       database "postgres 2
       {host=127.0.0.1 port=5432 dbname=bind9_dlz user=postgres password=your_password}
       {SELECT zone FROM dns_record WHERE zone = '$zone$'}
       {SELECT ttl, type, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data FROM dns_record WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> 'NS'}
       {SELECT ttl, type, data, primary_ns, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}
	{SELECT ttl, type, host, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '$zone$' AND type <> 'SOA' AND type <> 'NS'}
       {SELECT zone FROM dns_xfr where zone='$zone$' AND client = '$client$'}";
};


```


Now start named
```

/etc/init.d/bind9 start

```

Now test whether it works:
```

dig @127.0.0.1  example.com
dig @127.0.0.1  www.example.com

```

If it gives you the IP, then it works, else there is something wrong.


Now you have to watch out.
You might have already realized that the entire process isn't that simple.

So let's come to the pitfalls, which foremost include:
- wrong IP (timeout)
- wrong database name (case-sensitive)
- wrong database password (case-sensitive, nonsensical error message)
- wrong order of columns in the named.conf file's SQL statements (since the column names are freely choosable, access depends on column indexes, and if they are wrong, but not of the wrong datatype, it won't throw an error, but resolving won't work)
- wrong escape sequence for named.conf (the old % instead of the new $)

But on top of all those obvious things, there is another thing that isn't that obvious.

Now it (should) work/s fine, but you'll realize that your named daemon will be gone when you restart your server.

This is because bind9 now depends on mysql/postgresql/firebird.
And rebooting your system will start bind before mysql/pgsql which causes bind to exit. 

Changing the boot order of init scripts is a bit involved, so stay tuned.



Install insserv (service dependency resolver)
```

apt-get install insserv

```

Now edit these mysql init scripts:
```

/etc/init.d/mysql-ndb
/etc/init.d/mysql-ndb-mgm 
/etc/init.d/mysql

```

and remove the $named from the two lines beginning with # Should-Start: and # Should-Stop.

Now edit
```

/etc/init.d/bind9

```
and append mysql to the Should-Start and Should-Stop lines. The 3rd file does not exsist on Lucid. Ignore it.

Dito for postgre/firebird.


Now run insserv to set up the necessary symlinks in /etc/rcX.d.
```

insserv mysql
insserv bind9

```
and there you go.

---

### Post by RaythXC on 2012-07-10
I followed this tutorial exactly using the latest version of BIND9 (9.9.1-P1) and got as far as starting bind and it just failed to start saying it couldn't connect to the database. I tried everything myself and another person could think of and nothing would work.

I also tried using 9.7.3 like you were using but still couldn't get it to work and the /etc/bind folder only had the file bind.keys in it.

My ubuntu version is 10.10 as it is the latest one my vps host provides.

Any tips?

---

### Post by WitchCraft on 2012-08-04
> **RaythXC said:**
> I followed this tutorial exactly using the latest version of BIND9 (9.9.1-P1) and got as far as starting bind and it just failed to start saying it couldn't connect to the database. I tried everything myself and another person could think of and nothing would work.

I also tried using 9.7.3 like you were using but still couldn't get it to work and the /etc/bind folder only had the file bind.keys in it.

My ubuntu version is 10.10 as it is the latest one my vps host provides.

Any tips?



Yes, but I don't know if they apply to 11.10 as well.

If I do apt-get build-dep bind9 on 12.04, it installs 
> 
  libdb-dev libdb5.1-dev
If you then do
```

apt-get install  libdb4.8-dev

```then it will remove libdb-dev and libdb5.1-dev in order to be able to install libdb4.8-dev...

And of course this is wrong - newer version of bind needs newer version of libdb.
if you did that, do apt-get install build-dep bind9 again, then it will remove 4.8 and install 5.1 again.

Probably I should have written
```

apt-get install libdb-dev

```for this is a meta-package that always points to the latest version.


The same applies to MySqlClient:
```

apt-get install libmysqlclient-dev

```
Also, as per the first tip, start it in debugging mode:
```

named -g -d 9

```
As for other things, check if you can connect to the db at all from the same computer using an admin tool.
Check the database name and IP and the password again. 
Remember: Case-sensitive !

---

### Post by WitchCraft on 2012-08-04
Also note:
On 12.04, do NOT use the bind sources of the ubuntu repository, which comes from:
[git://git.debian.org/~lamont/]("git://git.debian.org/%7Elamont/")

Instead, use the official latest stable version from
[https://www.isc.org/software/bind/](https://www.isc.org/software/bind/)


And with that, on 12.04, you still can't re-eanble --with-dlz-bdb:
```

./configure --prefix=/usr --sysconfdir=/etc/bind --localstatedir=/var \
--mandir=/usr/share/man --infodir=/usr/share/info \
--enable-threads --enable-largefile --with-libtool --enable-shared --enable-static \
--with-openssl=/usr --with-gssapi=/usr --with-gnu-ld \
--with-dlz-postgres=yes --with-dlz-mysql=yes --with-dlz-bdb=no \
--with-dlz-filesystem=yes --with-dlz-ldap=yes \
--with-dlz-stub=yes --with-geoip=/usr --enable-ipv6

```
Another source of trouble is apparmor (on 12.04):
You might want to switch it off permanently.

Here are some options:
[http://ubuntu-for-humans.blogspot.ch/2009/11/start-stop-and-remove-apparmor-in.html](http://ubuntu-for-humans.blogspot.ch/2009/11/start-stop-and-remove-apparmor-in.html)

It might be better to not remove apparmor, but only remove it from starting automatically:
```

sudo /etc/init.d/apparmor stop
sudo update-rc.d -f apparmor remove

```
as recommended here: [http://linuxpoison.blogspot.ch/2010/10/how-to-disable-apparmor-in-ubuntu-linux.html](http://linuxpoison.blogspot.ch/2010/10/how-to-disable-apparmor-in-ubuntu-linux.html)

Note that

```

sudo "/etc/init.d/apparmor" stop

```
is not enough. You need
```

sudo "/etc/init.d/apparmor" teardown

```
Here's my /etc/init.d/bind9 file:
```

#!/bin/sh -e

### BEGIN INIT INFO
# Provides:          bind9
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Should-Start:      $network $syslog postgresql
# Should-Stop:       $network $syslog postgresql
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start and stop bind9
# Description:       bind9 is a Domain Name Server (DNS)
#        which translates ip addresses to and from internet names
### END INIT INFO

PATH=/sbin:/bin:/usr/sbin:/usr/bin

# for a chrooted server: "-u bind -t /var/lib/named"
# Don't modify this line, change or create /etc/default/bind9.
OPTIONS=""
RESOLVCONF=no

sudo "/etc/init.d/apparmor" teardown
#sudo "/etc/init.d/apparmor" stop


test -f /etc/default/bind9 && . /etc/default/bind9

test -x /usr/sbin/rndc || exit 0

. /lib/lsb/init-functions
PIDFILE=/var/run/named/named.pid

check_network() {
    if [ -x /usr/bin/uname ] && [ "X$(/usr/bin/uname -o)" = XSolaris ]; then
    IFCONFIG_OPTS="-au"
    else
    IFCONFIG_OPTS=""
    fi
    if [ -z "$(/sbin/ifconfig $IFCONFIG_OPTS)" ]; then
       #log_action_msg "No networks configured."
       return 1
    fi
    return 0
}

case "$1" in
    start)
    log_daemon_msg "Starting domain name service..." "bind9"

    modprobe capability >/dev/null 2>&1 || true

    # dirs under /var/run can go away on reboots.
    mkdir -p /var/run/named
    chmod 775 /var/run/named
    chown root:bind /var/run/named >/dev/null 2>&1 || true

    if [ ! -x /usr/sbin/named ]; then
        log_action_msg "named binary missing - not starting"
        log_end_msg 1
    fi

    if ! check_network; then
        log_action_msg "no networks configured"
        log_end_msg 1
    fi

    if start-stop-daemon --start --oknodo --quiet --exec /usr/sbin/named \
        --pidfile ${PIDFILE} -- $OPTIONS; then
        if [ "X$RESOLVCONF" != "Xno" ] && [ -x /sbin/resolvconf ] ; then
        echo "nameserver 127.0.0.1" | /sbin/resolvconf -a lo.named
        fi
        log_end_msg 0
    else
        log_end_msg 1
    fi
    ;;

    stop)
    log_daemon_msg "Stopping domain name service..." "bind9"
    if ! check_network; then
        log_action_msg "no networks configured"
        log_end_msg 1
    fi

    if [ "X$RESOLVCONF" != "Xno" ] && [ -x /sbin/resolvconf ] ; then
        /sbin/resolvconf -d lo.named
    fi
    pid=$(/usr/sbin/rndc stop -p | awk '/^pid:/ {print $2}') || true
    if [ -z "$pid" ]; then        # no pid found, so either not running, or error
        pid=$(pgrep -f ^/usr/sbin/named) || true
        start-stop-daemon --stop --oknodo --quiet --exec /usr/sbin/named \
            --pidfile ${PIDFILE} -- $OPTIONS
    fi
    if [ -n $pid ]; then
      while kill -0 $pid 2>/dev/null; do
        log_progress_msg "waiting for pid $pid to die"
        sleep 1
      done
    fi
    log_end_msg 0
    ;;

    reload|force-reload)
    log_daemon_msg "Reloading domain name service..." "bind9"
    if ! check_network; then
        log_action_msg "no networks configured"
        log_end_msg 1
    fi

    /usr/sbin/rndc reload >/dev/null && log_end_msg 0 || log_end_msg 1
    ;;

    restart)
    if ! check_network; then
        log_action_msg "no networks configured"
        exit 1
    fi

    $0 stop
    $0 start
    ;;
    
    status)
        ret=0
    status_of_proc -p ${PIDFILE} /usr/sbin/named bind9 2>/dev/null || ret=$?
    exit $ret
    ;;

    *)
    log_action_msg "Usage: /etc/init.d/bind9 {start|stop|reload|restart|force-reload|status}"
    exit 1
    ;;
esac

sudo "/etc/init.d/apparmor" start
exit 0

```


Also note that by default, user bind has no write rights to /var/log/WHATEVER_BINDLOG_IS_CALLED

You need to give the bind user file access permission.
Follow this link for that:
[http://askubuntu.com/questions/172017/how-can-i-add-file-create-read-write-and-delete-for-a-specific-user/174221#174221](http://askubuntu.com/questions/172017/how-can-i-add-file-create-read-write-and-delete-for-a-specific-user/174221#174221)

---

### Post by RaythXC on 2012-12-07
I got this working on my current server, but I am moving to a new server running 12.04. I now run into this error:

> 
root@vps:/home/rayth/bind-9.9.2-P1# /etc/init.d/bind9 start
 * Starting domain name service... bind9                                                                                                  * named binary missing - not starting




I've looked around and can't find a solution to this.

---

### Post by WitchCraft on 2013-02-09
> **RaythXC said:**
> 
I got this working on my current server, but I am moving to a new server running 12.04. I now run into this error:

I've looked around and can't find a solution to this.


looks like there is no bind9 executable.
Did you try 
```

chmod +x /usr/sbin/named

```
?

What's the output of which named ?
It should be 
```

/usr/sbin/named

```

---

### Post by stevenjgarner on 2013-02-15
> **RaythXC said:**
> I got this working on my current server, but I am moving to a new server running 12.04. I now run into this error:




I've looked around and can't find a solution to this.

Most likely it is because you need to execute a:

```

make install

```

after the "make" following the compilation above.  Alternatively, you could just perform a:

```

make && make install

```

instead of just the "make"

---

### Post by WitchCraft on 2013-05-08
OK, I was now able to resolve the apparmor problem:

bind9 was not allowed to write into /var/log by apparmor.
To change that, go to /etc/apparmor.d/
And after
```

  /var/log/named/** rw,
  /var/log/named/ rw,

```

Add this
```

  /var/log/** rw,
  /var/log/ rw,

```


Then save the file and reload all apparmor profiles
```

sudo invoke-rc.d apparmor reload

```

Now remove all apparmor entries you added to /etc/init.d/bind9 and then restart the named service
```

/etc/init.d/bind9 restart

```

---

### Post by DantePasquale on 2013-12-11
Hi, Great tutorial and everything is working fine after fallowing your instructions for Ubuntu 12.04 64. 

However, I can't get reverse DNS lookups to succeed and that's causing Kerberos issues. Here's what I have in the mysql DB:
```

mysql> select * from bind9_dlz.dns_records order by 1;
+----+-----------------------------+---------------+-------+---------------+------+-------------+---------+-------+--------+---------+------------+-----------------------+---------------+
| id | zone                        | host          | type  | data          | ttl  | mx_priority | refresh | retry | expire | minimum | serial     | resp_person           | primary_ns    |
+----+-----------------------------+---------------+-------+---------------+------+-------------+---------+-------+--------+---------+------------+-----------------------+---------------+
|  1 | sfpi-test.local             | @             | SOA   | NULL          |  180 |        NULL |   10800 |  7200 | 604800 |   86400 | 2013121002 | DanteBell@cocoanet.us | 192.168.4.110 |
|  2 | sfpi-test.local             | @             | NS    | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
|  3 | sfpi-test.local             | @             | A     | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
|  4 | sfpi-test.local             | www           | CNAME | @             | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
|  5 | sfpi-test.local             | openchangedev | A     | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
|  6 | xn--unicode-sfpi-test.local | @             | SOA   | NULL          | 1080 |        NULL |   10800 |  7200 | 604800 |   86400 | 2013121002 | DanteBell@cocoanet.us | 192.168.4.110 |
|  7 | xn--unicode-sfpi-test.local | @             | NS    | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
|  8 | xn--unicode-sfpi-test.local | @             | A     | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
|  9 | xn--unicode-sfpi-test.local | www           | CNAME | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
| 10 | xn--unicode-sfpi-test.local | openchangedev | A     | 192.168.4.110 | 1080 |        NULL |    NULL |  NULL |   NULL |    NULL |       NULL | NULL                  | NULL          |
+----+-----------------------------+---------------+-------+---------------+------+-------------+---------+-------+--------+---------+------------+-----------------------+---------------+
```

Forward resolution works great:
```
nslookup openchangedev.sfpi-test.local
Server:		192.168.4.110
Address:	192.168.4.110#53

Name:	openchangedev.sfpi-test.local
Address: 192.168.4.110
```


But If I try:

```
nslookup 192.168.4.110
Server:		192.168.4.110
Address:	192.168.4.110#53

** server can't find 110.4.168.192.in-addr.arpa.: NXDOMAIN

```

Any suggestions? Thanks!

---

