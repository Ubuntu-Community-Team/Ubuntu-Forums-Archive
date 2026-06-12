---
title: "pvpgn server"
date: 2006-06-25
forum: Server Platforms
---

### Post by verbatim210 on 2006-06-25
my server is up and running, everything functions fine.
approximately after 2-3 days, it will die.
the problem can be temporarily fixed by STOP/START pvpgn.
after 3 days it will die again, so i STOPPED pvpgn, except this time i cannot START it back up.  here is some information from the log...

[I]Jun 26 09:49:06 [info ] eventlog_startup: logging event levels: fatal,error,warn,info,debug,trace
Jun 26 09:49:06 [debug] give_up_root_privileges: **about to give up root privileges**
Jun 26 09:49:06 [info ] pvpgn_greeting: PvPGN BnetD Mod version 1.8.0rc2 process 6539
Jun 26 09:49:06 [error] storage_init: **malformed storage_path , driver not found**
Jun 26 09:49:06 [error] pre_server_startup: **storage init failed**[/I]

anything pointing me in the right direction appreciated.

---

### Post by Kurt` on 2006-06-26
[QUOTE=verbatim210]Jun 26 09:49:06 [error] storage_init: **malformed storage_path , driver not found**[/QUOTE]
From that error, I can assume you were using a SQL database for storage. Perhaps PVPGN can no longer find the client libraries it requires to connect?

---

