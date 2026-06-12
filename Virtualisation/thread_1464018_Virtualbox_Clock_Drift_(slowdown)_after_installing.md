---
title: "Virtualbox Clock Drift (slowdown) after installing SQL Server 2005"
date: 2010-04-27
forum: Virtualisation
---

### Post by mattkenn4545 on 2010-04-27
I have the latest version of VirtualBox installed and without fail, after installing SQL Server in a Windows VM the clock slows way down.

I have tried just about every solution I could find via Google, this forum and VB forum but nothing seems to have any affect.

Also note that I have an identically configured VM (cloned the .vdi) and as soon as I finish the SQL Server installation and restart the clock starts to slow down.  All other VMs that I have  run with dang near perfect clock sync.

I also saw similar effect when using VMware Server 1 and 2.

This effect also occurs with other MS SQL driven products such as WSUS.

Does not seem to matter if host OS is 32 or 64bit.  Host currently is a 64Bit 9.10 Server install

Any Ideas, why does SQL Server cause slowing of Guest Clock?

Thanks in advance,

Matt

---

### Post by mattkenn4545 on 2010-04-27
Update, turning off the MSSQL Service allows the clock to catch up and stay in sync.

---

### Post by mattkenn4545 on 2010-04-27
More updates

The Log for the VM in question shows the following

'Occurs when the SQL server is started and clock calls behind
01:28:05.732 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)

'Occurs when the SQL server is stopped and clock stays in sync
01:28:50.514 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)

Any ideas how to fix?

---

### Post by mattkenn4545 on 2010-04-27
Sometimes I annoy myself,  I installed the rt kernel 'linux-image-rt' and issue now is fixed

Issue was that when the sql service started the PT timer tried to go to 1000hz and the host couldn't handle that so it lost time.

The RT kernel has a 1000Hz kernel so now when the guests go to 1000Hz the host can deal and all is well.

Hopefully others find this thread useful

---

### Post by TheFu on 2010-04-29
I'm glad you found a solution.  For others where your solution doesn't work, I've had issues with time loss on Vista and Win7 systems. After trying all the registry stuff and trying to use pool.ntp.org with daily updates, the clocks were still losing over 3 minutes daily.  The only solution I found that has worked is to run an NTP server on my network and have the offending clients update every 15 minutes.  

The old rules used to be, don't run NTP on the VMs since the host should be providing the correct time. That may be true for some hosts and you'll want to check your hypervisor for specifics and whether the client-tools include time updates which can be better managed before heading the NTP server/15 min sync way.

---

### Post by mattkenn4545 on 2010-05-01
Here is a great article that explaines why SQL server was causing the issue.  BTW I have no issues now with sync.  The two Domain Controllers that I have running in a test network (one has sql server installed) now have clock diff of < 0.001 seconds usually :)

[http://blogs.msdn.com/psssql/archive/2008/12/16/how-it-works-sql-server-no-longer-uses-rdtsc-for-timings-in-sql-2008-and-sql-2005-service-pack-3-sp3.aspx](http://blogs.msdn.com/psssql/archive/2008/12/16/how-it-works-sql-server-no-longer-uses-rdtsc-for-timings-in-sql-2008-and-sql-2005-service-pack-3-sp3.aspx)

---

