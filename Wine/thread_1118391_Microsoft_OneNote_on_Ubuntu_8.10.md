---
title: "Microsoft OneNote on Ubuntu 8.10"
date: 2009-04-06
forum: Wine
---

### Post by Dark Samurai on 2009-04-06
Hey all-
I have been trying to install Microsoft's OneNote on Ubuntu through WINE, and I always seem to get the same error message:
```
err:msidb:msi_table_load_transform no matching row to transform
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msid0e8.tmp":L"OfficeDataLockPermissions") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7e5f3eb8 "handle.c: MSI_object_cs" wait timed out in thread 0025, blocked by 004d, retrying (60 sec)
fixme:hook:IsWinEventHookInstalled (32773)-stub!
wine: Critical section 7e5f3eb8 wait failed at address 0x7bc3bfd0 (thread 0025), starting debugger...
Unhandled exception: wait failed on critical section 0x7e5f3eb8
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3bfd0
Process of pid=0057 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c 
	0000001f    0
	0000000e    0
	0000000d    0
0000000f 
	00000010    0
0000001c 
	00000022    0
	00000021    0
	0000001e    0
	0000001d    0
0000002d 
	00000035    0
	00000034    0
	0000002f    0
	0000002e    0
00000055 
	00000056    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```
That is just the final part of the error message.  The first line was repeated a ton before the other stuff.
Please help me figure out what is wrong!

---

### Post by aaroncoffman on 2009-04-09
Are you just trying to install one note or the office suite? 

I found [**_this link_**]("http://techsvk.blogspot.com/2009/02/microsoft-office-2007-running-in-ubuntu.html") that installs the office suite. Maybe it could guide you to install one note. I do want to let you know that I have heard if you get the 07 office products working they do have quite a bit of errors obviously. 

Also [**_here_**]("http://ubuntuforums.org/showthread.php?t=1121139") is a link to easily upgrade your WINE version.

Let us know how it goes!

---

### Post by Dark Samurai on 2009-04-09
Hey-
So I have the newest version of WINE.  The same issue occurred when i tried it again...

---

### Post by NightMKoder on 2009-04-10
I didn't know of anyone trying to install onenote without office. The install works if you install it with office 2007.

In terms of office 2007, PLEASE use [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840) and not that blog post. You will most likely have a lot of things crash when following those instructions (they're outdated).

Onenote 2007 works, but not with ink-created drawings. Take a look at the AppDB page for details [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899) .

---

### Post by aaroncoffman on 2009-04-10
Let me apologise for posting out of date information! I wasn't aware that there had been yet another update.

---

