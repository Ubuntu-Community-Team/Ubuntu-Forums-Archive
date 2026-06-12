---
title: "windows 7 joinging samba domain help"
date: 2012-06-30
forum: Server Platforms
---

### Post by korenje on 2012-06-30
Hi. I am trying to join windows 7 to samba domain. I read everything and I can't make it work...

I can join domain in linux. It normally creates another user$ on the system, depending on computer netbios name.

This is what I get in log when I connect in linux to samba domain:

>   check_ntlm_password:  authentication for user [korenje] -> [korenje] -> [korenje] succeeded
[2012/06/30 17:41:46.205503,  2] rpc_server/samr/srv_samr_nt.c:4071(_samr_LookupDomain)
  Returning domain sid for domain THE-NOX.COM -> S-1-5-21-10560820-41971740-2138972874
[2012/06/30 17:41:46.634807,  2] auth/auth.c:309(check_ntlm_password)
  check_ntlm_password:  authentication for user [NOX$] -> [NOX$] -> [nox$] succeeded
[2012/06/30 17:41:46.640577,  2] rpc_server/samr/srv_samr_nt.c:4071(_samr_LookupDomain)
  Returning domain sid for domain THE-NOX.COM -> S-1-5-21-10560820-41971740-2138972874


This is what I get if I try to connect through windows:
> [2012/06/30 17:50:57.305564,  2] auth/auth.c:309(check_ntlm_password)
  check_ntlm_password:  authentication for user [korenje] -> [korenje] -> [korenje] succeeded
[2012/06/30 17:51:13.139451,  1] smbd/process.c:457(receive_smb_talloc)
  receive_smb_raw_talloc failed for client 192.168.0.11 read error = NT_STATUS_CONNECTION_RESET.


My samba config file:

```
[global]
        netbios name = nox
        workgroup = the-nox.com

        lanman auth = no
        ntlm auth = yes
        client lanman auth = no
        client plaintext auth = no
        client ntlmv2 auth = yes
        encrypt passwords = yes
        obey pam restrictions = yes

        passdb backend = smbpasswd

        os level = 33
        preferred master = yes
        domain master = yes
        local master = yes
        wins support = yes
        name resolve order = wins lmhosts host bcast
        dns proxy = no
        security = ads
        interfaces = eth0 eth1 eth2 lo
        bind interfaces only = yes

* * * * add user script = /usr/sbin/useradd -m %u
* * * * delete user script = /usr/sbin/userdel -r %u
* * * * add group script = /usr/sbin/groupadd %g
* * * * delete group script = /usr/sbin/groupdel %g
* * * * delete user from group script = /usr/sbin/groupmod -R %u %g
* * * * add user to group script = /usr/sbin/usermod -A %u %g
* * * * add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null -g machines %u
* * * * invalid users = root
* * * * passwd program = /usr/bin/passwd %u
* * * * passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n

        domain logons = yes
        logon path = \\%N\profile\%U
        logon drive = M:
        logon home = \\%N\%U
        logon script = logon.cmd

        hide dot files = yes
        hide unreadable = yes
        nt acl support = no

[profile]
    comment = User profiles
    path = /srv/samba/profile
    oplocks = false
    level2 oplocks = false
    csc policy = disable
    browseable = No
    writeable = Yes
    read only = No
    profile acls = yes
    create mask = 0600
    store dos attributes = Yes
    directory mask = 0700

[netlogon]
    comment = Network Logon Service
    path = /srv/samba/netlogon/
    browseable = No
    writeable = No
    write list = @adm, root
-------- filtered unneeded stuff

```

So what am I missing here?
When I try to join, it asks for username and password... once I confirm, it takes around 4 seconds before displaying error unknown username or bad password.

If I change security = user it doesn't even ask me for password and after some time it displays another error - the specified domain does not exsist....




root@the-nox:/etc/samba# smbd --version
Version 3.6.3

root@the-nox:/etc/samba# uname -a
Linux the-nox.com 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

ubuntu server version 12.04

---

### Post by korenje on 2012-06-30
I've found out 1 more thing...

syslog displays this:


Jun 30 18:54:23 the-nox slapd[7540]: SASL [conn=1000] Failure: no secret in database
Jun 30 18:54:23 the-nox slapd[7540]: SASL [conn=1001] Failure: no secret in database

Also slapd keeps open 2 connections for every attempt forever. After 10 tries I had 20 open connections to slapd.

---

### Post by luvshines on 2012-07-01
Try increasing the log level for the Samba server, that may give a better hint to your issue
Add 'log level = 10' in [global] section of your smb.conf file and restart the Samba service

---

### Post by korenje on 2012-07-14
ok.
It seems it's getting stuck at group finding...



>   Primary group is 0 and contains 0 supplementary groups
[2012/07/14 17:27:34.180196,  5] lib/smbldap.c:1439(smbldap_search_ext)
  smbldap_search_ext: base => [dc=the-nox,dc=com], filter => [(&(objectClass=sambaGroupMapping)(gidNumber=20))], scope => [2]
[2012/07/14 17:27:34.180436,  4] passdb/pdb_ldap.c:2543(ldapsam_getgroup)
  ldapsam_getgroup: Did not find group, filter was (&(objectClass=sambaGroupMapping)(gidNumber=20))
[2012/07/14 17:27:34.180506,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2012/07/14 17:27:34.180550, 10] passdb/lookup_sid.c:1181(legacy_gid_to_sid)
  LEGACY: gid 20 -> sid S-1-22-2-20
[2012/07/14 17:27:34.180617,  5] passdb/lookup_sid.c:1384(gid_to_sid)
  gid_to_sid: winbind failed to find a sid for gid 24
[2012/07/14 17:27:34.180660,  4] smbd/sec_ctx.c:214(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2012/07/14 17:27:34.180703,  4] smbd/uid.c:460(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2012/07/14 17:27:34.180743,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2012/07/14 17:27:34.180785,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/07/14 17:27:34.180826,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0


This message repeats about 20 times, then it stops.

I got this groups in my ldap:

> root@the-nox:/etc/samba# net groupmap list
Domain Admins (S-1-5-21-10560820-41971740-2138972874-512) -> 512
Domain Users (S-1-5-21-10560820-41971740-2138972874-513) -> 513
Domain Guests (S-1-5-21-10560820-41971740-2138972874-514) -> 514
Domain Computers (S-1-5-21-10560820-41971740-2138972874-515) -> 515
Administrators (S-1-5-32-544) -> 544
Account Operators (S-1-5-32-548) -> 548
Print Operators (S-1-5-32-550) -> 550
Backup Operators (S-1-5-32-551) -> 551
Replicators (S-1-5-32-552) -> 552


I added username to a group Domain Users.

[IMG]http://shrani.si/f/2Z/In/3Kfb37Gc/ldap.png[/IMG]

So what am I missing here?

---

### Post by korenje on 2012-07-14
I have no idea what's wrong...


root@the-nox:/var/log/samba# net ads search 127.0.0.1
ads_connect: No logon servers
ads_connect: No logon servers


Do I need winbind? ldap not enough?



root@the-nox:/etc/samba# net ads info
ads_connect: No logon servers
ads_connect: No logon servers
Didn't find the ldap server!

---

