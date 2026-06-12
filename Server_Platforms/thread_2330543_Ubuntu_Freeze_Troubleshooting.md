---
title: "Ubuntu Freeze Troubleshooting"
date: 2016-07-12
forum: Server Platforms
---

### Post by jared32 on 2016-07-12
Hello,

I am trying to troubleshoot a new issue on an ubuntu server and am having issues determining the next steps to take.

The sever has an ubuntu x32 14.04 sever that has been hardened to CIS lvl 2 standards. The server runs a custom application gui on boot.

The server setup has been experiencing an issue where the system will freeze. The freeze means that the gui still shows but all inputs do not work. Further, I cannot ssh into the box and the box stops producing logs when the freeze occurs.

Based on some preliminary testing, the freeze happens under the following conditions. 1, when the system is idle (seems to happen over weekends). 2, when all required peripherals are connected.

Now, there is a chance that this could be a hardware issue but soo far, no one has been able to show that it is hardware causing the issue.

At this point, the proof of burden seems to be on me to determine if the OS configuration is causing the issue.

What troubleshooting methods can I pursue to try to determine the cause of this issue?

Thanks in advance
,

---

### Post by jared32 on 2016-07-12
Hello,

I am trying to troubleshoot a new issue on an ubuntu server and am having issues determining the next steps to take.

The sever has an ubuntu x32 14.04 sever that has been hardened to CIS lvl 2 standards. The server runs a custom application gui on boot.

The server setup has been experiencing an issue where the system will freeze. The freeze means that the gui still shows but all inputs do not work. Further, I cannot ssh into the box and the box stops producing logs when the freeze occurs.

Based on some preliminary testing, the freeze happens under the following conditions. 1, when the system is idle (seems to happen over weekends). 2, when all required peripherals are connected.

Now, there is a chance that this could be a hardware issue but soo far, no one has been able to show that it is hardware causing the issue.

At this point, the proof of burden seems to be on me to determine if the OS configuration is causing the issue.

What troubleshooting methods can I pursue to try to determine the cause of this issue?

Thanks in advance
,

---

### Post by oldfred on 2016-07-12
Threads merged.

Do not post duplicate threads on the same topic.

---

### Post by TheFu on 2016-07-12
Log files. That's the first place. Be certain to check apparmor.

System monitoring.  That data might show something just before lockups.  Perhaps too many files are open by a process?  Too many threads?  Stuff like that will show up in the monitoring. There are hundreds of other things that will show up in monitoring as "funny."

Move to a different system and run the same stuff. Still happen?

Can't move?  Disable that "custom gui" ... still happen?

Oh, and if that custom GUI is running as root, fix that so it runs as a different userid - not root.

Beginning around 2006, where I worked moved all applications into virtual machines as the default deployment.  That makes all sorts of things easier because the HW is abstracted. It is handy to migrate an application from 1 physical machine to another.

That's all I've got for suggestions.  If the software runs on multiple systems, be certain the times are all set to the same NTP server. Once had to troubleshoot an issue spread across almost 50 systems - and the admins hadn't bothered to run ntpd on them, so all the times were different. Makes comparing events in log files on different systems nearly impossible ... ok, just a nasty hassle, but extra work for no real reason.

---

