---
title: "URGENT: Cannot list the TAPE files"
date: 2010-03-02
forum: Server Platforms
---

### Post by andremta on 2010-03-02
I've having problems in listing files from a TAPE. I did not create this tape and I'm assuming that the files were successfully backed up to this tape.

Some commands that I've tried:


[PHP]atenreiro@intranet:~$ sudo mt -f /dev/nst0 status
SCSI 2 tape drive:
File number=0, block number=0, partition=0.
Tape block size 512 bytes. Density code 0x47 (TR-5).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN
atenreiro@intranet:~$[/PHP]

[PHP]atenreiro@intranet:~$ sudo mt -f /dev/nst0 tell
At block 0.
atenreiro@intranet:~$[/PHP]

[PHP]atenreiro@intranet:~$ sudo tar -tzf /dev/st0
tar: /dev/st0: Cannot read: Input/output error
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors
atenreiro@intranet:~$[/PHP]


**dmesg log:**
[PHP]
...
[9712060.289420] st0: Incorrect block size.
...
[/PHP]

even with [PHP]mt -f /dev/nst0 setblk 512[/PHP] does not work!

---

### Post by andremta on 2010-03-02
How do I find out the correct TAPE Block Size?

---

