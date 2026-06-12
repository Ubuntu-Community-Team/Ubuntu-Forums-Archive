---
title: "Can't compile samba-vscan..."
date: 2008-09-24
forum: Server Platforms
---

### Post by Fenix999 on 2008-09-24
Hi,

I have been searching for a solution in the web but it seems that every one says more or less the same thing:

```
1. Prepare package Clamav and supporting packages
apt-get install clamav arj unzoo lha clamav-freshclam clamav-daemon clamav-testfiles

You may also need build-essential package

Test: Please make sure that we can scan infected files.
clamscan -ir /usr/share/clamav-testfiles

We should see lines like the following:

----------- SCAN SUMMARY -----------
Known viruses: 266917
Engine version: 0.91.2
Scanned directories: 1
Scanned files: 7
Infected files: 6
Data scanned: 0.00 MB
Time: 3.762 sec (0 m 3 s)


2. Prepare packages to install clamav-scan into Samba
apt-get install dpkg-dev
apt-get source samba
apt-get build-dep samba
wget -c http://optusnet.dl.sourceforge.net/sourceforge/openantivirus/samba-vscan-0.3.6b.tar.bz2

3. Compiling
cd samba-3.0.24
./debian/rules configure-stamp
cd source
make proto
cd ../..

tar -jxvf samba-vscan-0.3.6b.tar.bz2 -C /usr/src
cd samba-vscan-0.3.6b
./configure --with-samba-source=/usr/src/samba-3.0.24/source
make && make install

Now the vscan-clamav module is ready to use

4. Configuring Samba to cooperate with vscan-clamav
mkdir /etc/samba/vfs-config
cp /usr/src/samba-vscan-0.3.6b/clamav/vscan-clamav.conf /etc/samba/vfs-config/

change some values in the /etc/../vfs-config/vscan-clamav.conf:
clamd socket name = /var/run/clamav/clamd.ctl
infected files action = quarantine
; By default, the quarantine directory is /tmp
; quarantine directory = /mnt/office-shared-files/.quarantine


Add some values in samba config file: /etc/samba/smb.conf. We may add this line under [global] configuration or specific directory configuration
vfs objects = vscan-clamav
vscan-clamav: config-file = /etc/samba/vfs-config/vscan-clamav.conf

5. We must recompile vscan-clamav if we upgrade our Samba. To lock Samba version from upgrading, we must do this:
echo samba hold | dpkg --set-selections
echo samba install | dpkg --set-selections

6. Now restart Samba
/etc/init.d/samba restart
```

it doesn't matter how hard I try I can't get passed step 3,
with a error like this 

```
/usr/src/sources/samba-3.0.28a/source/include/proto.h:6290: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7577: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7579: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7580: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7582: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7583: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7586: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8250: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8847: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8848: error: expected â;â, â,â or â)â before âvoidâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8879: error: expected â)â before â*â token
make: *** [global/vscan-functions.po] Error 1

```

Does any one have any idea? 

Or is there any other software like this one?

Many thanks in advance..

---

### Post by cariboo on 2008-09-24
You are missing a file of some sort. You didn't post enough of the listing, but just before it starts you shuold see a line ending with this:

```
No such file or directory
```

Here is a link to a page that will help fix this error:

[http://www.howtoforge.com/apt_file_debian_ubuntu](http://www.howtoforge.com/apt_file_debian_ubuntu)

Jim

---

### Post by bab1 on 2008-09-24
Are you sure Jim?  I'm certainly no expert in this, but usually when I screw up a script (by forgeting an opening or closing () or " "), I get "token" error. The proto.h is a header file for C, correct?  I'll bet the 8879 (or some such) is a line number.

---

### Post by Fenix999 on 2008-09-24
The complete code...

I would go more to the case of a mising () or "", but I haven't changed nothing...

```
fenix@ubuntuser:/usr/src/sources/samba3-vscan-0.4.0-snapshot1$ make
Compiling global/vscan-functions.c with -fPIC
In file included from /usr/src/sources/samba3-vscan-0.4.0-snapshot1/include/vscan-global.h:4,
                 from global/vscan-functions.c:15:
/usr/src/sources/samba-3.0.28a/source/include/includes.h:639:17: error: tdb.h: No such file or directory
In file included from /usr/src/sources/samba-3.0.28a/source/include/includes.h:640,
                 from /usr/src/sources/samba3-vscan-0.4.0-snapshot1/include/vscan-global.h:4,
                 from global/vscan-functions.c:15:
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:35: error: expected specifier-qualifier-list before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:48: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:51: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:53: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:58: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:58: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:60: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:61: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âtdb_fetch_bystringâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:67: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âmake_tdb_dataâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:68: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âstring_tdb_dataâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:69: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:69: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:71: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/util_tdb.h:73: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/includes.h:641:21: error: tdbback.h: No such file or directory
In file included from /usr/src/sources/samba-3.0.28a/source/librpc/gen_ndr/srvsvc.h:3,
                 from /usr/src/sources/samba-3.0.28a/source/librpc/gen_ndr/wkssvc.h:3,
                 from /usr/src/sources/samba-3.0.28a/source/include/smb.h:331,
                 from /usr/src/sources/samba-3.0.28a/source/include/includes.h:664,
                 from /usr/src/sources/samba3-vscan-0.4.0-snapshot1/include/vscan-global.h:4,
                 from global/vscan-functions.c:15:
/usr/src/sources/samba-3.0.28a/source/librpc/gen_ndr/security.h:1:26: error: ndr/security.h: No such file or directory
In file included from /usr/src/sources/samba-3.0.28a/source/include/includes.h:692,
                 from /usr/src/sources/samba3-vscan-0.4.0-snapshot1/include/vscan-global.h:4,
                 from global/vscan-functions.c:15:
/usr/src/sources/samba-3.0.28a/source/include/rpc_eventlog.h:63: error: expected specifier-qualifier-list before âTDB_CONTEXTâ
In file included from /usr/src/sources/samba-3.0.28a/source/nsswitch/winbind_client.h:1,
                 from /usr/src/sources/samba-3.0.28a/source/include/includes.h:709,
                 from /usr/src/sources/samba3-vscan-0.4.0-snapshot1/include/vscan-global.h:4,
                 from global/vscan-functions.c:15:
/usr/src/sources/samba-3.0.28a/source/nsswitch/winbind_nss_config.h:39:28: error: system/filesys.h: No such file or directory
/usr/src/sources/samba-3.0.28a/source/nsswitch/winbind_nss_config.h:40:28: error: system/network.h: No such file or directory
/usr/src/sources/samba-3.0.28a/source/nsswitch/winbind_nss_config.h:41:27: error: system/passwd.h: No such file or directory
In file included from /usr/src/sources/samba-3.0.28a/source/include/includes.h:789,
                 from /usr/src/sources/samba3-vscan-0.4.0-snapshot1/include/vscan-global.h:4,
                 from global/vscan-functions.c:15:
/usr/src/sources/samba-3.0.28a/source/include/proto.h:249: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:529: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1468: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âmake_tdb_dataâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1469: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âstring_tdb_dataâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1470: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1471: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1472: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1474: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1475: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1476: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1477: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1478: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1479: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1480: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1481: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1482: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1483: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1484: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1485: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1486: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âtdb_fetch_bystringâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1487: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1488: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1489: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1495: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1497: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1500: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1500: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:1502: error: expected declaration specifiers or â...â before âTDB_DATAâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:2975: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:3689: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:4718: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âget_printer_notify_pid_listâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:4802: error: expected â)â before âkeyâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:4807: error: expected declaration specifiers or â...â before âTDB_CONTEXTâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:4811: error: expected declaration specifiers or â...â before âTDB_CONTEXTâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:6289: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:6290: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7577: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7579: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7580: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7582: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7583: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:7586: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8250: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8847: error: expected â)â before â*â token
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8848: error: expected â;â, â,â or â)â before âvoidâ
/usr/src/sources/samba-3.0.28a/source/include/proto.h:8879: error: expected â)â before â*â token
make: *** [global/vscan-functions.po] Error 1

```

---

### Post by bab1 on 2008-09-24
@ Fenix999,

This is not your fault.  It is the package that is not working correctly.  I see that there are a lot of errors.  None are related to you directly.

The only thing I can offer is to make sure all the dependancies are met le: all libs needed are installed.

---

### Post by Fenix999 on 2008-09-25
how can I know the dependancies??

or install all libs?

---

### Post by eewoud on 2010-10-18
I see that you are using a newer version of samba. The latest version of samba that's supported with vscan is samba version 3.0.24. Try again using this version of samba and it should work.

---

