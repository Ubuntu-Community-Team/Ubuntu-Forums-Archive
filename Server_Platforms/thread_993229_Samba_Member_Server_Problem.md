---
title: "Samba Member Server Problem"
date: 2008-11-25
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2008-11-25
Whenever I restart my samba servers the member server refuses to  authenticate users. Sometimes is will only authenticate some users on  some shares. Usually by fiddling with it I can eventually get it to work  but I can't identify the solution so I can replicate it. Once it finally starts to work it works fine until the next restart.

"fiddling with it" means that I run a bunch of commands to try to identify the problem and restarting the processes on the two servers. It eventually starts working. I haven't been able identify which command actually causes the system to start working. It doesn't appear to be the same one every time. For example sometimes "net rpc join" seems to work, but not this time.

Users on the XP machines can browse the network and see the Domain, both servers and all of the shares on either server. They can access shares on the PDC with no problem. When they attempt to access the shares on the Member Server sometimes they get a user/password window and no combination of user and password is accepted.

I'm completely stumped, which isn't hard. This is driving me nuts.

Among other commands I have run;

wbinfo -u and -g  get what I expect, alist of users and groups
net status shares returns a list of shares
net status  sessions return a list of sessions
getent passwd lists the domain users
getent group lists the groups including the domain groups
netlookup dc returns the correct ip address
netlookup master returns the correct ip address

Here is a log of one of the failed connections;

[2008/11/25 12:50:57, 3] smbd/process.c:switch_message(927)
 switch message SMBtconX (pid 7447) conn 0x0
[2008/11/25 12:50:57, 3] smbd/sec_ctx.c:set_sec_ctx(241)
 setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/25 12:50:57, 3] lib/access.c:check_access(312)
 check_access: no hostnames in host allow/deny list.
[2008/11/25 12:50:57, 2] lib/access.c:check_access(323)
 Allowed connection from  (192.168.1.9)
[2008/11/25 12:50:57, 3] smbd/sec_ctx.c:push_sec_ctx(208)
 push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/25 12:50:57, 3] smbd/uid.c:push_conn_ctx(358)
 push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/25 12:50:57, 3] smbd/sec_ctx.c:set_sec_ctx(241)
 setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/25 12:50:57, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
 pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/25 12:50:57, 3] smbd/service.c:find_forced_group(525)
 Forced group samba
[2008/11/25 12:50:57, 3] smbd/service.c:make_connection_snum(806)
 Connect path is '/files/Lucretia/Sigma' for service [Sigma]
[2008/11/25 12:50:57, 3] lib/util_seaccess.c:se_access_check(250)
[2008/11/25 12:50:57, 3] lib/util_seaccess.c:se_access_check(251)
 se_access_check: user sid is S-1-5-21-4166445610-3302986456-3838465043-3066
 se_access_check: also S-1-22-2-2003
 se_access_check: also S-1-5-2
 se_access_check: also S-1-5-11
[2008/11/25 12:50:57, 3] lib/util_seaccess.c:se_access_check(250)
[2008/11/25 12:50:57, 3] lib/util_seaccess.c:se_access_check(251)
 se_access_check: user sid is S-1-5-21-4166445610-3302986456-3838465043-3066
 se_access_check: also S-1-22-2-2003
 se_access_check: also S-1-5-2
 se_access_check: also S-1-5-11
[2008/11/25 12:50:57, 0] smbd/service.c:make_connection_snum(850)
 make_connection: connection to Sigma denied due to security descriptor.
[2008/11/25 12:50:57, 3] smbd/error.c:error_packet_set(106)
 error packet at smbd/reply.c(514) cmd=117 (SMBtconX) NT_STATUS_ACCESS_DENIED
[2008/11/25 12:51:08, 3] smbd/process.c:process_smb(1069)
 Transaction 173 of length 43
[2008/11/25 12:51:08, 3] smbd/process.c:switch_message(927)
 switch message SMBulogoffX (pid 7447) conn 0x0


If any other information would help let me know.

Here is my configuration.

Ubuntu 8.04 LTS AMD 64
Samba Version 3.0.28a

I have an NT style domain with XP pro desktops.
1 -PDC
1- Member Server
No AD No LDAP

On the PDC smbd and nmbd are unning
On the Member Server smbd nmbd and winbind are running.

Here is part of nsswitch.con;

passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind


Here is the Globals Section of the PDC

[global]
       workgroup = ATLANTA
       server string = %h mail passwd server (Samba, Ubuntu)
       passdb backend = tdbsam
       passwd program = /usr/bin/passwd %u
       passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
       syslog = 0
       log file = /var/log/samba/log.%m
       max log size = 1000
       time server = Yes
       hostname lookups = Yes
       logon path = \\THELMA\%U\.profiles
       logon drive = U:
       logon home = \\THELMA\%U
       domain logons = Yes
       domain master = Yes
       preferred master = Yes
       security = user

Here is the Globals for the Member Server

[global]
       workgroup = ATLANTA
       server string = %h file server (Samba, Ubuntu)
       security = domain
       password server = 192.168.1.24
       log level = 3
       syslog = 0
       log file = /var/log/samba/log.%m
       max log size = 1000
       wins proxy = yes
       wins server = 192.168.1.24
       panic action = /usr/share/samba/panic-action %d
       idmap uid = 10000-20000
       idmap gid = 10000-20000
       template shell = /bin/bash
       name resolve order = wins bcast hosts
       hosts allow = 192.168.1.0/255.255.255.0
       winbind enum groups = yes
       winbind enum users = yes

Here are two shares one worked and one didn't last time.

[Projects]
       path = /files/Lucretia/Projects
       comment = Project Specific Data
       force group = samba
       read only = no
       create mask = 0764
       directory mask = 0775

[Office]
       comment = General Office Data
       path = /files/Lucretia/Office
       force group = samba
       read only = No
       create mask = 0764
       directory mask = 0775

This time neither work but this one does.

[Vault]
       comment = Ancient Files
       path = /files/Vault

All directories have the same ownership and linux permissions

drwxrwsr-x  69 rob  samba 16416 2008-10-24 17:15 Office
drwxrwsr-x  51 rob  samba  4032 2008-11-12 09:43 Projects

drwxrwsr-x 24 rob    samba       688 2008-06-11 12:01 Vault

---

### Post by Coreigh on 2008-11-25
Could it be that the processes are starting to early or that the SDC needs to start *AFTER* the PDC? What I am suggesting is a complete shot in the dark but along the lines of things that have worked for me before.

Configure the PDC to delay the start of domain services for a few seconds after boot up. And then the SDC to start services after the PDC is up and running. Further more it is probably important the order in which Samba, bind and LDAP (and kerberos if used) start up.

I am sorry I don't have any direct experience with Samba as a domain controller (its on my todo list) but as I said this kind of thinking has been successful for me in other areas.

---

### Post by rsteinmetz70112 on 2008-11-25
I have tried restarting the services manually and sometimes it seems to work and sometimes not. If there is a magic order I haven't found it.

If there is it seem to be start the PDC, which runs smbd and nmbd, both of which seems to be working fine. Then start the Member Server. I'm not sure if winbind should be started before the samba daemons, but I've tried it both ways.  wonder if 

The problem seem to be with winbind not being able to properly authenticate users.

Since we have only a few users we are not running LDAP, bind or any other services which would be involved in user authentication.

---

### Post by rsteinmetz70112 on 2008-11-25
I have now upgraded from 8.04 to 8.10 and am having the same problem. I'm sure it's a configuration issue somewhere but I'm stumped.

---

