---
title: "trouble with SNMP"
date: 2009-05-04
forum: Server Platforms
---

### Post by m_kk on 2009-05-04
Hi,

I have installed SNMP from sources and it was working fine until today snmpget and snmpwalk started timing out. While restarting the service I get an error .
```
Starting network management services:
/usr/sbin/snmpd: symbol lookup error: /usr/sbin/snmpd: undefined symbol: smux_listen_sd
```

ldd /usr/sbin/snmpd gave me this result 

```
linux-gate.so.1 =>  (0xb7f5a000)
	libnetsnmpagent.so.15 => /usr/local/lib/libnetsnmpagent.so.15 (0xb7eee000)
	libnetsnmphelpers.so.15 => /usr/local/lib/libnetsnmphelpers.so.15 (0xb7eca000)
	libnetsnmpmibs.so.15 => /usr/local/lib/libnetsnmpmibs.so.15 (0xb7d9c000)
	libwrap.so.0 => /lib/libwrap.so.0 (0xb7d93000)
	libperl.so.5.10 => /usr/lib/libperl.so.5.10 (0xb7c42000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c1c000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c03000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7aa5000)
	libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7a72000)
	libnetsnmp.so.15 => /usr/local/lib/libnetsnmp.so.15 (0xb79c0000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb79bc000)
	libsensors.so.3 => /usr/lib/libsensors.so.3 (0xb7985000)
	libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7839000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb781f000)
	/lib/ld-linux.so.2 (0xb7f40000)
	libsysfs.so.2 => /lib/libsysfs.so.2 (0xb7815000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb77ff000)


```

Also when i do snmpget --version and snmpwalk --version I get
```
NET-SNMP version: 5.4.2.1
```

I searched the web but none of them have a solution. I also reinstalled again from the sources but no use. 

Any suggestions would be great.
Thanks in advance

---

### Post by m_kk on 2009-05-05
Any help?

---

### Post by m_kk on 2009-05-06
ok at least can some one tell me how to remove the snmp related packages from my system. I installed it from the sources. I feel there are more than one version of snmp running on my system. I am using Ubuntu 8.10.

---

### Post by wirelessmonkey on 2009-05-06
I believe you can go into your net-snmp source directory and do:
```
 sudo make uninstall 
sudo make distclean 
```
to remove it... and to install from repos, or to check if it is installed:
```
 sudo apt-get update
sudo apt-get install net-snmp 
```

---

