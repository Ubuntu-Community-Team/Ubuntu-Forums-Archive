---
title: "dmraid error, hda-intel troubles and login time outs."
date: 2010-05-21
forum: Server Platforms
---

### Post by .ubik on 2010-05-21
I'm installing Ubuntu Server 10.04 (amd64) on a computer with fakeRAID. Now I'm getting strange errors when booting. From /var/log/messages

dmraid-activate: ERROR: Cannot retrieve RAID set information for pdc_ihiffc
kernel: hda-intel: Codec #0 probe error; disabling it...
kernel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000


The hda-intel error seems to be related to the motherboard sound card. 
The RAID error worries me tho, is it a problem?
"dmraid -r" gives me:
/dev/sdb: pdc, "pdc_ihiffc", mirror, ok, 624999936 sectors, data@ 0
/dev/sda: pdc, "pdc_ihiffc", mirror, ok, 624999936 sectors, data@ 0


However, the strangest issue is that it takes at least 4 login attempts to login without getting "Login timed out after 60 seconds". This started today, three days after the installation, and I have only messed with Samba so far. Could this be due to the other issues, or is it unrelated?

---

### Post by .ubik on 2010-05-21
I have worked some more on the login timed out error, but still got no solution.
If I try to login with any random string as username and password, it will give me a "login failed" instead of timed out, so at least there is some response. If I try to login over SSH, it will also time out and connection is reset by host.
There are nothing in messages or dmesg that will hint to a reason for this, other than the errors above.

Does anyone have a clue to what this can be, or where I can look to find out?

---

### Post by .ubik on 2010-05-24
I have made a little progress.
I reinstalled Ubuntu Server, and the dmraid errors went away.

The login time outs seems to be related to Samba.

First of all, the the 10.04 guide for configuring Samba as a PDC is wrong in the [netlogon] section, as "share modes" is not a valid parameter anymore. Debian bug report:
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/00212383277f212b]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/00212383277f212b")
Ubuntu Server Samba Guide:
[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html")

But correcting this does not seem to fix my login time outs. Instead, the time outs are related to errors in /var/log/samba/log.winbind , and these errors are not very consistent. I can get a flow of several reboots without any complications. I would appreciate any help I can get in understanding what these errors mean!

[INDENT]  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/05/24 12:38:47,  0] winbindd/winbindd_cache.c:2578(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/05/24 12:40:02,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 90 ltype=1 (Interrupted system call)
[2010/05/24 12:40:02,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key FILSERVER in tdb /var/run/samba/mutex.tdb
[2010/05/24 12:40:02,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for FILSERVER
[2010/05/24 12:40:02,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for FILSERVER
[2010/05/24 12:40:45,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 90 ltype=1 (Interrupted system call)
[2010/05/24 12:40:45,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key FILSERVER in tdb /var/run/samba/mutex.tdb
[2010/05/24 12:40:45,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for FILSERVER
[2010/05/24 12:40:45,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for FILSERVER
[2010/05/24 12:41:27,  1] lib/util_tdb.c:521(tdb_wrap_log)
  tdb(/var/run/samba/mutex.tdb): tdb_lock failed on list 90 ltype=1 (Interrupted system call)
[2010/05/24 12:41:27,  0] lib/util_tdb.c:69(tdb_chainlock_with_timeout_internal)
  tdb_chainlock_with_timeout_internal: alarm (40) timed out for key FILSERVER in tdb /var/run/samba/mutex.tdb
[2010/05/24 12:41:27,  1] lib/server_mutex.c:71(grab_named_mutex)
  Could not get the lock for FILSERVER
[2010/05/24 12:41:27,  0] winbindd/winbindd_cm.c:782(cm_prepare_connection)
  cm_prepare_connection: mutex grab failed for FILSERVER
[2010/05/24 12:42:37,  0] libsmb/namequery.c:75(saf_store)
  saf_store: refusing to store 0 length domain or servername!
[2010/05/24 12:42:37,  1] rpc_client/cli_pipe.c:949(cli_pipe_validate_current_pdu)
  cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host FILSERVER!
[2010/05/24 12:45:33,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/05/24 12:46:36,  0] winbindd/winbindd.c:1252(main)
  winbindd version 3.4.7 started.
[/INDENT]

---

### Post by freedumb2000 on 2010-06-04
This is an old thread, but I am on Lucid and i just hit the dreaded login timeout problem!
What seems to help is to disable winbind. Why? I have no idea :P But your post helped me get on the right track.

Edit:
Now, this seems to solve it, at least for Lucid:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg427544.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg427544.html)

---

