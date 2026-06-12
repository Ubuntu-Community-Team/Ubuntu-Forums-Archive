---
title: "Adjusting date and time to Ubuntu production file server"
date: 2023-06-13
forum: Server Platforms
---

### Post by jmestradave on 2023-06-13
Hola! This might seems a silly topic but I am a little bit worried since I remember that chaos came to one of our Ubuntu file server back in the day right after playing around with server date / time adjustment. USB external HD filesystem just broke down after changing date / time and we almost loose all data in drive.

So I noticed that time is not correct on this Ubuntu file server and I strongly believe that this issue is causing problems to backup routines on Windows clients running robocopy for file backups on Ubuntu secondary HD.

Being said that, what kind of issues might date / time adjustment causes to files on Ubuntu file server, if any?

Thank you so much in advance.

---

### Post by TheFu on 2023-06-13
Cryptography between systems is dependent on time.

How do I say this nicely.  Computers need to have the correct time and on Unix systems, that time should be within 1 second of accurate, easily.  This is a solved problem and has been over 30 yrs.  It should happen automatically, but in a corporate environment, perhaps they need to run an NTP server for all internal systems to hit for accurate time.  ntpd is becoming deprecated.  I use chronyd and chronyc on my Unix systems.  

Now, on MS-Windows, keeping time has been a problem since 1995.  In the early 2000s, I asked 3 on-site MSFT engineers about their poor time keeping. Their response was that ±5 min was close enough and they didn't consider anything within that range a bug.  To make my point, I started showing up to all their meetings 5 minutes late - after all, ±5 min was close enough.

My single Windows system hits my local chronyd server every 15 minutes to keep accurate time. Once an hour wasn't sufficient to stay within 1 min accuracy.  Over a week, it was crazy how off the Windows systems I've had over the decades got.  What's even funnier is that my main time server system started out running MS-Windows and couldn't keep time.  I swapped in Ubuntu Server and it never lost a beat. It is the time server for all other systems here and is µsec accurate and has been 12 yrs.

---

### Post by jmestradave on 2023-06-15
Thanks for replying, mate! If I understood correctly, all I should do is to install chronyc in the Ubuntu file server and let it take care of pretty much everything related to date / time service? Maybe I should just find out why robocopy is not able to accomplish the backup tasks. Correct? This is funny because I remember I already faced this issue with robocopy in the past and had to use 7zip instead for backups which is still working smooth on a couple of VPSs but this time creating a .zip file is not useful, what we need is to copy files and folders as it is from Windows 10 terminal source to Ubuntu file server shared folder.

---

### Post by LHammonds on 2023-06-16
@TheFu, I've not had problems like that with my Windows servers.  I typically configure the DC to sync with a list of atomic clock services over the internet and all other servers, PCs, equipment on the LAN sync their time with the DC.

So rather than have all machines looking to an outside time service, the all look to a single internal (or any of the DC servers) and only a very small amount have to traverse the Internet looking for time setting.  This tended to keep everyone together.   I did not have any login, backup or other issues related to time drift.

I used this batch file to [set the master](https://github.com/LHammonds/dos-batch/blob/master/TimeSetMaster.bat) and this batch file to [set the slave](https://github.com/LHammonds/dos-batch/blob/master/TimeSetSlave.bat) and this batch file to [check the status](https://github.com/LHammonds/dos-batch/blob/master/TimeGetStatus.bat).

I'm pretty sure I had my Linux servers using NTP and pointed them to my Windows DC servers but I no longer work at that company to look and see.

LHammonds

---

### Post by TheFu on 2023-06-16
> **jmestradave said:**
> Thanks for replying, mate! If I understood correctly, all I should do is to install chronyc in the Ubuntu file server and let it take care of pretty much everything related to date / time service? Maybe I should just find out why robocopy is not able to accomplish the backup tasks. Correct? This is funny because I remember I already faced this issue with robocopy in the past and had to use 7zip instead for backups which is still working smooth on a couple of VPSs but this time creating a .zip file is not useful, what we need is to copy files and folders as it is from Windows 10 terminal source to Ubuntu file server shared folder.

**What you should or shouldn't do is up to you.**  For most people, the default **systemd-timed** is sufficient. I have a dislike of the typical interfaces the systemd team designs and chrony is higher resolution.

I know nothing about robocopy - other than the name.  Where I've worked the last 20+ yrs, we never left anything important on any MS-Windows system, even if every desktop was MS-Windows.  People were expected/required to use server storage.  I do the same with my single, remaining, MS-Windows system at home.  Data is never left on it and it isn't allowed to talk on the internet.

ZIP is NOT an appropriate backup tool for anything larger than 500MB. Same for tar/gnutar.  There are so many better options.

Perhaps incorrect time is only a tiny part of the issue. IDK.  File sync tools usually check the update times on both files (local/remote) as a first check for which is newer and needs to be updated.  If the mtime is wrong, then the update may not happen.  IDK how robocopy does it.

---

