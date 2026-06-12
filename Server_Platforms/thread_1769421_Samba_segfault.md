---
title: "Samba segfault?"
date: 2011-05-27
forum: Server Platforms
---

### Post by Ghosthaven on 2011-05-27
Hi all,
I'm still kinda a newbie to using Samba so I need a little help
with an email my home server just sent me (and saying that a
machine sent me an email without my control is both scary and
really cool).

As far as I can tell, my samba shares are all functioning
properly, but I still received this email:
```

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 27153 ().

This means there was a problem with the program, such as a segfault.
However, the executable could not be found for process 27153.
It may have died unexpectedly, or you may not have permission to debug
the process.

```

How would I go about tracking down whatever this problem is?

---

### Post by doas777 on 2011-05-27
I would start by using the System -> Administration -> Log File Viewer utility to look for related messages in kern.log, syslog.log, and check /var/log/samba for log files (in the log viewer, use file -> open and browse to it). 
the likelyhood is that the samba process has restarted and has a new PID, so the good news is that your server is recovering from the error. your logs should give some clue as to why the process is dying.

---

### Post by Ghosthaven on 2011-05-28
Well I think I found a related log file, but the output is all
greek to me.

I googled signal 11 and came up with a lot of people asking for
help but very few replies.

Log:
```

[2011/05/27 22:44:25.038298,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/27 22:44:25.038428,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 27153 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/27 22:44:25.038477,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/27 22:44:25.038518,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/27 22:44:25.038547,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 27153): internal error
[2011/05/27 22:44:25.060273,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/27 22:44:25.060589,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 27153]
[2011/05/27 22:44:25.148384,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/27 22:44:25.201912,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/27 22:44:30.205342,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 908)

```

Any clue what this means?

Also, I checked /var/log/samba/cores/smbd but there isn't a core
dump there. Its empty.

---

### Post by capscrew on 2011-05-28
> **Ghosthaven said:**
> Well I think I found a related log file, but the output is all
greek to me.

I googled signal 11 and came up with a lot of people asking for
help but very few replies.

Log:
```

[COLOR="Red"][2011/05/27 22:44:25.038298,  0] lib/fault.c:46(fault_report)[/COLOR]
  ===============================================================
[2011/05/27 22:44:25.038428,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 27153 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/27 22:44:25.038477,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/27 22:44:25.038518,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/27 22:44:25.038547,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 27153): internal error
[2011/05/27 22:44:25.060273,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/27 22:44:25.060589,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 27153]
[2011/05/27 22:44:25.148384,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/27 22:44:25.201912,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/27 22:44:30.205342,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 908)

```

Any clue what this means?

Also, I checked /var/log/samba/cores/smbd but there isn't a core
dump there. Its empty.

It would be informative if we could see the entries in the log just *before* the portion you posted (above the line I marked in red).

Are you running winbind?  Is this host part of Windows domain?

---

### Post by Ghosthaven on 2011-05-28
My apologies, the log was rather large (as the error has happened
many times) and I didn't know if there was a limit to post size so
I tried to figure out what was related to the most recent error
and post that.

I'll attempt to post the whole log now:

```


[2011/05/23 11:05:24.951900,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/23 11:05:25.117416,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service public initially as user andy (uid=1000, gid=1000) (pid 2199)
[2011/05/23 11:28:25.060125,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service public
[2011/05/23 11:49:36.923148,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. Permission denied
[2011/05/23 11:49:36.925031,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. Permission denied
[2011/05/23 11:49:36.926360,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:36.927640,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:36.928983,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:36.934040,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:38.033354,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:39.038153,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. Permission denied
[2011/05/23 11:49:39.039878,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:39.041124,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:39.042477,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:39.047508,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.052003,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.053930,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.055202,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.059735,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.061920,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.063154,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 11:49:40.064392,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/download failed. No such file or directory
[2011/05/23 13:02:08.863602,  0] lib/util_sock.c:680(write_data)
[2011/05/23 13:02:08.871138,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2011/05/23 13:02:08.871267,  0] smbd/process.c:79(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2011/05/23 13:02:14.658414,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2011/05/23 13:02:14.914523,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service music initially as user andy (uid=1000, gid=1000) (pid 6101)
[2011/05/23 13:02:15.100116,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2011/05/23 13:05:41.360474,  0] smbd/nttrans.c:2204(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.
[2011/05/23 16:13:42.785228,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/downloads failed. Permission denied
[2011/05/23 16:13:42.993022,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service downloads initially as user andy (uid=1000, gid=1000) (pid 6101)
[2011/05/23 16:13:53.184483,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service downloads
[2011/05/23 16:13:53.377270,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service downloads initially as user andy (uid=1000, gid=1000) (pid 6101)
[2011/05/23 16:14:03.611433,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service downloads
[2011/05/23 16:14:34.598372,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2011/05/23 16:16:55.520648,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/23 16:16:56.080985,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service public initially as user andy (uid=1000, gid=1000) (pid 6101)
[2011/05/23 16:17:09.738865,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/23 16:17:09.945663,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service public initially as user andy (uid=1000, gid=1000) (pid 6101)
[2011/05/23 20:34:31.670082,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service public
[2011/05/23 20:34:31.730218,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service public
[2011/05/23 20:34:31.790240,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service downloads
[2011/05/23 20:56:26.959687,  0] lib/util_sock.c:680(write_data)
[2011/05/23 20:56:26.970486,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2011/05/23 20:56:26.970594,  0] smbd/process.c:79(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2011/05/23 20:56:27.052147,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service public initially as user andy (uid=1000, gid=1000) (pid 1860)
[2011/05/23 20:56:27.515459,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/23 20:56:27.679520,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service public initially as user andy (uid=1000, gid=1000) (pid 1860)
[2011/05/23 20:56:30.254658,  0] smbd/nttrans.c:2204(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.
[2011/05/23 20:56:34.657787,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service music initially as user andy (uid=1000, gid=1000) (pid 1860)
[2011/05/23 20:56:34.962505,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2011/05/23 20:56:50.191420,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/23 20:56:50.191503,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 1860 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/23 20:56:50.191599,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/23 20:56:50.191636,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/23 20:56:50.191664,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 1860): internal error
[2011/05/23 20:56:50.200034,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb73b1a4d]
   #1 smbd(smb_panic+0x2d) [0xb73b1b6d]
   #2 smbd(+0x36352e) [0xb739f52e]
   #3 [0xb701d400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb713405c]
   #5 smbd(+0xff129) [0xb713b129]
   #6 smbd(reply_trans2+0x6a6) [0xb713cb86]
   #7 smbd(+0x12a106) [0xb7166106]
   #8 smbd(+0x12a4e2) [0xb71664e2]
   #9 smbd(+0x12aab4) [0xb7166ab4]
   #10 smbd(run_events+0x1b1) [0xb73c3041]
   #11 smbd(smbd_process+0x9d2) [0xb7165652]
   #12 smbd(+0x6cd1ec) [0xb77091ec]
   #13 smbd(run_events+0x1b1) [0xb73c3041]
   #14 smbd(+0x38733f) [0xb73c333f]
   #15 smbd(_tevent_loop_once+0x98) [0xb73c3978]
   #16 smbd(main+0xdaa) [0xb770a20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6c8cce7]
   #18 smbd(+0x9d751) [0xb70d9751]
[2011/05/23 20:56:50.200283,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 1860]
[2011/05/23 20:56:50.219982,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/23 20:56:50.220228,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/23 20:56:50.478342,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service music initially as user andy (uid=1000, gid=1000) (pid 1867)
[2011/05/23 21:00:33.962431,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service public initially as user andy (uid=1000, gid=1000) (pid 1867)
[2011/05/23 21:00:37.132844,  0] smbd/nttrans.c:2204(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x9005c): Currently not implemented.
[2011/05/24 00:27:31.597230,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service public
[2011/05/24 00:27:31.597454,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service music
[2011/05/24 00:27:33.042110,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2011/05/24 00:27:33.217726,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.100) connect to service music initially as user andy (uid=1000, gid=1000) (pid 5216)
[2011/05/24 13:53:06.459617,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/05/24 13:53:06.459738,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
[2011/05/24 13:53:06.459851,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.100) closed connection to service music
[2011/05/24 15:33:46.826902,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service music initially as user andy (uid=1000, gid=1000) (pid 30520)
[2011/05/24 15:33:47.068915,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2011/05/24 15:34:17.937740,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 30520)
[2011/05/24 15:34:18.130602,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/24 15:34:18.295943,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 30520)
[2011/05/25 12:55:04.789408,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 21622)
[2011/05/25 12:55:22.010387,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/25 12:55:22.266784,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 21622)
[2011/05/25 20:38:01.876416,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/25 20:42:22.891157,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/25 20:42:22.891265,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 21622 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/25 20:42:22.891314,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/25 20:42:22.891355,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/25 20:42:22.891388,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 21622): internal error
[2011/05/25 20:42:22.913014,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/25 20:42:22.913330,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 21622]
[2011/05/25 20:42:23.001470,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/25 20:42:23.024469,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/25 20:42:23.585283,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 18111)
[2011/05/25 20:42:26.353824,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 18111)
[2011/05/25 22:06:08.963425,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/25 22:17:42.864844,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/25 22:17:42.864950,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 18111 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/25 22:17:42.864999,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/25 22:17:42.865040,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/25 22:17:42.865072,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 18111): internal error
[2011/05/25 22:17:42.873756,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/25 22:17:42.874058,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 18111]
[2011/05/25 22:17:42.895277,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/25 22:17:42.910867,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
send-mail: 517 Syntax error.
[2011/05/25 22:17:43.611988,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 24690)
[2011/05/26 10:09:33.114589,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/26 10:09:33.466127,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 24690)
[2011/05/26 22:44:14.282024,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/26 22:44:20.970059,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/26 22:44:20.970171,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 24690 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/26 22:44:20.970219,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/26 22:44:20.970259,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/26 22:44:20.970290,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 24690): internal error
[2011/05/26 22:44:20.991814,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/26 22:44:20.992143,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 24690]
[2011/05/26 22:44:21.190891,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/26 22:44:21.223884,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/26 22:44:25.596922,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 30112)
[2011/05/26 22:44:25.618276,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 30112)
[2011/05/27 08:25:09.516667,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/27 08:32:51.989894,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/27 08:32:51.989993,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 30112 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/27 08:32:51.990042,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/27 08:32:51.990084,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/27 08:32:51.990114,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 30112): internal error
[2011/05/27 08:32:51.998519,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/27 08:32:51.998818,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 30112]
[2011/05/27 08:32:52.021464,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/27 08:32:52.021674,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
send-mail: 421 4.7.0 Temporary System Problem.  Try again later (). ck16sm114297vdb.32
[2011/05/27 08:33:57.644831,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 25247)
[2011/05/27 13:34:42.331808,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/27 13:34:42.487064,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 25247)
[2011/05/27 17:54:36.045247,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/27 20:46:20.644793,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/27 20:46:20.644900,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 25247 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/27 20:46:20.644957,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/27 20:46:20.644999,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/27 20:46:20.645030,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 25247): internal error
[2011/05/27 20:46:20.653460,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/27 20:46:20.671244,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 25247]
[2011/05/27 20:46:20.804348,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/27 20:46:20.820571,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/27 20:46:25.137240,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 27153)
[2011/05/27 21:37:49.870193,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/27 21:37:50.323681,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 27153)
[2011/05/27 22:44:23.064392,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/27 22:44:25.038298,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/27 22:44:25.038428,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 27153 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/27 22:44:25.038477,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/27 22:44:25.038518,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/27 22:44:25.038547,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 27153): internal error
[2011/05/27 22:44:25.060273,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7214a4d]
   #1 smbd(smb_panic+0x2d) [0xb7214b6d]
   #2 smbd(+0x36352e) [0xb720252e]
   #3 [0xb6e80400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f9705c]
   #5 smbd(+0xff129) [0xb6f9e129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f9fb86]
   #7 smbd(+0x12a106) [0xb6fc9106]
   #8 smbd(+0x12a4e2) [0xb6fc94e2]
   #9 smbd(+0x12aab4) [0xb6fc9ab4]
   #10 smbd(run_events+0x1b1) [0xb7226041]
   #11 smbd(smbd_process+0x9d2) [0xb6fc8652]
   #12 smbd(+0x6cd1ec) [0xb756c1ec]
   #13 smbd(run_events+0x1b1) [0xb7226041]
   #14 smbd(+0x38733f) [0xb722633f]
   #15 smbd(_tevent_loop_once+0x98) [0xb7226978]
   #16 smbd(main+0xdaa) [0xb756d20a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6aefce7]
   #18 smbd(+0x9d751) [0xb6f3c751]
[2011/05/27 22:44:25.060589,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 27153]
[2011/05/27 22:44:25.148384,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/27 22:44:25.201912,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/27 22:44:30.205342,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 908)
[2011/05/28 00:29:56.943474,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/05/28 00:29:56.943609,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
[2011/05/28 00:29:56.943709,  1] smbd/service.c:1251(close_cnum)
  x (192.168.1.103) closed connection to service public

```

I'm pretty sure that I'm not running winbind, I did the lazy/easy
method of just letting nautilus setup my samba share after many
days of fighting to set it up manually (and much help from this
forum, thanks guys :)

I am part of a windows workgroup, I edited etc/samba/smb.conf
to join the workgroup but beyond that, everything is setup by
nautilus.

The computers involved are server (the machine running ubuntu
and samba) and x (a windows xp machine with the samba shares
mounted as network drives).

At the time I got this log x machine was shut down, which is why
I'm assuming it says no route to host and connection closed.

I am no longer sharing the downloads directory but I am sharing
public and music.

Is there any other information you need? Again, sorry for only
posting a partial log before.

---

### Post by doas777 on 2011-05-28
lets take a look at the samba configuration and your file permissions on the server:
```

sudo testparm -s
sudo net usershare info
ls -al <path to pubic>
ls -al <path to download>
ls -al <path to music>

```

you can trim the ls commands, just leave '.', '..', and a handful of other entries for each. a mix of folders and files would be best.

---

### Post by capscrew on 2011-05-28
One can not overlook these major problems.  With so many errors the smbd daemon looks like it crashes and spits out errors.  The default is to not provide a dump. I have separated out the most egregious ones below.

Permissions problems?
```

param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: s[COLOR="Blue"]tat of /var/lib/samba/usershares/public failed. Permission denied[/COLOR]
param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of [COLOR="Green"]/var/lib/samba/usershares/download failed. Permission denied[/COLOR]
param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of [COLOR="Purple"]/var/lib/samba/usershares/music failed. Permission denied[/COLOR]

```
Location Problems?
```

param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of [COLOR="Green"]/var/lib/samba/usershares/download failed. No such file or director[/COLOR]

```
Nameservices Problems?
```

lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2011/05/23 13:02:08.871267,  0] smbd/process.c:79(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)

```

---

### Post by Ghosthaven on 2011-05-29
I apologize for taking a while to reply to your posts.

Here's the output of the commands doas777 asked me to run:

sudo testparm -s:
```


Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = GHOST2
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

sudo net usershare info:
nothing

ls -al /home/andy/Public:
```

drwxrwxrwx 20 andy   andy         4096 2011-05-28 17:04 .
drwxr-xr-x 52 andy   andy         4096 2011-05-29 00:06 ..
-rwxr--r--  1 nobody nogroup    187112 2011-05-25 16:38 aftershave coupon.xps
drwxr-xr-x  2 andy   andy         4096 2011-05-26 17:37 BT5-GNOME-32
-rwxr--r--  1 andy   andy         3275 2011-04-18 21:28 linux info.txt
drwxr-xr-x  2 andy   andy         4096 2011-05-24 19:38 backup

```

ls -al /home/andy/Downloads:
```

drwxr-xr-x  2 andy   andy       4096 2011-05-29 14:00 .
drwxr-xr-x 54 andy   andy       4096 2011-05-29 14:03 ..
-rw-r--r--  1 andy   andy      81794 2011-05-23 19:53 134401-Desu_Sheets (Death-Note) Emerald.emerald
-rw-r--r--  1 andy   andy     234960 2011-05-23 19:50 136218-Onux-Emerald.tar.gz
-rw-r--r--  1 andy   andy      41330 2011-05-23 19:48 139046-Hardware.emerald

```
Downloads should no longer be shared though, I disabled it
via nautilus.

ls -al /home/andy/Music:
```

drwxrwxrwx 132 andy   andy       12288 2011-05-24 03:22 .
drwxr-xr-x  54 andy   andy        4096 2011-05-29 14:03 ..
-rwxr--r--   1 nobody nogroup  3997894 2010-03-10 14:50 01 Track 01 22.m4a
-rwxr--r--   1 nobody nogroup  5960768 2009-05-09 09:02 10 - Nickelback - If Today Was Your Last Day.mp3
-rwxr--r--   1 andy   andy     4747438 2008-12-23 12:25 12 The Lakes of Pontchartrain.mp3
-rwxr--r--   1 andy   andy     8188315 2006-01-26 18:57 13 Overcome.mp3

```

I had a new problem pop up...one of the computers connected to
the lan (X) now requires username and password to access the
shares.

It works fine otherwise, but it just happened out of the blue
when I rebooted that computer.

The other computer on the lan works fine with the server.

Is setting up Samba on a linux system always this hard? Would
I be better off just simply creating a windows VM and using that
to share files?

---

### Post by doas777 on 2011-05-29
ok, it looks like your usershare configuration is messed up, which is related to the log entries capscrew pointed out. 

whats the output of
```
ls -al  /var/lib/samba/usershares
```

I'll be honest, classic samba is not for the faint of heart, but your issue is not normal for usershare scenarios. something is not right.

---

### Post by Ghosthaven on 2011-05-30
Thanks for the help, and the honesty.

I'm no stranger to computer problems (been working with computers
since the ancient 8086 days) but I had assumed it wouldn't be so
hard to setup/fix such an important feature.

I'm assuming pretty much everyone with a lan uses Samba... so it
seems that the process could be a bit easier.

Here's the output of the command you asked for:
```

drwxrwx--T 2 root sambashare 4096 2011-05-24 00:23 .
drwxr-xr-x 5 root root       4096 2011-05-23 11:01 ..
-rw-r--r-- 1 andy andy         77 2011-05-23 13:01 music
-rw-r--r-- 1 andy andy         78 2011-05-23 11:03 public

```

Thanks again.

Edit:
Here's the contents of the two files as well:
Public:
```

#VERSION 2
path=/home/andy/Public
comment=
usershare_acl=S-1-1-0:F
guest_ok=y

```

Music:
```

#VERSION 2
path=/home/andy/Music
comment=
usershare_acl=S-1-1-0:F
guest_ok=y

```

Hope that helps.

---

### Post by capscrew on 2011-05-30
> **doas777 said:**
> ok, it looks like your usershare configuration is messed up, which is related to the log entries capscrew pointed out. 

whats the output of
```
ls -al  /var/lib/samba/usershares
```

I'll be honest, classic samba is not for the faint of heart, but your issue is not normal for usershare scenarios. something is not right.

I think that any complex application can be a PITA if not understood or there is no tutorial for the average user.  On the other hand it can be made harder than it need be.  I have described the basic idea [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823&highlight=atomicben") at post #6 on.  The tutorial I reference can be see [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1590").

I personally don't like Samba usershares.  They were created for users that have only had experience with the way shares are created on Windows hosts.

@Ghosthaven:

Too many cooks spoil the broth...  I'm here, but I'll let doas777 take the lead.

---

### Post by doas777 on 2011-05-31
ok, it looks like the permissions are off on your usershare files.

try this:
```
sudo chgrp sambashare /var/lib/samba/usershares/*
```then restart samba or reboot:
```
sudo service smbd restart
```and try this again:
```

sudo net usershare info

```and give it a test. do the log entries continue to come up?

---

### Post by Ghosthaven on 2011-05-31
Yes, unfortunately the log files still report a panic and I still
receive the emails.

I changed the groups as you said, and ls does show they are now
part of the sambashare group.

Unfortunately sudo net usershare info still does nothing.
I both restarted samba with the command you said, and did an
actual shutdown/restart cycle.

Any clue what else could be wrong?

---

### Post by doas777 on 2011-05-31
at this point, I am quite confused, so this is just a shot in the dark, but can you change the permissions on /home/andy/public/ to 777, and see if that has any effect?

also try dropping the 'sudo' from the net usershare info command. perhaps it is looking for roots usershare config.

---

### Post by capscrew on 2011-05-31
> **Ghosthaven said:**
> Yes, unfortunately the log files still report a panic and I still receive the emails.
Is there any change it the log files.  There was plenty of information on usershares that did not exist as well as permissions not being correct.> 

I changed the groups as you said, and ls does show they are now
part of the sambashare group.

Unfortunately sudo net usershare info still does nothing.
I both restarted samba with the command you said, and did an
actual shutdown/restart cycle.

Any clue what else could be wrong?
This ```
path=/home/andy/Public

path=/home/andy/Music
```

Is not the same as this ```
-rw-r--r-- 1 andy andy         78 2011-05-23 11:03 public

-rw-r--r-- 1 andy andy         77 2011-05-23 13:01 music

```

What do you get from this```
getent group|grep sambashare
```

At this point I feel you should delete the usershares from the /var/lib/samba/usershares directory and start over.

As far as directory permissions go: the /var/lib/samba/usershares need to be at least 755.  This allows the owner (root) to modify it. and all others (groups and others) to traverse it.  That is all that is needed.  Nautilus will create the new usershares with the proper permissions if you tick the correct boxes *share, allow others, Guest access * or whatever.

How about you just remove the usershares, restart Samba and post the latest part of the logs back here.

---

### Post by Ghosthaven on 2011-06-01
doas777:
I already had both Public and Music set to 777.

Dropping sudo worked, I'm shocked that I didn't think to even try that.
Guess my head wasn't on straight.

Output:
```

[music]
path=/home/andy/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[public]
path=/home/andy/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

capscrew:
Here's the last bit of the log file from just after the most recent
change that doas777 suggested:
```

[2011/05/31 21:30:46.998796,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 2092)
[2011/05/31 21:30:55.502514,  0] smbd/nttrans.c:2204(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.
[2011/05/31 21:37:33.309554,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2011/05/31 21:37:42.246321,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2011/05/31 21:37:42.246413,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 2092 (3.5.4)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2011/05/31 21:37:42.246461,  0] lib/fault.c:49(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2011/05/31 21:37:42.246501,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2011/05/31 21:37:42.246530,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 2092): internal error
[2011/05/31 21:37:42.252091,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb71e9a4d]
   #1 smbd(smb_panic+0x2d) [0xb71e9b6d]
   #2 smbd(+0x36352e) [0xb71d752e]
   #3 [0xb6e55400]
   #4 smbd(smbd_do_qfsinfo+0x99c) [0xb6f6c05c]
   #5 smbd(+0xff129) [0xb6f73129]
   #6 smbd(reply_trans2+0x6a6) [0xb6f74b86]
   #7 smbd(+0x12a106) [0xb6f9e106]
   #8 smbd(+0x12a4e2) [0xb6f9e4e2]
   #9 smbd(+0x12aab4) [0xb6f9eab4]
   #10 smbd(run_events+0x1b1) [0xb71fb041]
   #11 smbd(smbd_process+0x9d2) [0xb6f9d652]
   #12 smbd(+0x6cd1ec) [0xb75411ec]
   #13 smbd(run_events+0x1b1) [0xb71fb041]
   #14 smbd(+0x38733f) [0xb71fb33f]
   #15 smbd(_tevent_loop_once+0x98) [0xb71fb978]
   #16 smbd(main+0xdaa) [0xb754220a]
   #17 /lib/libc.so.6(__libc_start_main+0xe7) [0xb6ac1ce7]
   #18 smbd(+0x9d751) [0xb6f11751]
[2011/05/31 21:37:42.252185,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 2092]
[2011/05/31 21:37:42.327136,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/05/31 21:37:42.327281,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2011/05/31 21:37:47.691766,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 2666)
[2011/05/31 21:48:21.991430,  0] smbd/nttrans.c:2204(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.
[2011/05/31 23:39:14.300418,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied

```

I assume that by path=/home/andy/Public not being the same as
-rw-r--r-- 1 andy andy         78 2011-05-23 11:03 public
that your talking about the case of the directory name, its correct
as far as I know. For some reason the usershares listing does have
them converted to lowercase, but inside the usershares it has the
correct path.

The output from getent group|grep sambashare:
```

sambashare:x:122:andy

```


So by deleting it I assume you mean just
```

sudo rm /var/lib/samba/usershares/*
sudo service smbd restart

```
and then reset the shares in nautilus by right clicking on the Public
directory and going to Sharing Options then checking the three boxes?
Sorry to be dense, but I want to make sure I understand before I go
deleting stuff.

As far as the /var/lib/samba/usershares permission, it was previously
```

drwxrwx--T 2 root sambashare 4096 2011-05-24 00:23 /var/lib/samba/usershares

```
I set it to 775 but it spit out a new error in the logs:
```

[2011/06/01 00:35:29.257305,  0] param/loadparm.c:8909(load_usershare_service)
  load_usershare_service: directory /var/lib/samba/usershares is not owned by root or does not have the sticky bit 't' set or is writable by anyone.

```

So I just did sudo chmod +t /var/lib/samba/usershares

No real change that I can see, it still requires me to enter my password
to access the share. I have to wait to see if it panics... it
seems rather random when it does. I'll notify you one way or
another soon.


I did notice something interesting though.
In log.x (the log related to my desktop) it has this:
```

[2011/06/01 06:20:08.230679,  1] smbd/service.c:1070(make_connection_snum)
  x (192.168.1.103) connect to service public initially as user andy (uid=1000, gid=1000) (pid 26749)
[2011/06/01 06:20:34.280136,  0] smbd/nttrans.c:2204(call_nt_transact_ioctl)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.

```

But in log.stardust (my wife's computer) it has:
```

[2011/06/01 06:22:16.065572,  1] smbd/service.c:1070(make_connection_snum)
  stardust (192.168.1.101) connect to service public initially as user nobody (uid=65534, gid=65534) (pid 26860)

```
and doesn't request a password.

It seems that on a windows system connecting to it that has the username
andy it'll request a password. It still panicked before with any
computer connected but that's something of note I think. Can I do
something like force user= nobody and have it not require a password?

---

### Post by Ghosthaven on 2011-06-03
Several days now and no problems other than having to enter my
password on any machine where my account name is the same as the
username on the server.

I can get used to the password thing, I'm just glad samba is
finally working.

Thanks to everyone who helped me out!

---

