---
title: "Samba Domain controller Server Upgrade from 8.04 to 8.10"
date: 2008-11-01
forum: Server Platforms
---

### Post by damies on 2008-11-01
Hi All,

I have a server that is currently configured with Ubuntu Server 8.04 and Samba as the Domain Controller. 

This server is all configured the way the customer wanted but never went to production as Samba 3.0 didn't work with Windows Vista SP1. 

About a month ago when this server was setup the announcement for Samba 3.2 was out, Samba 3.2's features was better support for Vista and Windows server 2008, as I could see Samba 3.2 was going to be included Ubuntu 8.10 and waiting for 8.10 suited both our schedules we decided to wait.

Now my question is how easy is it to go about the upgrade of the server from 8.04 to 8.10, specifically will the samba configuration (Shares and Domain Settings) migrate smoothly and automatically or will I have to configure it all from scratch?

I would also appreciate any other general advice or gotcha's to watch out for in the upgrade from 8.04 to 8.10.

Dave.

---

### Post by damies on 2008-11-17
well I did the upgrade.... now having a problem the Vista Machines are not able to join the domain or even connect to the Samba server.

Server: Ubuntu 8.10
Client: Vista Business SP1
Client2: Mac OSX 10.4.11


when I run the following command from the Samba Server or the OSX client and type the users password, I can sucessfuly connect:
```

smbclient \\\\rfccserver1\\Files -U RFCC\\rfcc-admin

```
When I try the following command from the Vista client:
```

net use * \\rfccserver1\Files /u:RFCC\rfcc-admin

```
I get Access is Denied.

I enabled samba log level 10, so here is the log file /var/log/samba/log.vistabus:

```

[2008/11/18 00:09:10,  6] param/loadparm.c:lp_file_list_changed(6724)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Mon Nov 17 23:41:30 2008
  
[2008/11/18 00:09:10,  4] smbd/map_username.c:map_username(145)
  Scanning username map /etc/samba/smbusers
[2008/11/18 00:09:10, 10] smbd/password.c:user_in_list(504)
  user_in_list: checking user rfcc-admin in list
[2008/11/18 00:09:10, 10] smbd/password.c:user_in_list(509)
  user_in_list: checking user |rfcc-admin| against |Administrator|
[2008/11/18 00:09:10,  5] auth/auth_util.c:make_user_info_map(206)
  make_user_info_map: Mapping user [RFCC]\[rfcc-admin] from workstation [VISTABUS]
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10,  5] auth/auth_util.c:is_trusted_domain(2055)
  is_trusted_domain: Checking for domain trust with [RFCC]
[2008/11/18 00:09:10,  5] passdb/secrets.c:secrets_fetch_trusted_domain_password(644)
  secrets_fetch failed!
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:09:10, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = TDOM/RFCC couldn't be found
[2008/11/18 00:09:10,  5] libsmb/trustdom_cache.c:trustdom_cache_fetch(183)
  no entry for trusted domain RFCC found.
[2008/11/18 00:09:10,  5] auth/auth_util.c:make_user_info(120)
  attempting to make a user_info for rfcc-admin (rfcc-admin)
[2008/11/18 00:09:10,  5] auth/auth_util.c:make_user_info(130)
  making strings for rfcc-admin's user_info struct
[2008/11/18 00:09:10,  5] auth/auth_util.c:make_user_info(162)
  making blobs for rfcc-admin's user_info struct
[2008/11/18 00:09:10, 10] auth/auth_util.c:make_user_info(180)
  made an encrypted user_info for rfcc-admin (rfcc-admin)
[2008/11/18 00:09:10,  3] auth/auth.c:check_ntlm_password(220)
  check_ntlm_password:  Checking password for unmapped user [RFCC]\[rfcc-admin]@[VISTABUS] with the new password interface
[2008/11/18 00:09:10,  3] auth/auth.c:check_ntlm_password(223)
  check_ntlm_password:  mapped user is: [RFCC]\[rfcc-admin]@[VISTABUS]
[2008/11/18 00:09:10, 10] auth/auth.c:check_ntlm_password(232)
  check_ntlm_password: auth_context challenge created by NTLMSSP callback (NTLM2)
[2008/11/18 00:09:10, 10] auth/auth.c:check_ntlm_password(234)
  challenge is: 
[2008/11/18 00:09:10,  5] lib/util.c:dump_data(2223)
  [000] B1 54 1B 8F C6 4E 76 CC                           .T...Nv. 
[2008/11/18 00:09:10, 10] auth/auth.c:check_ntlm_password(260)
  check_ntlm_password: guest had nothing to say
[2008/11/18 00:09:10,  8] lib/util.c:is_myname(2098)
  is_myname("RFCC") returns 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_username(580)
  pdb_set_username: setting username rfcc-admin, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_domain(603)
  pdb_set_domain: setting domain RFCCSERVER1, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_nt_username(626)
  pdb_set_nt_username: setting nt username , was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_fullname(649)
  pdb_set_full_name: setting full name rfcc-admin,,,, was 
[2008/11/18 00:09:10,  4] lib/substitute.c:automount_server(500)
  Home server: rfccserver1
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_homedir(742)
  pdb_set_homedir: setting home dir \\rfccserver1\rfcc-admin, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_dir_drive(718)
  pdb_set_dir_drive: setting dir drive H:, was NULL
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_logon_script(672)
  pdb_set_logon_script: setting logon script logon.cmd, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_profile_path(695)
  pdb_set_profile_path: setting profile path \\rfccserver1\rfcc-admin\.Profile\Vista, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_workstations(785)
  pdb_set_workstations: setting workstations , was 
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: password history, val: 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_user_sid(509)
  pdb_set_user_sid: setting user sid S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:09:10, 10] passdb/pdb_compat.c:pdb_set_user_sid_from_rid(72)
  pdb_set_user_sid_from_rid:
        setting user sid S-1-5-21-2464266467-478960352-278798856-3000 from rid 3000
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: maximum password age, val: -1
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  5] lib/username.c:Get_Pwnam_alloc(133)
  Finding user rfcc-admin
[2008/11/18 00:09:10,  5] lib/username.c:Get_Pwnam_internals(77)
  Trying _Get_Pwnam(), username as lowercase is rfcc-admin
[2008/11/18 00:09:10,  5] lib/username.c:Get_Pwnam_internals(110)
  Get_Pwnam_internals did find user [rfcc-admin]!
[2008/11/18 00:09:10, 10] passdb/lookup_sid.c:lookup_sid(950)
  lookup_sid called for SID 'S-1-5-21-2464266467-478960352-278798856-1007'
[2008/11/18 00:09:10, 10] passdb/lookup_sid.c:check_dom_sid_to_level(705)
  Accepting SID S-1-5-21-2464266467-478960352-278798856 in level 1
[2008/11/18 00:09:10, 10] passdb/lookup_sid.c:lookup_rids(468)
  lookup_rids called for domain sid 'S-1-5-21-2464266467-478960352-278798856'
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10,  5] passdb/pdb_interface.c:lookup_global_sam_rid(1499)
  lookup_global_sam_rid: looking up RID 1007.
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 3
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 3
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10,  5] passdb/pdb_tdb.c:tdbsam_getsampwrid(963)
  pdb_getsampwrid (TDB): error looking up RID 1007 by key RID_000003ef.
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  5] passdb/pdb_interface.c:pdb_default_lookup_rids(1621)
  lookup_rids: Domain Admins:2
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10, 10] passdb/lookup_sid.c:lookup_sid(985)
  Sid S-1-5-21-2464266467-478960352-278798856-1007 -> RFCC\Domain Admins(2)
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: password history, val: 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_username(580)
  pdb_set_username: setting username rfcc-admin, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_domain(603)
  pdb_set_domain: setting domain RFCCSERVER1, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_nt_username(626)
  pdb_set_nt_username: setting nt username , was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_fullname(649)
  pdb_set_full_name: setting full name rfcc-admin,,,, was 
[2008/11/18 00:09:10,  4] lib/substitute.c:automount_server(500)
  Home server: rfccserver1
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_homedir(742)
  pdb_set_homedir: setting home dir \\rfccserver1\rfcc-admin, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_dir_drive(718)
  pdb_set_dir_drive: setting dir drive H:, was NULL
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_logon_script(672)
  pdb_set_logon_script: setting logon script logon.cmd, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_profile_path(695)
  pdb_set_profile_path: setting profile path \\rfccserver1\rfcc-admin\.Profile\Vista, was 
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_workstations(785)
  pdb_set_workstations: setting workstations , was 
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1

[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: password history, val: 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10, 10] passdb/pdb_get_set.c:pdb_set_user_sid(509)
  pdb_set_user_sid: setting user sid S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:09:10, 10] passdb/pdb_compat.c:pdb_set_user_sid_from_rid(72)
  pdb_set_user_sid_from_rid:
        setting user sid S-1-5-21-2464266467-478960352-278798856-3000 from rid 3000
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:09:10,  9] passdb/passdb.c:pdb_update_autolock_flag(1417)
  pdb_update_autolock_flag: Account rfcc-admin not autolocked, no check needed
[2008/11/18 00:09:10,  4] libsmb/ntlm_check.c:ntlm_password_check(328)
  ntlm_password_check: Checking NT MD4 password
[2008/11/18 00:09:10,  4] auth/auth_sam.c:sam_account_ok(137)
  sam_account_ok: Checking SMB password for user rfcc-admin
[2008/11/18 00:09:10,  5] auth/auth_sam.c:logon_hours_ok(119)
  logon_hours_ok: user rfcc-admin allowed to logon at this time (Mon Nov 17 14:09:10 2008
  )
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: maximum password age, val: -1
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:09:10,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:09:10,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:09:10, 10] lib/system_smbd.c:sys_getgrouplist(122)
  sys_getgrouplist: user [rfcc-admin]
[2008/11/18 00:09:48,  5] passdb/lookup_sid.c:gid_to_sid(1330)
  gid_to_sid: winbind failed to find a sid for gid 1000
[2008/11/18 00:10:31,  6] param/loadparm.c:lp_file_list_changed(6724)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Mon Nov 17 23:41:30 2008
  
[2008/11/18 00:10:31,  4] smbd/map_username.c:map_username(145)
  Scanning username map /etc/samba/smbusers
[2008/11/18 00:10:31, 10] smbd/password.c:user_in_list(504)
  user_in_list: checking user rfcc-admin in list
[2008/11/18 00:10:31, 10] smbd/password.c:user_in_list(509)
  user_in_list: checking user |rfcc-admin| against |Administrator|
[2008/11/18 00:10:31,  5] auth/auth_util.c:make_user_info_map(206)
  make_user_info_map: Mapping user [RFCC]\[rfcc-admin] from workstation [VISTABUS]
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31,  5] auth/auth_util.c:is_trusted_domain(2055)
  is_trusted_domain: Checking for domain trust with [RFCC]
[2008/11/18 00:10:31,  5] passdb/secrets.c:secrets_fetch_trusted_domain_password(644)
  secrets_fetch failed!
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:31, 10] lib/gencache.c:gencache_get(194)
  Cache entry with key = TDOM/RFCC couldn't be found
[2008/11/18 00:10:31,  5] libsmb/trustdom_cache.c:trustdom_cache_fetch(183)
  no entry for trusted domain RFCC found.
[2008/11/18 00:10:31,  5] auth/auth_util.c:make_user_info(120)
  attempting to make a user_info for rfcc-admin (rfcc-admin)
[2008/11/18 00:10:31,  5] auth/auth_util.c:make_user_info(130)
  making strings for rfcc-admin's user_info struct
[2008/11/18 00:10:31,  5] auth/auth_util.c:make_user_info(162)
  making blobs for rfcc-admin's user_info struct
[2008/11/18 00:10:31, 10] auth/auth_util.c:make_user_info(180)
  made an encrypted user_info for rfcc-admin (rfcc-admin)
[2008/11/18 00:10:31,  3] auth/auth.c:check_ntlm_password(220)
  check_ntlm_password:  Checking password for unmapped user [RFCC]\[rfcc-admin]@[VISTABUS] with the new password interface
[2008/11/18 00:10:31,  3] auth/auth.c:check_ntlm_password(223)
  check_ntlm_password:  mapped user is: [RFCC]\[rfcc-admin]@[VISTABUS]
[2008/11/18 00:10:31, 10] auth/auth.c:check_ntlm_password(232)
  check_ntlm_password: auth_context challenge created by NTLMSSP callback (NTLM2)
[2008/11/18 00:10:31, 10] auth/auth.c:check_ntlm_password(234)
  challenge is: 
[2008/11/18 00:10:31,  5] lib/util.c:dump_data(2223)
  [000] CC FF 34 48 2A AF CB C1                           ..4H*... 
[2008/11/18 00:10:31, 10] auth/auth.c:check_ntlm_password(260)
  check_ntlm_password: guest had nothing to say
[2008/11/18 00:10:31,  8] lib/util.c:is_myname(2098)
  is_myname("RFCC") returns 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_username(580)
  pdb_set_username: setting username rfcc-admin, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_domain(603)
  pdb_set_domain: setting domain RFCCSERVER1, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_nt_username(626)
  pdb_set_nt_username: setting nt username , was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_fullname(649)
  pdb_set_full_name: setting full name rfcc-admin,,,, was 
[2008/11/18 00:10:31,  4] lib/substitute.c:automount_server(500)
  Home server: rfccserver1
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_homedir(742)
  pdb_set_homedir: setting home dir \\rfccserver1\rfcc-admin, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_dir_drive(718)
  pdb_set_dir_drive: setting dir drive H:, was NULL
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_logon_script(672)
  pdb_set_logon_script: setting logon script logon.cmd, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_profile_path(695)
  pdb_set_profile_path: setting profile path \\rfccserver1\rfcc-admin\.Profile\Vista, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_workstations(785)
  pdb_set_workstations: setting workstations , was 
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: password history, val: 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_user_sid(509)
  pdb_set_user_sid: setting user sid S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:10:31, 10] passdb/pdb_compat.c:pdb_set_user_sid_from_rid(72)
  pdb_set_user_sid_from_rid:
        setting user sid S-1-5-21-2464266467-478960352-278798856-3000 from rid 3000
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: maximum password age, val: -1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  5] lib/username.c:Get_Pwnam_alloc(133)
  Finding user rfcc-admin
[2008/11/18 00:10:31,  5] lib/username.c:Get_Pwnam_internals(77)
  Trying _Get_Pwnam(), username as lowercase is rfcc-admin
[2008/11/18 00:10:31,  5] lib/username.c:Get_Pwnam_internals(110)
  Get_Pwnam_internals did find user [rfcc-admin]!
[2008/11/18 00:10:31, 10] passdb/lookup_sid.c:lookup_sid(950)
  lookup_sid called for SID 'S-1-5-21-2464266467-478960352-278798856-1007'
[2008/11/18 00:10:31, 10] passdb/lookup_sid.c:check_dom_sid_to_level(705)
  Accepting SID S-1-5-21-2464266467-478960352-278798856 in level 1
[2008/11/18 00:10:31, 10] passdb/lookup_sid.c:lookup_rids(468)
  lookup_rids called for domain sid 'S-1-5-21-2464266467-478960352-278798856'
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31,  5] passdb/pdb_interface.c:lookup_global_sam_rid(1499)
  lookup_global_sam_rid: looking up RID 1007.
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 3
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 3
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31,  5] passdb/pdb_tdb.c:tdbsam_getsampwrid(963)
  pdb_getsampwrid (TDB): error looking up RID 1007 by key RID_000003ef.
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  5] passdb/pdb_interface.c:pdb_default_lookup_rids(1621)
  lookup_rids: Domain Admins:2
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31, 10] passdb/lookup_sid.c:lookup_sid(985)
  Sid S-1-5-21-2464266467-478960352-278798856-1007 -> RFCC\Domain Admins(2)
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: password history, val: 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_username(580)
  pdb_set_username: setting username rfcc-admin, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_domain(603)
  pdb_set_domain: setting domain RFCCSERVER1, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_nt_username(626)
  pdb_set_nt_username: setting nt username , was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_fullname(649)
  pdb_set_full_name: setting full name rfcc-admin,,,, was 
[2008/11/18 00:10:31,  4] lib/substitute.c:automount_server(500)
  Home server: rfccserver1
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_homedir(742)
  pdb_set_homedir: setting home dir \\rfccserver1\rfcc-admin, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_dir_drive(718)
  pdb_set_dir_drive: setting dir drive H:, was NULL
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_logon_script(672)
  pdb_set_logon_script: setting logon script logon.cmd, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_profile_path(695)
  pdb_set_profile_path: setting profile path \\rfccserver1\rfcc-admin\.Profile\Vista, was 
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_workstations(785)
  pdb_set_workstations: setting workstations , was 
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: password history, val: 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31, 10] passdb/pdb_get_set.c:pdb_set_user_sid(509)
  pdb_set_user_sid: setting user sid S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:10:31, 10] passdb/pdb_compat.c:pdb_set_user_sid_from_rid(72)
  pdb_set_user_sid_from_rid:
        setting user sid S-1-5-21-2464266467-478960352-278798856-3000 from rid 3000
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:31,  9] passdb/passdb.c:pdb_update_autolock_flag(1417)
  pdb_update_autolock_flag: Account rfcc-admin not autolocked, no check needed
[2008/11/18 00:10:31,  4] libsmb/ntlm_check.c:ntlm_password_check(328)
  ntlm_password_check: Checking NT MD4 password
[2008/11/18 00:10:31,  4] auth/auth_sam.c:sam_account_ok(137)
  sam_account_ok: Checking SMB password for user rfcc-admin
[2008/11/18 00:10:31,  5] auth/auth_sam.c:logon_hours_ok(119)
  logon_hours_ok: user rfcc-admin allowed to logon at this time (Mon Nov 17 14:10:31 2008
  )
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] lib/account_pol.c:account_policy_get(332)
  account_policy_get: name: maximum password age, val: -1
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:31,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:31,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:31, 10] lib/system_smbd.c:sys_getgrouplist(122)
  sys_getgrouplist: user [rfcc-admin]
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 4 -> sid S-1-22-2-4
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 1000 -> sid S-1-5-21-2464266467-478960352-278798856-1007
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 20 -> sid S-1-22-2-20
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 4 -> sid S-1-22-2-4
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 24 -> sid S-1-22-2-24
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 20 -> sid S-1-22-2-20
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 25 -> sid S-1-22-2-25
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 24 -> sid S-1-22-2-24
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 29 -> sid S-1-22-2-29
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 25 -> sid S-1-22-2-25
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 30 -> sid S-1-22-2-30
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 29 -> sid S-1-22-2-29
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 44 -> sid S-1-22-2-44
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 30 -> sid S-1-22-2-30
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 46 -> sid S-1-22-2-46
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 44 -> sid S-1-22-2-44
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 107 -> sid S-1-22-2-107
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 46 -> sid S-1-22-2-46
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 113 -> sid S-1-22-2-113
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 107 -> sid S-1-22-2-107
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 114 -> sid S-1-22-2-114
[2008/11/18 00:10:37,  5] auth/auth_util.c:make_server_info_sam(650)
  make_server_info_sam: made server info for user rfcc-admin -> rfcc-admin
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  3] auth/auth.c:check_ntlm_password(269)
  check_ntlm_password: sam authentication for user [rfcc-admin] succeeded
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(469)
  smb_pam_start: PAM: Init user: rfcc-admin
[2008/11/18 00:10:37,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(486)
  smb_pam_start: PAM: setting rhost to: 0.0.0.0
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(495)
  smb_pam_start: PAM: setting tty
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(503)
  smb_pam_start: PAM: Init passed for user: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_account(561)
  smb_pam_account: PAM: Account Management for User: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_account(580)
  smb_pam_account: PAM: Account OK for User: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_end(449)
  smb_pam_end: PAM: PAM_END OK.
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  5] auth/auth.c:check_ntlm_password(295)
  check_ntlm_password:  PAM Account for user [rfcc-admin] succeeded
[2008/11/18 00:10:37,  2] auth/auth.c:check_ntlm_password(308)
  check_ntlm_password:  authentication for user [rfcc-admin] -> [rfcc-admin] -> [rfcc-admin] succeeded
[2008/11/18 00:10:37,  5] auth/auth_util.c:free_user_info(1985)
  attempting to free (and zero) a user_info structure
[2008/11/18 00:10:37, 10] auth/auth_util.c:free_user_info(1989)
  structure was created for rfcc-admin
[2008/11/18 00:10:37, 10] auth/token_util.c:create_local_nt_token(302)
  Create local NT token for S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 113 -> sid S-1-22-2-113
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:gid_to_sid(1335)
  gid 114 -> sid S-1-22-2-114
[2008/11/18 00:10:37,  5] auth/auth_util.c:make_server_info_sam(650)
  make_server_info_sam: made server info for user rfcc-admin -> rfcc-admin
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  3] auth/auth.c:check_ntlm_password(269)
  check_ntlm_password: sam authentication for user [rfcc-admin] succeeded
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(469)
  smb_pam_start: PAM: Init user: rfcc-admin
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1431)
  sid S-1-5-32-544 -> gid 18121
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1431)
  sid S-1-5-32-545 -> gid 115
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-21-2464266467-478960352-278798856-3000]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-0-0]
[2008/11/18 00:10:37,  5] lib/privileges.c:get_privileges_for_sids(128)
  get_privileges_for_sids: sid = S-1-1-0
  Privilege set:
  SE_PRIV  0x0 0x0 0x0 0x0
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-4]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-20]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-24]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-25]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-29]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-30]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-44]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-46]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-32-545]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-107]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-113]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-114]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-1000]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-115]
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(486)
  smb_pam_start: PAM: setting rhost to: 192.168.13.24
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(495)
  smb_pam_start: PAM: setting tty
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(503)
  smb_pam_start: PAM: Init passed for user: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_account(561)
  smb_pam_account: PAM: Account Management for User: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_account(580)
  smb_pam_account: PAM: Account OK for User: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_end(449)
  smb_pam_end: PAM: PAM_END OK.
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  5] auth/auth.c:check_ntlm_password(295)
  check_ntlm_password:  PAM Account for user [rfcc-admin] succeeded
[2008/11/18 00:10:37,  2] auth/auth.c:check_ntlm_password(308)
  check_ntlm_password:  authentication for user [rfcc-admin] -> [rfcc-admin] -> [rfcc-admin] succeeded
[2008/11/18 00:10:37,  5] auth/auth_util.c:free_user_info(1985)
  attempting to free (and zero) a user_info structure
[2008/11/18 00:10:37, 10] auth/auth_util.c:free_user_info(1989)
  structure was created for rfcc-admin
[2008/11/18 00:10:37, 10] auth/token_util.c:create_local_nt_token(302)
  Create local NT token for S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-0-0
[2008/11/18 00:10:37, 10] auth/auth_util.c:create_local_token(755)
  Could not convert SID S-1-0-0 to gid, ignoring it
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-1-0
[2008/11/18 00:10:37, 10] auth/auth_util.c:create_local_token(755)
  Could not convert SID S-1-1-0 to gid, ignoring it
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-5-2
[2008/11/18 00:10:37, 10] auth/auth_util.c:create_local_token(755)
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1431)
  Could not convert SID S-1-5-2 to gid, ignoring it
  sid S-1-5-32-544 -> gid 18121
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-5-11
[2008/11/18 00:10:37, 10] auth/auth_util.c:create_local_token(755)
  Could not convert SID S-1-5-11 to gid, ignoring it
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-4 -> gid 4
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-20 -> gid 20
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-24 -> gid 24
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-25 -> gid 25
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-29 -> gid 29
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-30 -> gid 30
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-44 -> gid 44
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-46 -> gid 46
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1431)
  sid S-1-5-32-545 -> gid 115
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-107 -> gid 107
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-113 -> gid 113
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1431)
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-114 -> gid 114
  sid S-1-5-32-545 -> gid 115
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-1000 -> gid 1000
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:push_sec_ctx(224)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37, 10] passdb/lookup_sid.c:sid_to_gid(1413)
[2008/11/18 00:10:37,  3] smbd/uid.c:push_conn_ctx(357)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
  sid S-1-22-2-115 -> gid 115
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2008/11/18 00:10:37, 10] auth/token_util.c:debug_nt_user_token(470)
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
  NT user token of user S-1-5-21-2464266467-478960352-278798856-3000
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
  contains 19 SIDs
  SID[  0]: S-1-5-21-2464266467-478960352-278798856-3000
  SID[  1]: S-1-0-0
  SID[  2]: S-1-1-0
  SID[  3]: S-1-5-2
  SID[  4]: S-1-5-11
  SID[  5]: S-1-22-2-4
  SID[  6]: S-1-22-2-20
  SID[  7]: S-1-22-2-24
  SID[  8]: S-1-22-2-25
  SID[  9]: S-1-22-2-29
  SID[ 10]: S-1-22-2-30
  SID[ 11]: S-1-22-2-44
  SID[ 12]: S-1-22-2-46
  SID[ 13]: S-1-5-32-545
  SID[ 14]: S-1-22-2-107
  SID[ 15]: S-1-22-2-113
  SID[ 16]: S-1-22-2-114
  SID[ 17]: S-1-22-2-1000
  SID[ 18]: S-1-22-2-115
  SE_PRIV  0x0 0x0 0x0 0x0
[2008/11/18 00:10:37, 10] auth/auth_ntlmssp.c:auth_ntlmssp_check_password(137)
  Got NT session key of length 16
[2008/11/18 00:10:37, 10] libsmb/ntlmssp.c:ntlmssp_server_auth(811)
  ntlmssp_server_auth: Created NTLM2 session key.
[2008/11/18 00:10:37,  3] libsmb/ntlmssp_sign.c:ntlmssp_sign_init(337)
  NTLMSSP Sign/Seal - Initialising with flags:
[2008/11/18 00:10:37,  3] libsmb/ntlmssp.c:debug_ntlmssp_flags(62)
  Got NTLMSSP neg_flags=0xe2088215
    NTLMSSP_NEGOTIATE_UNICODE
    NTLMSSP_REQUEST_TARGET
    NTLMSSP_NEGOTIATE_SIGN
    NTLMSSP_NEGOTIATE_NTLM
    NTLMSSP_NEGOTIATE_ALWAYS_SIGN
    NTLMSSP_NEGOTIATE_NTLM2
    NTLMSSP_NEGOTIATE_128
    NTLMSSP_NEGOTIATE_KEY_EXCH
    NTLMSSP_NEGOTIATE_56
[2008/11/18 00:10:37, 10] smbd/password.c:register_existing_vuid(310)
  register_existing_vuid: (1000,1000) rfcc-admin rfcc-admin RFCCSERVER1 guest=0
[2008/11/18 00:10:37,  3] smbd/password.c:register_existing_vuid(314)
  register_existing_vuid: User name: rfcc-admin Real name: rfcc-admin,,,
[2008/11/18 00:10:37,  3] smbd/password.c:register_existing_vuid(326)
  register_existing_vuid: UNIX uid 1000 is UNIX user rfcc-admin, and will be vuid 100
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(100)
  Locking key 49442F353535352F3130
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(129)
  Allocated locked data 0x0x7f07d7b9f6e0
[2008/11/18 00:10:37,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
[2008/11/18 00:10:37,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:pop_sec_ctx(432)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(469)
  smb_pam_start: PAM: Init user: rfcc-admin
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-21-2464266467-478960352-278798856-3000]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-21-2464266467-478960352-278798856-1007]
[2008/11/18 00:10:37,  5] lib/privileges.c:get_privileges_for_sids(128)
  get_privileges_for_sids: sid = S-1-1-0
  Privilege set:
  SE_PRIV  0x0 0x0 0x0 0x0
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-4]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-20]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-24]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-25]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-29]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-30]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-44]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-46]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-5-32-545]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-107]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-113]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-114]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-1000]
[2008/11/18 00:10:37,  3] lib/privileges.c:get_privileges(63)
  get_privileges: No privileges assigned to SID [S-1-22-2-115]
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(486)
  smb_pam_start: PAM: setting rhost to: 0.0.0.0
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(495)
  smb_pam_start: PAM: setting tty
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(503)
  smb_pam_start: PAM: Init passed for user: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_internal_pam_session(640)
  smb_internal_pam_session: PAM: tty set to: smb/5555/100
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_end(449)
  smb_pam_end: PAM: PAM_END OK.
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_record_destr(42)
  Unlocking key 49442F353535352F3130
[2008/11/18 00:10:37,  7] param/loadparm.c:lp_servicenumber(9027)
  lp_servicenumber: couldn't find rfcc-admin
[2008/11/18 00:10:37,  3] smbd/password.c:register_existing_vuid(350)
  Adding homes service for user 'rfcc-admin' using home directory: '/home/rfcc-admin'
[2008/11/18 00:10:37,  8] param/loadparm.c:add_a_service(5785)
  add_a_service: Creating snum = 11 for rfcc-admin
[2008/11/18 00:10:37, 10] param/loadparm.c:hash_a_service(5832)
  hash_a_service: hashing index 11 for service name rfcc-admin
[2008/11/18 00:10:37,  3] param/loadparm.c:lp_add_home(5881)
  adding home's share [rfcc-admin] for user 'rfcc-admin' at '/home/rfcc-admin'
[2008/11/18 00:10:37,  6] param/loadparm.c:lp_file_list_changed(6724)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Mon Nov 17 23:41:30 2008
  
[2008/11/18 00:10:37,  5] lib/util.c:show_msg(642)
[2008/11/18 00:10:37,  5] lib/util.c:show_msg(652)
  size=96
  smb_com=0x73
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=136
  smb_flg2=51201
  smb_tid=65535
  smb_pid=65279
  smb_uid=100
  smb_mid=128
  smt_wct=4
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_vwv[ 2]=    0 (0x0)
  smb_vwv[ 3]=    9 (0x9)
  smb_bcc=53
[2008/11/18 00:10:37, 10] lib/util.c:dump_data(2223)
  [000] A1 07 30 05 A0 03 0A 01  00 55 00 6E 00 69 00 78  ..0..... .U.n.i.x
  [010] 00 00 00 53 00 61 00 6D  00 62 00 61 00 20 00 33  ...S.a.m .b.a. .3
  [020] 00 2E 00 32 00 2E 00 33  00 00 00 52 00 46 00 43  ...2...3 ...R.F.C
  [030] 00 43 00 00 00                                    .C... 
[2008/11/18 00:10:37,  0] lib/util_sock.c:write_data(1059)
[2008/11/18 00:10:37,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2008/11/18 00:10:37,  0] smbd/process.c:srv_send_smb(74)
  Error writing 100 bytes to client. -1. (Transport endpoint is not connected)
[2008/11/18 00:10:37, 10] lib/events.c:run_events(263)
  Running event "idle_evt(deadtime)" 7f07d7ba90e0
[2008/11/18 00:10:37, 10] lib/events.c:timed_event_destructor(65)
  Destroying timed event 7f07d7ba90e0 "idle_evt(deadtime)"
[2008/11/18 00:10:37,  2] smbd/server.c:deadtime_fn(1044)
  Closing idle connection
[2008/11/18 00:10:37, 10] lib/messages_local.c:messaging_tdb_store(215)
  messaging_tdb_store:
      array: struct messaging_array
          num_messages             : 0x00000001 (1)
          messages: ARRAY(1)
              messages: struct messaging_rec
                  msg_version              : 0x00000002 (2)
                  msg_type                 : 0x0000000d (13)
                  dest: struct server_id
                      id                       : 0x000015b3 (5555)
                  src: struct server_id
                      id                       : 0x000015b3 (5555)
                  buf                      : DATA_BLOB length=0
[2008/11/18 00:10:37, 10] lib/messages_local.c:message_dispatch(419)
  message_dispatch: received_signal = 1
[2008/11/18 00:10:37, 10] lib/messages_local.c:messaging_tdb_fetch(174)
  messaging_tdb_fetch:
      result: struct messaging_array
          num_messages             : 0x00000001 (1)
          messages: ARRAY(1)
              messages: struct messaging_rec
                  msg_version              : 0x00000002 (2)
                  msg_type                 : 0x0000000d (13)
                  dest: struct server_id
                      id                       : 0x000015b3 (5555)
                  src: struct server_id
                      id                       : 0x000015b3 (5555)
                  buf                      : DATA_BLOB length=0
[2008/11/18 00:10:37,  3] smbd/server.c:msg_exit_server(223)
  got a SHUTDOWN message
[2008/11/18 00:10:37,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:37,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:37,  5] smbd/uid.c:change_to_root_user(287)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(100)
  Locking key 49442F353535352F3130
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(129)
  Allocated locked data 0x0x7f07d7badc40
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(469)
  smb_pam_start: PAM: Init user: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(486)
  smb_pam_start: PAM: setting rhost to: 0.0.0.0
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(495)
  smb_pam_start: PAM: setting tty
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_start(503)
  smb_pam_start: PAM: Init passed for user: rfcc-admin
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_internal_pam_session(640)
  smb_internal_pam_session: PAM: tty set to: smb/5555/100
[2008/11/18 00:10:37,  4] auth/pampass.c:smb_pam_end(449)
  smb_pam_end: PAM: PAM_END OK.
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_record_destr(42)
  Unlocking key 49442F353535352F3130
[2008/11/18 00:10:37,  3] smbd/connection.c:yield_connection(31)
  Yielding connection to 
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(100)
  Locking key B3150000FFFFFFFF0000
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(129)
  Allocated locked data 0x0x7f07d7ba70e0
[2008/11/18 00:10:37, 10] lib/dbwrap_tdb.c:db_tdb_record_destr(42)
  Unlocking key B3150000FFFFFFFF0000
[2008/11/18 00:10:37,  3] smbd/server.c:exit_server_common(949)
  Server exit (normal exit)
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1431)
  sid S-1-5-21-2464266467-478960352-278798856-1007 -> gid 1000
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-1-0
[2008/11/18 00:10:40, 10] auth/auth_util.c:create_local_token(755)
  Could not convert SID S-1-1-0 to gid, ignoring it
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-5-2
[2008/11/18 00:10:40, 10] auth/auth_util.c:create_local_token(755)
  Could not convert SID S-1-5-2 to gid, ignoring it
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1426)
  winbind failed to find a gid for sid S-1-5-11
[2008/11/18 00:10:40, 10] auth/auth_util.c:create_local_token(755)
  Could not convert SID S-1-5-11 to gid, ignoring it
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-4 -> gid 4
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-20 -> gid 20
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-24 -> gid 24
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-25 -> gid 25
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-29 -> gid 29
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-30 -> gid 30
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-44 -> gid 44
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-46 -> gid 46
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1431)
  sid S-1-5-32-545 -> gid 115
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-107 -> gid 107
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-113 -> gid 113
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-114 -> gid 114
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-1000 -> gid 1000
[2008/11/18 00:10:40, 10] passdb/lookup_sid.c:sid_to_gid(1413)
  sid S-1-22-2-115 -> gid 115
[2008/11/18 00:10:40, 10] auth/token_util.c:debug_nt_user_token(470)
  NT user token of user S-1-5-21-2464266467-478960352-278798856-3000
  contains 19 SIDs
  SID[  0]: S-1-5-21-2464266467-478960352-278798856-3000
  SID[  1]: S-1-5-21-2464266467-478960352-278798856-1007
  SID[  2]: S-1-1-0
  SID[  3]: S-1-5-2
  SID[  4]: S-1-5-11
  SID[  5]: S-1-22-2-4
  SID[  6]: S-1-22-2-20
  SID[  7]: S-1-22-2-24
  SID[  8]: S-1-22-2-25
  SID[  9]: S-1-22-2-29
  SID[ 10]: S-1-22-2-30
  SID[ 11]: S-1-22-2-44
  SID[ 12]: S-1-22-2-46
  SID[ 13]: S-1-5-32-545
  SID[ 14]: S-1-22-2-107
  SID[ 15]: S-1-22-2-113
  SID[ 16]: S-1-22-2-114
  SID[ 17]: S-1-22-2-1000
  SID[ 18]: S-1-22-2-115
  SE_PRIV  0x0 0x0 0x0 0x0
[2008/11/18 00:10:40, 10] auth/auth_ntlmssp.c:auth_ntlmssp_check_password(137)
  Got NT session key of length 16
[2008/11/18 00:10:40, 10] libsmb/ntlmssp.c:ntlmssp_server_auth(811)
  ntlmssp_server_auth: Created NTLM2 session key.
[2008/11/18 00:10:40,  3] libsmb/ntlmssp_sign.c:ntlmssp_sign_init(337)
  NTLMSSP Sign/Seal - Initialising with flags:
[2008/11/18 00:10:40,  3] libsmb/ntlmssp.c:debug_ntlmssp_flags(62)
  Got NTLMSSP neg_flags=0xe2088215
    NTLMSSP_NEGOTIATE_UNICODE
    NTLMSSP_REQUEST_TARGET
    NTLMSSP_NEGOTIATE_SIGN
    NTLMSSP_NEGOTIATE_NTLM
    NTLMSSP_NEGOTIATE_ALWAYS_SIGN
    NTLMSSP_NEGOTIATE_NTLM2
    NTLMSSP_NEGOTIATE_128
    NTLMSSP_NEGOTIATE_KEY_EXCH
    NTLMSSP_NEGOTIATE_56
[2008/11/18 00:10:40, 10] smbd/password.c:register_existing_vuid(310)
  register_existing_vuid: (1000,1000) rfcc-admin rfcc-admin RFCCSERVER1 guest=0
[2008/11/18 00:10:40,  3] smbd/password.c:register_existing_vuid(314)
  register_existing_vuid: User name: rfcc-admin Real name: rfcc-admin,,,
[2008/11/18 00:10:40,  3] smbd/password.c:register_existing_vuid(326)
  register_existing_vuid: UNIX uid 1000 is UNIX user rfcc-admin, and will be vuid 100
[2008/11/18 00:10:40, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(100)
  Locking key 49442F353538352F3130
[2008/11/18 00:10:40, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(129)
  Allocated locked data 0x0x7f07d7b9ec20
[2008/11/18 00:10:40,  4] auth/pampass.c:smb_pam_start(469)
  smb_pam_start: PAM: Init user: rfcc-admin
[2008/11/18 00:10:40,  4] auth/pampass.c:smb_pam_start(486)
  smb_pam_start: PAM: setting rhost to: 192.168.13.24
[2008/11/18 00:10:40,  4] auth/pampass.c:smb_pam_start(495)
  smb_pam_start: PAM: setting tty
[2008/11/18 00:10:40,  4] auth/pampass.c:smb_pam_start(503)
  smb_pam_start: PAM: Init passed for user: rfcc-admin
[2008/11/18 00:10:40,  4] auth/pampass.c:smb_internal_pam_session(640)
  smb_internal_pam_session: PAM: tty set to: smb/5585/100
[2008/11/18 00:10:40,  4] auth/pampass.c:smb_pam_end(449)
  smb_pam_end: PAM: PAM_END OK.
[2008/11/18 00:10:40, 10] lib/dbwrap_tdb.c:db_tdb_record_destr(42)
  Unlocking key 49442F353538352F3130
[2008/11/18 00:10:40,  7] param/loadparm.c:lp_servicenumber(9027)
  lp_servicenumber: couldn't find rfcc-admin
[2008/11/18 00:10:40,  3] smbd/password.c:register_existing_vuid(350)
  Adding homes service for user 'rfcc-admin' using home directory: '/home/rfcc-admin'
[2008/11/18 00:10:40,  8] param/loadparm.c:add_a_service(5785)
  add_a_service: Creating snum = 11 for rfcc-admin
[2008/11/18 00:10:40, 10] param/loadparm.c:hash_a_service(5832)
  hash_a_service: hashing index 11 for service name rfcc-admin
[2008/11/18 00:10:40,  3] param/loadparm.c:lp_add_home(5881)
  adding home's share [rfcc-admin] for user 'rfcc-admin' at '/home/rfcc-admin'
[2008/11/18 00:10:40,  6] param/loadparm.c:lp_file_list_changed(6724)
  lp_file_list_changed()
  file /etc/samba/smb.conf -> /etc/samba/smb.conf  last mod_time: Mon Nov 17 23:41:30 2008
  
[2008/11/18 00:10:40,  5] lib/util.c:show_msg(642)
[2008/11/18 00:10:40,  5] lib/util.c:show_msg(652)
  size=96
  smb_com=0x73
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=136
  smb_flg2=51201
  smb_tid=65535
  smb_pid=65279
  smb_uid=100
  smb_mid=256
  smt_wct=4
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_vwv[ 2]=    0 (0x0)
  smb_vwv[ 3]=    9 (0x9)
  smb_bcc=53
[2008/11/18 00:10:40, 10] lib/util.c:dump_data(2223)
  [000] A1 07 30 05 A0 03 0A 01  00 55 00 6E 00 69 00 78  ..0..... .U.n.i.x
  [010] 00 00 00 53 00 61 00 6D  00 62 00 61 00 20 00 33  ...S.a.m .b.a. .3
  [020] 00 2E 00 32 00 2E 00 33  00 00 00 52 00 46 00 43  ...2...3 ...R.F.C
  [030] 00 43 00 00 00                                    .C... 
[2008/11/18 00:10:40, 10] lib/util_sock.c:read_smb_length_return_keepalive(1118)
  got smb length of 88
[2008/11/18 00:10:40,  6] smbd/process.c:process_smb(1546)
  got message type 0x0 of len 0x58
[2008/11/18 00:10:40,  3] smbd/process.c:process_smb(1549)
  Transaction 3 of length 92 (0 toread)
[2008/11/18 00:10:40,  5] lib/util.c:show_msg(642)
[2008/11/18 00:10:40,  5] lib/util.c:show_msg(652)
  size=88
  smb_com=0x75
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=24
  smb_flg2=51207
  smb_tid=0
  smb_pid=65279
  smb_uid=100
  smb_mid=320
  smt_wct=4
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=   88 (0x58)
  smb_vwv[ 2]=    8 (0x8)
  smb_vwv[ 3]=    1 (0x1)
  smb_bcc=45
[2008/11/18 00:10:40, 10] lib/util.c:dump_data(2223)
  [000] 00 5C 00 5C 00 52 00 46  00 43 00 43 00 53 00 45  .\.\.R.F .C.C.S.E
  [010] 00 52 00 56 00 45 00 52  00 31 00 5C 00 49 00 50  .R.V.E.R .1.\.I.P
  [020] 00 43 00 24 00 00 00 3F  3F 3F 3F 3F 00           .C.$...? ????.
[2008/11/18 00:10:40,  3] smbd/process.c:switch_message(1361)
  switch message SMBtconX (pid 5585) conn 0x0
[2008/11/18 00:10:40,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:40,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:40,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:40,  5] smbd/uid.c:change_to_root_user(287)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2008/11/18 00:10:40,  4] smbd/reply.c:reply_tcon_and_X(653)
  Client requested device type [?????] for share [IPC$]
[2008/11/18 00:10:40,  5] smbd/service.c:make_connection(1376)
  making a connection to 'normal' service ipc$
[2008/11/18 00:10:40,  3] lib/access.c:check_access(389)
  check_access: no hostnames in host allow/deny list.
[2008/11/18 00:10:40,  0] lib/access.c:check_access(410)
  Denied connection from  (192.168.13.24)
[2008/11/18 00:10:40,  3] smbd/error.c:error_packet_set(61)
  error packet at smbd/reply.c(662) cmd=117 (SMBtconX) NT_STATUS_ACCESS_DENIED
[2008/11/18 00:10:40,  5] lib/util.c:show_msg(642)
[2008/11/18 00:10:40,  5] lib/util.c:show_msg(652)
  size=35
  smb_com=0x75
  smb_rcls=34
  smb_reh=0
  smb_err=49152
  smb_flg=136
  smb_flg2=51201
  smb_tid=0
  smb_pid=65279
  smb_uid=100
  smb_mid=320
  smt_wct=0
  smb_bcc=0
[2008/11/18 00:10:52, 10] lib/util_sock.c:read_smb_length_return_keepalive(1118)
  got smb length of 39
[2008/11/18 00:10:52,  6] smbd/process.c:process_smb(1546)
  got message type 0x0 of len 0x27
[2008/11/18 00:10:52,  3] smbd/process.c:process_smb(1549)
  Transaction 4 of length 43 (0 toread)
[2008/11/18 00:10:52,  5] lib/util.c:show_msg(642)
[2008/11/18 00:10:52,  5] lib/util.c:show_msg(652)
  size=39
  smb_com=0x74
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=24
  smb_flg2=51207
  smb_tid=0
  smb_pid=65279
  smb_uid=100
  smb_mid=384
  smt_wct=2
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_bcc=0
[2008/11/18 00:10:52,  3] smbd/process.c:switch_message(1361)
  switch message SMBulogoffX (pid 5585) conn 0x0
[2008/11/18 00:10:52,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:52,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:52,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:52,  5] smbd/uid.c:change_to_root_user(287)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2008/11/18 00:10:52, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(100)
  Locking key 49442F353538352F3130
[2008/11/18 00:10:52, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(129)
  Allocated locked data 0x0x7f07d7bb0750
[2008/11/18 00:10:52,  4] auth/pampass.c:smb_pam_start(469)
  smb_pam_start: PAM: Init user: rfcc-admin
[2008/11/18 00:10:52,  4] auth/pampass.c:smb_pam_start(486)
  smb_pam_start: PAM: setting rhost to: 192.168.13.24
[2008/11/18 00:10:52,  4] auth/pampass.c:smb_pam_start(495)
  smb_pam_start: PAM: setting tty
[2008/11/18 00:10:52,  4] auth/pampass.c:smb_pam_start(503)
  smb_pam_start: PAM: Init passed for user: rfcc-admin
[2008/11/18 00:10:52,  4] auth/pampass.c:smb_internal_pam_session(640)
  smb_internal_pam_session: PAM: tty set to: smb/5585/100
[2008/11/18 00:10:52,  4] auth/pampass.c:smb_pam_end(449)
  smb_pam_end: PAM: PAM_END OK.
[2008/11/18 00:10:52, 10] lib/dbwrap_tdb.c:db_tdb_record_destr(42)
  Unlocking key 49442F353538352F3130
[2008/11/18 00:10:52,  3] smbd/reply.c:reply_ulogoffX(1910)
  ulogoffX vuid=100
[2008/11/18 00:10:52,  5] lib/util.c:show_msg(642)
[2008/11/18 00:10:52,  5] lib/util.c:show_msg(652)
  size=39
  smb_com=0x74
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=136
  smb_flg2=51201
  smb_tid=0
  smb_pid=65279
  smb_uid=100
  smb_mid=384
  smt_wct=2
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_bcc=0
[2008/11/18 00:10:52,  5] lib/util_sock.c:read_socket_with_timeout(928)
  read_socket_with_timeout: blocking read. EOF from client.
[2008/11/18 00:10:52, 10] smbd/process.c:receive_smb_raw_talloc(276)
  receive_smb_raw: NT_STATUS_END_OF_FILE
[2008/11/18 00:10:52,  3] smbd/process.c:smbd_process(2035)
  receive_message_or_smb failed: NT_STATUS_END_OF_FILE, exiting
[2008/11/18 00:10:52,  5] lib/gencache.c:gencache_shutdown(93)
  Closing cache file
[2008/11/18 00:10:52,  5] libsmb/namecache.c:namecache_shutdown(81)
  namecache_shutdown: netbios namecache closed successfully.
[2008/11/18 00:10:52,  3] smbd/sec_ctx.c:set_sec_ctx(324)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/11/18 00:10:52,  5] auth/token_util.c:debug_nt_user_token(464)
  NT user token: (NULL)
[2008/11/18 00:10:52,  5] auth/token_util.c:debug_unix_user_token(490)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/11/18 00:10:52,  5] smbd/uid.c:change_to_root_user(287)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2008/11/18 00:10:52,  3] smbd/connection.c:yield_connection(31)
  Yielding connection to 
[2008/11/18 00:10:52, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(100)
  Locking key D1150000FFFFFFFF0000
[2008/11/18 00:10:52, 10] lib/dbwrap_tdb.c:db_tdb_fetch_locked(129)
  Allocated locked data 0x0x7f07d7ba70e0
[2008/11/18 00:10:52, 10] lib/dbwrap_tdb.c:db_tdb_record_destr(42)
  Unlocking key D1150000FFFFFFFF0000
[2008/11/18 00:10:52,  3] smbd/server.c:exit_server_common(949)
  Server exit (normal exit)



```

Hope someone can help me?

Dave.

---

