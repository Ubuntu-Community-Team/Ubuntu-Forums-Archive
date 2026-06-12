---
title: "Ubuntu server 18.04 crashes within 5-30 minutes"
date: 2019-04-03
forum: Server Platforms
---

### Post by gimpacause on 2019-04-03
Hi all,

I've been running an Ubuntu Server for the past few years, besides a dead motherboard and PSU, its been stable, 

Last moth i went away on the first (sunday) and left the server do its monthly check array, i logged in a few days later and the check had finished, logged out all was fine, then i got a call that the server was inaccessible, logged in and noticed its uptime was 3 minutes, with alot of crash entries when i checked previous logins, so i shutdown the server until now


basically this is what i found , 

1. if i boot the server normally it will last between 3-30 minutes before rebooting with a crash logged 
2. running in recovery mode the system was up without any issue (idling) for 36 hours

the system runs a 15x6tb Raid6 array and just serves media out to the rest of the house

where should i start looking, i have attempted to start ssh server in recovery mode and its starts, but when i try to log in from my desktop or laptop, putty boots me out, although the server is still running when i manually go to the KVM in the garage, how can i get SSH to allow the connection in recovery mode so i can check logs,


thank you very much

-Ben

---

### Post by TheFu on 2019-04-04
You should look at the log files in /var/log/   .... all of them.
Look for warnings and errors.
**sudo egrep -i 'warn|error' /var/log/*g** is how I'd do it to get a feel for which specific files I need to look into more detail.

---

### Post by gimpacause on 2019-04-05
thanks TheFu will go through logs, how do i go about not getting kicked out of an SSH session in recovery mode, as the server is headless, thank you

---

### Post by TheFu on 2019-04-05
> **gimpacause said:**
> thanks TheFu will go through logs, how do i go about not getting kicked out of an SSH session in recovery mode, as the server is headless, thank you

Check the logs for issues.  Actually, in recovery mode, is networking even enabled? I thought the system was staying up 5-30 min?

Systems here have multiple NICs, so if 1 fails, I can get in either on the failover NIC or on the backup/admin network subnet.
BTW, you really need a method that provides a remote console.  About once a year I need a remote console into one of my servers when networking is broke. Sometimes there just isn't any substitute for a console. 

BTW, I don't have any 18.04 systems in production. It hasn't gotten to the stable-enough point for me. I'm building a new hypervisor host server today and it will be using 16.04.

---

### Post by gimpacause on 2019-04-05
Hi TheFu,

 yes networking is working in recovery as i updated packages last time i was in front of the machine with recovery mode, machine has a static ip set, i'll have another shot at getting SSH working, would have made it easier to paste logs here if i find something, i'll go through the logs later tonight to see if i can find something, thank you

---

### Post by gimpacause on 2019-04-06
Hi TheFu, looks like SPO2 is the issue, which is my OS drive, running the command

```
**sudo egrep -i 'warn|error' /var/log/*g**
```

gave me the following

```
[COLOR=#FAFAFA]/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [    0.116550] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)[/COLOR]/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [    0.116575] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [    0.985968] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [    1.551562] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   21.016982] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   40.935043] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   42.963909] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   42.963917] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   42.963921] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   42.963924] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:33:23 ubuntu kernel: [   42.963927] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [    0.116550] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [    0.116576] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [    0.997874] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [    1.563856] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   17.078495] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   41.706288] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   42.548580] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   42.548591] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   42.548594] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   42.548597] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 24 23:59:15 ubuntu kernel: [   42.548600] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [    0.116550] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [    0.116575] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [    0.989814] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [    1.557379] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   27.193197] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   40.948707] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   41.900389] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   41.900404] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   41.900407] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   41.900409] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:15:06 ubuntu kernel: [   41.900412] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [    0.119742] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [    0.119742] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [    0.997873] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [    1.563679] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   21.037169] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   40.938901] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   43.261117] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   43.261125] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   43.261128] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   43.261131] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:27:18 ubuntu kernel: [   43.261134] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [    0.120548] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [    0.120574] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [    0.989772] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [    1.555845] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   21.089128] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   41.393427] EXT4-fs (sde2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   43.025053] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   43.025061] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   43.025065] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   43.025068] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:36:59 ubuntu kernel: [   43.025071] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [    0.119756] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [    0.119756] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [    0.989535] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [    1.555970] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   27.088768] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   41.289672] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   42.921308] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   42.921317] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   42.921320] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   42.921323] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 00:51:23 ubuntu kernel: [   42.921326] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [    0.120551] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [    0.120577] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [    0.989837] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [    1.556452] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   27.202603] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   41.080212] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   42.346281] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   42.346289] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   42.346292] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   42.346295] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:10:12 ubuntu kernel: [   42.346298] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [    0.120551] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [    0.120577] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [    1.006035] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [    1.573249] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   27.209785] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   41.329970] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   42.370099] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   42.370106] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   42.370110] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   42.370113] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:20:19 ubuntu kernel: [   42.370116] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [    0.120553] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [    0.120579] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [    0.989903] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [    1.556842] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   27.133574] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   41.603452] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   42.127315] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   42.127324] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   42.127327] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   42.127330] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:31:01 ubuntu kernel: [   42.127333] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [    0.120549] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [    0.120575] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [    0.989757] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [    1.557346] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   21.090483] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   41.157760] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   42.173278] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   42.173287] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   42.173290] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   42.173293] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 01:44:35 ubuntu kernel: [   42.173296] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [    0.120552] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [    0.120578] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [    1.005955] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [    1.573260] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   17.087087] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   41.128786] EXT4-fs (sde2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   42.321767] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   42.321775] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   42.321778] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   42.321781] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 25 02:02:40 ubuntu kernel: [   42.321784] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [    0.120549] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [    0.120574] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [    0.993872] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [    1.562019] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   21.003983] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   40.740893] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   42.200970] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   42.200978] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   42.200982] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   42.200985] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:37:04 ubuntu kernel: [   42.200988] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [    0.120551] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [    0.120577] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [    0.993750] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [    1.562734] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   21.015634] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   40.987469] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   41.961352] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   41.961360] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   41.961364] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   41.961367] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 11:46:06 ubuntu kernel: [   41.961369] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [    0.120549] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [    0.120574] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [    0.993757] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [    1.561868] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   20.953609] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   40.564499] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   41.649166] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   41.649174] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   41.649178] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   41.649181] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 12:53:30 ubuntu kernel: [   41.649184] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [    0.120552] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [    0.120578] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [    1.005843] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [    1.573785] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   20.981326] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   41.063881] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   42.087198] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   42.087206] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   42.087209] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   42.087212] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 27 13:01:29 ubuntu kernel: [   42.087215] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000052F (\_SI.SIOR) (20170831/utaddress-247)
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [    0.120551] ACPI Error: Needed type [Reference], found [Integer]         (ptrval) (20170831/exresop-103)
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [    0.120577] ACPI Error: Method parse/execution failed \_PR.CPU0._PDC, AE_AML_OPERAND_TYPE (20170831/psparse-550)
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [    0.993782] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [    1.561866] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [   20.959883] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [   40.500047] EXT4-fs (sdp2): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [   41.663966] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [   41.663975] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [   41.663978] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
/var/log/kern.log:Mar 30 02:50:46 ubuntu kernel: [   41.663981] ACPI Warning: SystemIO range 0x0000000000000500-0x0000000000 *Total output of 708.40 kB was truncated at 97.66 kB.*
```

sdp is my boot ssd, thinking its possible gone bad, and that is whats causing my stability issue, thank you for the help so far

---

### Post by TheFu on 2019-04-06
Check the SMART data on the device.  Might be just a bad connector/cable.  Ask if you need help.

---

### Post by gimpacause on 2019-04-18
hi TheFu, just an update to the above, smart data showed the drive as good, i tore down the server rebuilt it (to ensure everything was seated correctly) updated all packages, the server lasted a solid 5 days of uptime , but now its become unstable again, i'm going to swap out the ram tomorrow just as a precaution and run memtest on the current set in my test bench and replace my boots drives sata cable

I will post logs in here if the issue continues

thank you

---

### Post by TheFu on 2019-04-18
SMART cannot say that a disk is good. 22% of the time, storage devices fail without SMART showing anything wrong.
I would run a different OS on it.  16.04 has support for 2 more years.

And I would have replaced the SATA cable 1st thing. Easy things should happen first.

---

### Post by gimpacause on 2019-05-04
Hi TheFu, I've replaced all SATA cables, and re tested the power supplies, the system was stable for a solid 8 days, then since yesterday it's been rebooting anywhere from 30 minutes to 6 hours, sorry for long delays in replies, im interstate at the moment and only in front of the server fortnightly, thank you

---

