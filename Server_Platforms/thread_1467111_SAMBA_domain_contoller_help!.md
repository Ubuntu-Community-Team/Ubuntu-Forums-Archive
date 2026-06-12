---
title: "SAMBA domain contoller help!"
date: 2010-04-30
forum: Server Platforms
---

### Post by BarryDocks on 2010-04-30
I am trying to setup samba as a PDC, followed this guide:
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2556806]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2556806")
Also looked at:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html#id2654460]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html#id2654460")
XP clients are not able to log on to the domian, with a bad user name or password error.

Also have the following errors in the syslog:
```
Apr 30 19:59:11 Server64 nmbd[6772]: [2010/04/30 19:59:11, 0] nmbd/nmbd_logonnames.c:add_logon_names(163) 
Apr 30 19:59:11 Server64 nmbd[6772]:   add_domain_logon_names: 
Apr 30 19:59:11 Server64 nmbd[6772]:   Attempting to become logon server for workgroup WORKGROUP on subnet 192.168.1.2 
Apr 30 19:59:11 Server64 nmbd[6772]: [2010/04/30 19:59:11, 0] nmbd/nmbd_logonnames.c:add_logon_names(163) 
Apr 30 19:59:11 Server64 nmbd[6772]:   add_domain_logon_names: 
Apr 30 19:59:11 Server64 nmbd[6772]:   Attempting to become logon server for workgroup WORKGROUP on subnet 10.10.64.1 
Apr 30 19:59:11 Server64 nmbd[6772]: [2010/04/30 19:59:11, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(290) 
Apr 30 19:59:11 Server64 nmbd[6772]:   become_domain_master_browser_bcast: 
Apr 30 19:59:11 Server64 nmbd[6772]:   Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.1.2 
Apr 30 19:59:11 Server64 nmbd[6772]: [2010/04/30 19:59:11, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(303) 
Apr 30 19:59:11 Server64 nmbd[6772]:   become_domain_master_browser_bcast: querying subnet 192.168.1.2 for domain master browser on workgroup WORKGROUP 
Apr 30 19:59:11 Server64 nmbd[6772]: [2010/04/30 19:59:11, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(290) 
Apr 30 19:59:11 Server64 nmbd[6772]:   become_domain_master_browser_bcast: 
Apr 30 19:59:11 Server64 nmbd[6772]:   Attempting to become domain master browser on workgroup WORKGROUP on subnet 10.10.64.1 
Apr 30 19:59:11 Server64 nmbd[6772]: [2010/04/30 19:59:11, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(303) 
Apr 30 19:59:11 Server64 nmbd[6772]:   become_domain_master_browser_bcast: querying subnet 10.10.64.1 for domain master browser on workgroup WORKGROUP 
Apr 30 19:59:11 Server64 winbindd[6353]: [2010/04/30 19:59:11, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Apr 30 19:59:11 Server64 winbindd[6353]:   ERROR: Initialization failed for alloc backend, deferred! 
Apr 30 19:59:11 Server64 smbd[6774]: [2010/04/30 19:59:11, 0] auth/auth_util.c:create_builtin_administrators(792) 
Apr 30 19:59:11 Server64 smbd[6774]:   create_builtin_administrators: Failed to create Administrators 
Apr 30 19:59:11 Server64 winbindd[6353]: [2010/04/30 19:59:11, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Apr 30 19:59:11 Server64 winbindd[6353]:   ERROR: Initialization failed for alloc backend, deferred! 
Apr 30 19:59:11 Server64 smbd[6774]: [2010/04/30 19:59:11, 0] auth/auth_util.c:create_builtin_users(758) 
Apr 30 19:59:11 Server64 smbd[6774]:   create_builtin_users: Failed to create Users 
Apr 30 19:59:11 Server64 winbindd[6353]: [2010/04/30 19:59:11, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Apr 30 19:59:11 Server64 winbindd[6353]:   ERROR: Initialization failed for alloc backend, deferred! 
Apr 30 19:59:11 Server64 smbd[6774]: [2010/04/30 19:59:11, 0] auth/auth_util.c:create_builtin_administrators(792) 
Apr 30 19:59:11 Server64 smbd[6774]:   create_builtin_administrators: Failed to create Administrators 
Apr 30 19:59:11 Server64 winbindd[6353]: [2010/04/30 19:59:11, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Apr 30 19:59:11 Server64 winbindd[6353]:   ERROR: Initialization failed for alloc backend, deferred! 
Apr 30 19:59:11 Server64 smbd[6774]: [2010/04/30 19:59:11, 0] auth/auth_util.c:create_builtin_users(758) 
Apr 30 19:59:11 Server64 smbd[6774]:   create_builtin_users: Failed to create Users 
Apr 30 19:59:15 Server64 nmbd[6772]: [2010/04/30 19:59:15, 0] nmbd/nmbd_logonnames.c:become_logon_server_success(124) 
Apr 30 19:59:15 Server64 nmbd[6772]:   become_logon_server_success: Samba is now a logon server for workgroup WORKGROUP on subnet 192.168.1.2 
Apr 30 19:59:15 Server64 nmbd[6772]: [2010/04/30 19:59:15, 0] nmbd/nmbd_logonnames.c:become_logon_server_success(124) 
Apr 30 19:59:15 Server64 nmbd[6772]:   become_logon_server_success: Samba is now a logon server for workgroup WORKGROUP on subnet 10.10.64.1 
Apr 30 19:59:19 Server64 nmbd[6772]: [2010/04/30 19:59:19, 0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(113) 
Apr 30 19:59:19 Server64 nmbd[6772]:   ***** 
Apr 30 19:59:19 Server64 nmbd[6772]:    
Apr 30 19:59:19 Server64 nmbd[6772]:   Samba server SERVER64 is now a domain master browser for workgroup WORKGROUP on subnet 192.168.1.2 
Apr 30 19:59:19 Server64 nmbd[6772]:    
Apr 30 19:59:19 Server64 nmbd[6772]:   ***** 
Apr 30 19:59:19 Server64 nmbd[6772]: [2010/04/30 19:59:19, 0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(113) 
Apr 30 19:59:19 Server64 nmbd[6772]:   ***** 
Apr 30 19:59:19 Server64 nmbd[6772]:    
Apr 30 19:59:19 Server64 nmbd[6772]:   Samba server SERVER64 is now a domain master browser for workgroup WORKGROUP on subnet 10.10.64.1 
Apr 30 19:59:19 Server64 nmbd[6772]:    
Apr 30 19:59:19 Server64 nmbd[6772]:   ***** 

```

Current smb.conf:
```
[global]
	passdb backend = tdbsam
	printcap name = cups
	add user script = /usr/sbin/useradd -m %u
	delete user script = /usr/sbin/userdel -r %u
	add group script = /usr/sbin/groupadd %g
	delete group script = /usr/sbin/groupdel %g
	add user to group script = /usr/sbin/groupmod -A %u %g
	delete user from group script = /usr/sbin/groupmod -R %u %g
	add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
	logon script = scripts\logon.bat
	logon path = \\%L\Profiles\%U
	logon drive = H:
	logon home = \\%L\%U
	domain logons = Yes
	os level = 65
	preferred master = Yes
	domain master = Yes
	idmap uid = 15000-20000
	idmap gid = 15000-20000

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printer admin = root, system
	create mask = 0600
	guest ok = Yes
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers Share
	path = /var/lib/samba/drivers
	write list = system, root
	printer admin = system, root

[netlogon]
	comment = Roaming Profile Share
	path = /var/lib/samba/netlogon
	admin users = root, system
	guest ok = Yes
	browseable = No
root@Server64:~# 

```

Any suggestions very welcome!!

---

### Post by BarryDocks on 2010-05-01
A bit more information, I removed samba and winbind and then reinstalled them.  The errors in the smbd log when starting samba are: 
```
[2010/04/30 23:28:25, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2010/04/30 23:30:28, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2010/04/30 23:30:28, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 544 (NT_STATUS_UNSUCCESSFUL)
[2010/04/30 23:30:28, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2010/04/30 23:30:28, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 545 (NT_STATUS_UNSUCCESSFUL)
[2010/04/30 23:30:28, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```
I think this is likely to be a permissions problem but don't know where to look?:confused:

---

### Post by tenmoi on 2010-05-01
I'm also a newbie to samba. But I think your smb.conf lacks these vital lines:
Workgroup =
Netbios name = 

And may I recommend you to use samba4. There's a, well, less-than excellent howto on the web. Just google it. I have set up a Samba4 AD and can join both Windows and Ubuntu clients to it. 

If you did, I think you would get rid of having to administer 2 user account databases.

Regards.

---

### Post by BarryDocks on 2010-05-01
> **tenmoi said:**
> I'm also a newbie to samba. But I think your smb.conf lacks these vital lines:
Workgroup =
Netbios name = 
yep, you are probably right, when I posted the message I had been working on the problem all day and couldn't see the wood for the trees.

I am about to upgrade to ubuntu 10 and so will expect samba v4 to be installed with that?

Have you configured the AD using DNS or winbind?

---

### Post by tenmoi on 2010-05-01
Here's the link: [http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

You'd better compile samba4. I once installed samba4 from the repo but you would not have the choice to provision.

of course, if you compile from source you do not use winbind. you'll have to configure bind9. 

And if you go the compilation way and get stuck at step 8 of the howto, post here and I will help.

Regards.

---

### Post by BarryDocks on 2010-05-02
> **tenmoi said:**
> Here's the link: [http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

You'd better compile samba4. I once installed samba4 from the repo but you would not have the choice to provision.

of course, if you compile from source you do not use winbind. you'll have to configure bind9. 

And if you go the compilation way and get stuck at step 8 of the howto, post here and I will help.

Regards.

Thanks for this, I now have a working dns set up, but after looking at the smaba4 how to will probably need some help!!

I also added the workgruop and netbios name line to my smb but still no luck.  I am still getting the following errors in the smbd log:
```
[2010/05/02 09:06:00, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2010/05/02 09:06:00, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 544 (NT_STATUS_UNSUCCESSFUL)
[2010/05/02 09:06:00, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2010/05/02 09:06:00, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 545 (NT_STATUS_UNSUCCESSFUL)
[2010/05/02 09:06:00, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2010/05/02 09:06:00, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 544 (NT_STATUS_UNSUCCESSFUL)
[2010/05/02 09:06:00, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2010/05/02 09:06:00, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 545 (NT_STATUS_UNSUCCESSFUL)
[2010/05/02 09:06:00, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

```

Interestingly if I revert back to my old smb.conf (with no PDC configuration) I still get the same errors.  I also had a look at the server in my office which doesn't have winbind installed and these errors are not apparent.  Clearly it's a winbind/permissions issue but I don't have a clue where to look:confused:

Thanks

---

### Post by tenmoi on 2010-05-03
Dear BD,

I don't know if you have any background on samba. Should you have followed the howto "blindly", I do not think you'd go anywhere.

You know, you'll have to add the [COLOR="Red"]linux[/COLOR] admin groups and admin users, then add separate [COLOR="Red"]samba[/COLOR] ones. Your server would then be in a mess.

[HTML]create_builtin_administrators: Failed to create Administrators[/HTML]

You see, you have not created the corresponding linux admin group for your samba admin.

I once set up a PDC using samba3 with an ldap backend, but I dropped it long ago.

You said you have a working DNS (bind9) server on your Ubuntu server, then I recommend setting up an AD server using samba4. It would take you 1 hour (30' to git pull the source code + 20' to compile and the rest to join a WIndows client and Ubuntu).

Please do! alpha does not mean bad with samba4. It is working extremly well for me.

Follow the howto in the previous link. When you get to step 8, open the *.zone file in /usr/local/samba/private/dns, go to the line starting with "gc ......." and highlight from there till the end. Copy and append the highlighted passage to your forward-mapping zone file (not the reverse mapping zone file!). 
Make sure "bind"  can read the dns.keytab, named.conf.update files ( chown it was what I did)

Then follow exactly what the howto instructs.

Joining an Ubuntu client to this AD is a little involved. So if you are interested in doing it, just ask here.

Regards,

---

### Post by BarryDocks on 2010-05-17
> **tenmoi said:**
> Dear BD,

I don't know if you have any background on samba. Should you have followed the howto "blindly", I do not think you'd go anywhere.

You know, you'll have to add the [COLOR="Red"]linux[/COLOR] admin groups and admin users, then add separate [COLOR="Red"]samba[/COLOR] ones. Your server would then be in a mess.

[HTML]create_builtin_administrators: Failed to create Administrators[/HTML]

You see, you have not created the corresponding linux admin group for your samba admin.

I once set up a PDC using samba3 with an ldap backend, but I dropped it long ago.

You said you have a working DNS (bind9) server on your Ubuntu server, then I recommend setting up an AD server using samba4. It would take you 1 hour (30' to git pull the source code + 20' to compile and the rest to join a WIndows client and Ubuntu).

Please do! alpha does not mean bad with samba4. It is working extremly well for me.

Follow the howto in the previous link. When you get to step 8, open the *.zone file in /usr/local/samba/private/dns, go to the line starting with "gc ......." and highlight from there till the end. Copy and append the highlighted passage to your forward-mapping zone file (not the reverse mapping zone file!). 
Make sure "bind"  can read the dns.keytab, named.conf.update files ( chown it was what I did)

Then follow exactly what the howto instructs.

Joining an Ubuntu client to this AD is a little involved. So if you are interested in doing it, just ask here.

Regards,

Thank you for your help, I have only really been using linux of any sort for the last 12 months or so and so I am still on a very steep learning curve!!

I plan on trying samba4 with lucid on my spare machine first, probably at the beginning of next month.  Please keep an eye on this thread as I will surely need some help.

---

### Post by BarryDocks on 2010-06-25
One quick question: will samba4 act as a print server?  I have read in several places that function is not yet available?
Thanks

---

