---
title: "HOW TO : Wifi Access Point with hostap + hostapd + freeradius + mysql backend Part 1"
date: 2006-03-28
forum: Tutorials
---

### Post by phoboulinos on 2006-03-28
Part 1


This howto will allow you to setup a software access point on a Prism based card with hostap on your ubuntu but thats not all, this AP will support 128bit WEP rekeying every N seconds which makes it virtually imposible to crack, username/password authentication over a TLS/SSL tunnel using IEEE 802.1X from a radius server using a mysql database to store username/password information since using MSCHAP to authenticate requires that passwords are provided clear-text but they are transmited encrypted over the air. This way you can use web based radius administration to manage your accounts and have accounting at the same time. This setup supports both linux and windows clients. I believe that this is the best solution when you have to do with Prism based card that dont support WPA and I also believe that its the only way to run an access point. If someone feels diffently on this please post it here so I can shutdown my AP.

I will divide this how in to parts 1 for setting up the access point and one to setup the clients


Please note that this howto requires a certain amount of linux mysql and other administrative knowledge so I will not go in depth on a few steps

Ok lets start.

Lets setup our mysql server first

```

sudo apt-get install mysql-server mysql-server mysql-client
mysqladmin -u root password
<Enter your administrative password>

```

I will describe the whole database here since its required to use accounting. This sql setup will allow you to use the dialupadmin web interface that is provided in the freeradius tarball.

```

-- MySQL dump 10.9
--
-- Host: localhost    Database: radius
-- ------------------------------------------------------
-- Server version	4.1.15-Debian_1ubuntu5-log

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `badusers`
--

DROP TABLE IF EXISTS `badusers`;
CREATE TABLE `badusers` (
  `id` int(10) NOT NULL auto_increment,
  `UserName` varchar(30) default NULL,
  `Date` datetime NOT NULL default '0000-00-00 00:00:00',
  `Reason` varchar(200) default NULL,
  `Admin` varchar(30) default '-',
  PRIMARY KEY  (`id`),
  KEY `UserName` (`UserName`),
  KEY `Date` (`Date`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `badusers`
--


/*!40000 ALTER TABLE `badusers` DISABLE KEYS */;
LOCK TABLES `badusers` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `badusers` ENABLE KEYS */;

--
-- Table structure for table `mtotacct`
--

DROP TABLE IF EXISTS `mtotacct`;
CREATE TABLE `mtotacct` (
  `MTotAcctId` bigint(21) NOT NULL auto_increment,
  `UserName` varchar(64) NOT NULL default '',
  `AcctDate` date NOT NULL default '0000-00-00',
  `ConnNum` bigint(12) default NULL,
  `ConnTotDuration` bigint(12) default NULL,
  `ConnMaxDuration` bigint(12) default NULL,
  `ConnMinDuration` bigint(12) default NULL,
  `InputOctets` bigint(12) default NULL,
  `OutputOctets` bigint(12) default NULL,
  `NASIPAddress` varchar(15) default NULL,
  PRIMARY KEY  (`MTotAcctId`),
  KEY `UserName` (`UserName`),
  KEY `AcctDate` (`AcctDate`),
  KEY `UserOnDate` (`UserName`,`AcctDate`),
  KEY `NASIPAddress` (`NASIPAddress`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `mtotacct`
--


/*!40000 ALTER TABLE `mtotacct` DISABLE KEYS */;
LOCK TABLES `mtotacct` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `mtotacct` ENABLE KEYS */;

--
-- Table structure for table `nas`
--

DROP TABLE IF EXISTS `nas`;
CREATE TABLE `nas` (
  `id` int(10) NOT NULL auto_increment,
  `nasname` varchar(128) NOT NULL default '',
  `shortname` varchar(32) default NULL,
  `type` varchar(30) default 'other',
  `ports` int(5) default NULL,
  `secret` varchar(60) NOT NULL default 'secret',
  `community` varchar(50) default NULL,
  `description` varchar(200) default 'RADIUS Client',
  PRIMARY KEY  (`id`),
  KEY `nasname` (`nasname`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `nas`
--


/*!40000 ALTER TABLE `nas` DISABLE KEYS */;
LOCK TABLES `nas` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `nas` ENABLE KEYS */;

--
-- Table structure for table `radacct`
--

DROP TABLE IF EXISTS `radacct`;
CREATE TABLE `radacct` (
  `RadAcctId` bigint(21) NOT NULL auto_increment,
  `AcctSessionId` varchar(32) NOT NULL default '',
  `AcctUniqueId` varchar(32) NOT NULL default '',
  `UserName` varchar(64) NOT NULL default '',
  `Realm` varchar(64) default '',
  `NASIPAddress` varchar(15) NOT NULL default '',
  `NASPortId` int(12) default NULL,
  `NASPortType` varchar(32) default NULL,
  `AcctStartTime` datetime NOT NULL default '0000-00-00 00:00:00',
  `AcctStopTime` datetime NOT NULL default '0000-00-00 00:00:00',
  `AcctSessionTime` int(12) default NULL,
  `AcctAuthentic` varchar(32) default NULL,
  `ConnectInfo_start` varchar(32) default NULL,
  `ConnectInfo_stop` varchar(32) default NULL,
  `AcctInputOctets` bigint(12) default NULL,
  `AcctOutputOctets` bigint(12) default NULL,
  `CalledStationId` varchar(50) NOT NULL default '',
  `CallingStationId` varchar(50) NOT NULL default '',
  `AcctTerminateCause` varchar(32) NOT NULL default '',
  `ServiceType` varchar(32) default NULL,
  `FramedProtocol` varchar(32) default NULL,
  `FramedIPAddress` varchar(15) NOT NULL default '',
  `AcctStartDelay` int(12) default NULL,
  `AcctStopDelay` int(12) default NULL,
  PRIMARY KEY  (`RadAcctId`),
  KEY `UserName` (`UserName`),
  KEY `FramedIPAddress` (`FramedIPAddress`),
  KEY `AcctSessionId` (`AcctSessionId`),
  KEY `AcctUniqueId` (`AcctUniqueId`),
  KEY `AcctStartTime` (`AcctStartTime`),
  KEY `AcctStopTime` (`AcctStopTime`),
  KEY `NASIPAddress` (`NASIPAddress`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `radacct`
--


/*!40000 ALTER TABLE `radacct` DISABLE KEYS */;
LOCK TABLES `radacct` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `radacct` ENABLE KEYS */;

--
-- Table structure for table `radcheck`
--

DROP TABLE IF EXISTS `radcheck`;
CREATE TABLE `radcheck` (
  `id` int(11) unsigned NOT NULL auto_increment,
  `UserName` varchar(64) NOT NULL default '',
  `Attribute` varchar(32) NOT NULL default '',
  `op` char(2) NOT NULL default '==',
  `Value` varchar(253) NOT NULL default '',
  PRIMARY KEY  (`id`),
  KEY `UserName` (`UserName`(32))
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `radcheck`
--


/*!40000 ALTER TABLE `radcheck` DISABLE KEYS */;
LOCK TABLES `radcheck` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `radcheck` ENABLE KEYS */;

--
-- Table structure for table `radgroupcheck`
--

DROP TABLE IF EXISTS `radgroupcheck`;
CREATE TABLE `radgroupcheck` (
  `id` int(11) unsigned NOT NULL auto_increment,
  `GroupName` varchar(64) NOT NULL default '',
  `Attribute` varchar(32) NOT NULL default '',
  `op` char(2) NOT NULL default '==',
  `Value` varchar(253) NOT NULL default '',
  PRIMARY KEY  (`id`),
  KEY `GroupName` (`GroupName`(32))
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `radgroupcheck`
--


/*!40000 ALTER TABLE `radgroupcheck` DISABLE KEYS */;
LOCK TABLES `radgroupcheck` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `radgroupcheck` ENABLE KEYS */;

--
-- Table structure for table `radgroupreply`
--

DROP TABLE IF EXISTS `radgroupreply`;
CREATE TABLE `radgroupreply` (
  `id` int(11) unsigned NOT NULL auto_increment,
  `GroupName` varchar(64) NOT NULL default '',
  `Attribute` varchar(32) NOT NULL default '',
  `op` char(2) NOT NULL default '=',
  `Value` varchar(253) NOT NULL default '',
  `prio` int(10) unsigned NOT NULL default '0',
  PRIMARY KEY  (`id`),
  KEY `GroupName` (`GroupName`(32))
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `radgroupreply`
--


/*!40000 ALTER TABLE `radgroupreply` DISABLE KEYS */;
LOCK TABLES `radgroupreply` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `radgroupreply` ENABLE KEYS */;

--
-- Table structure for table `radpostauth`
--

DROP TABLE IF EXISTS `radpostauth`;
CREATE TABLE `radpostauth` (
  `id` int(11) NOT NULL auto_increment,
  `user` varchar(64) NOT NULL default '',
  `pass` varchar(64) NOT NULL default '',
  `reply` varchar(32) NOT NULL default '',
  `date` timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `radpostauth`
--


/*!40000 ALTER TABLE `radpostauth` DISABLE KEYS */;
LOCK TABLES `radpostauth` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `radpostauth` ENABLE KEYS */;

--
-- Table structure for table `radreply`
--

DROP TABLE IF EXISTS `radreply`;
CREATE TABLE `radreply` (
  `id` int(11) unsigned NOT NULL auto_increment,
  `UserName` varchar(64) NOT NULL default '',
  `Attribute` varchar(32) NOT NULL default '',
  `op` char(2) NOT NULL default '=',
  `Value` varchar(253) NOT NULL default '',
  PRIMARY KEY  (`id`),
  KEY `UserName` (`UserName`(32))
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `radreply`
--


/*!40000 ALTER TABLE `radreply` DISABLE KEYS */;
LOCK TABLES `radreply` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `radreply` ENABLE KEYS */;

--
-- Table structure for table `totacct`
--

DROP TABLE IF EXISTS `totacct`;
CREATE TABLE `totacct` (
  `TotAcctId` bigint(21) NOT NULL auto_increment,
  `UserName` varchar(64) NOT NULL default '',
  `AcctDate` date NOT NULL default '0000-00-00',
  `ConnNum` bigint(12) default NULL,
  `ConnTotDuration` bigint(12) default NULL,
  `ConnMaxDuration` bigint(12) default NULL,
  `ConnMinDuration` bigint(12) default NULL,
  `InputOctets` bigint(12) default NULL,
  `OutputOctets` bigint(12) default NULL,
  `NASIPAddress` varchar(15) default NULL,
  PRIMARY KEY  (`TotAcctId`),
  KEY `UserName` (`UserName`),
  KEY `AcctDate` (`AcctDate`),
  KEY `UserOnDate` (`UserName`,`AcctDate`),
  KEY `NASIPAddress` (`NASIPAddress`),
  KEY `NASIPAddressOnDate` (`AcctDate`,`NASIPAddress`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `totacct`
--


/*!40000 ALTER TABLE `totacct` DISABLE KEYS */;
LOCK TABLES `totacct` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `totacct` ENABLE KEYS */;

--
-- Table structure for table `usergroup`
--

DROP TABLE IF EXISTS `usergroup`;
CREATE TABLE `usergroup` (
  `id` int(11) unsigned NOT NULL auto_increment,
  `UserName` varchar(64) NOT NULL default '',
  `GroupName` varchar(64) NOT NULL default '',
  PRIMARY KEY  (`id`),
  KEY `UserName` (`UserName`(32))
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `usergroup`
--


/*!40000 ALTER TABLE `usergroup` DISABLE KEYS */;
LOCK TABLES `usergroup` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `usergroup` ENABLE KEYS */;

--
-- Table structure for table `userinfo`
--

DROP TABLE IF EXISTS `userinfo`;
CREATE TABLE `userinfo` (
  `id` int(10) NOT NULL auto_increment,
  `UserName` varchar(30) default NULL,
  `Name` varchar(200) default NULL,
  `Mail` varchar(200) default NULL,
  `Department` varchar(200) default NULL,
  `WorkPhone` varchar(200) default NULL,
  `HomePhone` varchar(200) default NULL,
  `Mobile` varchar(200) default NULL,
  PRIMARY KEY  (`id`),
  KEY `UserName` (`UserName`),
  KEY `Departmet` (`Department`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

--
-- Dumping data for table `userinfo`
--


/*!40000 ALTER TABLE `userinfo` DISABLE KEYS */;
LOCK TABLES `userinfo` WRITE;
UNLOCK TABLES;
/*!40000 ALTER TABLE `userinfo` ENABLE KEYS */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;


```


Lets insert a username and password in the database

```

INSERT INTO `radcheck` VALUES (1,'phoboulinos','User-Password','==','supersecret');

```

Lets create a user group to state that it will use EAP authentication

```

INSERT INTO `radgroupcheck` VALUES (1,'WifiAP-EAP','Auth-Type','==','EAP');

```

Insert user "phoboulinos" in that group

```

INSERT INTO `usergroup` VALUES (6,'phoboulinos','WifiAP-EAP');

```

Insert user information (Looks good in the radius log and web interface)

```

INSERT INTO `userinfo` VALUES (1,'phoboulinos','Stratos Goudelis','phobos@artica.gr','','-','-','-');

```

Ok, now that our mysql database is setup we must compile freeradius from source (sorry guys), apperantly, the breezy deb does not have a TLS EAP module required in this setup.

Get it here [ftp://ftp.freeradius.org/pub/radius/old/freeradius-1.1.0.tar.gz](ftp://ftp.freeradius.org/pub/radius/old/freeradius-1.1.0.tar.gz)
There is a good howto on compiling freeradius and using it with mysql here : [http://www.frontios.com/freeradius.html](http://www.frontios.com/freeradius.html) but not everything stated there is what we are trying to do here so some things may not work. Although the configuration about how to make freeradius use mysql is correct and just that.

I will not go through the process of compiling freeradius (it been a while since I did it and I dont want to mess up my setup), I will tell though that you must compile it with all availiable options especially anything that has to to with TLS PEAP EAP SSL SQL MSCHAP

We will configure freeradius later in this howto.

Next we must setup hostap + hostapd

If you have a Prism-based card ubuntu should already have inserted the module hostap and hostap_pci (if it a PCI). If you have a PCMCIA card or anything else with a Prism chip you must setup it up, I will not go in to that. Fortunatly the Ubuntu team has everyting compiled for hostap related functions and they did a very good job to.

When you have made sure that the hostap modules are correclty inserted you should ... well look what I have done with my setup:

File : /etc/network/interface
```

auto br0
iface br0 inet static
       address 10.10.10.100
       netmask 255.255.255.128
       gateway 10.10.10.100 
       bridge_ports wlan0 eth0
       up \
       /sbin/iwconfig wlan0 essid MY_SSID && \
       /sbin/iwconfig wlan0 channel 8 && \
       /sbin/iwconfig wlan0 mode Master

```

For the sake of privacy I used fake ips here but I normally use real ips and bridge my ethernet card with my wlan card so that the clients that use the access point will be able to use real ips to. I also use iwconfig to set my access point name, MY_SSID in this case, set the channel to 8 (use kismet to see which chanell is rarely used in your area) and set the card in Master mode.

Please note that until hostapd launches the access point will be unecrypted and it should transmit every packet the bridge captures.

Lets setup hostapd authenticator

```

sudo apt-get install hostapd hostap-utils

```


Here is my /etc/hostapd/hostapd.conf

```

# Lose the comment after its line

ssid=MY_SSID
interface=wlan0 # The interface name of the card
driver=hostap   # The card driver
macaddr_acl=0
accept_mac_file=/etc/hostapd.accept
deny_mac_file=/etc/hostapd.deny
ieee8021x=1    # Use 802.1X authentication
wep_key_len_broadcast=13
wep_key_len_unicast=13
wep_rekey_period=300   # WEP rekeying interval
own_ip_addr=10.10.10.100  # The interface IP
nas_identifier=some_name
auth_server_addr=127.0.0.1 # Where is the radius server
auth_server_port=1812      # The port the radius server runs on
auth_server_shared_secret=supersecretradiuskey  # This is used to authenticate the hostapd to the radius server so none can use your raduis server
acct_server_addr=127.0.0.1 # Where is the radius server
acct_server_port=1813      # Where the accounting port is (I think)
acct_server_shared_secret=supersecretradiuskey # Same as above

```

Here comes the hard part, configuring freeradius

Go there the freeradius confs are, the default dir /usr/local/etc/raddb
Leave everything as it is except what I say here, I will try to remember everything

You must edit the following files and not replace them I will only show what I have edited.
Also you might need to keep the original files because the comment they have are very informative.

File : clients.conf

```

client 127.0.0.1 {
        secret          = supersecretradiuskey
        shortname       = some_name
}

```

This will accept connections only from localhost, (we dont want to show up in nmap now do we ? )


File : eap.conf

```

        eap {
                default_eap_type = peap
                timer_expire     = 60
                ignore_unknown_eap_types = no
                cisco_accounting_username_bug = no
                md5 {
                }
                leap {
                }
                gtc {
                        auth_type = PAP
                }
                tls {
                        private_key_password = whatever
                        private_key_file = ${raddbdir}/certs/cert-srv.pem
                        certificate_file = ${raddbdir}/certs/cert-srv.pem
                        CA_file = ${raddbdir}/certs/demoCA/cacert.pem
                        dh_file = ${raddbdir}/certs/dh
                        random_file = /dev/urandom
                }
                peap {
                        default_eap_type = mschapv2
                }
                mschapv2 {
                }
        }

```

File : radiusd.conf
NOTE: What follows is NOT the whole file, you must edit it and make the respective sections of it look like this
```

modules {
	pap {
		encryption_scheme = crypt
	}
	chap {
		authtype = CHAP
	}
	pam {
		pam_auth = radiusd
	}
	unix {
		cache = no
		cache_reload = 600
		radwtmp = ${logdir}/radwtmp
	}
$INCLUDE ${confdir}/eap.conf
	mschap {
		authtype = MS-CHAP
		
		use_mppe = yes
		require_encryption = yes
		require_strong = yes
	}
	ldap {
		server = "ldap.your.domain"
		basedn = "o=My Org,c=UA"
		filter = "(uid=%{Stripped-User-Name:-%{User-Name}})"
		start_tls = no
		access_attr = "dialupAccess"
		dictionary_mapping = ${raddbdir}/ldap.attrmap
		ldap_connections_number = 5
		timeout = 4
		timelimit = 3
		net_timeout = 1
	}
	realm IPASS {
		format = prefix
		delimiter = "/"
		ignore_default = no
		ignore_null = no
	}
	realm suffix {
		format = suffix
		delimiter = "@"
		ignore_default = no
		ignore_null = no
	}
	realm realmpercent {
		format = suffix
		delimiter = "%"
		ignore_default = no
		ignore_null = no
	}
	realm ntdomain {
		format = prefix
		delimiter = "\\"
		ignore_default = no
		ignore_null = no
	}	
	checkval {
		item-name = Calling-Station-Id
		check-name = Calling-Station-Id
		data-type = string
	}
	
	preprocess {
		huntgroups = ${confdir}/huntgroups
		hints = ${confdir}/hints
		with_ascend_hack = no
		ascend_channels_per_line = 23
		with_ntdomain_hack = no
		with_specialix_jetstream_hack = no
		with_cisco_vsa_hack = no
	}
	files {
		usersfile = ${confdir}/users
		acctusersfile = ${confdir}/acct_users
		preproxy_usersfile = ${confdir}/preproxy_users
		compat = no
	}
	detail {
		detailfile = ${radacctdir}/%{Client-IP-Address}/detail-%Y%m%d
		detailperm = 0600
	}
	acct_unique {
		key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
	}
	$INCLUDE  ${confdir}/sql.conf
	
	radutmp {
		filename = ${logdir}/radutmp
		username = %{User-Name}
		case_sensitive = yes
		check_with_nas = yes		
		perm = 0600
		callerid = "yes"
	}
	radutmp sradutmp {
		filename = ${logdir}/sradutmp
		perm = 0644
		callerid = "no"
	}
	attr_filter {
		attrsfile = ${confdir}/attrs
	}
	counter daily {
		filename = ${raddbdir}/db.daily
		key = User-Name
		count-attribute = Acct-Session-Time
		reset = daily
		counter-name = Daily-Session-Time
		check-name = Max-Daily-Session
		allowed-servicetype = Framed-User
		cache-size = 5000
	}
	sqlcounter dailycounter {
		counter-name = Daily-Session-Time
		check-name = Max-Daily-Session
		sqlmod-inst = sql
		key = User-Name
		reset = daily
		query = "SELECT SUM(AcctSessionTime - \
                 GREATEST((%b - UNIX_TIMESTAMP(AcctStartTime)), 0)) \
                 FROM radacct WHERE UserName='%{%k}' AND \
                 UNIX_TIMESTAMP(AcctStartTime) + AcctSessionTime > '%b'"
	}
	sqlcounter monthlycounter {
		counter-name = Monthly-Session-Time
		check-name = Max-Monthly-Session
		sqlmod-inst = sql
		key = User-Name
		reset = monthly
		query = "SELECT SUM(AcctSessionTime - \
                 GREATEST((%b - UNIX_TIMESTAMP(AcctStartTime)), 0)) \
                 FROM radacct WHERE UserName='%{%k}' AND \
                 UNIX_TIMESTAMP(AcctStartTime) + AcctSessionTime > '%b'"
	}
	always fail {
		rcode = fail
	}
	always reject {
		rcode = reject
	}
	always ok {
		rcode = ok
		simulcount = 0
		mpp = no
	}
	expr {
	}
	digest {
	}
	exec {
		wait = yes
		input_pairs = request
	}
	exec echo {
		wait = yes
		program = "/bin/echo %{User-Name}"
		input_pairs = request
		output_pairs = reply
	}
	ippool main_pool {
		range-start = 192.168.1.1
		range-stop = 192.168.3.254
		netmask = 255.255.255.0
		cache-size = 800
		session-db = ${raddbdir}/db.ippool
		ip-index = ${raddbdir}/db.ipindex
		override = no
		maximum-timeout = 0
	}
}
instantiate {
	exec
	expr
}
authorize {
	preprocess
	
	chap
	mschap
	suffix
	eap
	files
	sql
}
authenticate {
	Auth-Type PAP {
		pap
	}
	Auth-Type CHAP {
		chap
	}
	Auth-Type MS-CHAP {
		mschap
	}
	unix
	eap
}
preacct {
	preprocess
	acct_unique
	suffix
	files
}
accounting {
	detail
	unix
	radutmp
	sql
}
session {
	radutmp
}
post-auth {
	sql
}
pre-proxy {
}
post-proxy {
	eap
}


```

File : sql.conf
NOTE: You can safely move the original file somewhere else for backup and make it look like this, just change the mysql username password

```

sql {
	driver = "rlm_sql_mysql"
	server = "localhost"
	login = "root"
	password = "<MYSQL Administrative password here>"
	radius_db = "radius"
	acct_table1 = "radacct"
	acct_table2 = "radacct"
	postauth_table = "radpostauth"
	authcheck_table = "radcheck"
	authreply_table = "radreply"
	groupcheck_table = "radgroupcheck"
	groupreply_table = "radgroupreply"
	usergroup_table = "usergroup"
	nas_table = "nas"
	deletestalesessions = yes
	sqltrace = no
	sqltracefile = ${logdir}/sqltrace.sql
	num_sql_socks = 5
	connect_failure_retry_delay = 60
	sql_user_name = "%{User-Name}"
	authorize_check_query = "SELECT id, UserName, Attribute, Value, op \
          FROM ${authcheck_table} \
          WHERE Username = '%{SQL-User-Name}' \
          ORDER BY id"
	authorize_reply_query = "SELECT id, UserName, Attribute, Value, op \
          FROM ${authreply_table} \
          WHERE Username = '%{SQL-User-Name}' \
          ORDER BY id"
	authorize_group_check_query = "SELECT ${groupcheck_table}.id,${groupcheck_table}.GroupName,${groupcheck_table}.Attribute,${groupcheck_table}.Value,${groupcheck_table}.op  FROM ${groupcheck_table},${usergroup_table} WHERE ${usergroup_table}.Username = '%{SQL-User-Name}' AND ${usergroup_table}.GroupName = ${groupcheck_table}.GroupName ORDER BY ${groupcheck_table}.id"
	authorize_group_reply_query = "SELECT ${groupreply_table}.id,${groupreply_table}.GroupName,${groupreply_table}.Attribute,${groupreply_table}.Value,${groupreply_table}.op  FROM ${groupreply_table},${usergroup_table} WHERE ${usergroup_table}.Username = '%{SQL-User-Name}' AND ${usergroup_table}.GroupName = ${groupreply_table}.GroupName ORDER BY ${groupreply_table}.id"
	accounting_onoff_query = "UPDATE ${acct_table1} SET AcctStopTime='%S', AcctSessionTime=unix_timestamp('%S') - unix_timestamp(AcctStartTime), AcctTerminateCause='%{Acct-Terminate-Cause}', AcctStopDelay = '%{Acct-Delay-Time}' WHERE AcctSessionTime=0 AND AcctStopTime=0 AND NASIPAddress= '%{NAS-IP-Address}' AND AcctStartTime <= '%S'"
	accounting_update_query = "UPDATE ${acct_table1} \
          SET FramedIPAddress = '%{Framed-IP-Address}', \
          AcctSessionTime = '%{Acct-Session-Time}', \
          AcctInputOctets = '%{Acct-Input-Octets}', \
          AcctOutputOctets = '%{Acct-Output-Octets}' \
          WHERE AcctSessionId = '%{Acct-Session-Id}' \
          AND UserName = '%{SQL-User-Name}' \
          AND NASIPAddress= '%{NAS-IP-Address}'"
	accounting_update_query_alt = "INSERT into ${acct_table1} (AcctSessionId, AcctUniqueId, UserName, Realm, NASIPAddress, NASPortId, NASPortType, AcctStartTime, AcctSessionTime, AcctAuthentic, ConnectInfo_start, AcctInputOctets, AcctOutputOctets, CalledStationId, CallingStationId, ServiceType, FramedProtocol, FramedIPAddress, AcctStartDelay) values('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}', '%{SQL-User-Name}', '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}', '%{NAS-Port-Type}', DATE_SUB('%S',INTERVAL (%{Acct-Session-Time:-0} + %{Acct-Delay-Time:-0}) SECOND), '%{Acct-Session-Time}', '%{Acct-Authentic}', '', '%{Acct-Input-Octets}', '%{Acct-Output-Octets}', '%{Called-Station-Id}', '%{Calling-Station-Id}', '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}', '0')"
	accounting_start_query = "INSERT into ${acct_table1} (AcctSessionId, AcctUniqueId, UserName, Realm, NASIPAddress, NASPortId, NASPortType, AcctStartTime, AcctStopTime, AcctSessionTime, AcctAuthentic, ConnectInfo_start, ConnectInfo_stop, AcctInputOctets, AcctOutputOctets, CalledStationId, CallingStationId, AcctTerminateCause, ServiceType, FramedProtocol, FramedIPAddress, AcctStartDelay, AcctStopDelay) values('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}', '%{SQL-User-Name}', '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}', '%{NAS-Port-Type}', '%S', '0', '0', '%{Acct-Authentic}', '%{Connect-Info}', '', '0', '0', '%{Called-Station-Id}', '%{Calling-Station-Id}', '', '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}', '%{Acct-Delay-Time}', '0')"
	accounting_start_query_alt  = "UPDATE ${acct_table1} SET AcctStartTime = '%S', AcctStartDelay = '%{Acct-Delay-Time}', ConnectInfo_start = '%{Connect-Info}' WHERE AcctSessionId = '%{Acct-Session-Id}' AND UserName = '%{SQL-User-Name}' AND NASIPAddress = '%{NAS-IP-Address}'"
	accounting_stop_query = "UPDATE ${acct_table2} SET AcctStopTime = '%S', AcctSessionTime = '%{Acct-Session-Time}', AcctInputOctets = '%{Acct-Input-Octets}', AcctOutputOctets = '%{Acct-Output-Octets}', AcctTerminateCause = '%{Acct-Terminate-Cause}', AcctStopDelay = '%{Acct-Delay-Time}', ConnectInfo_stop = '%{Connect-Info}' WHERE AcctSessionId = '%{Acct-Session-Id}' AND UserName = '%{SQL-User-Name}' AND NASIPAddress = '%{NAS-IP-Address}'"
	accounting_stop_query_alt = "INSERT into ${acct_table2} (AcctSessionId, AcctUniqueId, UserName, Realm, NASIPAddress, NASPortId, NASPortType, AcctStartTime, AcctStopTime, AcctSessionTime, AcctAuthentic, ConnectInfo_start, ConnectInfo_stop, AcctInputOctets, AcctOutputOctets, CalledStationId, CallingStationId, AcctTerminateCause, ServiceType, FramedProtocol, FramedIPAddress, AcctStartDelay, AcctStopDelay) values('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}', '%{SQL-User-Name}', '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}', '%{NAS-Port-Type}', DATE_SUB('%S', INTERVAL (%{Acct-Session-Time:-0} + %{Acct-Delay-Time:-0}) SECOND), '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '', '%{Connect-Info}', '%{Acct-Input-Octets}', '%{Acct-Output-Octets}', '%{Called-Station-Id}', '%{Calling-Station-Id}', '%{Acct-Terminate-Cause}', '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}', '0', '%{Acct-Delay-Time}')"
	simul_verify_query = "SELECT RadAcctId, AcctSessionId, UserName, NASIPAddress, NASPortId, FramedIPAddress, CallingStationId, FramedProtocol FROM ${acct_table1} WHERE UserName='%{SQL-User-Name}' AND AcctStopTime = 0"
	group_membership_query = "SELECT GroupName FROM ${usergroup_table} WHERE UserName='%{SQL-User-Name}'"
	postauth_query = "INSERT into ${postauth_table} (id, user, pass, reply, date) values ('', '%{User-Name}', '%{User-Password:-Chap-Password}', '%{reply:Packet-Type}', NOW())"
	readclients = yes
}

```


I think this is everything, now here are some tips running everything

I suggest you run the radius server in verbose mode to report everything, very good for debugging purposes, something you may need to do.

```

# radiusd -X

```

Same thing applies when running hostapd, you may need to see the messages hostapd prints to test everything

```

# hostapd /etc/hostapd/hostapd.conf

```

Note: Run everything in this order:

1. Ubuntu loads hostap modules for the card
Note: Until hostapd starts the access point does not have encryption you should know that
2. MySQL starts
3. Radius server starts
3. hostapd starts


The dialupadmin web interface uses the sql database I described here BUT it does not support many of the thing we are doing here, I use a modified version (modified by me) I will post it here if neccesary but I thing that someone should make a new one.

This is the end of Part 1

---

### Post by the slayer on 2006-08-24
And part two?

---

### Post by sangamc on 2008-03-03
not a bad post, but is there a part 2?

---

### Post by Master Chief on 2008-07-27
> **sangamc said:**
> not a bad post, but is there a part 2?

Yes there is:

[http://ubuntuforums.org/showthread.php?t=151782](http://ubuntuforums.org/showthread.php?t=151782)

---

### Post by goldyfruit on 2013-04-14
Hi,

I found this very nice howto, thanks for that !
I've one question about the clear-text password in the database, there is no solution to encrypt the password with md5 or sha1 with EAP-TTLS ?

Thanks for your help.

---

