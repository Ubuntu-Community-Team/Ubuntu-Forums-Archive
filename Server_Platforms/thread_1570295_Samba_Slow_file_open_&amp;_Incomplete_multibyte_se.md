---
title: "Samba: Slow file open &amp; Incomplete multibyte sequence error"
date: 2010-09-08
forum: Server Platforms
---

### Post by EXJ on 2010-09-08
I also posted this issue [**over at launchpad**]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/631383"). Im hoping to possibly find a solution (if its my id10t error or a samba bug)

Thanks in advance for any assistance you can render.

-----------------------------------

Description: Ubuntu 10.04.1 LTS
Release:	10.04
Samba version 3.4.7

The Setup & The problem:

We are running Windows 2008 R2 acting as a AD server. We are using SAMBA as a fileserver authenticating off of the AD server.
We are a company situated within Asia, as such most of our files are in either Japanese, Korean, or Chinese.

Everything is running nicely execpt for:

The SAMBA server might take up to 30seconds to open a binary file (mostly msword docs, but some photoshop files as well from a windows workstation.) This *does not* occur when I access the shares from my linux (ubuntu) workstation.

This error keeps showing up in the logs:

[2010/09/06 12:52:31, 3] lib/charcnv.c:242(convert_string_internal)
convert_string_internal: Conversion error: Incomplete multibyte sequence(&#65533;&#65533;&#12488;_20091125.xls)

Our smb.conf (information erased to protect the innocent)
As I thought the problem was related to optlocks, apparently it had no effect.

[global]
        workgroup = OOOOO
        realm = OOOOO
        server string = OOOO
        security = ADS
        password server = OOOO
        restrict anonymous = 2
        client NTLMv2 auth = Yes
        log level = 3
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 10000
        unix extensions = No
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        template homedir = OOOO
        template shell = /bin/bash
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        veto files = /Thumbs.db/
        oplocks = No
        level2 oplocks = No
        wide links = Yes

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0664
        force create mode = 0664
        force security mode = 0664
        directory mask = 0775
        force directory mode = 0755
        hide dot files = No
        browseable = No
        browsable = No

---

