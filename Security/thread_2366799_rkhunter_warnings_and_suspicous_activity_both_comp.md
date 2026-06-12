---
title: "rkhunter warnings and suspicous activity both computers"
date: 2017-07-21
forum: Security
---

### Post by jeff666 on 2017-07-21
I'm think some one might be remote accessing my machines and running Firefox scripts. I have no proof with sockets, process, files. logs seam a little odd (but nothing definitive) and tripwire is hard to tell because im always changing stuff. The main thing im suspicous of is after a update my drive encryption magically disappeared! I'm thinking a root kit any advice?
here are the rkhunter results:

[19:12:23]   /usr/bin/lwp-request                            [ Warning ]

 [19:12:23] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable
 
 
 [19:13:15]   Checking /dev for suspicious file types         [ Warning ]
 [19:13:15] Warning: Suspicious file types found in /dev:
 [19:13:15]          /dev/shm/pulse-shm-4084307814: data

 [19:13:15]          /dev/shm/pulse-shm-2591725429: data

 [19:13:15]          /dev/shm/pulse-shm-4232073678: data
 [19:13:15]          /dev/shm/pulse-shm-3356329673: data
 [19:13:15]          /dev/shm/pulse-shm-1613302195: data
 [19:13:15]          /dev/shm/pulse-shm-2559727733: data
 [19:13:15]          /dev/shm/pulse-shm-3780778465: data
 [19:13:15]          /dev/shm/pulse-shm-476975036: data
 [19:13:15]          /dev/shm/ecryptfs-bb-Private: ASCII text
 [19:13:15]          /dev/shm/pulse-shm-3800984784: data
 [19:13:15]          /dev/shm/pulse-shm-1823948470: data
 [19:13:15]          /dev/shm/pulse-shm-1065044916: data
 [19:13:15]   Checking for hidden files and directories       [ Warning ]
 [19:13:15] Warning: Hidden directory found: /etc/.java

---

