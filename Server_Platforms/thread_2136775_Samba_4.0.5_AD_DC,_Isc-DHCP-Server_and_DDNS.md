---
title: "Samba 4.0.5 AD DC, Isc-DHCP-Server and DDNS"
date: 2013-04-18
forum: Server Platforms
---

### Post by JnPson on 2013-04-18
I run Samba 4.0.5 as AD DC and I have installed Isc-DHCP-Server that I hopefully can use for dynamically updates to my Samba internal DNS (DDNS).
Last week I had samba 4 alpha18 installed and I could find several howto's on DDNS that helped me solved this issue. But now the paths and much more has changed for Samba and DNS, and as far as I understand BIND9 is not in use. I don't know where I can find *named.conf*, or if it even exist in samba 4.0.5. This means that all the howto's I followed before is a bit dated.

In *dhcpd.conf* I've added *ddns-update-style interim;* but that is not enough, or maybe even wrong *update-style*. I admin the DNS server with ssh and from an XP machine using Adminpak. Through the mmc I've added the zone in-addr.arpa because I thought that might solve the error.

But now I get repeated errors in syslog that says 'Timed out' for every new IP lease. Their IP is added to the DNS when added to the domain but the isc-dhcp-server cannot update the records.

```

Apr 18 13:21:12 dc01 dhcpd: Unable to add forward map from pc01.mydomain.lan to 10.0.0.164: timed out

Apr 18 14:22:44 dc01 dhcpd: unable to add reverse map from 164.0.0.10.in-addr.arpa. to pc01.mydomain.lan: timed out 
```

I wonder, how do I get my DHCP-server to update DNS dynamically? And does *named.conf* exist in Samba 4.0.5

An additional question: How do I start|stop|restart DNS in Samba 4.0.5? Do I have to restart samba4 to restart DNS?

//
JnPson

---

### Post by Toxic64 on 2013-04-19
Hi Jpson,

I have the same issue here. I'm working on it but *ddns-update-style *doesn't work with Samba 4 but It might be corrected in Samba 4 next release

DNS is integrated to samba4 restart your Samba 4 daemon will restart DNS.

I found the problem but don't have a solution ...yet

It seems SAMBA_INTERNAL accepts only secure updates via kerberos from your DHCP.
It seems it's not possible to configure SAMBA_INTERNAL to accept unsecure updates so you have to configure your ISC-DHCP-SERVER to work with Kerberos allowing secure connections to the DNS. I don't know how it's done.

---

### Post by JnPson on 2013-04-19
Hi Toxic64. Thank you for responding. 
Is there another dhcp-server I could install maybe that supports kerberos?
I have only heard of isc-dhcp-server. 

//JnPson

---

### Post by Toxic64 on 2013-04-19
I think you understood me wrong. Isc-dhcp certainly works with Kerberos but has to be configured. I now no other DHCP you can use as a replacement

---

### Post by JnPson on 2013-04-19
Oh sorry. I did misunderstand. 
Then it is about finding the right guide/howto for samba 4.0.5. and isc-dhcp-server.

---

### Post by Toxic64 on 2013-04-25
I'm still on it.

---

### Post by JnPson on 2013-04-26
Thank you Toxic64.

---

### Post by Toxic64 on 2013-04-29
HI . seems to be a pretty known issue or bug no real fix at the moment. probably in next update

---

### Post by JnPson on 2013-04-29
Hi Toxic64 and thanks for helping me. 

I did an *update* and *upgrade* this moring at work and after that samba4 is not responding as usual. I get a strange result when running testparm and I can't use samba-tool testparm either. Testparm is checking the old smb.conf in /etc/samba/smb.conf, and I can no longer do a version-check on samba with samba -V or samba4 -V.

But the domain controller seems to be running and I can create accounts using Active Directory Users and Computer-snap-in. 
 
I should say that I installed samba-tools twice. First I thought I just missed some lines of error when it didn't give the expected result. I thought it was because I didn't pay attention so I installed it again and noticed the same error with *samba-tool testparm*

The result using only testparm: 

```
root@dc01:/# testparm
Load smb config files from **/etc/samba/smb.conf**
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
[I]ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist[/I]
Server role: **ROLE_STANDALONE**
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

The testresult is not how I configured it. I should see /*User*, /*Profiles *and /*Files*. And the domain-info is missing. 

This is the result using samba-tool testparm
```
root@dc01:/# samba-tool testparm
Traceback (most recent call last):
  File "/usr/bin/samba-tool", line 26, in <module>
    from samba.netcmd.main import cmd_sambatool
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/main.py", line 23, in <module>
    from samba.netcmd.dbcheck import cmd_dbcheck
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 23, in <module>
    from samba.auth import system_session
ImportError: libauth4.so: cannot open shared object file: No such file or directory
```

This is the result using Samba -V and Samba4 -V

```
root@dc01:/etc/samba# Samba -V
No command 'Samba' found, did you mean:
 Command 'samba' from package 'samba4' (universe)
Samba: command not found
root@dc01:/etc/samba# samba4 -V
No command 'samba4' found, did you mean:
 Command 'samba' from package 'samba4' (universe)
samba4: command not found
root@dc01:/etc/samba# Samba4 -V
Samba4: command not found
```

Now I'm confused. 

//JnPson

---

### Post by Toxic64 on 2013-04-29
Wrong move my friend. you installed samba4 from git if I recall correctly then you should have updated from git too...

Ubuntu repos do not hold samba4.0.5 updates...only samba 4.0.0 Alpha 18 if I recall correctly.

[https://wiki.samba.org/index.php/Build_Samba#Upgrading_a_source_version](https://wiki.samba.org/index.php/Build_Samba#Upgrading_a_source_version)

---

### Post by JnPson on 2013-04-29
That's correct. But I did a clean install of Ubuntu without samba 4.0.0 alpha18, so it shouldn't update samba at all.

---

### Post by Toxic64 on 2013-04-29
would you please send [COLOR=#ff0000]/var/lib/dpkg/status[/COLOR] file?

---

### Post by JnPson on 2013-04-29
Ok. But it'll have to wait until tomorrow as this ubuntu server is at work and I've at home now.

---

### Post by JnPson on 2013-04-30
Hi again.
Here comes the dpkg-status file. 

//JnPson

---

### Post by Toxic64 on 2013-04-30
Thanks.
Reading this file you'll find a lot of samba/Samba4 related components are detected as installed on your machine (via apt and the script I gave you because those are necessary components for samba to run).
When a package is detected as installed, it will be upgraded via apt-get upgrade. 
Those components related to samba4 have been upgraded:

```
**[COLOR=#ff0000]Package: libndr0[/COLOR]**
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 150
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Depends: libc6 (>= 2.4), libsamba-util0, libtalloc2 (>= 2.0.4~git20101213)
Pre-Depends: multiarch-support
Description: NDR marshalling library

[COLOR=#ff0000]**Package: libgensec0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: net
Installed-Size: 750
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: winbind4 (<< 4.0.0~alpha17~git20110724.dfsg1-1)
Depends: samba-common (>= 2:3.4.0~pre2-1), libasn1-8-heimdal (>= 1.4.0+git20110226), libbsd0 (>= 0.0), libc6 (>= 2.4), libcomerr2 (>= 1.01), libgcrypt11 (>= 1.4.5), libgnutls26 (>= 2.12.6.1-0), libgssapi3-heimdal (>= 1.4.0+git20110226), libhdb9-heimdal (>= 1.4.0+git20110226), libkrb5-26-heimdal (>= 1.4.0+git20110226), libldb1 (>= 0.9.21), libndr-standard0, libndr0, libroken18-heimdal (>= 1.4.0+git20110226), libsamba-credentials0, libsamba-hostconfig0, libsamba-util0, libsamdb0, libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libtevent0 (>= 0.9.13)
Pre-Depends: multiarch-support
Description: Generic Security Library

**[COLOR=#ff0000]Package: libsamba-hostconfig0[/COLOR]**
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 218
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: libsamba-util0 (<< 4.0.0~alpha17~git20110724.dfsg1-1)
Depends: libbsd0 (>= 0.0), libc6 (>= 2.4), libsamba-util0, libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214)
Pre-Depends: multiarch-support
Description: Samba host configuration library
[B][COLOR=#ff0000]
Package: samba-dsdb-modules[/COLOR][/B]
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 923
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: libgensec0 (<< 4.0.0~alpha17~git20110724.dfsg1-1)
Depends: libbsd0 (>= 0.0), libc6 (>= 2.4), libcomerr2 (>= 1.01), libdcerpc0, libgensec0, libkrb5-26-heimdal (>= 1.4.0+git20110226), libldb1 (>= 1.1.2~), libndr0, libpopt0 (>= 1.14), libsamba-credentials0, libsamba-hostconfig0, libsamba-util0, libsamdb0, libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libtevent0 (>= 0.9.9)
Enhances: libldb1
Description: Samba Directory Services Database

[COLOR=#ff0000]**Package: libsmbclient-raw0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: net
Installed-Size: 1628
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: python-samba (<< 4.0.0~alpha18)
Depends: libasn1-8-heimdal (>= 1.4.0+git20110226), libbsd0 (>= 0.0), libc6 (>= 2.11), libcomerr2 (>= 1.01), libgensec0, libgssapi3-heimdal (>= 1.4.0+git20110226), libkrb5-26-heimdal (>= 1.4.0+git20110226), libldap-2.4-2 (>= 2.4.7), libndr-standard0, libndr0, libsamba-credentials0, libsamba-hostconfig0, libsamba-util0, libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libtevent0 (>= 0.9.12)
Pre-Depends: multiarch-support
Description: SMB client library

[COLOR=#ff0000]**Package: samba4-common-bin**[/COLOR]
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 178
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: samba4-common (<< 2:3.4.0~pre2-1)
Depends: python-samba (= 4.0.0~alpha18.dfsg1-4ubuntu2), samba-common (>= 2:3.4.0~pre2-1), python
Conflicts: samba (<< 2:3.3.0~rc2-5), samba-common (<< 2:3.3.0~rc2-5)
Description: Samba 4 common files used by both the server and the client

[COLOR=#ff0000]**Package: python-samba**[/COLOR]
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 6566
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Provides: python2.7-samba
Depends: python-ldb (>= 1.1.2~), python-tdb, python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8), libbsd0 (>= 0.0), libc6 (>= 2.4), libdcerpc0, libgensec0, libldap-2.4-2 (>= 2.4.7), libldb1 (>= 0.9.21), libndr-standard0, libndr0, libpython2.7 (>= 2.7), libregistry0, libroken18-heimdal (>= 1.4.0+git20110226), libsamba-credentials0, libsamba-hostconfig0, libsamba-policy0, libsamba-util0, libsamdb0, libsmbclient-raw0, libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libtevent0 (>= 0.9.9), python-talloc (>= 2.0.6)
Description: Python bindings for Samba

[COLOR=#ff0000]**Package: libsamba-policy0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: net
Installed-Size: 114
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Depends: libldb1 (<< 1:1.1.5~), libldb1 (>> 1:1.1.4~), libc6 (>= 2.4), libdcerpc0, libndr0, libsamba-hostconfig0, libsamba-util0, libsmbclient-raw0, libtalloc2 (>= 2.0.4~git20101213)
Pre-Depends: multiarch-support
Description: Samba policy management

**[COLOR=#ff0000]Package: samba-common[/COLOR]**
Status: install ok installed
Multi-Arch: foreign
Priority: optional
Section: net
Installed-Size: 665
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: samba
Version: 2:3.6.3-2ubuntu2.6
Replaces: samba (<< 3.0.20b-1), samba4-common (<< 4.0.0~alpha7-1)
Depends: ucf, debconf (>= 0.5) | debconf-2.0
Recommends: samba-common-bin
Conflicts: samba4-common (<< 4.0.0~alpha7-1)
Conffiles:
 /etc/dhcp3/dhclient-enter-hooks.d/samba 732cae8c1d0d7a7f80e8597ae551ea0d
 /etc/samba/gdbcommands 898c523d1c11feeac45538a65d00c838
 /etc/pam.d/samba a69b859744494a52ecf10bb604544093
Description: common files used by both the Samba server and client

[COLOR=#ff0000]**Package: smbclient**[/COLOR]
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 41609
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba
Version: 2:3.6.3-2ubuntu2.6
Replaces: samba (<< 2.999+3.0.alpha21-4), smbget
Provides: samba-client
Depends: samba-common (= 2:3.6.3-2ubuntu2.6), libc6 (>= 2.15), libcap2 (>= 2.10), libcomerr2 (>= 1.01), libgssapi-krb5-2 (>= 1.10+dfsg~), libk5crypto3 (>= 1.6.dfsg.2), libkrb5-3 (>= 1.10+dfsg~), libldap-2.4-2 (>= 2.4.7), libpopt0 (>= 1.14), libreadline6 (>= 6.0), libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libwbclient0 (>= 2:3.6.0~pre3), zlib1g (>= 1:1.1.4)
Suggests: cifs-utils
Conflicts: samba4-clients
Description: command-line SMB/CIFS clients for Unix

[COLOR=#ff0000]**Package: libsamba-credentials0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: net
Installed-Size: 126
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Depends: libbsd0 (>= 0.0), libc6 (>= 2.4), libcomerr2 (>= 1.01), libgssapi3-heimdal (>= 1.4.0+git20110226), libkrb5-26-heimdal (>= 1.4.0+git20110226), libldb1 (>= 0.9.21), libndr0, libsamba-hostconfig0, libsamba-util0, libtalloc2 (>= 2.0.4~git20101213)
Pre-Depends: multiarch-support
Description: Samba Credentials management library

[COLOR=#ff0000]**Package: libsamba-util0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 724
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Depends: libattr1 (>= 1:2.4.46-5), libbsd0 (>= 0.0), libc6 (>= 2.4), libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214), libtevent0 (>= 0.9.9)
Pre-Depends: multiarch-support
Description: Samba utility function library
 Samba is an implementation of the SMB/CIFS protocol for Unix systems,

[COLOR=#ff0000]**Package: libsamdb0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: net
Installed-Size: 425
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: samba-ldb-tools
Depends: libldb1 (<< 1:1.1.5~), libldb1 (>> 1:1.1.4~), libbsd0 (>= 0.0), libc6 (>= 2.4), libgssapi3-heimdal (>= 1.4.0+git20110226), libkrb5-26-heimdal (>= 1.4.0+git20110226), libndr0, libpopt0 (>= 1.14), libsamba-credentials0, libsamba-hostconfig0, libsamba-util0, libtalloc2 (>= 2.0.4~git20101213), libtdb1 (>= 1.2.7+git20101214)
Pre-Depends: multiarch-support
Recommends: samba-dsdb-modules
Conflicts: samba-ldb-tools
Description: SAM database

[COLOR=#ff0000]**Package: libregistry0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 212
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Depends: libc6 (>= 2.4), libdcerpc0, libldb1 (>= 0.9.21), libndr-standard0, libndr0, libsamba-hostconfig0, libsamba-util0, libtalloc2 (>= 2.0.4~git20101213)
Pre-Depends: multiarch-support
Description: Registry library

[COLOR=#ff0000]**Package: libndr-standard0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 7691
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: libsamba-util0 (<< 4.0.0~alpha17~git20110724.dfsg1-1), libsmbclient-raw0 (<< 4.0.0~alpha18-1)
Depends: libbsd0 (>= 0.0), libc6 (>= 2.4), libndr0, libsamba-util0, libtalloc2 (>= 2.0.4~git20101213), libtevent0 (>= 0.9.14), zlib1g (>= 1:1.1.4)
Pre-Depends: multiarch-support
Description: Standard NDR interfaces

[COLOR=#ff0000]**Package: libdcerpc0**[/COLOR]
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: net
Installed-Size: 2305
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: samba4
Version: 4.0.0~alpha18.dfsg1-4ubuntu2
Replaces: libgensec0 (<< 4.0.0~alpha17~git20110724.dfsg1-1)
Depends: libbsd0 (>= 0.0), libc6 (>= 2.4), libgensec0, libhdb9-heimdal (>= 1.4.0+git20110226), libkrb5-26-heimdal (>= 1.4.0+git20110226), libldb1 (>= 0.9.21), libndr-standard0, libndr0, libpython2.7 (>= 2.7), libsamba-credentials0, libsamba-hostconfig0, libsamba-util0, libsamdb0, libsmbclient-raw0, libtalloc2 (>= 2.0.4~git20101213), libtevent0 (>= 0.9.12), python-talloc (>= 2.0.6)
Pre-Depends: multiarch-support
Description: DCE/RPC client library
```

I'd say your installation of samba4 as DC is screwed.
I would not bother try to repair it if you're not on production stage yet... just reinstall.
Or.... for science prupose...you could try removing those packages and then update/upgrade from git again but the chances that it works again would be very low.

---

### Post by JnPson on 2013-04-30
](*,)Ok, the server is not in production yet so I can install it from scratch. But how do I prevent this from happening again? 

The installation and configuration is good practice for me so I will go for it.

---

### Post by Toxic64 on 2013-04-30
Just don't do bulk upgrades I guess.

Just upgrade needed components.

also when you first install your server, don't install any optionnal components. and chose to only do automatic security upgrades

---

### Post by JnPson on 2013-04-30
Thanks.

---

### Post by JnPson on 2013-04-30
One quick question. 
Is there a way for me to transfer the old domain to a new server? I have installed Ubuntu at home and it's using alpha18 and I would like to keep the user, and computer accounts together with shares I've made.

I'm doing this at my server at home and I'm planning on replacing my old IBM with a newer no-name PC and install samba 4.0.5, and this would be good practice for me during my day-off. 
I won't be back to work before Thursday.

---

### Post by Toxic64 on 2013-04-30
certainly not. upgrade path would not work correctly from Alpha18 to final 4.0.5 with a lot of malfunctions.

what you certainly could do though is install a second DC on 4.0.5 and join it to your existing domain, force data replication and take your old DC offline 
you'll have to recreate the sahres you ve created as they won't replicate for they are not part of active directory datas.

 I would help you in such matters. (you can skype me if needed ;) )

---

### Post by JnPson on 2013-04-30
Ok :) thank you.

---

### Post by Toxic64 on 2013-04-30
my skype ID is in my profile

---

### Post by JnPson on 2013-05-01
Hi.
I'm working on the samba server, creating it with the script I got from you Toxic64, and was a little confused about what role the BDC of my domain should have. Is it Member server or should I join the domain as member server?
//edit
It should read: Member server or Domain controller//

The script works for me connecting to git, and I've made the changes necessary for my server. I didn't have to downlod the tar-file this time.

---

### Post by Toxic64 on 2013-05-01
Long awaited question my friend, I'll have to crack my fingers on this one.

When you're thinking PDC/BDC, you're talking NT Domains, like NT4 in a simplification matter, NT4 Used PDC essentially for logon and general authentication purpose and maintain the user database and BDC for other domain services. one was slave to the other

MS Active Directory/ Samba4 are totally  different.
In such context, all DCs stand equal (this is a very simplified explanation).

In AD/S4 Context, each DC maintains the domain, topology, authentication services and its own copy of the User/Group/OU database. all DCs share the (quite) the same domain informations. 

Now your second DC (which is not a BDC) will be joined to existing domain thus, fully replicating infos from the first DC.
This implies you will not provision it like you did for the first one

You'll only have to run the first script from the two I provided and then carefully follow the steps provided here[https://wiki.samba.org/index.php/Samba4/HOWTO/Join_a_domain_as_a_DC](https://wiki.samba.org/index.php/Samba4/HOWTO/Join_a_domain_as_a_DC) to join your new DC to the existing domain.

at the end of the installation you might want to carefully transfer FSMO knowing that MS recommends:

-PDC emulator and RID master Roles to be on the same DC
-Schema master and naming master to be on the same DC (naming master has to be on a Global catalog or it will not work...)
-Not placing the infrastructure mater on a Global catalog

the infrastructure master is responsible for the updates of his domain's objects references. It compares the data it maintains to the ones stored in the global catalog.
Global catalogs receive updates for every object in all the domains via the replication process. If the Infrastructure master ever finds datas that are not up-to date in its database, it will ask the global catalogs updates for those objects.
If the Infrastructure master and the global catalog are on the same DC, this process won't work as it will never find up-to-date datas and won't replicate those datas on the other DCs.

The only case you will have a GC and an infrastructure master on the same DC in on a single DC infrastructure. 

So for your infrastructure, I'd advise disabling GC on the second DC and transfer the infrastructure master role to it. (On a windows DC, you have the choice between transfer and seize...never seize a role unless emergency on a windows DC though cause you might end with a duplicate role which is not good. )

the Samba4 only available command for FSMO transfer is "seize" though so you ll have to go with it.


So:
 PDC , RID, Schema, naming --->>> DC1 where DC1 is a GC
infrastructure --->>> DC2 where DC2 is not a GC

My friend, I found something that could solve your original DNS update problem...
We knew the problem was that S4 INTERNAL_DNS didn't allow for unsigned updates.
Here is the parameter to add/change in your smb.conf


> 
#Allow unsigned updates | don't allow any updates | only allow signed updates 
allow dns updates = True | False | signed 
 # If recursive queries = yes is set, the following is also needed 
dns forwarder = <ip addr of external dns server>


Found that very deep in the wiki.
I didn't test it though but it should work.

---

### Post by JnPson on 2013-05-05
Thank you again. 
I will go through the installation tomorrow and make these changes.

---

### Post by Toxic64 on 2013-05-06
No problem. Keep me updated.

---

### Post by Toxic64 on 2013-05-10
how did it go?

---

### Post by JnPson on 2013-05-13
Hi Toxic64. I've been home sick for over a week, but now I'm back at work.

I've just started the new installation of ubuntu server 12.04.2 and when that is finished I will install dhcp and run your script. 

//JnPson

Ok. I have installed ubuntu, samba4.05, dhcp and I have added ```
[Global]
allow dns updates = True
``` in smb.conf and I have not received any errors in syslog. This is good, because earlier syslog was overflowing with errors when clients tried to updated DNS.

I can connect to AD DC with adminpak as usual and I can create users. I can also see in the dns snap-in that clients is added dynamically. The only problem I have now is roaming profiles.
I've added ```
\\dc01\Profiles\%USERNAME%
``` in the users profile path and ```
\\dc01\Users\%USERNAME%
``` to connect to H: for the template-user.
My test-user get *access denied *when he logs on for the first time. I have copied the local admin profile to ```
\\dc01\netlogon\Default Profile
``` and gave *everyone* permission to use it.

It must be the initial permissions for netlogon that is incorrect. 
Any ideas coming to mind?
//edit
My test user can logon to my domain but with a temp profile

//JnPson

---

### Post by Toxic64 on 2013-05-13
DHCP issue: could you release the IP one one of your client and change it then see if it updates dynamically in your DNS

Access right issue: you don't have to grant rights issue to everyone. I already answered that in the previous thread you had opened and the solution was working I think.

> The problem was: A permission problem solved with:
   
     
```
mkdir -m 770 /Users chmod g+s /Users chown root:users /Users 
//Edit
Forgot this part in smb.conf
```
   
     
```
[Users] directory_mode: parameter = 0700 read only = no path = /Users csc policy = documents 
```
This problem was solved and users could create files and folders in their own Home Folder. 
A bug in Samba 4.0.0alpha18 did prevent me from creating it as I should  so I have installed and configured Samba 4.0.5 from GIT with the great  help of [Toxic64]("http://ubuntuforums.org/member.php?u=1807148").                 


I think the same goes for roaming profiles.

By the way, are you absolutely sure you need roaming profiles?
I'm asking because those can be a major drawback in an infrastructure. If you need more informations about that I'll be glad to provide

---

### Post by JnPson on 2013-05-13
> **Toxic64 said:**
> DHCP issue: could you release the IP one one of your client and change it then see if it updates dynamically in your DNS
Hmm, it doesnt update dynamically. 

> **Toxic64 said:**
> Access right issue: you don't have to grant rights issue to everyone. I already answered that in the previous thread you had opened and the solution was working I think.
When I copied the profile from the xp machine I gave everyone access to the default profile. I didn't create Default Profile folder with mkdir on the server but from xp as administrator.

> **Toxic64 said:**
> I think the same goes for roaming profiles.

I did miss *chown root:users /Profiles* and afterwards users can logon with a roaming user profile.

> **Toxic64 said:**
> By the way, are you absolutely sure you need roaming profiles?
I'm asking because those can be a major drawback in an infrastructure. If you need more informations about that I'll be glad to provide

Yes, it is one of the most important reason for setting up a domain, as the users will be moving between different rooms and we have no laptops, only deskptop pc's.

---

### Post by Toxic64 on 2013-05-13
that's a network killer though....
As a long time Windows IT professional , I'd advise not to use roaming profiles. 
Perhaps your IT dept. needs to rethink the strategy, because depending on your number of users and the size of the profiles, you will experiment major frustration when your network gets bloated during the profile copy at each opening of a new session and the countless problems that go with it..
you will also experiment the joy of timeouts on session openings when the profile is too heavy and windows clients decide to load the local copy and not save your works to your remote profile server.
Expect users coming at you with torches, forks and spears all at once trying to find the right witch to burn...

---

### Post by JnPson on 2013-05-13
haha yes I'll be burned at a stake, but the possiblity of roaming user profiles are exiting for them and the users are looking forward to be able to move around without limits. I'll need to educate them on how to not save big files on the desktop and so on.

---

### Post by Toxic64 on 2013-05-13
educating users? 

What kind of sorcery is this????

There are better way for moving users files than roaming profiles.
I can assure you I faced this dozens of times and there is always a better solution.
perhaps mandatory profiles (so they don't **** it up + a DFS root with protected shares would be the solution.

---

### Post by JnPson on 2013-05-13
Yes, DFS is a good solution, but I haven't been able to implement it on linux. I found ceph and Gluster, but with the limited knowledge I've got, I think it will be difficult for me setting up DFS.

---

### Post by Toxic64 on 2013-05-13
I know DFS is a little tricky to implement with samba. I'll take a look at ceph and gluster and let you know

---

### Post by JnPson on 2013-05-13
Much appreciated.

Here are the links for them. 
[http://ceph.com/](http://ceph.com/)
[http://www.gluster.org/category/ubuntu/](http://www.gluster.org/category/ubuntu/)

---

### Post by Toxic64 on 2013-05-14
you could also get a glance at openAFS which works kind of like DFS. There are many guides to OpenAFS implementation.

---

### Post by JnPson on 2013-05-14
Very interesting, but extremely terrifying to try and grasp all that information, where as I'm already trying to get my head around AD DC, quotas, CUPS, Postfix, roaming profiles, permissions and rights on Linux fs and at the same time try to master Linux basics.
Remember, I'm new to Linux. I dived into this "world" September last year and was trying to find the best Linux distro by installing every distro I could find.
I have tested, OpenSuSE 10 11 12, SUSE, Mandriva (was so easy I got bored), CentOS, SlackWare, Fedora, USC, Calculate, FreeNAS, pfSense, Red Hat.  

 You name it, I've tried it. 

I februari I found Debian and later on Ubuntu, which I liked and decided to learn. 
I was noob enough to look for GUI linux, but with Debian and Ubuntu I realized I needed to learn CLI.
I chose Ubuntu because of the support for samba 4, and apt-get :P

But I'm intrigued by OpenAFS because I wanted DFS in my network.

---

### Post by Toxic64 on 2013-05-14
Ok that's a lot of things to learn but very interresting.
I'm not a linux veteran either but 12 years of IT Security Consulting gave me a pretty good knowledge of network and system management and a great hunger for learning. 
I'd be happy to help you go through all of this but that's a lot to go in one thread. Perhaps we could go through all of it more profitiently.
I would advise to go and test each of these subjects through skype and write tutorials for each one to be published on the forum tutorial thread.

I have a hardware server at home to test everything and absolutely no fear to **** it up.
I also have a nice powerfull computer which can run 20 Vm's at once if we ever need a virtual lab.

Let me know if you are OK with it.

---

### Post by lingpanda on 2013-05-14
> **JnPson said:**
> Hmm, it doesnt update dynamically. 


When I copied the profile from the xp machine I gave everyone access to the default profile. I didn't create Default Profile folder with mkdir on the server but from xp as administrator.

It's a known bug with dynamic updates. [https://bugzilla.samba.org/show_bug.cgi?id=9559](https://bugzilla.samba.org/show_bug.cgi?id=9559) I'm in the same boat as far as DNS is concerned. I'm trying to force it thru GPO's though.

---

### Post by Toxic64 on 2013-05-14
@Lingpanda.

doing it by gpo is not a good idea. you will send release/renew signals from all over your clients on your network which might result in bad response from your dhcp (ack/syn/ack) and will inevitably cause traffic cause dhcp uses broadcast.

---

### Post by JnPson on 2013-05-14
> **Toxic64 said:**
> Ok that's a lot of things to learn but very interresting.
I'm not a linux veteran either but 12 years of IT Security Consulting gave me a pretty good knowledge of network and system management and a great hunger for learning. 
I'd be happy to help you go through all of this but that's a lot to go in one thread. Perhaps we could go through all of it more profitiently.
I would advise to go and test each of these subjects through skype and write tutorials for each one to be published on the forum tutorial thread.

I have a hardware server at home to test everything and absolutely no fear to **** it up.
I also have a nice powerfull computer which can run 20 Vm's at once if we ever need a virtual lab.

Let me know if you are OK with it.

Let's do this. I've added you to skype. We have a big job ahead of us then. ](*,)

---

### Post by lingpanda on 2013-05-14
> **Toxic64 said:**
> @Lingpanda.

doing it by gpo is not a good idea. you will send release/renew signals from all over your clients on your network which might result in bad response from your dhcp (ack/syn/ack) and will inevitably cause traffic cause dhcp uses broadcast.

Good to know. Just deleted that GPO.

---

### Post by JnPson on 2013-05-14
> **lingpanda said:**
> It's a known bug with dynamic updates. [https://bugzilla.samba.org/show_bug.cgi?id=9559](https://bugzilla.samba.org/show_bug.cgi?id=9559) I'm in the same boat as far as DNS is concerned. I'm trying to force it thru GPO's though.

Thank you lingpanda. I read it now and I recognize the bug. The same happened on my server. The first initial update worked but no updates and one IP was even deleted after ipconfig /release and didn't reappear.

---

### Post by Toxic64 on 2013-05-14
Ok. maybe not tonight as I have my kids with me.
tell me what project you want to start with so I can setup a lab environnement.

the DHCP issue should be corrected soon I think as it's a major issue when you are working with DNS.
as per DFS, I think it might also be fully implemented very soon or samba4 won't be able to replicate AD with a windows 2008 DC (AD 2008 replication is done only via DFS-R)

---

### Post by JnPson on 2013-05-14
> **Toxic64 said:**
> Ok. maybe not tonight as I have my kids with me.
tell me what project you want to start with so I can setup a lab environnement.

No, not tonight. 

Well, as I already have AD DC, internal DNS and DHCP up and running I think roaming profiles, quotas, cups and postfix would be the best order. I don't know if there is a good tutorial on rights and permissions on Ubuntu, cause I haven't needed it yet, but it could be good to have one basic which we noobs can follow. 

Later on perhaps OpenAFS. I might come up with more stuff I need.

---

### Post by lingpanda on 2013-05-14
How do I change the Internal DNS options? For instance run /samba-tool dns serverinfo IP -Uadministrator. I can't find any documentation to adjust these settings.

---

### Post by Toxic64 on 2013-05-14
there are very good tutorials about rights and permissions on linux but in your context you'll need more about AD/windows rights and permissions

---

### Post by JnPson on 2013-05-14
Then we must add that one to the list.

---

### Post by lingpanda on 2013-05-14
Another thing I noticed even when using allow dns updates = True is that Windows RSAT DNS snap in still shows Dynamic updates = secure only.

---

### Post by Toxic64 on 2013-05-14
did you try to change it to allow unsigned?

lingpanda, I'm setting up a new samba4 server to test. I'll let you know about Internal DNS options

---

### Post by JnPson on 2013-05-14
> **Toxic64 said:**
> lingpanda, I'm setting up a new samba4 server to test. I'll let you know about Internal DNS options

It would be a nice to have tutorial on that too.

> **Toxic64 said:**
> did you try to change it to allow unsigned?

If this was a question meant for me, yes. If that was what I did with ```
allow dns update = Yes
``` :confused:

---

### Post by Toxic64 on 2013-05-14
I will write one soon.

I menat from the dnsmgmt.msc console on windows RSAT

---

### Post by JnPson on 2013-05-14
No, I did the changes in smb.conf only.

---

### Post by lingpanda on 2013-05-15
> **Toxic64 said:**
> did you try to change it to allow unsigned?

Yes and I receive this error.

[IMG][[IMG]http://s9.postimg.org/7my73muqz/dnssigned.jpg[/IMG]]("http://postimg.org/image/7my73muqz/")[/IMG]

You may have to click the image to see it.

Wanted to add I found this below from here [http://www.sloop.net/smb.conf.html](http://www.sloop.net/smb.conf.html) Didn't make a difference to RSAT

allow dns updates (G)

This option determines what kind of updates to the DNS are allowed.

DNS updates can either be disallowed completely by setting it to disabled, enabled over secure connections only by setting it to secure or allowed in all cases by setting it to enabled or nonsecure.

Default: allow dns updates = secure only

Example: allow dns updates = disabled

Small update. Tried every available option for "allow dns updates" and samba still shows 

 fAllowUpdate                : DNS_ZONE_UPDATE_SECURE

Used the following command: /samba-tool dns zoneinfo sambapdc.mydomain.local mydomain.local -Uadministrator

Just found something very interesting. So I ran command

/samba-tool testparm

and it gave me an interesting result. It gives me the output of smb.conf but it now displays

"allow dns updates = nonsecure and secure"

This is with "allow dns updates = True" in my smb.conf file.

---

### Post by JnPson on 2013-05-15
When I run the command samba-tool testparm I get this error:
```
root@dc02:~# samba-**tool** testparm
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.2.44

```And if I run samba-tools testparm I get the same error:
```
root@dc02:~# samba-**tools** testparm
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.2.44
```
Samba-tools is installed and is the latest version. 
```
root@dc02:~# apt-get install samba-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
If I try to show samba version I get:
```
root@dc02:~# Samba -V
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.2.44
root@dc02:~# samba -V
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.2.44

```
These errors is on a newly installed and updated ubuntu server. I installed it this morning together with Samba 4.0.5. 
I have no idea what's wrong and it's getting very annoying. Any ideas?

---

### Post by lingpanda on 2013-05-15
> **JnPson said:**
> When I run the command samba-tool testparm I get this error:

```
root@dc02:~# samba-tool testparm

Sorry, command-not-found has crashed! Please file a bug report at:

https://bugs.launchpad.net/command-not-found/+filebug

Please include the following information with the report:



command-not-found version: 0.2.44


```And if I run samba-tools testparm I get the same error:

```
root@dc02:~# samba-tools testparm

Sorry, command-not-found has crashed! Please file a bug report at:

https://bugs.launchpad.net/command-not-found/+filebug

Please include the following information with the report:



command-not-found version: 0.2.44
```

Samba-tools is installed and is the latest version. 

```
root@dc02:~# apt-get install samba-tools

Reading package lists... Done

Building dependency tree       

Reading state information... Done

samba-tools is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

If I try to show samba version I get:

```
root@dc02:~# Samba -V

Sorry, command-not-found has crashed! Please file a bug report at:

https://bugs.launchpad.net/command-not-found/+filebug

Please include the following information with the report:



command-not-found version: 0.2.44

root@dc02:~# samba -V

Sorry, command-not-found has crashed! Please file a bug report at:

https://bugs.launchpad.net/command-not-found/+filebug

Please include the following information with the report:



command-not-found version: 0.2.44


```

These errors is on a newly installed and updated ubuntu server. I installed it this morning together with Samba 4.0.5. 

I have no idea what's wrong and it's getting very annoying. Any ideas?



Make sure you type the complete path to the command. For example /usr/local/samba/bin/samba-tool

---

### Post by JnPson on 2013-05-16
Thanks lingpanda. That's working. But is there some way to make use of the command without the path? Like registering the path to samba-tool in that I just have to type samba-tool testparm and not /usr/local/samba/bin/samba-tool testparm? Some like of short-cut?

---

### Post by lingpanda on 2013-05-16
> **JnPson said:**
> Thanks lingpanda. That's working. But is there some way to make use of the command without the path? Like registering the path to samba-tool in that I just have to type samba-tool testparm and not /usr/local/samba/bin/samba-tool testparm? Some like of short-cut?

Yes you have to use symlinks. See this website for info.

[http://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/](http://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/)

---

### Post by JnPson on 2013-05-16
That'st great news. Thank you. I will read up on that link and try to implement it on my server.

---

### Post by lingpanda on 2013-05-16
The more I dig into the dynamic update issue with the internal DNS server the more I think its a lost cause. I don't think it's ready for production status. I think I might have to look at using bind.

---

### Post by JnPson on 2013-05-17
Toxic64 has written a nice tutorial on **[FONT=arial][SIZE=2]How to install samba 4 as an active directory domain controller[/SIZE][/FONT]** 

[http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198)

---

### Post by lingpanda on 2013-05-18
> **JnPson said:**
> Toxic64 has written a nice tutorial on How to install samba 4 as an active directory domain controller 



[http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198)



Im currently using 4 DC with 100+ users in production status. Using Windows and Ubuntu clients. I made sure to create a lenghtly tutorial for myself. +1 for Toxic's write up! It's always nice to see more tutorials out in the wild.

---

### Post by JnPson on 2013-05-19
Lingpanda: His tutorial is for samba 4.0.5. Is yours for 4.0.0 alpha18 or other versions? If so I would like to have a look too, if it's possible?

---

### Post by lingpanda on 2013-05-20
> **JnPson said:**
> Lingpanda: His tutorial is for samba 4.0.5. Is yours for 4.0.0 alpha18 or other versions? If so I would like to have a look too, if it's possible?

JnPson it was for 4.0.0. Not Alpha. It's a mash up of text from several blogs and forum posts. I take no credit for it. Let me go thru it to make sure nothing personal or confidential is in the doc and I will post. It's for Ubuntu 12.04. I find myself constantly adding to it.

As requested. "My" tutorial.

---

### Post by JnPson on 2013-05-20
Thank you. I will read it.

---

### Post by lingpanda on 2013-05-29
Looks like the DNS issue has been resolved. Posted to the Samba mail list.

> Hi, 

Here are the patches for managing SOA record from samba-tool dns command. 
There is a also a patch for bug fix #9599. 

The patches are also available in my dns-wip branch. 
[https://git.samba.org/?p=amitay/samba.git;a=shortlog;h=refs/heads/dns-wip](https://git.samba.org/?p=amitay/samba.git;a=shortlog;h=refs/heads/dns-wip)

Please review and feel free to push. 

Thanks. 

Amitay.

---

