---
title: "Monitoring Adaptec HW RAID (6805) with 12.04 and Nagios"
date: 2012-04-27
forum: Server Platforms
---

### Post by LCPSWolf on 2012-04-27
I recently spent a couple days trying to get software loaded that would let me monitor my Adaptec hardware RAID - drove me nuts not being able to find easy-to-follow instructions, so I want to write up my steps to save someone else some time. 
 
I have a Bytespeed 2U server with an Adaptec hardware RAID, 6805
 
Various sources point to the fact that Adaptec doesn't release source code for monitors its RAID controllers, but does release some partially-working software. I found software for the 6805 here:
 
Download Adaptec Storage Manager:
 
[http://www.adaptec.com/en-us/speed/raid/storage_manager/asm_linux_x64_v7_30_18837_tgz.htm](http://www.adaptec.com/en-us/speed/raid/storage_manager/asm_linux_x64_v7_30_18837_tgz.htm)
 
Unzip / untar, copy arcconf to the server
 
run the following:
```

sudo chmod +x arcconf
sudo apt-get install libstdc++5
sudo ./arcconf GETCONFIG 1

```
 
For those that may need the info:
chmod +x - give arcconf the ability to be ran
libstdc++5: required for use with arcconf - will give errors w/out installing
arcconf GETCONFIG 1: returns status of RAID controller #1
 
The results from GETCONFIG should show your controller, statues, etc. I expect there are already Nagios plugins to monitor this info, but I'll post back as I figure this out.
 
Example results from GETCONFIG:
```
 
Controllers found: 1
----------------------------------------------------------------------
Controller information
----------------------------------------------------------------------
   Controller Status                        : Optimal
   Channel description                      : SAS/SATA
   Controller Model                         : Adaptec 6805
   Controller Serial Number                 : 1A15119C445
   Physical Slot                            : 5
   Temperature                              : 49 C/ 120 F (Normal)
   Installed memory                         : 512 MB
   Copyback                                 : Disabled
   Background consistency check             : Disabled
   Automatic Failover                       : Enabled
   Global task priority                     : High
   Performance Mode                         : Default/Dynamic
   Stayawake period                         : Disabled
   Spinup limit internal drives             : 0
   Spinup limit external drives             : 0
   Defunct disk drive count                 : 0
   Logical devices/Failed/Degraded          : 1/0/0
   MaxCache Read, Write Balance Factor      : 3,1
   NCQ status                               : Enabled
   Statistics data collection mode          : Enabled
   --------------------------------------------------------
   Controller Version Information
   --------------------------------------------------------
   BIOS                                     : 5.2-0 (18301)
   Firmware                                 : 5.2-0 (18301)
   Driver                                   : 1.1-7 (28000)
   Boot Flash                               : 5.2-0 (18301)
   --------------------------------------------------------
   Controller ZMM Information
   --------------------------------------------------------
   Status                                   : ZMM not installed
----------------------------------------------------------------------
Logical device information
----------------------------------------------------------------------
Logical device number 0
   Logical device name                      : 0
   RAID level                               : 1
   Status of logical device                 : Optimal
   Size                                     : 476150 MB
   Read-cache mode                          : Enabled
   Write-cache mode                         : Enabled (write-back)
   Write-cache setting                      : Enabled (write-back)
   Partitioned                              : Yes
   Protected by Hot-Spare                   : No
   Bootable                                 : Yes
   Failed stripes                           : No
   Power settings                           : Disabled
   --------------------------------------------------------
   Logical device segment information
   --------------------------------------------------------
   Segment 0                                : Present (Controller:1,Enclosure:0,                                                                             Slot:0) 9WJ19F3H00009137LYHH
   Segment 1                                : Present (Controller:1,Enclosure:0,                                                                             Slot:1) 9WJ19JHN00009137LYYR
 
----------------------------------------------------------------------
Physical Device information
----------------------------------------------------------------------
      Device #0
         Device is a Hard drive
         State                              : Online
         Supported                          : Yes
         Transfer Speed                     : SAS 6.0 Gb/s
         Reported Channel,Device(T:L)       : 0,0(0:0)
         Reported Location                  : Enclosure 0, Slot 0
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : SEAGATE
         Model                              : ST3500414SS
         Firmware                           : 0006
         Serial number                      : 9WJ19F3H00009137LYHH
         World-wide name                    : 5000C50034182BDC
         Size                               : 476940 MB
         Write Cache                        : Enabled (write-back)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         Power State                        : Full rpm
         Supported Power States             : Full rpm,Powered off
      Device #1
         Device is a Hard drive
         State                              : Online
         Supported                          : Yes
         Transfer Speed                     : SAS 6.0 Gb/s
         Reported Channel,Device(T:L)       : 0,1(1:0)
         Reported Location                  : Enclosure 0, Slot 1
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : SEAGATE
         Model                              : ST3500414SS
         Firmware                           : 0006
         Serial number                      : 9WJ19JHN00009137LYYR
         World-wide name                    : 5000C50034180B58
         Size                               : 476940 MB
         Write Cache                        : Enabled (write-back)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         Power State                        : Full rpm
         Supported Power States             : Full rpm,Powered off
      Device #2
         Device is an Enclosure services device
         Reported Channel,Device(T:L)       : 2,0(0:0)
         Enclosure ID                       : 0
         Type                               : SES2
         Vendor                             : ESG-SHV.
         Model                              : SCA HSBP M11....
         Firmware                           : 2.17
         Status of Enclosure services device
            Power supply 1 status           : Optimal
            Power supply 2 status           : Optimal
            Temperature Sensor Status 1     : Normal
 
Command completed successfully.
 

```

---

### Post by kinglear333 on 2012-07-16
Thank you very much for your quick how-to! I managed to install this in no time and now I got access to my Adaptec 2405.

Just a note to anyone looking for latest Adaptec Storage Monitor, go to your specific model's Adaptec page and click on Downloads, then click on Adaptec Storage Manager and from there you can find the latest version. Sorry if this is common knowledge for others but it took me a good 15 minutes to figure out where the latest version was :(

---

### Post by funkyhead on 2012-11-22
**Adaptec controller status on Ubuntu 12.04 :**

To help those who come here for probleme of : 
- afacli in ubuntu 12.04
- check status of aac Raid controllers of Adaptec

The solution is here via a package of Debian/Ubuntu : [http://hwraid.le-vert.net/](http://hwraid.le-vert.net/)

In summary what to do for ubuntu 12.04 :
*Edit *: /etc/apt/sources.list
*Add *_for binary on Ubuntu precise_ : deb [http://hwraid.le-vert.net/ubuntu](http://hwraid.le-vert.net/ubuntu) precise main
*Execute *: apt-get update
*Execute *: apt-get install aacraid-status
*Execute for controller info* : arcconf GETCONFIG 1
*Execute for controller status* : aacraid-status

You've got it !
_Result _:
-- Controller informations --
-- ID | Model | Status
c0 | Adaptec 2410SA | Optimal

-- Arrays informations --
-- ID | Type | Size | Status | Task | Progress
c0u0 | RAID5 | 313G | Optimal

-- Disks informations
-- ID | Model | Status
c0u0d0 | ST332041 8AS | Online
c0u0d1 | HDS72251 6VLSA80 | Online
c0u0d2 | HDS72251 6VLSA80 | Online


Thanks a lot for this great job on hwraid.le-vert.net for who want to use and manage and harware RAID on our favorite Linux OS.

---

### Post by sdpagent on 2013-01-03
> **LCPSWolf said:**
> I recently spent a couple days trying to get software loaded that would let me monitor my Adaptec hardware RAID - drove me nuts not being able to find easy-to-follow instructions, so I want to write up my steps to save someone else some time. 
 
I have a Bytespeed 2U server with an Adaptec hardware RAID, 6805
 
Various sources point to the fact that Adaptec doesn't release source code for monitors its RAID controllers, but does release some partially-working software. I found software for the 6805 here:
 
Download Adaptec Storage Manager:
 
[http://www.adaptec.com/en-us/speed/raid/storage_manager/asm_linux_x64_v7_30_18837_tgz.htm](http://www.adaptec.com/en-us/speed/raid/storage_manager/asm_linux_x64_v7_30_18837_tgz.htm)
 
Unzip / untar, copy arcconf to the server
 
run the following:
```

sudo chmod +x arcconf
sudo apt-get install libstdc++5
sudo ./arcconf GETCONFIG 1

```For those that may need the info:
chmod +x - give arcconf the ability to be ran
libstdc++5: required for use with arcconf - will give errors w/out installing
arcconf GETCONFIG 1: returns status of RAID controller #1
 
The results from GETCONFIG should show your controller, statues, etc. I expect there are already Nagios plugins to monitor this info, but I'll post back as I figure this out.
 
Example results from GETCONFIG:
```
 
Controllers found: 1
----------------------------------------------------------------------
Controller information
----------------------------------------------------------------------
   Controller Status                        : Optimal
   Channel description                      : SAS/SATA
   Controller Model                         : Adaptec 6805
   Controller Serial Number                 : 1A15119C445
   Physical Slot                            : 5
   Temperature                              : 49 C/ 120 F (Normal)
   Installed memory                         : 512 MB
   Copyback                                 : Disabled
   Background consistency check             : Disabled
   Automatic Failover                       : Enabled
   Global task priority                     : High
   Performance Mode                         : Default/Dynamic
   Stayawake period                         : Disabled
   Spinup limit internal drives             : 0
   Spinup limit external drives             : 0
   Defunct disk drive count                 : 0
   Logical devices/Failed/Degraded          : 1/0/0
   MaxCache Read, Write Balance Factor      : 3,1
   NCQ status                               : Enabled
   Statistics data collection mode          : Enabled
   --------------------------------------------------------
   Controller Version Information
   --------------------------------------------------------
   BIOS                                     : 5.2-0 (18301)
   Firmware                                 : 5.2-0 (18301)
   Driver                                   : 1.1-7 (28000)
   Boot Flash                               : 5.2-0 (18301)
   --------------------------------------------------------
   Controller ZMM Information
   --------------------------------------------------------
   Status                                   : ZMM not installed
----------------------------------------------------------------------
Logical device information
----------------------------------------------------------------------
Logical device number 0
   Logical device name                      : 0
   RAID level                               : 1
   Status of logical device                 : Optimal
   Size                                     : 476150 MB
   Read-cache mode                          : Enabled
   Write-cache mode                         : Enabled (write-back)
   Write-cache setting                      : Enabled (write-back)
   Partitioned                              : Yes
   Protected by Hot-Spare                   : No
   Bootable                                 : Yes
   Failed stripes                           : No
   Power settings                           : Disabled
   --------------------------------------------------------
   Logical device segment information
   --------------------------------------------------------
   Segment 0                                : Present (Controller:1,Enclosure:0,                                                                             Slot:0) 9WJ19F3H00009137LYHH
   Segment 1                                : Present (Controller:1,Enclosure:0,                                                                             Slot:1) 9WJ19JHN00009137LYYR
 
----------------------------------------------------------------------
Physical Device information
----------------------------------------------------------------------
      Device #0
         Device is a Hard drive
         State                              : Online
         Supported                          : Yes
         Transfer Speed                     : SAS 6.0 Gb/s
         Reported Channel,Device(T:L)       : 0,0(0:0)
         Reported Location                  : Enclosure 0, Slot 0
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : SEAGATE
         Model                              : ST3500414SS
         Firmware                           : 0006
         Serial number                      : 9WJ19F3H00009137LYHH
         World-wide name                    : 5000C50034182BDC
         Size                               : 476940 MB
         Write Cache                        : Enabled (write-back)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         Power State                        : Full rpm
         Supported Power States             : Full rpm,Powered off
      Device #1
         Device is a Hard drive
         State                              : Online
         Supported                          : Yes
         Transfer Speed                     : SAS 6.0 Gb/s
         Reported Channel,Device(T:L)       : 0,1(1:0)
         Reported Location                  : Enclosure 0, Slot 1
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : SEAGATE
         Model                              : ST3500414SS
         Firmware                           : 0006
         Serial number                      : 9WJ19JHN00009137LYYR
         World-wide name                    : 5000C50034180B58
         Size                               : 476940 MB
         Write Cache                        : Enabled (write-back)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         Power State                        : Full rpm
         Supported Power States             : Full rpm,Powered off
      Device #2
         Device is an Enclosure services device
         Reported Channel,Device(T:L)       : 2,0(0:0)
         Enclosure ID                       : 0
         Type                               : SES2
         Vendor                             : ESG-SHV.
         Model                              : SCA HSBP M11....
         Firmware                           : 2.17
         Status of Enclosure services device
            Power supply 1 status           : Optimal
            Power supply 2 status           : Optimal
            Temperature Sensor Status 1     : Normal
 
Command completed successfully.
 

```

Sounds awesome, but when I try following those steps I get the following error:
```
./arcconf: 1: ./arcconf: Syntax error: word unexpected (expecting ")")
```

However using the second post with the debian packages works (you just have to remember to use 'sudo' to start with')

---

