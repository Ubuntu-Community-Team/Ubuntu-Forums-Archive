---
title: "Bind9 zone transfer issue"
date: 2009-02-18
forum: Server Platforms
---

### Post by dhagens on 2009-02-18
Dear Community,

I'm currently setting up ubuntu server with bind9 as a secondary to our win2k3 domainserver. basic setup seems to be working just fine however the zone transfer seems to cause me some trouble. I am not running bind chrooted. FYI its my first time setting up bind, so it could also be an obvious mistake on my side.

**The logging:**
Feb 18 15:33:50 TXS-MSP-NS01 named[9847]: zone techaccess.local/IN: Transfer started.
Feb 18 15:33:50 TXS-MSP-NS01 named[9847]: transfer of 'techaccess.local/IN' from 10.20.1.11#53: connected using 10.10.1.120#48682
Feb 18 15:33:50 TXS-MSP-NS01 kernel: [12350.687642] type=1503 audit(1234967630.671:1520): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=105 name="/etc/bind/slaves/tmp-8wxKgf7uA8" pid=9848 profile="/usr/sbin/named"
**Feb 18 15:33:50 TXS-MSP-NS01 named[9847]: dumping master file: /etc/bind/slaves/tmp-8wxKgf7uA8: open: permission denied**
Feb 18 15:33:50 TXS-MSP-NS01 named[9847]: transfer of 'techaccess.local/IN' from 10.20.1.11#53: failed while receiving responses: permission denied
Feb 18 15:33:50 TXS-MSP-NS01 named[9847]: transfer of 'techaccess.local/IN' from 10.20.1.11#53: Transfer completed: 56 messages, 57 records, 4118 bytes, 0.240 secs (17158 bytes/sec)

**Version is a brand new 8.10 server 32 bit:**
root@TXS-MSP-NS01:/etc/bind# uname -a
Linux TXS-MSP-NS01 2.6.27-7-server #1 SMP Fri Oct 24 07:37:55 UTC 2008 i686 GNU/Linux


**Bind is running under user bind:**
root@TXS-MSP-NS01:/etc/bind# ps aux | grep named
bind      9847  0.0  1.6  41396  8412 ?        Ssl  15:33   0:00 /usr/sbin**/named -u bind**
root      9854  0.0  0.1   3236   796 pts/0    R+   15:34   0:00 grep named

**The (sub)directories are owned by the user bind:**
root@TXS-MSP-NS01:/etc# ls -al | grep bind
drwxr-sr-x  3 bind bind     4096 2009-02-18 15:33 bind
-rw-r--r--  1 root root      332 2008-09-29 11:20 bindresvport.blacklist

root@TXS-MSP-NS01:/etc/bind# ls -al
total 56
drwxr-sr-x  3 bind bind 4096 2009-02-18 15:33 .
drwxr-xr-x 73 root root 4096 2009-02-18 13:32 ..
-rw-r--r--  1 root root  237 2009-01-08 02:31 db.0
-rw-r--r--  1 root root  271 2009-01-08 02:31 db.127
-rw-r--r--  1 root root  237 2009-01-08 02:31 db.255
-rw-r--r--  1 root root  353 2009-01-08 02:31 db.empty
-rw-r--r--  1 root root  270 2009-01-08 02:31 db.local
-rw-r--r--  1 root root 2878 2009-01-08 02:31 db.root
-rw-r--r--  1 root bind  907 2009-02-18 14:28 named.conf
-rw-r--r--  1 root bind  280 2009-02-18 15:33 named.conf.local
-rw-r--r--  1 root bind  572 2009-02-18 14:20 named.conf.options
-rw-r-----  1 bind bind   77 2009-02-18 11:51 rndc.key
drwxrwsrwx  2 bind bind 4096 2009-02-18 14:38 slaves
-rw-r--r--  1 root root 1317 2009-01-08 02:31 zones.rfc1918

root@TXS-MSP-NS01:/etc/bind/slaves# ls -al
total 8
drwxrwsrwx 2 bind bind 4096 2009-02-18 14:38 .
drwxr-sr-x 3 bind bind 4096 2009-02-18 15:33 ..
-rw-r--r-- 1 bind bind    0 2009-02-18 14:24 db.techaccess.local

**Bind config is pretty straight foreward i think:**

**named.conf:**
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";

**named.conf.local:**
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "techaccess.local" {
	type slave;
	file "/etc/bind/slaves/db.techaccess.local";
	masters { 10.20.1.11; } ;
};



TIA for any assistance!

Dennis

---

### Post by Fire_Chief on 2009-02-18
On your Windows DNS server do you have the Linux box specified in the Allow Zone Transfers section? Also, do you have the Bind Secondaries box checked?

---

### Post by dhagens on 2009-02-18
Hi Fire_Chief,

Thanks for your response!

Zone transfer is allowed. "dig @10.20.1.11 -t AXFR" works as confirmation on that.

What do you mean with the secondaries box ? I run cli mode only, so i do all configs by editing the config files which i displayed in my first post.
I did set the zone type to slave as you can see in named.conf.local.

Dennis

---

### Post by Fire_Chief on 2009-02-18
The secondaries checkbox is a setting in the Windows DNS server. It is usually checked by default however you may want to confirm. This can be found under the Properties section of the DNS server.

---

### Post by dhagens on 2009-02-19
Under server options "BIND Secondaries" is checked.

---

### Post by jbarnett on 2009-02-22
When I set up ubuntu bind as a secondary I had problems getting it so write zone data with the same error that you show.  I found the problem was with the configuration of 'apparmor'.

---

### Post by RealPSL on 2009-02-22
I agree with jbarnett. You have to watch out for apparmor especially if you start using non-standard directories which chroot requires. If you choose to at least temporarily disable apparmor to eliminate it as the source of the problem there are instructions below.

[https://help.ubuntu.com/community/AppArmor]("https://help.ubuntu.com/community/AppArmor")

---

