---
title: "What do you use to monitor your box ?"
date: 2005-01-27
forum: Server Platforms
---

### Post by rich on 2005-01-27
I have in the past used MRTG to give me a quick "heads up" on how happy my box is. If you've not seen it, it just builds graphs based on a snapshot stored every 5 mins. You view them via a browser on an [https://ip/mrtg](https://ip/mrtg) page. It's great - you quickly get a feel for whether everything is going OK (or not). And - unlike top - you can click to see history stretching back months. 

I had a look in Synaptic, and MRTG is there. But it doesn't have a friendly little orange & red logo next to it. Before I stick with what I know, are all you lot using something better / more integrated / more ubuntu-ish ?


Advice would be appreciated - I'm experimenting with postgres and a fairly fat database, so tuning might be an issue. 

Rich

---

### Post by machiner on 2005-01-27
Armed guards and bear traps.

Nothing less will do.

---

### Post by thewanderer on 2005-01-28
Unsure if there are packages available but this is my network and system monitoring tool of choice. Based on rrdtool. Fully open source of course.

Everything from network traffic, network errors to disk space available on your servers. Historical data and all graphed as is mrtg.

[http://www.cacti.net](http://www.cacti.net)

---

### Post by Jad on 2005-01-28
[QUOTE=thewanderer]Unsure if there are packages available but this is my network and system monitoring tool of choice. Based on rrdtool. Fully open source of course.

Everything from network traffic, network errors to disk space available on your servers. Historical data and all graphed as is mrtg.

[http://www.cacti.net](http://www.cacti.net)[/QUOTE]
 Cacti rocks!

---

### Post by rbrugman on 2005-02-01
Can you get cacti going via apt-get?

Robert

---

### Post by Jad on 2005-02-01
[QUOTE=rbrugman]Can you get cacti going via apt-get?

Robert[/QUOTE]
 yeah! sure,

---

### Post by crane on 2005-02-01
[QUOTE=rbrugman]Can you get cacti going via apt-get?

Robert[/QUOTE]


Apt-get install prickly protection :-D

---

### Post by Jad on 2005-02-01
I wish I could apt ..  
Apt-get redalert2 
Apt-get generalz
Apt-get need4speed

---

### Post by arx-lupus on 2005-02-04
[QUOTE=thewanderer]Unsure if there are packages available but this is my network and system monitoring tool of choice. Based on rrdtool. Fully open source of course.

Everything from network traffic, network errors to disk space available on your servers. Historical data and all graphed as is mrtg.

[http://www.cacti.net](http://www.cacti.net)[/QUOTE]

Had a look at this one, but having problems. 

Fatal error: Call to undefined function: mysql_connect() in /var/www/httpdocs/cacti/lib/adodb/drivers/adodb-mysql.inc.php on line 338

looking this up on the cacti forums [http://forums.cacti.net/post-22543.html](http://forums.cacti.net/post-22543.html)
 it says that  :

> Solutions is to run

dpkg-reconfigure php4-mysql

and enable mysql for CLI applications...

But I don't have php4-mysql listed installed or available in repository. 
```

admin@crux:/etc/apache2 $ sudo dpkg-reconfigure php4-mysql
Password:
Package `php4-mysql' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: php4-mysql is not installed
```

Don't know if I am missing something?!

---

### Post by ups on 2005-02-04
Do you have "universe" enabled? php4-mysql is present in the universe repository.

---

### Post by arx-lupus on 2005-02-17
[QUOTE=ups]Do you have "universe" enabled? php4-mysql is present in the universe repository.[/QUOTE]
 Hi again, 

Thanks for that, you were right, I hadn't added it; I thought basic server stuff woud have been in base setup for apt-get.

Still having problems though with it, on first run the Install page shown in the browser is saying that [NOT FOUND] PHP Binary Path: The path to your PHP binary file (may require a php recompile to get this file). I tried a recompile but keep falling down on a gzip/bzip error - I don't have the details to hand but can update it later.

Does this ring a bell with anyone?

---

### Post by 0xBulbizarre on 2005-02-18
Maybe you forgot to enable loading of mysql.so ... check 
/etc/php4/apache2/php.ini

and uncomment the line :
extension=mysql.so

Arnaud

---

### Post by Ubuntu Warrior on 2006-02-02
We are using cacti for the monitoring of our various systems and it works like a dream.

---

### Post by LordMerlin on 2006-07-02
Ok, so I tried installing cacti from apt-get on Ubuntu 5.10 with Apache2, MySQL 4.0.12, PHP 5 already installed. MySQL already has some databases and security setup. the cacti installer thus couldn't create the MySQL DB @ installation. I then manually created a cacti username, password & DB. I coulnd't find anything in the cacti site folder to manually create the MySQL DB, so I uninstalled it, and reinstalled it. The problem now is, that it doesn't even prompt me what DB to use, and I just get this error:

```
**Notice**: Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Notice**:  Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Notice**:  Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Notice**:  Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Notice**:  Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Notice**:  Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Notice**:  Only variable references should be returned by reference in  **/usr/share/adodb/adodb.inc.php** on line **854**

**Warning**:  Cannot modify header information - headers already sent by (output started at  /usr/share/adodb/adodb.inc.php:854) in  **/usr/share/cacti/site/include/auth.php** on line **31**

```


So..... I decided to try mrtg instead, following this tutorial: [http://www.debianhelp.co.uk/mrtg.htm](http://www.debianhelp.co.uk/mrtg.htm).

Unfortunattely I run into come more problems:

```
root@Gimbli:/var/www/mrtg# cfgmaker public@localhost >> /etc/mrtg.cfg
--base: Get Device Info on public@localhost:
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.1.9.1.4.9)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133942
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 733
--base: Vendor Id:
--base: Populating confcache
--coca: populate confcache public@localhost:
--coca: Skipping ifName scanning because public@localhost: does not seem to support it
--coca: Skipping ifDescr scanning because public@localhost: does not seem to support it
--coca: Skipping ifType scanning because public@localhost: does not seem to support it
--coca: Skipping ipAdEntIfIndex scanning because public@localhost: does not seem to support it
--coca: Skipping ifPhysAddress scanning because public@localhost: does not seem to support it
--base: Get Interface Info
--base: Walking ifIndex
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.1)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133936
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.1 on public@localhost::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifType
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.3)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133935
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.3 on public@localhost::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifAdminStatus
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.7)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133934
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.7 on public@localhost::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifOperStatus
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.8)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133933
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.8 on public@localhost::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifMtu
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.4)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133932
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.4 on public@localhost::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifSpeed
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.5)
SNMPv1_Session (remote host: "localhost" [127.0.0.1].161)
                  community: "public"
                 request ID: -1367133931
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.5 on public@localhost::::::v4only
 at /usr/bin/cfgmaker line 183
root@Gimbli:/var/www/mrtg#

```

Does anyone have a working tutorial for either of these, for Ubuntu 5.10?

---

### Post by faultyCPU on 2006-07-03
NAGIOS works very fine and its easy to setup on ubuntu . :)

---

### Post by RShadow on 2006-07-12
> **faultyCPU said:**
> NAGIOS works very fine and its easy to setup on ubuntu . :)
Perhaps you could post a simple HOWTO then? I've been trying to setup nagios for about three days now.  The documentation is horrible! It contains to many "well you have to do this too.. so click here to figure that out" entirely too complicated for my needs, If I could get all the documention in one single file it would proably be easier... All I want is for something to tell me "Hey bonehead.. apache isn't responsding.. go do something about it" or "your box is gettin kind of low on memory.. go fix it"

---

