---
title: "Samba4 AD DC and Folder Redirection: corrupted Word-documents"
date: 2013-10-05
forum: Server Platforms
---

### Post by bouke-d on 2013-10-05
Hi all,

I got Samba4 running for a couple of months right now. I started with version 4.0.6 and now I am at 4.0.9.

Everything runs like a charm except one thing: sometimes Word-documents  get corrupted. This happens when they are opened/edited for several  hours.

I suspect that this issue has to do with folder redirection and the users temp files.

I already tried some things:
[LIST]
[*]smb.conf > [global] > added: **kernel** **oplocks = no**
[*]smb.conf > share [profiles] > added: **blocking locks = no**
[*]smb.conf > share [profiles] > added: **veto oplock files = /*.doc*/*.DOC*/*.xls*/*.XLS*/*.txt/*.TXT/*.log/*.LOG/*.csv/*.CSV/*.*-ms/*.*-MS/**
[/LIST]

I also created a policy that adds a registry key:
**REG ADD HKLM\Software\Microsoft\Windows\CurrentVersion\NetCache /v RoundUpWriteTimeOnSync /t REG_DWORD /d 00000001 /f**

Well... that didn't work... so next I tried the following:
[LIST]
[*]smb.conf > share [profiles] > added: **oplocks = no**
[*]smb.conf > share [profiles] > added: **level2 oplocks = no**
[/LIST]

But this did not solve the issue.

There are oplock-aerrors in my log.smbd. Is there any way to solve this  issue. Maybe somebody has seen this problem before and knows the answer?
As a last resort I could disable locks and oplocks permenently... but I do not know if this would be wise.

I checked the whole route: cables, switches, router, network adapters. Everything seems to be fine...
The workstation is a laptop with a new SSD.

This is an example of an error:

```

[2013/09/26 08:56:54.058490,  0] ../source3/smbd/oplock.c:333(oplock_timeout_handler)
  Oplock break failed for file S01D02/WPKG-s01d02-2013-09-26.log -- replying anyway

```

This is my smb.conf file:

```

[global]
        workgroup = TH01
        realm = TH01.INET
        netbios name = COMSRV01A
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
        guest account = nobody
        map to guest = bad user
        #printing = cups
        #printcap name = cups
        kernel oplocks = no

[netlogon]
        path = /opt/samba/var/locks/sysvol/th01.inet/scripts
        read only = No

[sysvol]
        path = /opt/samba/var/locks/sysvol
        read only = No

[profiles]
        comment = Profiles
        path = /data/profiles
        browsable = no
        read only = no
        writable = yes
        directory mask = 0700
        create mask = 0600
        #
        # oplocks are disabled for this share
        #
          oplocks = no
          level2 oplocks = no
        #
        # 'blocking locks' set to 'no' for Word documents
        #
          blocking locks = no
        #
        # do not oplock the following files
        #
          veto oplock files = /*.doc*/*.DOC*/*.xls*/*.XLS*/*.txt/*.TXT/*.log/*.LOG/*.csv/*.CSV/*.*-ms/*.*-MS/

[pdf-prints]
        comment = PDF Files
        path = /data/pdf
        browsable = yes
        read only = no
        writable = yes
        directory mask = 0775
        create mask = 0664
[wpkg]
        comment = Software Deployment
        path = /opt/wpkg
        browsable = no
        read only = no
        write list = 3000000,administrator,root
        directory mask = 0755
        create mask = 0644
        guest ok = yes
        strict locking = no
        oplocks = no
        blocking locks = no
        veto oplock files = /*.log/*.LOG/

[packages]
        comment = Software Packages
        path = /extra/packages
        browsable = no
        read only = no
        write list = 3000000,administrator,root
        create mask = 0644
        directory mask = 0755
        guest ok = yes

[wsus]
        comment = WSUS
        path = /extra/wsus
        browsable = no
        read only = no
        writelist = 3000000,administrator,root
        create mask = 0644
        directory mask = 0755
        guest ok = yes

[log]
        comment = Log Files
        path = /data/log
        browsable = no
        read only = no
        force create mode = 0664
        force directory mode = 0775
        guest ok = yes

[printers]
   comment = All Printers
   path = /opt/samba/var/spool
   browsable = no
   public = yes
   guest ok = yes
   writable = no
   printable = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /opt/samba/lib/printers
   browseable = yes
   guest ok = no
   read only = yes
   write list = root

```

---

