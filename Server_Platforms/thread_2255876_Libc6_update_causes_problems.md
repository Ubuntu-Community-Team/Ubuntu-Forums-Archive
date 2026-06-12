---
title: "Libc6 update causes problems?"
date: 2014-12-08
forum: Server Platforms
---

### Post by Michel2k on 2014-12-08
It seems an automatic update of libc6 caused one of my servers to display erratic behaviour.
The update shows up as: 
```
Preparing to replace libc6 2.15-0ubuntu10.7 (using .../libc6_2.15-0ubuntu10.9_amd64.deb) ...
```
And it was installed 4 Dec 2014 07:00 hours CET

After that my Samba daemon smbd started crashing regularly:

```

[2014/12/08 09:29:29.873516,  0] lib/util.c:1221(log_stack_trace)                                     
  BACKTRACE: 6 stack frames:                                                                          
   #0 smbd(log_stack_trace+0x1a) [0x7f09e19e54ba]                                                     
   #1 smbd(+0x6864a3) [0x7f09e1c534a3]                                                                
   #2 smbd(+0x6867a1) [0x7f09e1c537a1]                                                                
   #3 smbd(main+0xa52) [0x7f09e16c3be2]                                                               
   #4 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f09de57176d]                        
   #5 smbd(+0xf7545) [0x7f09e16c4545]                                                                 
[2014/12/08 09:29:29.873659,  0] lib/fault.c:372(dump_core)                                           
  dumping core in /var/log/samba/cores/smbd                                                           

```

I restarted the server today, hoping this problem was caused by replacing libc6 itself (have not seen those kind of problems for a *really* long time)
Another side effect of the libc6 update seems to be that the DHCP client seems to behave differently, causing it to re-request the lease more often than it should. As a result, it signals smbd with SIGHUP's a few times an hour. (I have installed isc-dhcp-client,  4.1.ESV-R4-0ubuntu5)

Anyone else experiencing these 2 problems?

---

