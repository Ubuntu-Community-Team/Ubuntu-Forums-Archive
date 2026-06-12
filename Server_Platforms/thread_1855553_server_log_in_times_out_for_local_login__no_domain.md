---
title: "server log in times out for local login  no domain master"
date: 2011-10-06
forum: Server Platforms
---

### Post by jazzon on 2011-10-06
Three machines all ubuntu 10.04 server 32 bit.
The machines all work independently of one another, no kerberos, no LDAP.
Two of the machines, when i attempt a local or a remote (SSH) login, will repeatedly give timeout errors on the login.  The only service they all share is samba, and none of the samba configs attempts to act as a master controller.  They all use the standard vote system.  All machines are able to authenticate for themselves, and all machines are set to allow only actual Linux account holders to be able to samba in.

Ive searched for months on many forums to try to get a fix for this and cant seem to find one.  Lots of posts describbing the same problem, but none seem to have been resolved.  Some blame PAM, some winbindd, and some LDAP/Kerberos or Samba.  So I am not sure what to make of it.

The /var/log/samba/log.winbindd shows a slew of errors, and as far as i know i dont NEED winbindd at all.  But if i remove it several needed packages get yanked as well.



-----cut paste of log.winbindd from recent ssh and local attempts----
[2011/10/06 12:04:26,  0] winbindd/winbindd.c:1258(main)
  winbindd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2011/10/06 12:04:26,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2011/10/06 12:05:11,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:05:11,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:05:11,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for SOUTHERN
[2011/10/06 12:05:11,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:06:14,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:06:14,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:07:20,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:07:20,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:08:30,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:08:30,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:08:30,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for SOUTHERN
[2011/10/06 12:08:30,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:09:12,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:09:12,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:09:12,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for SOUTHERN
[2011/10/06 12:09:12,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:09:55,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:09:55,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:09:55,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for SOUTHERN
[2011/10/06 12:09:55,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:09:55,  0] winbindd/winbindd_dual.c:186(async_request_timeout_handler)
  async_request_timeout_handler: child pid 1073 is not responding. Closing connection to it.
[2011/10/06 12:09:55,  1] winbindd/winbindd_util.c:303(trustdom_recv)
  Could not receive trustdoms
[2011/10/06 12:11:08,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:11:08,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:11:08,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for SOUTHERN
[2011/10/06 12:11:08,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:12:16,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:12:16,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:13:18,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:13:18,  1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
  failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:13:48,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:13:48,  1] rpc_client/cli_pipe.c:949(cli_pipe_validate_current_pdu)
  cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host SOUTHERN!
---------end cut/paste---------------------------------------------------

I dont have a clue how to configure winbindd, the man pages and most web resources are out of my league, but since there is no LDAP server can I:

1)  Remove winbind somehow;
2)  Configure it to not cause this issue (if it is the source);
and
3)  Would someone be kind enough to point me to a dummied down winbindd page to try to do these things.

---

### Post by capscrew on 2011-10-06
> **jazzon said:**
> Three machines all ubuntu 10.04 server 32 bit.
The machines all work independently of one another, no kerberos, no LDAP.
Two of the machines, when i attempt a local or a remote (SSH) login, will repeatedly give timeout errors on the login.  The only service they all share is samba, and none of the samba configs attempts to act as a master controller.  They all use the standard vote system.  All machines are able to authenticate for themselves, and all machines are set to allow only actual Linux account holders to be able to samba in.

Ive searched for months on many forums to try to get a fix for this and cant seem to find one.  Lots of posts describbing the same problem, but none seem to have been resolved.  Some blame PAM, some winbindd, and some LDAP/Kerberos or Samba.  So I am not sure what to make of it.
If all the hosts are set up for local linux login (this would include ssh) then winbind is not needed and indeed does create its own problems.  Winbind is used to map NT or AD domain user login databases to UNIX/Linux user logins> 
The /var/log/samba/log.winbindd shows a slew of errors, and as far as i know i dont NEED winbindd at all.  But if i remove it several needed packages get yanked as well.
**[COLOR="Blue"]What are all the packages that are removed?  What are the "*needed packages" * you are referring to?[/COLOR]**> 

```
-----cut paste of log.winbindd from recent ssh and local attempts----
[2011/10/06 12:04:26, 0] winbindd/winbindd.c:1258(main)
winbindd version 3.4.7 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
[2011/10/06 12:04:26, 0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2011/10/06 12:05:11, 1] lib/util_tdb.c:521(tdb_wrap_log)
tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:05:11, 0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:05:11, 1] lib/server_mutex.c:71(grab_named_mutex)
Could not get the lock for SOUTHERN
[2011/10/06 12:05:11, 0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:06:14, 0] libsmb/namequery.c:75(saf_store)
saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:06:14, 1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:07:20, 0] libsmb/namequery.c:75(saf_store)
saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:07:20, 1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:08:30, 1] lib/util_tdb.c:521(tdb_wrap_log)
tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:08:30, 0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:08:30, 1] lib/server_mutex.c:71(grab_named_mutex)
Could not get the lock for SOUTHERN
[2011/10/06 12:08:30, 0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:09:12, 1] lib/util_tdb.c:521(tdb_wrap_log)
tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:09:12, 0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:09:12, 1] lib/server_mutex.c:71(grab_named_mutex)
Could not get the lock for SOUTHERN
[2011/10/06 12:09:12, 0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:09:55, 1] lib/util_tdb.c:521(tdb_wrap_log)
tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:09:55, 0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:09:55, 1] lib/server_mutex.c:71(grab_named_mutex)
Could not get the lock for SOUTHERN
[2011/10/06 12:09:55, 0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:09:55, 0] winbindd/winbindd_dual.c:186(async_request_timeout_handler)
async_request_timeout_handler: child pid 1073 is not responding. Closing connection to it.
[2011/10/06 12:09:55, 1] winbindd/winbindd_util.c:303(trustdom_recv)
Could not receive trustdoms
[2011/10/06 12:11:08, 1] lib/util_tdb.c:521(tdb_wrap_log)
tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 122 ltype=1 (Interrupted system call)
[2011/10/06 12:11:08, 0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
tdb_chainlock_with_timeout_internal: alarm (40) timed out for key SOUTHERN in tdb /var/run/samba/mutex.tdb
[2011/10/06 12:11:08, 1] lib/server_mutex.c:71(grab_named_mutex)
Could not get the lock for SOUTHERN
[2011/10/06 12:11:08, 0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
cm_prepare_connection: mutex grab failed for SOUTHERN
[2011/10/06 12:12:16, 0] libsmb/namequery.c:75(saf_store)
saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:12:16, 1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:13:18, 0] libsmb/namequery.c:75(saf_store)
saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:13:18, 1] winbindd/winbindd_cm.c:977(cm_prepare_connection)
failed tcon_X with NT_STATUS_END_OF_FILE
[2011/10/06 12:13:48, 0] libsmb/namequery.c:75(saf_store)
saf_store: refusing to store 0 length domain or servername!
[2011/10/06 12:13:48, 1] rpc_client/cli_pipe.c:949(cli_pipe_validate_current_pdu)
cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host SOUTHERN!


```

I dont have a clue how to configure winbindd, the man pages and most web resources are out of my league, but since there is no LDAP server can I:

1)  Remove winbind somehow;
2)  Configure it to not cause this issue (if it is the source);
and
3)  Would someone be kind enough to point me to a dummied down winbindd page to try to do these things.

1. You should remove winbind if you are not using domain wide user login databases.

2. Winbind may not actually be the root cause.

3. I don't think there is a dummies explanation of how winbind works.  :-(

---

### Post by jazzon on 2011-10-06
@capscrew

lol was afraid of the "no dummies" response.

Last time i tried to pull winbindd, it also damaged my samba so badly I had to remove and reinstall it.  That was some time ago and unfortunately i do not recall what was removed.  I only began revisiting this stuff recently because my son needs remote access to these machines now, so much has been forgotten over time.

I will attempt a removal of winbind and get back to you to let you know what the exact issues were.

Oh yeah, by local I meant the keyboard was plugged into the computer in question.

---

### Post by capscrew on 2011-10-06
> **jazzon said:**
> @capscrew

lol was afraid of the "no dummies" response.

Last time i tried to pull winbindd, it also damaged my samba so badly I had to remove and reinstall it.  
There is only one file used to configure Samba.  Most likely you will not have to reinstall Samba.
That was some time ago and unfortunately i do not recall what was removed. 

I only began revisiting this stuff recently because my son needs remote access to these machines now, so much has been forgotten over time.
It helps to keep a journal of what you have done.  ;-)> 
I will attempt a removal of winbind and get back to you to let you know what the exact issues were.

Oh yeah, by local I meant the keyboard was plugged into the computer in question.

That's really an inadequate description of *local * login.  Local really means where the user database is in this context. For example ssh is a local login to the host (computer) from a remote host.

---

### Post by jazzon on 2011-10-06
@capscrew


hmmmm.....Linux For Dummies 101
  Chapter 1.)  Log files (and books!)

lol  I should really do that!  That not only makes sense, but should be common sense!  (Although i think it was Benjamin Franklin who said "Common sense realy is not all that common."  (he must have meant me)  )

Removed winbind, and now i cant seem to duplicate the original error, however that is not to surprising as the error was intermittent to begin with which is why I am having such a hard time with it.  Sometimes it would happen when there was a www connection to the computer, and some times it would not (network connection not user logged in), sometimes with no network wire at all, sometimes with, it has been a real puzzler.  The only think i have ruled out completely is hardware failure.  Pulled every piece and ran them for days on another machine without issue.  Motherboard also seems to be fine.  So this intermittent thing is weird.

On my 7th login with no issues.  Maybe a previous change was made to another file (samba config perhaps) which isn't there now.  It seems you were right that pulling it would solve it.  If I have no issues by tomorrow, i will remark this thread as solved.

As for local, i guess i didn't know what i was talking about.  I had the words right, but not the meaning.  Thanks for the correction.  A little knowledge can be a dangerous thing, and i just proved it!  ;)

---

### Post by capscrew on 2011-10-06
> **jazzon said:**
> @capscrew


hmmmm.....Linux For Dummies 101
  Chapter 1.)  Log files (and books!)

lol  I should really do that!  That not only makes sense, but should be common sense!  (Although i think it was Benjamin Franklin who said "Common sense realy is not all that common."  (he must have meant me)  )

Removed winbind, and now i cant seem to duplicate the original error, however that is not to surprising as the error was intermittent to begin with which is why I am having such a hard time with it.  Sometimes it would happen when there was a www connection to the computer, and some times it would not (network connection not user logged in), sometimes with no network wire at all, sometimes with, it has been a real puzzler.  The only think i have ruled out completely is hardware failure.  Pulled every piece and ran them for days on another machine without issue.  Motherboard also seems to be fine.  So this intermittent thing is weird.

On my 7th login with no issues.  Maybe a previous change was made to another file (samba config perhaps) which isn't there now.  It seems you were right that pulling it would solve it.  If I have no issues by tomorrow, i will remark this thread as solved.

As for local, i guess i didn't know what i was talking about.  I had the words right, but not the meaning.  Thanks for the correction.  A little knowledge can be a dangerous thing, and i just proved it!  ;)

I would wait a couple of days before marking it solved.  Maybe you should try to ssh to this host too.  I'll be here if you need help.

-Cap

---

