---
title: "Server 10.04, pam/winbind, delayed logins"
date: 2011-01-07
forum: Server Platforms
---

### Post by NIT006.5 on 2011-01-07
Another strange problem on 10.04 when running as a domain controller with Samba/LDAP: After initial boot-up, no login is possible for at least 3 minutes. I can login immediately via ssh, if an ssh key is configured, but anything requiring password authentication times out for several minutes and then magically starts working. This exact issue has already been discussed here: [http://ubuntuforums.org/showthread.php?t=1562869](http://ubuntuforums.org/showthread.php?t=1562869)

However, while that thread is marked as solved, the issue actually hasn't been solved. The only suggested solutions are to either completely disable all domain controller functionality, or to stop pam from waiting for winbind, which in turn means that any LDAP users will still be unable to log in. Other proposed solutions found elsewhere were to completely remove winbind, but this appears to be necessary for LDAP users to authenticate on the local server.

/var/log/samba/log.windbind shows:

```

[2011/01/07 22:09:39,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2011/01/07 22:10:24,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 91 ltype=1 (Interrupted system call)
[2011/01/07 22:10:24,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key MAIL in tdb /var/run/samba/mutex.tdb
[2011/01/07 22:10:24,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for MAIL
[2011/01/07 22:10:24,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for MAIL
[2011/01/07 22:11:27,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/01/07 22:11:27,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/01/07 22:12:33,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/01/07 22:12:33,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/01/07 22:13:43,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 91 ltype=1 (Interrupted system call)
[2011/01/07 22:13:43,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key MAIL in tdb /var/run/samba/mutex.tdb
[2011/01/07 22:13:43,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for MAIL
[2011/01/07 22:13:43,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for MAIL
[2011/01/07 22:14:53,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/01/07 22:14:53,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/01/07 22:16:03,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/01/07 22:16:03,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/01/07 22:16:03,  0] winbindd/winbindd_dual.c:186(async_request_timeout_handler)
  async_request_timeout_handler: child pid 1834 is not responding. Closing connection to it.
[2011/01/07 22:16:03,  1] winbindd/winbindd_util.c:303(trustdom_recv)
  Could not receive trustdoms
[2011/01/07 22:16:33,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/01/07 22:16:33,  1] rpc_client/cli_pipe.c:949(cli_pipe_validate_current_pdu)
  cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host MAIL!

```

But this is as far as I can get. Googling those errors, I have only been able to find others with the same problem whose posts have either gone unanswered, or who have been told to disable winbind or domain controller functionality, which isn't really a solution.

At first glance I would think that perhaps it is some sort of winbind configuration that is need, but then why does it start working several minutes later?

However, trying to check winbind authentication manually, with wbinfo -a username%password, I get:

```

plaintext password authentication failed
Could not authenticate user username%xxxxx with plaintext password
challenge/response password authentication failed
error code was NT_STATUS_CANT_ACCESS_DOMAIN_INFO (0xc00000da)
error messsage was: NT_STATUS_CANT_ACCESS_DOMAIN_INFO
Could not authenticate user username with challenge/response

```

I even get the above response after normal authentication has started to work on both the server and Windows clients.

I have been looking at this issue for so long that there is quite possibly something staring me in the face that I'm just not seeing. Any thoughts??

---

### Post by NIT006.5 on 2011-01-08
Haha. As expected, the solution is so simple I could slap myself. Even though the local host is the domain controller, it must still be specifically added to its own domain for winbind to authenticate properly.

```

net rpc join -U administrator%password

```

After three painful days of searching, problem solved. (Thanks to this post: [http://osdir.com/ml/network.samba.internals/2002-06/msg00216.html](http://osdir.com/ml/network.samba.internals/2002-06/msg00216.html))

---

### Post by NIT006.5 on 2011-01-08
Haha. As expected, the solution is so simple I could slap myself. Even though the local host is the domain controller, it must still be specifically added to its own domain for winbind to authenticate properly.

```

net rpc join -U administrator%password

```

After three painful days of searching, problem solved. (Thanks to this post: [http://osdir.com/ml/network.samba.internals/2002-06/msg00216.html](http://osdir.com/ml/network.samba.internals/2002-06/msg00216.html))

---

