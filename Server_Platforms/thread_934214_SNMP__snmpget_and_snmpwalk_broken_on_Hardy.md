---
title: "SNMP  snmpget and snmpwalk broken on Hardy"
date: 2008-09-30
forum: Server Platforms
---

### Post by n00b2ubuntu on 2008-09-30
Hi,

I have just upgraded Gutsy server to Hardy server. All went well except that I noticed my Nagios system was no longer receiving SNMP data.

On further examination it seems the snmpget command (part of the SNMP package) is failing. When I run it manually from the command line:

sudo /usr/bin/snmpget -t 1 -r 5 -m '' -v 2c -c public 192.168.2.5:161

I get the following:


```

/usr/bin/snmpget: symbol lookup error: /usr/local/lib/libnetsnmp.so.15: undefined symbol: RAND_bytes

```
I am lead to believe that this is something to do with the SNMP package now being linked to openssl?!

Is the SNMP package broken in Hardy? I have tried removing and reinstalling it but it makes no difference.

Any help greatfully received!

---

### Post by n00b2ubuntu on 2008-09-30
Further to this I have discovered that snmptrapd is failing to start:

```
Starting network management services:/usr/sbin/snmpd: symbol lookup error: /usr/sbin/snmpd: undefined symbol: smux_listen_sd
invoke-rc.d: initscript snmpd, action "start" failed.
```

More 'undefined symbol' errors :confused:

---

### Post by Paul Weaver on 2008-09-30
I'm running hardy on x86/32 with no problems

Linux $hostname 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

SNMPWALK:
 snmpwalk -v2c -c comm ip.ad.drr.ess
 SNMPv2-MIB::sysDescr.0 = STRING:...
 
 snmpwalk --version
 NET-SNMP version: 5.4.1
 
 ldd `which snmpget`
 linux-gate.so.1 =>  (0xb7f8d000)
 libnetsnmp.so.15 => /usr/lib/libnetsnmp.so.15 (0xb7ec7000)
 
 ii  snmp 5.4.1~dfsg-4ubuntu4 SNMP (Simple Network Management Protocol) ap

 apt-get install snmp
 snmp is already the newest version.

 /var/lib/dpkg/info/snmp.md5sums:02803c8f96c2ced634b6c7db2d1fae8b  usr/bin/snmpget

 /var/lib/dpkg/info/libsnmp15.md5sums:f1eb17b67deeb9fdc7f31f0fc680363b  usr/lib/libnetsnmp.so.15.1.0

 ii  libsnmp15 5.4.1~dfsg-4ubuntu4 SNMP (Simple Network Management Protocol) li

md5sums
8e0c117ffee493023ead290f06d386f0  /usr/bin/snmpwalk
f1eb17b67deeb9fdc7f31f0fc680363b  /usr/lib/libnetsnmp.so.15.1.0


Do yours match

---

### Post by Paul Weaver on 2008-09-30
Run 
 apt-get update
 apt-get upgrade

Any error messages? Try
 dpkg -C

---

### Post by n00b2ubuntu on 2008-09-30
Paul, thanks for your reply


No errors with apt-get or dpkg -C

Versions look different though...

```
snmpwalk --version
NET-SNMP version: 5.4

snmpget --version
NET-SNMP version: 5.4
```


```

ldd `which snmpget`
        linux-vdso.so.1 =>  (0x00007fff865fe000)
        libnetsnmp.so.15 => /usr/local/lib/libnetsnmp.so.15 (0x00007f517e3b6000)
        libc.so.6 => /lib/libc.so.6 (0x00007f517e004000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f517e366000)
```
```

sudo apt-get install snmp
Reading package lists... Done
Building dependency tree
Reading state information... Done
snmp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


:confused:

---

### Post by n00b2ubuntu on 2008-09-30
By the way, this is running on AMD64, if it makes a difference...

snmp_5.4.1~dfsg-4ubuntu4_amd64.deb

---

### Post by n00b2ubuntu on 2008-09-30
Ok, well I have fixed SNMP by compiling net-SNMP myself...

I did the following:

1) Downloaded the source from [https://launchpad.net/ubuntu/+source/net-snmp](https://launchpad.net/ubuntu/+source/net-snmp)

2) Extract:

```
tar -xvf net-snmp_5.4.1~dfsg.orig.tar.gz
```

3) Change directory

```
cd net-snmp-5.4.1
```

4) As per this article: [http://www.mail-archive.com/net-snmp-users@lists.sourceforge.net/msg10010.html](http://www.mail-archive.com/net-snmp-users@lists.sourceforge.net/msg10010.html)

```
./configure --with-openssl=/usr/lib --with-perl-modules
```

4) ```
./make
```

5) ```
./make install
```


Now my snmpwalk and snmpget versions are reporting as:

```
/usr/bin/snmpget -V
NET-SNMP version: 5.4.1

```



Problem still remains with snmpd though... looks like I'll have to compile that from source too....

---

### Post by Paul Weaver on 2008-09-30
The amd64 could be causing the difference in our installations, but it seems that you've somehow got a broken package -- perhaps move apt to using a different archive?

---

