---
title: "get_privileges: No privileges assigned to SID"
date: 2012-08-11
forum: Server Platforms
---

### Post by walkermd on 2012-08-11
Forgive me if this in posted somewhere incorrectly. I have been at this for 6 days. Searched the internet as much as I could for an answer. I have run down every rabbit hole possible. I am as fed up as I can get. I cannot get windows 7 systems to join the Domain. Before some one replies with an answer, I have done the windows regedits, combed the smb.conf file and use the 'ports =' settings. I will be happy to post the .conf files and log files if asked but I do not think it is just an entry in the smb.conf causing this issue. Thank you in advance
My versions of Ububtu, SaMBa, and OpenLDAP 
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty
SMB Version 3.5.8
ldapsearch: @(#) $OpenLDAP: ldapsearch 2.4.23 (Nov 14 2011 20:35:27) $
	buildd@yellow:/build/buildd/openldap-2.4.23/debian/build/clients/tools
	(LDAP library: OpenLDAP 20423)
The Windows error I get is varied from Domain does not exist to Operation cannot be performed.
Thanks in advance.

Here is a brief from my /var.log/log.machinename

It finds me;
[2012/08/11 11:55:18.045860,  3] auth/auth.c:216(check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [MONTGOMERY]\[walkerm]@[ILIKEFLOWERS] with the new password interface
[2012/08/11 11:55:18.045917,  3] auth/auth.c:219(check_ntlm_password)
  check_ntlm_password:  mapped user is: [MONTGOMERY]\[walkerm]@[ILIKEFLOWERS]

Connection made and auth made;
[2012/08/11 11:55:18.046548,  2] lib/smbldap.c:950(smbldap_open_connection)
  smbldap_open_connection: connection opened
[2012/08/11 11:55:18.049527,  3] lib/smbldap.c:1166(smbldap_connect_system)
  ldap_connect_system: successful connection to the LDAP server
[2012/08/11 11:55:18.050657,  2] passdb/pdb_ldap.c:572(init_sam_from_ldap)
  init_sam_from_ldap: Entry found for user: walkerm
[2012/08/11 11:55:18.078864,  2] auth/auth.c:304(check_ntlm_password)
  check_ntlm_password:  authentication for user [walkerm] -> [walkerm] -> [walkerm] succeeded

It starts to get an error: Not assigning privliges;
[2012/08/11 11:55:18.081893,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-21-4049939456-1513857517-1955023627-1104]
[2012/08/11 11:55:18.081969,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-10003]
[2012/08/11 11:55:18.082053,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2012/08/11 11:55:18.082124,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2012/08/11 11:55:18.082194,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-4]
[2012/08/11 11:55:18.082265,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-106]
[2012/08/11 11:55:18.082336,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-10000]
[2012/08/11 11:55:18.082409,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-21-4049939456-1513857517-1955023627-10010]

Don't know what happens here but look like a win!
[2012/08/11 11:55:18.084880,  3] smbd/password.c:282(register_existing_vuid)
  register_existing_vuid: User name: walkerm    Real name: Mitchell Walker
[2012/08/11 11:55:18.084963,  3] smbd/password.c:292(register_existing_vuid)
  register_existing_vuid: UNIX uid 1104 is UNIX user walkerm, and will be vuid 100
[2012/08/11 11:55:18.089404,  3] smbd/password.c:223(register_homes_share)
  Adding homes service for user 'walkerm' using home directory: '/home/walkerm'
[2012/08/11 11:55:18.089574,  3] param/loadparm.c:6265(lp_add_home)
  adding home's share [walkerm] for user 'walkerm' at '/home/walkerm'

This looks good too;
[2012/08/11 11:55:18.091680,  3] smbd/service.c:807(make_connection_snum)
  Connect path is '/tmp' for service [IPC$]
[2012/08/11 11:55:18.091797,  3] smbd/vfs.c:97(vfs_init_default)
  Initialising default vfs hooks
[2012/08/11 11:55:18.091888,  3] smbd/vfs.c:122(vfs_init_custom)
  Initialising custom vfs hooks from [/[Default VFS]/]

Again looks OKAY;
[2012/08/11 11:55:18.202356,  3] smbd/service.c:1070(make_connection_snum)
  ilikeflowers (10.5.31.254) connect to service IPC$ initially as user walkerm (uid=1104, gid=10003) (pid 1880)

This is ok too;
[2012/08/11 11:55:18.225525,  3] rpc_server/srv_pipe.c:2415(api_rpcTNP)
  api_rpcTNP: rpc command: SAMR_LOOKUPDOMAIN
[2012/08/11 11:55:18.225609,  2] rpc_server/srv_samr_nt.c:4124(_samr_LookupDomain)
  Returning domain sid for domain MONTGOMERY -> S-1-5-21-4049939456-1513857517-1955023627

Then it all goes bad;
2012/08/11 11:55:18.611965,  3] smbd/process.c:1298(switch_message)
  switch message SMBclose (pid 1880) conn 0x7f4bfd988260
[2012/08/11 11:55:18.611988,  3] smbd/reply.c:4653(reply_close)
  close fd=-1 fnum=5952 (numopen=1)
[2012/08/11 11:55:29.786738,  3] smbd/process.c:1489(process_smb)
  Transaction 37 of length 39 (0 toread)
[2012/08/11 11:55:29.786869,  3] smbd/process.c:1298(switch_message)
  switch message SMBtdis (pid 1880) conn 0x7f4bfd988260
[2012/08/11 11:55:29.786891,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/11 11:55:29.786972,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/11 11:55:29.787010,  3] smbd/service.c:1251(close_cnum)
  ilikeflowers (10.5.31.254) closed connection to service IPC$
[2012/08/11 11:55:29.787075,  3] smbd/connection.c:31(yield_connection)
  Yielding connection to IPC$
[2012/08/11 11:55:29.787184,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/11 11:55:29.787601,  3] smbd/process.c:1489(process_smb)
  Transaction 38 of length 43 (0 toread)
[2012/08/11 11:55:29.787648,  3] smbd/process.c:1298(switch_message)
  switch message SMBulogoffX (pid 1880) conn 0x0
[2012/08/11 11:55:29.787669,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/11 11:55:29.793241,  3] smbd/reply.c:2074(reply_ulogoffX)
  ulogoffX vuid=100
[2012/08/11 11:55:29.793946,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2012/08/11 11:55:29.794104,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2012/08/11 11:55:29.794327,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/11 11:55:29.794392,  3] smbd/connection.c:31(yield_connection)
  Yielding connection to
[2012/08/11 11:55:29.794560,  3] smbd/server.c:906(exit_server_common)
  Server exit (failed to receive smb request)

---

