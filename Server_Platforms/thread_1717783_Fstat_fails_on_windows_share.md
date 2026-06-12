---
title: "Fstat fails on windows share"
date: 2011-03-30
forum: Server Platforms
---

### Post by kgeekworking on 2011-03-30
Using Ubuntu Server 10.04.  We have been running pgdbf for a long time to copy FoxPro tables located on a Windows machine to our Postgresql server.  Recently this script started to fail with an Fstat Error: Value too large for defined data type

To eliminate the pgdbf program, I wrote a few line program to call the fstat function on a file.  This call will pass on local files, however it will fail on the files on the share files.

As far as I can tell (not a C programmer) that the fstat call is returning more data than is defined in the stat structure.  I do not know enough C to try to debug what is being returned to cause the overrun.

This had been working fine for many months and just recently stopped, so I am guessing that this is some regression in either some of the samba packages or in the system calls.

My workstation (kubuntu 10.10) has the same fstab entries as the server and both the pgdbf program and my test program work find from my workstation.

Does anybody have any advice as to where to look, how to troubleshoot the extra data returned, or how to back track update history to see what may have caused the breakage.

Thanks.

---

