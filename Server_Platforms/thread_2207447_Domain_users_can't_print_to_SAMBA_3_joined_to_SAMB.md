---
title: "Domain users can't print to SAMBA 3 joined to SAMBA4 AD"
date: 2014-02-23
forum: Server Platforms
---

### Post by volkswagner on 2014-02-23
Greetings,

I'd like to have domain user print to a samba3 print server.  I don't want to maintain Unix users on the SAMBA3 print server.

Print server = Ubuntu 12.04 server, SAMBA 3.6.3, following [this guide]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto").

ADS = Debian Wheezy, SAMBA4 4.1.0pre1-GIT-01f188a

From SAMBA3 I can run, getext passwd and getext group and see users and groups from AD.
I can login with smbclient and write to shares with Domain User.

I can print to shared printer from user with Unix account, but Domain Users can't print.  I do get print job written to /var/spool/samba as follows:
```
-rw------- 1 ro   domain users    0 Feb 23 14:06 smbprn..UeTZKZ

```
The print job never completes and there is no log activity.

When the Unix account prints to shared printer, similar spool is written:
```
-rw------- 1 eric domain users    0 Feb 23 14:34 smbprn..KmrIiW
```
but print job completes even with the following error in log.smbd.
```
[2014/02/23 14:34:06.438449,  0] printing/print_cups.c:940(cups_job_submit)
  cups_job_submit: failed to parse jobid from name /var/spool/samba/smbprn..KmrIiW
```

Things I have tried:[LIST]
[*]Modify idmap uid and idmap gid, inlcuding commenting it out. No change in behavior.
[*]Deleting SAMBA3 from domain and rejoining after deleting /var/lib/samba/secrets.tdb
[*]Changing valid users for printer share
[*]Set force user on [printers] share to force the unix user know to work. Spool file gets written as eric, but still does not print.
[*]set allow guest = ok on [printers] share
[*]Set CUPS config to share printers in main config and individual printer config.
[*]Comment out and uncomment password server in smb.conf (testparm throws error saying it should not be enabled with security = ADS)
[*]Set ip/hostname in /etc/hosts
[*]enabled and disabled winbind seperator
[*]Tried going the [LDAP route]("https://help.ubuntu.com/community/ActiveDirectoryHowto") with same results
[*]
[/LIST]


One thing I have not tried is changing CUPS authentication methods, or enabling Kerberos in CUPS interface.

Here is smb.conf
```
[global]
        security = ads
        realm = HOUSE.DOMAIN.COM
#        password server = 192.168.7.20
        workgroup = HOUSE
#       winbind separator = +
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
        printcap name = cups
        printing = cups
	load printers = yes	
[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = Yes
        browseable = No
	guest ok = yes
	valid users = @"Domain Users"
	force user = eric
[homes]
	valid users = %S
	writable = yes
	browseable = No
[files]
	path = /smb/files
	comment = Common Files
	browseable = yes
	writeable = yes
	valid users = @"Domain Users"

```

/etc/nsswitch.conf
```
# /etc/nsswitch.conf
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4
networks:       files dns
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

```

/etc/pam.d/common-auth
```
#
auth	[success=3 default=ignore]	pam_unix.so nullok_secure
auth	[success=2 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth	[success=1 default=ignore]	pam_ldap.so use_first_pass
auth	requisite			pam_deny.so
auth	required			pam_permit.so

```

/etc/pam.d/common-account
```
account	[success=3 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=2 new_authtok_reqd=done default=ignore]	pam_winbind.so 
account	[success=1 default=ignore]	pam_ldap.so 
account	requisite			pam_deny.so
account	required			pam_permit.so

```

I appreciate any help or testimonials that this does or does not work.

---

### Post by volkswagner on 2014-02-24
I have narrowed down the problem to Mac OSX clients. 

Windows clients can print to the SAMBA3 printer.  Print jobs get written the same way to /var/spool/samba.

The following was captured during print job sent from windows 7 joined computer.
```
-rw------- 1 ro   domain users 0 Feb 24 21:17 smbprn.00000002.6eHEGj
```

The above prints but the following generated from OSX never gets sent to CUPS.
-rw------- 1 ro   domain users 0 Feb 24 21:05 smbprn..MG6V4i

Perhaps there is a compatibility issue from OSX SAMBA version
```
Version 3.0.28a-apple
```

I just successfully printed from a domain user on OSX 10.7.3.  I could not find the smbd version on OSX 10.7 as I could on 10.6.8.
The same Mac can print to SAMBA Version 3.4.7.  Perhaps some where between Version 3.4.7 and Version 3.6.3 there is a problem for the older Mac client.

I hit this stumbling block so early.  My workstation is the OSX 10.6.8.  When I found shares were working but printing was not, I did not even think to setup the Windows clients!

I'll mark this thread solved once battle tested.

---

