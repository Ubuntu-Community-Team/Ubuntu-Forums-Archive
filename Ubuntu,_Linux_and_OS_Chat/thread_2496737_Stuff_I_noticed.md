---
title: "Stuff I noticed"
date: 2024-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by tinman456 on 2024-04-10
Hi all, it's been awhile since my last post probably because everything is going as good as could be with my 22.04. Recently I have noticed a couple of things that I thought worth mentioning.

First one concerns the Brave browser that I was using since I started. I went ahead and downloaded 'psensor' and found that my Intel CPU cores were generally running at 160-165 F and I found that to be a bit high. So after observing it for a few days I decided to try Firefox to see if it made a difference there and did it! My cores immediately started running at 130-140 F. Now this is a big difference so I am presently using Firefox as my default browser (they are now at 127F). I figured this was significant enough to post here to help any other users out or even to check the facts I observed on my system.

The second thing is to do with an external USB HDD that I had connected. I got caught up in something and disconnected the HDD while it still had 3 process running then when I reconnected it sometime later it refused to mount, Rather than trouble shooting it I used my Windows skills to connect it to a Windows laptop which immediately gave me a message that there was a problem and if I wanted to fix it - which i did and in a few short minutes the HDD was back in business. The reason for posting this is maybe hopefully to make the developers aware of it so that they may be able to improve Ubuntu in the future to have it do the same sort of thing - which was really very convenient.

---

### Post by TheFu on 2024-04-10
If you want developers to see this stuff, then you need to open a bug report.

Unplugging a mounted file system is dangerous AND has always been DANGEROUS.  Don't do it.  Never.  Just don't.  Doesn't matter if it is NTFS, exFAT, FAT32, ext4/xfs/ZFS or any other Linux native file system.  DON'T UNPLUG mounted file systems.  Doing so is a user error.

BTW, you didn't say which file system was on the unplugged HDD.  Without that basic knowledge, nobody can help .... and I suspect that since it wasn't a native Linux file system, based on your description of using MS-Windows to fix it, it isn't a Linux issue regardless.  Complain to MSFT.  Bet they'd love to hear from you.  If you do the same thing with MS-Windows, bet it will complain  ... or ignore the issues as long as possible, so more data can become corrupted.

I'm sure you already know this stuff.

---

### Post by tinman456 on 2024-04-10
Yes I do know that but I didn't give all the details for the sake of brevity. I had deleted a folder on the external drive but whatever went wrong the action would just not complete and give back control of the drive so I really had no choice but to unplug it. And - yes - as you suspected it was an NTFS file system. The point was how easily Windows repaired the problem as opposed to Linux which wouldn't. So I figured if Windows could fix it so easily Linux should be able to as well

---

### Post by TheFu on 2024-04-10
NTFS isn't native to Linux. It has been reverse engineered without help from the creators, MSFT.  So, it isn't strange that the reverse-engineered, barely working, access to a foreign file system has issues and cannot correct every possible issue.

We always say, use the OS native to the file system to correct any issues.  
 NTFS ----> MS-Windows
 ext4 ---> Linux

After all, would you expect MS-Windows to be able to fix ext4, jfs, xfs, zfs, btrfs, f2fs, or the other 30 file systems available as native to Linux?

Now, if MSFT wants to release all their NTFS source code under a F/LOSS license, there could be hope, but you shouldn't hold your breath. I won't be holding mine.

NTFS is a journaled, modern, file system just like ext3, ext4, xfs, jfs, and all the other journaled native file systems on Linux.  It does actually take effort + luck to corrupt data in any of those file systems.  Journalling makes that nearly impossible, unless there are other, hardware, issues happening too.

The way the disk errors begin is typically with slower performance or clearly corrupt director listings or data inside files.  My troubleshooting starts with the easy stuff first.

[LIST]
[*]I **umount**ed the file system and run an **fsck**. That didn't find logical issues in the file system.  
[*]Then move all the files in that file system to some spare storage and formatted it fresh, then copied the files back.  This was impacted by the slow/poor performance, which lead to .... 
[*]> To get the files off without corruption, I ended up using **ddrescue** on each file.  Left it running overnight.  It was really just stuck on 1 of the 250 files. In the morning, it was still stuck so I moved the "stuck file" to the end of the ddrescue script and started it over.  All but the last file finished in about 10 minutes.  The last file, which was about 2.8GB, took a few hours, but eventually finished.  

[*]Only then did I run the SMART tests and see the "FAILING NOW" line.  I usually pull HDDs from service before they fail.
[/LIST]

BTW, I have excellent backups for most stuff. I don't backup "working areas" - places where files that need more processing are left.  This file system is one of those "working areas".   SMART testing is good for a number of reasons. 

About 2 weeks ago, I saw some slowdowns for a relatively new (8 months) WD-Black HDD with a 5 yr warranty.  I've been using that type of HDD for decades and never had any of them fail.  Technically, the one that is failing now hasn't failed, yet, but I already have an approved RMA to return it.  Here's the SMART report:
```
**smartctl** 7.1 2019-12-30 r5022 [x86_64-linux-5.15.0-101-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD8002FZWX-00BKUA0
Serial Number:    xxxxxxxxxxxxxx
LU WWN Device Id: x xxxxxx xxxxxxxxxx
Firmware Version: 02.01A02
User Capacity:    8,001,563,222,016 bytes [8.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Apr  7 18:19:03 2024 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
...
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   001   001   051    Pre-fail  Always   [COLOR="#FF0000"]FAILING_NOW 87106[/COLOR]
  3 Spin_Up_Time            0x0027   161   115   021    Pre-fail  Always       -       [COLOR="#FF0000"]10933[/COLOR]
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       20
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       [COLOR="#00FF00"]0[/COLOR]
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       6133
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       20
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       7
194 Temperature_Celsius     0x0022   105   091   000    Old_age   Always       -       47
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       [COLOR="#00FF00"]0[/COLOR]
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       [COLOR="#00FF00"]0[/COLOR]
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       [COLOR="#00FF00"]0[/COLOR]
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       [COLOR="#00FF00"]0[/COLOR]
200 Multi_Zone_Error_Rate   0x0008   198   198   000    Old_age   Offline      -       [COLOR="#FF0000"]1819[/COLOR]

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      6013         -
# 2  Short offline       Completed without error       00%      5832         -
# 3  Short offline       Completed without error       00%      5664         -
# 4  Short offline       Completed without error       00%      5497         -
# 5  Extended offline    Completed without error       00%      5342         -
# 6  Short offline       Completed without error       00%      5162         -
# 7  Short offline       Completed without error       00%      4995         -
# 8  Short offline       Completed without error       00%      4827         -
# 9  Extended offline    Completed without error       00%      4670         -
#10  Short offline       Completed without error       00%      4491         -
#11  Short offline       Completed without error       00%      4323         -
#12  Short offline       Completed without error       00%      4155         -
#13  Short offline       Completed without error       00%      3988         -
#14  Extended offline    Completed without error       00%      3832         -
#15  Short offline       Completed without error       00%      3652         -
#16  Short offline       Completed without error       00%      3484         -
#17  Short offline       Completed without error       00%      3316         -
#18  Extended offline    Completed without error       00%      3160         -
#19  Short offline       Completed without error       00%      2981         -
#20  Short offline       Completed without error       00%      2813         -
#21  Short offline       Completed without error       00%      2645         -
```

There are 3 parts to the report.
a) Drive type, model, S/N,  ..... yadda, yadda, yadda.
b) Details for the current test run
c) Historical data for prior test runs.

Looking at the current test results, everything looks file except IDs: 1, 2, and 200.   I've never seen a drive fail in that way. Usually all spare sectors run out and the Reallocated_Sector_Ct,  Reallocated_Event_Count and the Current_Pending_Sector numbers are non-zero.  That didn't happen for this failure.

I run short tests weekly and long tests monthly (the 1st week of each month), as you can see. Also, I retain those test logs for many weeks so as things degrade, I can see those changes from week to week.  When something bad is notice, SMARTmon lets me know, daily.  The email looks like this:

```
This message was generated by the smartd daemon running on:

   host name:  hadar
   DNS domain: [Empty]

The following warning/error was logged by the smartd daemon:

Device: /dev/sda [SAT], [B][COLOR="#FF0000"]FAILED SMART[/COLOR] self-check. [COLOR="#FF0000"]BACK UP DATA NOW[/COLOR]!
[/B]
Device info:
WDC WD8002FZWX-00BKUA0, S/N:xxxxxxxxxxxxxx, WWN:x-xxxxxx-xxxxxxxxxx, FW:02.01A02, 8.00 TB

For details see host's SYSLOG.

You can also use the smartctl utility for further investigation.
The original message about this issue was sent at Wed Apr  3 14:23:58 2024 EDT
Another message will be sent in 24 hours if the problem persists.

```

---

### Post by tinman456 on 2024-04-10
Oh yes, very interesting stuff...thanks.

---

### Post by hyperlinxe on 2024-04-12
That's very brave of you to use brave browser which takes steps to protect you from exploitation. I myself couldn't possibly make such courageous decisions to support an organization that actively protects it's users from exploitation by corporate bullies

---

### Post by TheFu on 2024-04-12
> **hyperlinxe said:**
> That's very brave of you to use brave browser which takes steps to protect you from exploitation. I myself couldn't possibly make such courageous decisions to support an organization that actively protects it's users from exploitation by corporate bullies

I assume this is sarcasm?  The tone didn't come through, if that was your intent.

I use Brave, sometimes, but always inside a **firejail**.  I stopped using chromium when it became too hard to get a non-snap version.  I've never run Chrome browser on a computer. Why would anyone provide the largest internet marketing company in the world direct access to what they do on the web?  Some of Google's settings in their browsers they claim are for security reasons, could easily be used for tracking.  Almost every company has been caught misleading us. We expect that, but hope for better from certain companies.  We've been let down by Google over and over.  Google isn't our friend. They are a for-profit company.  When the corporation does something illegal, none of the management will go to jail. They might be fined the equivalent to 1 hr of profits for the specific country where they were caught.  To Corporate-Google, that is just a cost of doing business. They don't understand "morally wrong", just that they were caught and given a minimal fine.  To Google, any fine under $1B is a joke and doesn't even show up in the share price.

---

### Post by hyperlinxe on 2024-04-12
This website incorporates google into it. So are you saying now, that you would put ubuntuforums inside a firejail! You don't trust ubuntuforums?

---

### Post by 14nd on 2024-04-13
brave user all day every day 
say what you like 
:P

---

### Post by TheFu on 2024-04-13
> **hyperlinxe said:**
> This website incorporates google into it. So are you saying now, that you would put ubuntuforums inside a firejail! You don't trust ubuntuforums?

There are no black and white answers. There are degrees of trust.

I wish UF didn't require javascript, for example.  I think javascript is one of the chef problems for web security today and has been for 20 yrs.  Generally, I don't enable javascript when browsing the internet.  I think carefully about every web server visited, then decide if access that requires javascript is reasonable and necessary.  On UF, I block the google JS stuff and block thousands of privacy stealing web domains at the network layer across the board.

Do I trust UF?  Partially, but not completely.

My daily use browser for the main websites visited is Firefox ESR inside a normal firejail which allows some access to directories in my HOME, but not to all the directories on the system. I also limit the amount of RAM and specifically force DNS to use my DNS servers, not those that Mozilla or Google want us to use.  Firefox without javascript is normal. Selective portions of select websites may have some javascript enabled.  About 50% of the websites I visit daily are running on my local LAN.  These are not available to people outside the LAN, though I do run a few public web servers on a separate subnet for the public to visit. They are not high traffic ... any more.  Think of them as archived data that I leave up for others.  For a number of years, I was posting multiple times a week, information about security, linux, and how to do things in the Unix way.

I use Brave browser inside a private firejail for specific external websites.  I restart it between visiting different web URLs, so there isn't any tracking possible.Each restart makes for a "first run" of Brave.  I use this for booking hotels, flights, and visiting sites that mandate javascript to work at all, assuming I can' just grab the content using RSS or pandoc or wallabag.  Most of the time, I'll just skip those websites.

Security isn't black or white.  It is about risk management.

---

### Post by hyperlinxe on 2024-04-13
Have you ever tried to read the coding that google is developing? That is integrated onto webpages? (it's totally crazy, and is unreadable)

Like literally [www.google.com]("http://www.google.com")

Have you ever tried reading the coding behind [URL="http://www.google.com?"]www.google.com?

[/URL]
People can use programming to achieve different goals, so javascript can be used by a malicious organization, and the code can be obfuscated, so that no one can understand what it is doing, directly, but it can also be used to achieve moral ends. If people wont draw the distinction, and reference reality, saying, it's all bad, I don't trust any any of it, then it doesn't really help shed light on the issue.

---

