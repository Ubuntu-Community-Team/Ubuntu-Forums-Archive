---
title: "Samba / winbindd errors"
date: 2010-01-17
forum: Server Platforms
---

### Post by cmay4 on 2010-01-17
I just completed a fresh install of 9.10 and want to get an exteremely simple public shared directory accessible from my Windows machines.  I set up Samba after looking a numerous threads and it actually works perfectly.  Below is my smb.conf.  The only issue I am having is that every 30 minutes the syslog is filled with a bunch of winbindd errors.  I've listed a snittped of the syslog below.  

Has anyone seen this or have a suggestions as to where I can look?  As I said, everything *seems* to work correctly, but I'd like to figure out these log messages.

Thanks!

```
[global]
netbios name = homer
workgroup = WORKGROUP
preferred master = no
local master = no
domain master = no
security = share
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
map to guest = bad user
guest account = smbguest
wins support = no
create mask = 0666
directory mask = 0777
load printers = no
syslog = 1
syslog only = yes

[public]
path = /home/public
guest ok = yes
read only = no
``````
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jan 17 15:24:39 homer winbindd[9227]:   idmap_alloc module tdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module passdb already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap.c:149(smb_register_idmap)
Jan 17 15:24:39 homer winbindd[9227]:   Idmap module nss already registered!
Jan 17 15:24:39 homer winbindd[9227]: [2010/01/17 15:24:39,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jan 17 15:24:39 homer winbindd[9227]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
```

---

### Post by juun on 2010-01-22
i've the same issue. :( somebody an idea?

greez

---

### Post by martinveasey on 2010-02-05
I also get this. HELP !

---

### Post by huuan on 2010-02-08
and me too... everything seems to work but it would be nice to figure why these error messages keep popping up.

ubuntu 9.10 server
Samba 2:3.4.0-3ubuntu5.4 SMB/CIFS file, print, and login server
libwbclient0  2:3.4.0-3ubuntu5.4  Samba winbind client library
winbind  2:3.4.0-3ubuntu5.4 Samba nameservice integration server

The plot thickens: I see from
[http://ftp2.pl.freebsd.org/pub/Samba/GIT/source3/winbindd/idmap_tdb.c](http://ftp2.pl.freebsd.org/pub/Samba/GIT/source3/winbindd/idmap_tdb.c).
that this is where the error message comes from:

<code>
	/* check against earlier versions */
	version = dbwrap_fetch_int32(db, "IDMAP_VERSION");
	if (version != IDMAP_VERSION) {
		if (config_error) {
			DEBUG(0,("Upgrade of IDMAP_VERSION from %d to %d is not "
				 "possible with incomplete configuration\n",
				 version, IDMAP_VERSION));
			ret = NT_STATUS_UNSUCCESSFUL;
			goto done;
		}
</code>

Perhaps the version is not being set somewhere...klike in some config file

---

### Post by capscrew on 2010-02-08
> **huuan said:**
> and me too... 

...everything seems to work but it would be nice to figure why these error messages keep popping up.


I'm not altogether sure you need Winbind at all.  The OP for sure does not need the use of Winbind.  Winbind is for integration into a Windows 2000 or later AD system.  Is you network an AD domain?

I have a network successfully using 2 Samba servers with Ubuntu, Windows XP and Vista clients.  This is not an AD domain but rather a *workgroup *environment with all shares using *"security=user"*.  I don't run Winbind at all.

Can you describe your situation a little more fully?

---

### Post by huuan on 2010-02-10
> **capscrew said:**
> I'm not altogether sure you need Winbind at all.  The OP for sure does not need the use of Winbind.  Winbind is for integration into a Windows 2000 or later AD system.  Is you network an AD domain?

I have a network successfully using 2 Samba servers with Ubuntu, Windows XP and Vista clients.  This is not an AD domain but rather a *workgroup *environment with all shares using *"security=user"*.  I don't run Winbind at all.

Can you describe your situation a little more fully?

Sure.
I think I do need AD as the server is part of an AD domain and uses windbind, kerberos and ldap to authenticate for SAMBA.

That's my understanding of what winbindd is for, from man winbindd:
NAME
       winbindd - Name Service Switch daemon for resolving names from NT servers

SYNOPSIS
       winbindd [-D] [-F] [-S] [-i] [-Y] [-d <debug level>] [-s <smb config file>] [-n]

DESCRIPTION
       This program is part of the samba(7) suite.

...
FILES
       /etc/nsswitch.conf(5)
           Name service switch configuration file.


and here's my nsswitch.conf:
# /etc/nsswitch.conf

passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
----------------------------

It's clear to me from the error message and the code snippet that I posted earlier that the error message has to do with some kind of config setting that is missing. But where the tag is set I can't figure out. I have searched all over for 'IDMAP_VERSION' in all the help and man but there is no mention of it, must be called something else or not documented. I don't have the source for samba downloaded so I can only see that flag from googling for now.

---

### Post by nyktovus on 2010-11-24
so if winbind isnt needed to function properly, is there a way to disable it? i'm having a sh*tstorm of issues on a server, i cant tell if its samba, or the eth card, the network.. something is causing this puppy to freeze up.. i even lose keyboard control when it happens. 

help!

---

### Post by capscrew on 2010-11-24
> **nyktovus said:**
> so if winbind isnt needed to function properly, is there a way to disable it? i'm having a sh*tstorm of issues on a server, i cant tell if its samba, or the eth card, the network.. something is causing this puppy to freeze up.. i even lose keyboard control when it happens. 

help!
Then remove it ```
sudo apt-get purge winbind
```

This assumes you are not part of a Windows Active Directory domain.

---

### Post by huuan on 2010-11-24
I removed winbind some time back as it wasn't working as it should plus it works real slow when you have lots of users on AD in my case >30,000. Takes hours to sync.
TIGO on the samba list has suggested a way around this but I have not had a chance to test his solution yet.

Authenticating using AD credentials via kerberos and ldap only works a treat. The downside of this for me is that on AD without winbind you can't set ACL permissions from windows but everything else works just fine.

---

### Post by capscrew on 2010-11-24
> **huuan said:**
> I removed winbind some time back as it wasn't working as it should plus it works real slow when you have lots of users on AD in my case >30,000. Takes hours to sync.
TIGO on the samba list has suggested a way around this but I have not had a chance to test his solution yet.

Authenticating using AD credentials via kerberos and ldap only works a treat. The downside of this for me is that on AD without winbind you can't set ACL permissions from windows but everything else works just fine.

Winbind does not provide authentication.  All it does is map AD users to unix users on the Samba box.  As you say; in your situation you the only thing you can't do is set the perms on your file structure.  To my way of thinking this is a show stopper.

---

### Post by g4m3c4ck on 2011-02-09
I am running into the same issue I will try purging winbindd

---

### Post by freemant on 2013-03-25
Just set "idmap backend = tdb2" in /etc/samba/smb.conf and it will fix the problem.

---

