---
title: "Ubuntu 9.10 samba 3.4.0 -&gt; 3.4.2"
date: 2010-01-08
forum: Server Platforms
---

### Post by LarsEriksson on 2010-01-08
Hello.

I have a lot of problems with Windows 7 / Server 2008R2-computers joining my Samba 3.4.0 domain, so i thought an update of Samba could solve this since i read in changelogs that 3.4.2 should work better with theese new Windows versions.

So, i added the Lucid repo and updated samba, samba-common etc., but it wouldnt start.

This is what i got in log.smbd:
```
[2010/01/08 08:49:31,  0] smbd/server.c:1069(main)
  smbd version 3.4.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/01/08 08:49:31,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2010/01/08 08:49:31,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 6 in pid 10505 (3.4.3)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2010/01/08 08:49:31,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2010/01/08 08:49:31,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2010/01/08 08:49:31,  0] lib/util.c:1480(smb_panic)
  PANIC (pid 10505): internal error
[2010/01/08 08:49:31,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 18 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x1a) [0x7f4b551a982a]
   #1 /usr/sbin/smbd(smb_panic+0x1f) [0x7f4b551a98ef]
   #2 /usr/sbin/smbd [0x7f4b5519903d]
   #3 /lib/libpthread.so.0 [0x7f4b535f4190]
   #4 /lib/libc.so.6(gsignal+0x35) [0x7f4b519754b5]
   #5 /lib/libc.so.6(abort+0x180) [0x7f4b51978f50]
   #6 /usr/lib/libtalloc.so.1 [0x7f4b5086cbbb]
   #7 /usr/lib/libtalloc.so.1(talloc_free+0x21c) [0x7f4b50870dcc]
   #8 /usr/lib/libwbclient.so.0(wbcSidToGid+0xe0) [0x7f4b51cb5c10]
   #9 /usr/sbin/smbd(winbind_sid_to_gid+0x5f) [0x7f4b5517996f]
   #10 /usr/sbin/smbd(sid_to_gid+0x13b) [0x7f4b5515a2db]
   #11 /usr/sbin/smbd(create_local_nt_token+0x252) [0x7f4b551f7cc2]
   #12 /usr/sbin/smbd(get_root_nt_token+0xc3) [0x7f4b551f80e3]
   #13 /usr/sbin/smbd(svcctl_init_keys+0x24) [0x7f4b550c0884]
   #14 /usr/sbin/smbd(registry_init_full+0x66) [0x7f4b55405bc6]
   #15 /usr/sbin/smbd(main+0x735) [0x7f4b55437f45]
   #16 /lib/libc.so.6(__libc_start_main+0xfd) [0x7f4b51960abd]
   #17 /usr/sbin/smbd [0x7f4b54f51429]
[2010/01/08 08:49:31,  0] lib/util.c:1485(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 10505]
[2010/01/08 08:49:31,  0] lib/util.c:1493(smb_panic)
  smb_panic(): action returned status 0
[2010/01/08 08:49:31,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/01/08 08:50:32,  0] smbd/server.c:main(1213)
  smbd version 3.2.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2010/01/08 08:50:32,  0] passdb/pdb_tdb.c:tdbsam_open(853)
  tdbsam_open: unknown version => 4
[2010/01/08 08:50:32,  0] passdb/pdb_tdb.c:tdbsam_getsampwnam(903)
  tdbsam_getsampwnam: failed to open /var/lib/samba/passdb.tdb!

```

What am i doing wrong?

---

