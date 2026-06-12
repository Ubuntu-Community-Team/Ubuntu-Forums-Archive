---
title: "VirtualBox Terminal Doesn't Startup"
date: 2008-01-25
forum: Virtualisation
---

### Post by Sugi on 2008-01-25
I can't get the terminal to start up the Guest os.  My read outs:

> LongPENIS@LongPENIS:~$ VBoxManage startvm "Xp Professional SP2"
VirtualBox Command Line Management Interface Version 1.5.4
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling virtualBox->OpenRemoteSession(session, uuid, sessionType, env, progress.asOutParam()) at line 4377!
[!] Primary RC  = 0x80070005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070005
[!] Text        = A session for the machine 'Xp Professional SP2' is currently open (or being opened or closed)
[!] Component   = Machine, Interface: IMachine, {31f7169f-14da-4c55-8cb6-a3665186e35e}
[!] Callee      = IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
LongPENIS@LongPENIS:~$ 

How do I get the terminal to start up my guest os?  Don't I have to use the name of the VirtualBox in Identification as name box "Xp Professional SP2"?

---

### Post by ynef on 2008-01-25
The output states that an instance of the virtual machine is running, so you should check if that is the case and if so, nuke that process. By looking through the output of "ps aux" ("ps x" might be enough), you should be able to find the VirtualBox process. Shut it down, somehow -- either by using "kill" (supplying the process ID that you can find using the "ps" command from earlier) or via some other way -- perhaps VirtualBox has some command line switches or whatnot.

---

### Post by Sugi on 2008-01-25
Thank you.,  That worked. :)

Sugi

---

