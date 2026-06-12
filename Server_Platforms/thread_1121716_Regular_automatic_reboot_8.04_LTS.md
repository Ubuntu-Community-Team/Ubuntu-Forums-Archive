---
title: "Regular automatic reboot 8.04 LTS"
date: 2009-04-10
forum: Server Platforms
---

### Post by ManfredU on 2009-04-10
Hi,

we are facing a strange problem with regular spontaneous reboots where we can't figure out the cause of the problem.  
Our rented root server restarts about every 3 hours without any visible reason. We can't find any hints in the logs. After a hardware check by the datacenter the problem had gone for 18 days when it suddenly reappeared. 

Now they replaced the hardware (except the hard drives), but that didn't help either.

The system is a dual-core system with AMD Opteron(tm) Processor 1216 and 6 GB RAM.

Ubuntu 8.04 LTS, Kernel 2.6.24-23-generic.

Plesk Control Panel-Version psa v8.6.0_build86080722.00 os_Ubuntu 8.04

The system is used for the usual web and email stuff and had been configured by our ISP (S4Y). We just added SpamDyke to get the email spam under control.

Anything which could help to solve the issue would be appreciated.

Thanks.
Manfred

---

### Post by ManfredU on 2009-04-10
The times of the reboots are somehow regular. Maybe this gives a hint to somebody?

```

Apr  5 04:05:18 oslo074 syslogd 1.5.0#1ubuntu1: restart. First occurence
Apr  8 04:05:37 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 06:36:15 oslo074 syslogd 1.5.0#1ubuntu1: restart. 
Apr  6 05:54:21 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 06:06:28 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 05:48:27 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 09:03:46 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 08:36:05 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  8 09:12:32 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 08:28:13 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 11:35:58 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  6 11:35:10 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 11:38:11 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  8 12:33:26 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 11:43:09 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr 10 12:30:35 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 14:22:27 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  6 14:50:45 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 14:46:29 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  8 15:32:15 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 15:10:08 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr 10 15:09:38 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 17:03:47 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  6 17:27:34 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 17:41:31 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  8 18:33:28 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 17:31:49 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr 10 17:54:24 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 19:39:56 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  6 20:01:34 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 20:14:08 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  8 21:49:42 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  5 22:15:48 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  6 22:42:24 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 23:07:01 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  6 00:52:38 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 01:11:23 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  8 01:37:38 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 00:37:00 oslo074 syslogd 1.5.0#1ubuntu1: restart.

Apr  6 03:25:21 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  7 03:41:54 oslo074 syslogd 1.5.0#1ubuntu1: restart.
Apr  9 03:20:12 oslo074 syslogd 1.5.0#1ubuntu1: restart.

```

---

### Post by juancarlospaco on 2009-04-10
Hardware Problem? 
Check RAM, then Check Disk, check connectors, Check Coolers, check Temperature, 
Check BIOS *(overheat autoreset feature for example)*

---

### Post by cariboo on 2009-04-10
The log snippet you attached is just syslogd which restarts every 24 hours, it is only the syslogd daemon that restarts not the computer. It looks like there may be something wrong with syslogd

Jim

---

### Post by juancarlospaco on 2009-04-10
use it from a Ubuntu LiveCD, so if the Servers reboot is a Hardware problem, if not Software problem.

---

### Post by ManfredU on 2009-04-14
Its not just a syslogd problem. I can see the boot messages in the log and notice the service interruption...

The hardware has already been replaced except the hard drives...

---

### Post by TomB19 on 2009-04-14
Have you checked your BIOS for an overheat shutdown setting?

---

### Post by ManfredU on 2009-05-03
No reboots since 17.04. about 1:xx o'clock in the morning.

Since then continuous uptime. Until this morning 03.05 at 3:55. Now we are facing the regulare reboots again every 2.5 to 3 hours.

Last time it stopped on the 24th of March and continued on the 5th of April 4:05 in the morning.

---

### Post by ManfredU on 2009-05-04
The problem was a mdadm resync which started after the server restart and crashed the server wenn reaching 99%. After the restart, the resync started from the beginning... The was then running in circles for days. I can only assume that one day the resync was successful and we had no more resets until mdadm decided again that a resync was necessary. 

I'v now identified the broken harddisk and set it to faulty until it gets replaced. So no more resyncs and therefore no more restarts. :-)

---

### Post by Sismon on 2010-01-22
Hi there,

Sorry to dig into an old problem but I just encountered the same probleme myslef with the same release, Ubuntu 8.04 LTS.

So you said it was definitely an Hardware problem or might be a software RAID problem ?

Because our server was running for more than a year with no problem...

Then :

> Jan 22 08:59:41 srv01 syslogd 1.5.0#1ubuntu1: restart.

Any more hints would be appreciated, even if I know the thread is a few monthes old ^^

Thanks !

---

### Post by Sismon on 2010-01-22
Might do a follow up on this thread :
[http://ubuntuforums.org/showthread.php?t=970006&page=11](http://ubuntuforums.org/showthread.php?t=970006&page=11)

But I think I do have found the problem on my kern.log :
> 
Jan 22 00:20:08 srv01 kernel: [5701920.407878] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5701920.407949] aacraid: Host adapter reset request. SCSI hang ?
Jan 22 00:20:08 srv01 kernel: [5701981.143857] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5701981.143922] aacraid: Host adapter reset request. SCSI hang ?
Jan 22 00:20:08 srv01 kernel: [5702052.567931] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568246] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568269] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568292] aacraid: Host adapter abort request (0,0,0,0)
Jan 22 00:20:08 srv01 kernel: [5702052.568360] aacraid: Host adapter reset request. SCSI hang ?
Jan 22 08:59:41 srv01 kernel: Inspecting /boot/System.map-2.6.24-19-server

---

### Post by buntunoob on 2010-01-22
> **ManfredU said:**
> The problem was a mdadm resync which started after the server restart and crashed the server wenn reaching 99%. After the restart, the resync started from the beginning... The was then running in circles for days. I can only assume that one day the resync was successful and we had no more resets until mdadm decided again that a resync was necessary. 
 
I'v now identified the broken harddisk and set it to faulty until it gets replaced. So no more resyncs and therefore no more restarts. :-)
 
this was pulled from his reply #9

---

