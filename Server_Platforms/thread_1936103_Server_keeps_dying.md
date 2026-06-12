---
title: "Server keeps dying?"
date: 2012-03-05
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2012-03-05
Hi

Running an old HP desktop as a home server with a 160GB and 1TB HDD, on Ubuntu 10.04.2 server.

The server install is on the 160GB and the data (media e.g. mp3/video etc) is on the 1TB.

All goes well for @ a week then if I check the monitor (not logged in) I have a steam of errors (unrecoverable) see images:
[ATTACH]213758[/ATTACH]

[ATTACH]213759[/ATTACH]

I am unable to ssh into the server, nor access via SMB/NFS as a share, but the data on the 1TB remains available via SMB/NFS.

I have run SMART monitoring on the 160GB drive, and fsck, both report there is nothing wrong, and all is well.

I have to do a hard/cold reset and then everything is fine again - for @ a week or so.

Can anyone tell from the output what might be the problem? Or what other tests / checks / fixes I might want to apply.

Thanks, Jose

---

### Post by d4m1r on 2012-03-05
Looks like either your harddrive is hiccuping or the original partition you created for Ubuntu is corrupted. If the harddrive doesn't sound weird (if it doesn't click etc) I am guessing it is a software issue.

I'd say the best way to do it is move all the data off the HDD, wipe it, repartition it, and then reinstall Ubuntu.

---

### Post by matt_symes on 2012-03-05
Hi

First things i would do is image (backup) sda!

Did you run an extended test on the hard drive or just a short one ? Be sure to run an extended one.

```
sudo smartctl -t long /dev/sda
```

When it finishes

```
sudo smartctl -a /dev/sda
```

Power supply all right ? 

What's the temperature of the drive and board running at ?

It kind of points to hardware but it's odd that it works for a week or so before you are seeing these issues. Can you try the drive in a different box for a while ?

Problems like these are a pain to track down.

Kind regards

---

### Post by Jose Catre-Vandis on 2012-03-05
Thanks for the quick replies and some sound advice. I am running the long smart test, so can report back in a hour or so ;) I agree it looks like hardware, but it just has a little moment that causes the problem that a reboot cures.

Power supply OK as far as I know. Server lives in garage so nice and cool all round.

I have a second exact same PC I could swap the drives into.

If memory serves me right, problems can arise after using XBMC on my htpc (smb shares)? But not always....

Server is serving up everything SMB/NFS/FTP/HTTP/Webmin/GnuMp3d/ssh/.....

---

### Post by matt_symes on 2012-03-05
Hi

If you want to post the smartctl log when it's complete then we can take a look.

```
sudo smartctl -a /dev/sda > ~/drive_control
```

You can then post that file on the forums. I suspect you know that though :)

Kind regards

---

### Post by Jose Catre-Vandis on 2012-03-05
Outout from smartctl

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD160JJ/P
Serial Number:    S0DFJ1HL910670
Firmware Version: ZM100-46
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Mon Mar  5 20:06:17 2012 GMT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (3562) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  59) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0007   253   253   025    Pre-fail  Always       -       5760
  4 Start_Stop_Count        0x0032   094   094   000    Old_age   Always       -       6685
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       18578
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3428
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   081   051   045    Old_age   Always       -       19
194 Temperature_Celsius     0x0022   081   051   000    Old_age   Always       -       19
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       50058141
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0032   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     18577         -
# 2  Short offline       Completed without error       00%     18128         -
# 3  Selective offline   Completed without error       00%         1         -

SMART Selective self-test log data structure revision number 1
 SPAN    MIN_LBA    MAX_LBA  CURRENT_TEST_STATUS
    1          0   39062500  Not_testing
    2  273519307  312581807  Not_testing
    3          0          0  Not_testing
    4          0          0  Not_testing
    5          0          0  Completed [00% left] (312072000-312137535)
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

---

### Post by matt_symes on 2012-03-05
Hi

As you say, it looks all right. Are there any clues in syslog ?

```
grep sda /var/log/syslog* > ~/sda_log
```

Kind regards

---

### Post by CharlesA on 2012-03-05
Check the syslog as matt suggested. Judging from the error messages, it does sound like a hard drive problem - perhaps a corrupt file system, even if fsck disagrees.

---

### Post by matt_symes on 2012-03-05
Hi

> Judging from the error messages, it does sound like a hard drive problem - perhaps a corrupt file system, even if fsck disagrees.

This is good advice from CharlesA. I would image the drive and run fsck with the -f switch on the image to force a check even if fsck thinks it's fine.

It may also be the hard drive controller or dodgy power. I have seen these kinds of errors from bus powered external usb drives when not enough power gets to the drive. You could implicate / eliminate these by moving the drive to another box with a different board and power supply.

Kind regards

---

### Post by CharlesA on 2012-03-05
Agreed. I'd go for an image using ddrescue or maybe clonezilla or something.

Just so you don't lose any data, in case the drive is going out.

---

### Post by Jose Catre-Vandis on 2012-03-05
> grep sda /var/log/syslog* > ~/sda_log

That comes up empty :(

---

### Post by Jose Catre-Vandis on 2012-03-05
Thanks everyone. Looks like I have some time to find to rebuild server with new HDD :)

No data on the actual server HDD, just the install, so easy enough to rebuild.

---

### Post by CharlesA on 2012-03-05
Glad you didn't lose any data.

---

### Post by matt_symes on 2012-03-05
Hi

> **Jose Catre-Vandis said:**
> That comes up empty :(

Really ? You have rsyslogd running and configured correctly (it should be by default)?

```
matthew@server1:~$ ps aux | grep [r]syslogd
syslog    2657  0.0  0.1  27352  1324 ?        Sl   21:00   0:00 rsyslogd -c4
matthew@server1:~
```

This is just a small sample of mine (It greps both syslog and syslog.1 but the results below are just for syslog.1).

```
matthew@server1:~$ grep sda /var/log/syslog* | tail -n 5
/var/log/syslog.1:Mar  2 00:15:22 server1 kernel: [    2.272875] sd 0:0:0:0: [sda] Attached SCSI disk
/var/log/syslog.1:Mar  2 00:15:22 server1 kernel: [    3.598118] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
/var/log/syslog.1:Mar  2 00:15:22 server1 kernel: [   13.787245] Adding 1951740k swap on /dev/sda5.  Priority:-1 extents:1 across:1951740k 
/var/log/syslog.1:Mar  2 00:15:22 server1 kernel: [   14.520154] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/syslog.1:Mar  2 00:15:22 server1 kernel: [   14.832881] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
matthew@server1:~$
```

Kind regards

---

### Post by Jose Catre-Vandis on 2012-03-05
It's true :) I have have been through syslog and syslog.1 and there is not a single reference to "sda".

However, I dug back through the syslog.gz's and found when I last had to restart the server because it was "doing its thing" and had become unresponsive:

> Feb 29 15:26:27 server nmbd[1597]: [2012/02/29 15:26:27,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Feb 29 15:26:27 server nmbd[1597]:   find_domain_master_name_query_fail:
Feb 29 15:26:27 server nmbd[1597]:   Unable to find the Domain Master Browser name BOB<1b> for the workgroup BOB.
Feb 29 15:26:27 server nmbd[1597]:   Unable to sync browse lists in this workgroup.
Feb 29 15:37:32 server smbd[16098]: [2012/02/29 15:37:32,  0] printing/print_cups.c:103(cups_connect)
Feb 29 15:37:32 server smbd[16098]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 15:37:32 server smbd[16100]: [2012/02/29 15:37:32,  0] printing/print_cups.c:103(cups_connect)
Feb 29 15:37:32 server smbd[16100]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 15:37:35 server smbd[16101]: [2012/02/29 15:37:35,  0] printing/print_cups.c:103(cups_connect)
Feb 29 15:37:35 server smbd[16101]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 15:37:35 server smbd[16102]: [2012/02/29 15:37:35,  0] printing/print_cups.c:103(cups_connect)
Feb 29 15:37:35 server smbd[16102]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 15:39:01 server CRON[16110]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Feb 29 15:41:32 server nmbd[1597]: [2012/02/29 15:41:32,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Feb 29 15:41:32 server nmbd[1597]:   find_domain_master_name_query_fail:
Feb 29 15:41:32 server nmbd[1597]:   Unable to find the Domain Master Browser name BOB<1b> for the workgroup BOB.
Feb 29 15:41:32 server nmbd[1597]:   Unable to sync browse lists in this workgroup.
Feb 29 19:15:27 server kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb 29 19:15:27 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="765" x-info="http://www.rsyslog.com"] (re)start
Feb 29 19:15:27 server rsyslogd: rsyslogd's groupid changed to 103
Feb 29 19:15:27 server rsyslogd: rsyslogd's userid changed to 101
Feb 29 19:15:27 server rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb 29 19:15:27 server smbd[773]: [2012/02/29 19:15:27,  0] printing/print_cups.c:103(cups_connect)
Feb 29 19:15:27 server smbd[773]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 19:15:27 server smbd[774]: [2012/02/29 19:15:27,  0] printing/print_cups.c:103(cups_connect)
Feb 29 19:15:27 server smbd[774]:   Unable to connect to CUPS server localhost:631 - Connection refused

and there is some stuff in the bootup sequence:

> Feb 29 19:15:27 server kernel: [    1.118247] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Feb 29 19:15:27 server kernel: [    1.118253] EXT4-fs (sda1): write access will be enabled during recovery
Feb 29 19:15:27 server kernel: [    2.249622] EXT4-fs (sda1): orphan cleanup on readonly fs
Feb 29 19:15:27 server kernel: [    2.267665] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 16004
Feb 29 19:15:27 server kernel: [    2.288345] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 8351
Feb 29 19:15:27 server kernel: [    2.296970] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4351
Feb 29 19:15:27 server kernel: [    2.297795] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3796
Feb 29 19:15:27 server kernel: [    2.297818] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4512
Feb 29 19:15:27 server kernel: [    2.297832] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4506
Feb 29 19:15:27 server kernel: [    2.297846] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4477
Feb 29 19:15:27 server kernel: [    2.302960] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3810
Feb 29 19:15:27 server kernel: [    2.319505] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3776
Feb 29 19:15:27 server kernel: [    2.319523] EXT4-fs (sda1): 9 orphan inodes deleted
Feb 29 19:15:27 server kernel: [    2.319528] EXT4-fs (sda1): recovery complete
Feb 29 19:15:27 server kernel: [    2.516667] EXT4-fs (sda1): mounted filesystem with ordered data mode

There are loads of messages in syslog about cups and winbindd/idmap:

> Feb 29 21:15:38 server winbindd[1492]: [2012/02/29 21:15:38,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Feb 29 21:15:38 server winbindd[1492]:   idmap_alloc module tdb already registered!
Feb 29 21:15:38 server winbindd[1492]: [2012/02/29 21:15:38,  0] winbindd/idmap.c:149(smb_register_idmap)
Feb 29 21:15:38 server winbindd[1492]:   Idmap module passdb already registered!
Feb 29 21:15:38 server winbindd[1492]: [2012/02/29 21:15:38,  0] winbindd/idmap.c:149(smb_register_idmap)
Feb 29 21:15:38 server winbindd[1492]:   Idmap module nss already registered!
Feb 29 21:15:38 server winbindd[1492]: [2012/02/29 21:15:38,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Feb 29 21:15:38 server winbindd[1492]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Feb 29 21:17:01 server CRON[4057]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 29 21:18:37 server smbd[4064]: [2012/02/29 21:18:37,  0] printing/print_cups.c:103(cups_connect)
Feb 29 21:18:37 server smbd[4064]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 21:18:37 server smbd[4066]: [2012/02/29 21:18:37,  0] printing/print_cups.c:103(cups_connect)
Feb 29 21:18:37 server smbd[4066]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 21:24:25 server smbd[4175]: [2012/02/29 21:24:25,  0] printing/print_cups.c:103(cups_connect)
Feb 29 21:24:25 server smbd[4175]:   Unable to connect to CUPS server localhost:631 - Connection refused
Feb 29 21:24:25 server smbd[4177]: [2012/02/29 21:24:25,  0] printing/print_cups.c:103(cups_connect)
Feb 29 21:24:25 server smbd[4177]:   Unable to connect to CUPS server localhost:631 - Connection refused


---

### Post by matt_symes on 2012-03-05
Hi

> "doing its thing" 

Don't you just hate it when computers do that :D

The references to EXT-4 in the middle log is logging when an fsck is performed on the filing system at bootup.

The others may be a symptom and not the cause of your problems as they are cups and samba.

Personally, i would swap your drives in both boxes around for a couple of weeks and see what happens. If it's something on the board that has gone then you would be wasting your money on a new drive. 

I do suspect the drive though. Occams razor and all that.

Kind regards

---

### Post by Jose Catre-Vandis on 2012-04-14
Its been behaving itself for the last few weeks, then went down 2 days in a row.

```
name@myserver:~$ grep sda /var/log/syslog* | tail -n 15
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    0.781087]  sda5 > sda3
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    0.781443] sd 2:0:0:0: [sda] Attached SCSI disk
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.133513] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.133523] EXT4-fs (sda1): write access will be enabled during recovery
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490848] EXT4-fs (sda1): orphan cleanup on readonly fs
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490859] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3798
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490895] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3792
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490909] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3783
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490922] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 522
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490936] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 407
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490947] EXT4-fs (sda1): 5 orphan inodes deleted
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.490951] EXT4-fs (sda1): recovery complete
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    1.757449] EXT4-fs (sda1): mounted filesystem with ordered data mode
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [    9.152496] Adding 2980856k swap on /dev/sda5.  Priority:-1 extents:1 across:2980856k 
/var/log/syslog.1:Apr 13 19:38:58 server kernel: [   20.857173] EXT4-fs (sda3): mounted filesystem with ordered data mode
```

I've got it setup to fsck every boot now ;)

Be good if I could get the thinig to reboot once it starts having trouble. However, I recognise the inevitable, will try to hold out until the next LTS server comes out - soon I hope.

---

### Post by d4m1r on 2012-04-14
Like I said, it could be a hardware issue (HDD) **or** a corrupt partition...If you don't wanna blow $ on a brand new HDD right away, I'd try reformatting the disk and rebuilding a new EXT4 partition.

---

### Post by Vegan on 2012-04-14
curious as my old Acer T-320 has racked up 45,000 power on hours and it still runs as good as new (low end machine)

I make sure I have a vast number of hard disks, and this way I can have redundancy galore for problems.

Last year 2x 500 GB disks died, so far the new 750 GB and 2 TB disks have been running OK

I have the 2 TB disk as a secondary on my server, the boot disk on the sever is an old EIDE 160 GB hard disk that is completely expendable and it can be wiped on demand

I suggest when you install Linux fresh, you also use the latest LTS disk unless you do not mind installing it fresh every 6 months with the periodic updates like I do.

:guitar:

---

### Post by Jose Catre-Vandis on 2012-05-18
Just thought I would close this one out. With the arrival of 12.04 Server I replaced the offending HDD with another of the same size and type, and installed 12.04 and configured. Its been running happily for 18 days.....

This gave me a chance to run full smart test on the original HDD along with other tests I found on PartedMagic CD, which all came back with no problems on the HDD itself. So I must have had a software glitch in there somewhere. I'll try a new install on it and leave it running in a corner somewhere and see what happens.

---

### Post by CharlesA on 2012-05-18
Glad you played it safe and replaced the drive. :)

---

