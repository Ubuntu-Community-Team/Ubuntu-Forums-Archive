---
title: "can't transfer &quot;big&quot; files..."
date: 2006-03-11
forum: Server Platforms
---

### Post by KevlarGurra on 2006-03-11
Hi

I have a strange problem with samba - I can't transfer files that are bigger than about 10kB from xp to ubuntu..... If I try it I get an error message that says "path too long" or something. I can see the file if I do an ls, and it is as big as it should be but I can't open it.... (small files work fine though)

Any ideas...?

---

### Post by dermotti on 2006-03-11
What version of samba?

---

### Post by KevlarGurra on 2006-03-11
Latest I think... I downloaded and installed it quite recently.

---

### Post by KevlarGurra on 2006-03-13
No one who knows anything?

---

### Post by derelict on 2006-03-13
Please post more details, namely about the error message

---

### Post by KevlarGurra on 2006-03-14
The only error message I get is "path too long" in xp when I try to copy a file that is bigger than ~10 kB. I can see the files if I ls, but if I try to open them from my xp comp, I get an error message that says "wrong file format" or something which suggests that something has happened to the file. I haven't checked the log files in Ubuntu yet, I'll do that tonight if I have time.

---

### Post by derelict on 2006-03-14
Try to copy a file that produces that error and right after that post:
 - the result of "tail /var/log/samba/yourcomputername.log"
 - the _exact_ error message
 - the _complete_ name and path of the file you're trying to copy (like "C:\Windows\debug\dcdiag.txt")

---

### Post by KevlarGurra on 2006-03-14
Strange...I don't seem to have a mycomputername.log-file (could that indicate something?)... 
I only have log.nmbd, log.smbd, log.smbd.old and log.winbindd in that directory. Do you want to see the tail of any of those files when I transfer a file?

---

### Post by derelict on 2006-03-14
I only want those three informations _right after_ a failed copy operation

---

### Post by KevlarGurra on 2006-03-14
Yeah, ok, but the problem is that I don't have a file named aldebaran.log (aldebaran is the name of my comp). Do you want to see the tail of any of my other files after a failed copy operation or do you know why I don't have a mycomp.log-file?
Thanks a lot for trying to help me out btw.

---

### Post by derelict on 2006-03-14
[QUOTE=KevlarGurra]Do you want to see the tail of any of my other files after a failed copy operation[/quote]
OK, post the tail of log.smbd and the two other informations.

> do you know why I don't have a mycomp.log-file?
Maybe your Samba server is configured to log machine information to some other place, we can take care of that afterwards.

---

### Post by KevlarGurra on 2006-03-14
Ok, here's the the output of log.smbd when I'm trying to copy c:\php\news.txt to \\aldebaran\gurra\test\news.txt
The error message in xp says "couldn't copy news.txt. Path too long."

```
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
Transaction 249 of length 100
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
switch message SMBntcreateX (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/error.c:error_packet(105)
error string = File exists
[2006/03/14 19:44:32, 3] smbd/error.c:error_packet(129)
error packet at smbd/trans2.c(2200) cmd=162 (SMBntcreateX) NT_STATUS_OBJECT_NAME_COLLISION
[2006/03/14 19:44:32, 3] smbd/sec_ctx.c:set_sec_ctx(288)
 setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
 Transaction 250 of length 90
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/sec_ctx.c:set_sec_ctx(288)
 setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfilepathinfo(2418)
  call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfilepathinfo(2452)
 call_trans2qfilepathinfo test (fnum = -1) level=1004 call=5 total_data=0
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
 Transaction 251 of length 80
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
  switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfilepathinfo(2418)
call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfilepathinfo(2452)
 call_trans2qfilepathinfo . (fnum = -1) level=1004 call=5 total_data=0
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
Transaction 252 of length 74
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
 switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfsinfo(1775)
 call_trans2qfsinfo: level = 261
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
 Transaction 253 of length 74
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfsinfo(1775)
 call_trans2qfsinfo: level = 261
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
 Transaction 254 of length 118
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
 switch message SMBntcreateX (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/dosmode.c:unix_mode(111)
unix_mode(test/news.txt) returning 0744
[2006/03/14 19:44:32, 2] smbd/open.c:open_file(245)
  gurra opened file test/news.txt read=No write=Yes (numopen=1)
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
 Transaction 255 of length 76
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
  switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfilepathinfo(2363)
 call_trans2qfilepathinfo: TRANSACT2_QFILEINFO: level = 1006
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfilepathinfo(2452)
 call_trans2qfilepathinfo test/news.txt (fnum = 6951) level=1006 call=7 total_data=0
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
Transaction 256 of length 74
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
 switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2qfsinfo(1775)
  call_trans2qfsinfo: level = 261
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
Transaction 257 of length 88
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
 switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2setfilepathinfo(3267)
 call_trans2setfilepathinfo(8) test/news.txt (fnum 6951) info_level=1020 totdata=8
[2006/03/14 19:44:32, 3] smbd/process.c:process_smb(1091)
  Transaction 258 of length 120
[2006/03/14 19:44:32, 3] smbd/process.c:switch_message(886)
 switch message SMBtrans2 (pid 7247) conn 0x83954f8
[2006/03/14 19:44:32, 3] smbd/trans2.c:call_trans2setfilepathinfo(3267)
 call_trans2setfilepathinfo(8) test/news.txt (fnum 6951) info_level=1004 totdata=40
[2006/03/14 19:45:45, 0] lib/util_sock.c:read_socket_data(384)
 read_socket_data: recv failure for 46908. Error = Connection reset by peer
[2006/03/14 19:45:45, 3] smbd/process.c:timeout_processing(1340)
 timeout_processing: receive_smb error (Connection reset by peer) Exiting
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 2] smbd/server.c:exit_server(609)
  Closing connections
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 3] smbd/service.c:close_cnum(830)
vega (192.168.0.2) closed connection to service IPC$
[2006/03/14 19:45:45, 3] smbd/connection.c:yield_connection(69)
Yielding connection to IPC$
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
 setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 2] smbd/close.c:close_normal_file(272)
 gurra closed file test/news.txt (numopen=0) 
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 1] smbd/service.c:close_cnum(830)
  vega (192.168.0.2) closed connection to service gurra
[2006/03/14 19:45:45, 3] smbd/connection.c:yield_connection(69)
 Yielding connection to gurra
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
 setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 3] smbd/service.c:close_cnum(830)
 vega (192.168.0.2) closed connection to service IPC$
[2006/03/14 19:45:45, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to IPC$
[2006/03/14 19:45:45, 3] smbd/sec_ctx.c:set_sec_ctx(288)
 setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/03/14 19:45:45, 3] smbd/connection.c:yield_connection(69)
 Yielding connection to 
[2006/03/14 19:45:45, 3] smbd/server.c:exit_server(652)
 Server exit (normal exit)

```

---

### Post by derelict on 2006-03-14
Don't you mean "the path is too deep"?
After a failed copy run "ifconfig eth0 | grep errors" and post it's result here please.

---

### Post by KevlarGurra on 2006-03-14
The error message is in Swedish, the word for "long" can in this case probably be translated to "deep" as well...

```
RX packets:26149 errors:0 dropped:0 overruns:0 frame:1889
TX packets:33375 errors:62 dropped:0 overruns:0 carrier:118

```

---

### Post by derelict on 2006-03-14
There are some transmission errors there (though it'd be more expectable to experience reception errors) and that problem has sometimes been associated with problematic network cards...do you have a spare card that you can try on instead of the one you're currently using?

---

### Post by Horndog on 2006-03-14
Zone Alarm firewall or quotas set in XP can do this.

---

### Post by KevlarGurra on 2006-03-20
I don't think it's my network card - it works perfectly when I use it for other purposes than Samba (ie routing). I don't use Zone alarm or quotas either. Maybe I should just reinstall the whole thing.

---

### Post by KevlarGurra on 2006-03-27
Solved!!!
It was my network card's fault...apparantly some (old) network cards have problems with samba (but not with other stuff)...

---

### Post by derelict on 2006-03-27
AHA! :mrgreen:

---

