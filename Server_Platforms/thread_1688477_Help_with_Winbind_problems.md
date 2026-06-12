---
title: "Help with Winbind problems"
date: 2011-02-15
forum: Server Platforms
---

### Post by wedge1212 on 2011-02-15
I'm having a very odd problem with a machine running 9.04.  The machine can successfully join a server 2008r2 domain but authentication to shares and other applications (ftp) that use winbind authentication fail.  I've also verified my kerberos configuration is good.  I can run a kinit username and provide my password successfully.

wbinfo -t fails
wbinfo -u fails
wbinfo -g fails

 here's a snippet of my log.winbindd file:

[2011/02/15 14:02:33,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2011/02/15 14:03:18,  1] lib/util_tdb.c:tdb_wrap_log(886)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 92 ltype=1 (Interrupted system call)
[2011/02/15 14:03:18,  0] lib/util_tdb.c:tdb_chainlock_with_timeout_internal(91)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key plano-dc1a in tdb /var/run/samba/mutex.tdb
[2011/02/15 14:03:18,  1] lib/server_mutex.c:grab_named_mutex(71)
  Could not get the lock for plano-dc1a
[2011/02/15 14:03:18,  0] winbindd/winbindd_cm.c:cm_prepare_connection(782)
  cm_prepare_connection: mutex grab failed for plano-dc1a
[2011/02/15 14:06:18,  1] libsmb/clikrb5.c:ads_krb5_mk_req(686)
  ads_krb5_mk_req: krb5_get_credentials failed for domaincontroller$@DENBURY-D1 (Cannot resolve network address for KDC in requested realm)
[2011/02/15 14:06:18,  1] libsmb/cliconnect.c:cli_session_setup_kerberos(624)
  cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: Cannot resolve network address for KDC in requested realm
[2011/02/15 14:06:18,  0] lib/util_sock.c:write_data(1139)
  write_data: write failure. Error = Connection reset by peer
[2011/02/15 14:06:18,  0] libsmb/clientgen.c:write_socket(242)
  write_socket: Error writing 170 bytes to socket 19: ERRNO = Connection reset by peer
[2011/02/15 14:06:18,  0] libsmb/clientgen.c:cli_send_smb(290)
  Error writing 170 bytes to client. -1 (Connection reset by peer)
[2011/02/15 14:09:13,  1] libsmb/clikrb5.c:ads_krb5_mk_req(686)
  ads_krb5_mk_req: krb5_get_credentials failed for domaincontroller$@DENBURY-D1 (Cannot resolve network address for KDC in requested realm)
[2011/02/15 14:09:13,  1] libsmb/cliconnect.c:cli_session_setup_kerberos(624)
  cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: Cannot resolve network address for KDC in requested realm
[2011/02/15 14:09:13,  0] lib/util_sock.c:write_data(1139)
  write_data: write failure. Error = Connection reset by peer
[2011/02/15 14:09:13,  0] libsmb/clientgen.c:write_socket(242)
  write_socket: Error writing 170 bytes to socket 19: ERRNO = Connection reset by peer
[2011/02/15 14:09:13,  0] libsmb/clientgen.c:cli_send_smb(290)
  Error writing 170 bytes to client. -1 (Connection reset by peer)
[2011/02/15 14:09:13,  0] winbindd/winbindd_dual.c:async_request_timeout_handler(186)
  async_request_timeout_handler: child pid 6519 is not responding. Closing connection to it.
[2011/02/15 14:09:13,  1] winbindd/winbindd_util.c:trustdom_recv(303)
  Could not receive trustdoms
[2011/02/15 14:09:13,  1] winbindd/winbindd_util.c:trustdom_recv(303)
  Could not receive trustdoms
[2011/02/15 14:10:03,  1] lib/util_tdb.c:tdb_wrap_log(886)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 75 ltype=1 (Interrupted system call)
[2011/02/15 14:10:03,  0] lib/util_tdb.c:tdb_chainlock_with_timeout_internal(91)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key domaincontroller.denbury.com in tdb /var/run/samba/mutex.tdb
[2011/02/15 14:10:03,  1] lib/server_mutex.c:grab_named_mutex(71)
  Could not get the lock for domaincontroller.denbury.com
[2011/02/15 14:10:03,  0] winbindd/winbindd_cm.c:cm_prepare_connection(782)
  cm_prepare_connection: mutex grab failed for domaincontroller.denbury.com
[2011/02/15 14:10:43,  1] lib/util_tdb.c:tdb_wrap_log(886)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 75 ltype=1 (Interrupted system call)
[2011/02/15 14:10:43,  0] lib/util_tdb.c:tdb_chainlock_with_timeout_internal(91)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key domaincontroller.denbury.com in tdb /var/run/samba/mutex.tdb
[2011/02/15 14:10:43,  1] lib/server_mutex.c:grab_named_mutex(71)
  Could not get the lock for domaincontroller.denbury.com
[2011/02/15 14:10:43,  0] winbindd/winbindd_cm.c:cm_prepare_connection(782)
  cm_prepare_connection: mutex grab failed for domaincontroller.denbury.com
[2011/02/15 14:11:23,  1] lib/util_tdb.c:tdb_wrap_log(886)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 75 ltype=1 (Interrupted system call)
[2011/02/15 14:11:23,  0] lib/util_tdb.c:tdb_chainlock_with_timeout_internal(91)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for keydomaincontroller.denbury.com in tdb /var/run/samba/mutex.tdb
[2011/02/15 14:11:23,  1] lib/server_mutex.c:grab_named_mutex(71)
  Could not get the lock for domaincontroller.denbury.com
[2011/02/15 14:11:23,  0] winbindd/winbindd_cm.c:cm_prepare_connection(782)
  cm_prepare_connection: mutex grab failed for domaincontroller.denbury.com

---

