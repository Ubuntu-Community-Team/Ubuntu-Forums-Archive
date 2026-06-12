---
title: "Seeking Clarification About SMART Load_Cycle_Count Issue"
date: 2007-10-28
forum: System76 Support
---

### Post by blackhole54 on 2007-10-28
Hi All,

I would like to get System76's (and anybody else's) view on the issue being reported on recently about Ubuntu systems causing (as I understand it) excessive wear from loading and unloading of the heads on hard disk drives.  One article discussing this is [here](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear) with a followup article noting a response from a lead Ubuntu developer [here](http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions).

So I checked my Pangolin machine which I purchased last January which is still running *edgy eft* that it came pre-installed with.  Commands are in bold and what strike me as some of the relevant data is highlighted in red:

```

root@pangolin:~# **smartctl -d ata -i /dev/sda**
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K100 series
Device Model:     HTS541080G9AT00
Serial Number:    MPB4LAXNGM1T8G
Firmware Version: MB4OA60A
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 3a
Local Time is:    Fri Oct 26 21:07:09 2007 MDT
[color=red]SMART support is: Available - device has SMART capability.
SMART support is: Enabled[/color]

root@pangolin:~# **smartctl -d ata -H /dev/sda**
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
[color=red]SMART overall-health self-assessment test result: PASSED[/color]

root@pangolin:~# **smartctl -d ata -A /dev/sda**
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   144   144   033    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       697
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
[color=red]  9 Power_On_Hours          0x0012   093   093   000    Old_age   Always       -       3179[/color]
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
[color=red] 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       696[/color]
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       1
[color=red]192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       277
193 Load_Cycle_Count        0x0012   034   034   000    Old_age   Always       -       663303[/color]
194 Temperature_Celsius     0x0002   171   171   000    Old_age   Always       -       32 (Lifetime Min/Max 17/43)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       2
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

root@pangolin:~# 

```

I note that *Load_Cycle_Count* is already in excess of the 600,000 *Load/Unload cycle* figure quoted in my drive's [data sheet](http://www.hitachigst.com/hdd/support/5k100/5k100.htm).  Should this be cause for alarm?

Under the assumption that this is not a good situation, I've done a stop-gap mitigation by placing 

```

hdparm -B255 /dev/sda > /dev/null 2>&1

```

in */etc/rc.local*.  (I've never gotten either form of suspend to work right so I didn't worry about that contigency, and *rc.local* was an easy way to do this for now.)  So far this appears to result in *Load_Cycle_Count* incrincreasing by 1 to 3 upon reboot/power-cycle compared to the average increase of about 3/minute of runtime reflected in the above statitistics.  And I can't see that this change makes a noticable difference in the power consumption while running on battery as monitored by the Gnome Power Manager.

Since in the default installation of Ubuntu this does not appear to be a notebook specific issue, I also tried to check the Ratel I purchased at the same time.  While I can get **smartctl** to give me data on the Ratel, the specific item *Load_Cycle_Count* is not listed.

I would appreciate any help in interpreting this data, especially in deciding if the disk drive on the Pangolin should be considered nearly worn out.  Also appreciated would be any comments about mitigation and what I should make of the Ratel's lack of a *Load_Cycle_Count* number in **smartctl**.

Thanks for any responses.

P.S.  I have tried to review the threads on UbuntuForums that are relevant to  this.

---

### Post by pyropir on 2007-10-29
I'm in a similar situation and I'd also appreciate some guidance on this issue. I got a Pangolin in January, but I upgraded to feisty and now to gutsy when they came out. Load_Cycle_Count is not massive, but it is going up very fast now that I'm using gutsy - in the last coupld of days it increased from 16'000 to 24'000. After upgrading I did also notice frequent faint and previously unfamiliar noises coming from the hd that made me wonder if the drive was on its way out.
```
pir@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 7K100
Device Model:     HTS721080G9AT00
Serial Number:    MPC412Y4G6PAGE
Firmware Version: MC4OA51A
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 3a
Local Time is:    Mon Oct 29 12:07:14 2007 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 645) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  45) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   161   161   033    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       475
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   093   093   000    Old_age   Always       -       3265
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       475
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       59
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       24501
194 Temperature_Celsius     0x0002   171   171   000    Old_age   Always       -       32 (Lifetime Min/Max 15/45)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```

---

### Post by ubuntu_demon on 2007-10-29
I'm blogging about this issue to get awareness and raise the status of the bug(IMHO it should be critical). My blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

People with laptops who haven't enabled laptop-mode and think they are suffering from this problem might consider adding the following information to the bug report :
* the output of $sudo smartctl -a /dev/sda
* the age of your disk 
* an estimate of the total hours your disk has been running since you started using it  (to compare to Power_on_Hours because that value might be off)
* an estimate of the average increase of Load_Cycle_Count during one hour on AC

this is the bugreport we are talking about :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by thomasaaron on 2007-10-29
Well, all of that is a lot to digest at 8:30 on Monday morning. My coffee hasn't even hit bottom yet.

But it sounds like the Ubuntu developer is pretty convinced that, unless you are using really aggressive power management via laptop mode, Ubuntu isn't going to have any unnecessary wear on your hard drive. And if you ARE in laptop mode, it isn't going to be any more aggressive than any other computer set to laptop mode.

While I will pass this on to R&D for their evaluation, let me tell you what I SEE from a tech support perspective. 

1. Of course -- as with any other tech support department -- we do see hard drive failures occasionally. That said, I can count the failures I've seen on one hand -- and we have A LOT of computers out there.

2. We pretty much put our shop computers through H_LL on a daily basis. Imaging. Re-imaging. Suspending. Hibernating. Resuming. Completely hosing them and re-imaging them.  And I've NEVER killed a hard drive in the shop. I guarantee you that they take more abuse in a month here than most users can give them in a couple of years.

So, from a tech-support perspective, I'm seeing it as a non-issue. That, of course, doesn't mean I won't be solidly proven otherwise. But for now, I'm solidly happy with Ubuntu.

---

### Post by blackhole54 on 2007-10-29
ubuntu_daemon,

If you follow the second  link in my previous post, you will find a quote of the developer's response which ThomasAaron mentioned.  According to that,  with the default configuration, /etc/acpi/power.sh does not execute that **hdparm** statement with *-B1* in it.  I have just verified this experimentally on *edgy* by pulling the power and having **hdparm** report with *-I* (capital "aye").  Yet in my case, something obviously was increasing that count 2 to 3 times a minute.  Since my original post I have found out that prior to my altering it, the agressiveness of power save on my disk was set to "128."

@Thomas,

As I just indicated, I too find the developer's argument convincing that Ubuntu isn't changing anything from what the BIOS has set.  However, the statistics show that something on my machine had been averaging about 3 hits a minute before I made the adjustment.  Now that I have seen *pyropir*'s post, I am shocked at the difference on what sounds like the same machine.  Both have a similar number of hours logged, but my hit rate is about 30 times *pyropir*'s.  I can't think of anything too radical that I have done to the machine besides install **sshd** and **ntpd**.  I had assumed my high count was probably due to the (somewhat) agressive (128) power manager and the frequent logging I see on *syslog*.

---

### Post by ubuntu_demon on 2007-10-29
The following things might cause aggressive power management :

  * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
  * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
  * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

---

### Post by pyropir on 2007-10-29
@blackhole54  - it's true that my Load_Cycle_Count is 30 times less than yours, but I'm catching up fast! It's increasing by almost 200 per hour now, and I'm estimating that it must have been somewhere between 2-4 per hour on average before I upgraded to Gutsy. If the harddrive had been accumulating load cycles at the same rate it is increasing now over the whole of it's life, then the count would now be 173/h * 3272h = 566'056 ..... something's definately changed since I upgraded to Gutsy!


```
  9 Power_On_Hours          0x0012   093   093   000    Old_age   Always       -       3265
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       24501

*******

  9 Power_On_Hours          0x0012   093   093   000    Old_age   Always       -       3272
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       25715

```

---

### Post by pyropir on 2007-10-29
> **thomasaaron said:**
> 
But it sounds like the Ubuntu developer is pretty convinced that, unless you are using really aggressive power management via laptop mode, Ubuntu isn't going to have any unnecessary wear on your hard drive. And if you ARE in laptop mode, it isn't going to be any more aggressive than any other computer set to laptop mode.

AFAIK the ubuntu developer is saying that Ubuntu uses the factory default values. But some people are arguing that Windows overrides the defaults, that as a result manufacturers don't care much about the defaults, and that therefore some of the factory defaults are a bit insane. 
Anyway, whatever the values are, they will always have to be a compromise between low power consumption and drive longevity. Since lower power consumption for laptops is an important selling point, and since reduced longevity should increase the number of drives sold, shouldn't we expect this compromise to favour low power consumption and disfavour longevity?

---

### Post by sail on 2007-10-29
My cycles were going up by 100 per day, so I decided to just turn the APM off completely. 

Here's what my read out looks like after 5 months of use with my Gazelle:

```
rob@squirtle:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   180   180   000    Old_age   Always       -       60256
```

---

### Post by blackhole54 on 2007-10-30
> **pyropir said:**
>  it's true that my Load_Cycle_Count is 30 times less than yours, but I'm catching up fast! It's increasing by **almost 200 per hour** now ...

I don't know if it is relevant, but that's about what my average was with *edgy* before I tamed power management. 

BTW, even though I now tell it to set power management to "255," when I read it back with

```

hdparm -I /dev/sda

```

it shows 254.  But experimentally, the load count is still only increasing (by a few) when I boot.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
I added a bit of information about WORST and THRESHOLD relevant to your Load_Cycle_Count.

---

### Post by blackhole54 on 2007-11-01
> **thomasaaron said:**
> Well, all of that is a lot to digest at 8:30 on Monday morning. My coffee hasn't even hit bottom yet.

Sorry about that!  :)

> While I will pass this on to R&D for their evaluation ... 

Does R&D have any response?  In particular to the fact that for whatever reason (and realizing a big discrepency with pyropir's figures) my *Load_Cycle_Count* is already above the figure on the disk's data sheet.  (How should that figure be interpreted?)  WRT  ubuntu_demon's comment about comparing "WORST" to "THRESHOLD," the fact that all of my "THRESHOLD" figures for data deemed relevant to old age were zero made me suspicious regarding those values and made me wonder if such a comparison was really valid in those cases.

Also, why is that data not part of **smartctl**'s output for the disk on the Ratel system?.  Is such a figure simply not relevant for a desktop and/or SATA drive?

---

### Post by blackhole54 on 2007-11-02
Hi All,

A member over at Linux Questions has just posted a reply he has received from Bruce Allen (author of "Monitoring Hard Disks with SMART", *Linux Journal*, 2004) that appears germane to this discussion.  That post is [here]("http://www.linuxquestions.org/questions/showthread.php?p=2945630#post2945630").  

Bruce specifically requested that some of the info be "passed back to the Ubuntu community."

---

### Post by ubuntu_demon on 2007-11-02
> **blackhole54 said:**
> Hi All,

A member over at Linux Questions has just posted a reply he has received from Bruce Allen (author of "Monitoring Hard Disks with SMART", *Linux Journal*, 2004) that appears germane to this discussion.  That post is [here]("http://www.linuxquestions.org/questions/showthread.php?p=2945630#post2945630").  

Bruce specifically requested that some of the info be "passed back to the Ubuntu community."

Thanks for notifying us. 

I have posted about Bruce Allen's email at the bugreport :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

The general thread about this issue is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

The Load_Cycle_Count can still rise very fast when you set power management to 128. I set my power management to 128 somewhere between 16:20 and 16:40. Between 16:40 and 17:00 I see 42 Load_Cycles within 20 minutes. That's 2 Load_Cycles per minute.

```

193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 903 | Fri Nov 2 16:20:01 CET 2007
193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 920 | Fri Nov 2 16:40:02 CET 2007
193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 962 | Fri Nov 2 17:00:01 CET 2007

```

---

### Post by perce on 2007-11-02
Tom,

I've seen a flood of threads about the hard disk killing bug all over the forums in the last week.
Of course I believe you when you say that you see very few disk failures among your customers, and I have myself an old laptop which has been running only Linux for six years and has never had any disk problems. However this doesn't rule out the possibility that the bug, if it exists, is rather new and hasn't shown its effects yet. 

I don't understand the technical points of most posts on the topic because I've never played with kernels and hardware. 
Could you post a detailed description of what we should do to control if our hard disk is misbehaving?

Thank you

---

### Post by KentS on 2007-11-02
My load_cycle_count was increasing by 2-3 pr minute. I used the ugly fix with -B 254. That took care of the problem, but now my load_cycle_count ONLY increases when I shut off and on my computer. Shouldn't it increase more often? Have I set the value too high?
(Temperature seems stable at around 50-53 degrees, if that's relevant.)

Why is this an ugly fix?

---

### Post by ubuntu_demon on 2007-11-03
> **KentS said:**
> My load_cycle_count was increasing by 2-3 pr minute. I used the ugly fix with -B 254. That took care of the problem, but now my load_cycle_count ONLY increases when I shut off and on my computer. Shouldn't it increase more often? Have I set the value too high?
(Temperature seems stable at around 50-53 degrees, if that's relevant.)

Why is this an ugly fix?

In case of the ugly fix you probably want to set the power management value (-B) to somewhere between 128 and 254. If you are worried about power usage or heat you should try 128. You can experiment with values between 128 (low power usage) and 254 (best performance) although values below 254 still can do much head parks (depending on the harddrive) so you should keep watching your Load_Cycle_Count.

I set my power management to 128 somewhere between 16:20 and 16:40. Between 16:40 and 17:00 I see 42 Load_Cycles within 20 minutes. That&#8217;s 2 Load_Cycles per minute :

```

193 Load_Cycle_Count 0×0032 200 200 000 Old_age Always - 903 | Fri Nov 2
16:20:01 CET 2007
193 Load_Cycle_Count 0×0032 200 200 000 Old_age Always - 920 | Fri Nov 2
16:40:02 CET 2007
193 Load_Cycle_Count 0×0032 200 200 000 Old_age Always - 962 | Fri Nov 2
17:00:01 CET 2007

```

It's an ugly fix because it involves people altering their default configuration and because people have to understand what they are doing so that they can revert the fix if necessary (for example if an official fix would be released). It's also an ugly fix because you override default settings set by BIOS or harddrive firmware.

BIOS or harddrive firmware might set too aggressive power management defaults. Ubuntu's position has been that manufacturers know what they are doing and to not override these settings. see also : [http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

Also don't forget that if you are on battery having your harddisk head park protects your harddrive if you experience any bumps.

Only people who are heavily affected and understand what they are doing should apply the ugly fix. If you use suspend/hibernate you should also add the 99-hdd-spin-fix.sh files to the appropriate places. See :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

[B]The general support thread about this issue is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)[/B]

---

### Post by doublearon on 2007-11-05
Ok guys, at what point is the ugly fix warranted? 

Earlier today I had a load cycle count of 325,030 and now i have a load cycle count of 325,787. This seems like a lot to me. Does it to you too? 757 in 3 hours...

---

### Post by perce on 2007-11-06
How do you check your cycle count?

---

### Post by vivedekananda on 2007-11-06
run "hdparm -B 255 /dev/sda"
then check if you have power save flag 0x0ff set with
"hdparm -I /dev/sda | grep power"
on some machines value 255 sets values 128 (0x08), then  you need to use another value eg.
"hdparm -B 254 /dev/sda"

Btw, does your hdd not get warmer after applying the "ugly fix"?
I have a feeling that mine does, didn't have the opportunity to check though, I applied the fuix shortly after I bought the machine.

---

### Post by ubuntu_demon on 2007-11-06
> **doublearon said:**
> Ok guys, at what point is the ugly fix warranted? 

Earlier today I had a load cycle count of 325,030 and now i have a load cycle count of 325,787. This seems like a lot to me. Does it to you too? 757 in 3 hours...

If your Load_Cycle_Count increases with increments of one you might want to consider applying the ugly fix if you understand what you are doing so you can revert it if necessary.

The ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960](http://ubuntuforums.org/showpost.php?p=3675960)

IMHO this thread should focus on interacting with System76

The general support thread is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by ubuntu_demon on 2007-11-06
> **vivedekananda said:**
> run "hdparm -B 255 /dev/sda"
then check if you have power save flag 0x0ff set with
"hdparm -I /dev/sda | grep power"
on some machines value 255 sets values 128 (0x08), then  you need to use another value eg.
"hdparm -B 254 /dev/sda"

Btw, does your hdd not get warmer after applying the "ugly fix"?
I have a feeling that mine does, didn't have the opportunity to check though, I applied the fuix shortly after I bought the machine.

You can experiment with values between 128 and 254 to find a balance. Closer to 128 means less power usage and less high temperature. 254 means more performance and no parking/unparking. You can for example apply a lower value when on battery and a higher value when on AC.

IMHO this thread should focus on interacting with System76

The general support thread is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)
__________________

---

### Post by chrischan on 2007-11-06
Hi everybody,

I have a VIA Epia board (EX10000EG) and a pretty new Western Digital 1 Terabyte WD10EACS drive. I am running Ubuntu 7.04. No laptop mode, no fiddling with ACPI, just standard setup. Every few seconds I can hear the drive load/unload, my load cycle count is 5678 after 86 hours. The commonly mentioned fix "hdparm -B254 /dev/hda" gives me 

/dev/hda:
 setting Advanced Power Management level to 0xFE (254)
 HDIO_DRIVE_CMD failed: Input/output error

Can anyone comment on this latter issue or on the fact that I see this problem not on a laptop but on a desktop machine?

Best regards
Chrischan

---

### Post by palintheus on 2007-11-06
you need a space between -B and 254, but I do agree with ubuntu_demon

> IMHO this thread should focus on interacting with System76
The general support thread is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by ubuntu_demon on 2007-11-07
to chrischan :

You shouldn't cross post your question in three places. I already answered you :
[http://ubuntuforums.org/showpost.php?p=3719857&postcount=364](http://ubuntuforums.org/showpost.php?p=3719857&postcount=364)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/94](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/94)

IMHO this thread should focus on interacting with System76

The general support thread is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by perce on 2007-11-09
My Darter is about six months old, and the load cycle count is about 60,000. This means that I would arrive to the threshold of 600,000 in five years; that's OK.

However, the count went up by 3,500 in one day, If you divide 600,000 by 3,500 you get about 180, which means that I'm going to reach the threshold in six more months (hopefully not the day after my warranty expires).

Even more interesting, if we divide 60,000 by 3500 we get  18 days, more or less the number of days I've been using Gutsy for. This makes me think that the problem is new, and if it is really going to bring disk failures, System76 still has to see them, and they are going to see them in six month or a year.

---

### Post by ubuntu_demon on 2007-11-10
> **perce said:**
> My Darter is about six months old, and the load cycle count is about 60,000. This means that I would arrive to the threshold of 600,000 in five years; that's OK.

However, the count went up by 3,500 in one day, If you divide 600,000 by 3,500 you get about 180, which means that I'm going to reach the threshold in six more months (hopefully not the day after my warranty expires).

Even more interesting, if we divide 60,000 by 3500 we get  18 days, more or less the number of days I've been using Gutsy for. This makes me think that the problem is new, and if it is really going to bring disk failures, System76 still has to see them, and they are going to see them in six month or a year.

If you think Load_Cycle_Count didn't rise that quickly :
* See whether your swap is used (if there's a lot of swapping going on you might want to buy more ram): $ free -m 
* Try disabling tracker (system->preferences->sessions)
* Let us know whether disabling tracker helped 

If that doesn't work then read this first :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

If you need help here's the general support thread for this issue :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by pyropir on 2007-11-10
@perce,

I think you are right, Ubuntu users (and System76!) will probably see a massive increase in disk failures in a few months. After I upgraded to Gusty, my load cycle count went up to 40'000 now, from an estimated maximum of a few thousand.

I'm rather disappointed with Ubuntu and System76 - I expected them to give some advice, but it seems like nobody is taking responsibility for this problem and choose to blame others, like HD manufacturers, instead. [Bug 59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") is still marked as 'wishlist' and noone's replying on there, and  System76 is ignoring this thread also.......


@ubuntu_demon
I switched tracker off for a while, and load cycle count still increased failry rapidly (I didn't compare the rate of increase thought). I also tried swithcing off services (System >  services) one by one to see if I could narrow it down that way, but this caused me a whole lot of new problems as I disabled dbus that way and then had a lot of trouble switching it on again....

I have 1GB RAM, which I assumed would be enough, especially since System Monitor usually tells me that I use somewhere between 30% - 60% user memory, but to my surprise 'free -m' tells me that it's doing some swapping. How can I find out how much swapping happens on average?

```
pir@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1003        986         16          0         28        475
-/+ buffers/cache:        482        520
Swap:         2533         31       2502
```

---

### Post by blackhole54 on 2007-11-11
> **pyropir said:**
> I have 1GB RAM, which I assumed would be enough, especially since System Monitor usually tells me that I use somewhere between 30% - 60% user memory, but to my surprise 'free -m' tells me that it's doing some swapping. How can I find out how much swapping happens on average?


Even with plenty of RAM, it is not uncommon for a little bit to be swapped out in preferrence for additional caching of disk.  If you feel comfortable tinkering with the innards of your OS, you can change how aggressively the kernel swaps vs cache by setting the parameter *vm.swappiness* in */etc/sysctl.conf*.  (If you feel at all queasy about doing that, best to leave it alone.)  By deault, that parameter is not in that conf file, but you can add it.  I'd suggest researching this a little on the Internet before beginning to tinker.  (Disclosure:  I've never done this.)

You can monitor the swap activity with the command **vmstat**.  W/o parameters,  it will list the average swap rate (and other values) since the computer booted.  You can tell it to repeat at intervals, in which case the first output  will be the averages since boot, and subsequent output will be just for the previous interval.  See its *man page* for more details and info for interpretting the swap rates.

---

### Post by pyropir on 2007-11-11
blackhole54,
Thanks a lot for that. I don't think there's much swapping going on on my Pangolin (this is after 4-5 hours of activity):

```
pir@ubuntu:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0  35748  46068  29816 458688    0    2    50    37  208  491  7  1 90  2

```

---

### Post by blackhole54 on 2007-11-11
pyropir,

My guess is 35 MB got swapped out and that was the end of it (never swapped back in) and, since  **vmstat** reports averages, that figure will just keep falling.

BTW, are you running System76 hardware?

EDIT:  Never mind about my question ...  I just noticed your said you were running a (System76) Pangolin.  :oops:

---

### Post by pyropir on 2007-11-12
[QUOTE=blackhole54;3752830
BTW, are you running System76 hardware?
:[/QUOTE]

Yes, and I got[ my Pangolin]("http://ubuntuforums.org/showpost.php?p=3660854&postcount=2") in January this year, [like you]("http://ubuntuforums.org/showpost.php?p=3653021&postcount=1"), with 80G HD, although we seem to have different models.

---

### Post by ubuntu_demon on 2007-11-12
@pyropir:

You might want to apply an ugly unofficial fix using hdparm to tell your harddrive to turn down power management while on AC.

First read this :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

If you need help here's the general support thread for this issue :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by blackhole54 on 2007-11-13
pyropir,

My humblest appologies.  I have read so many posts and other materials on this issue, my mind is like mashed potatoes!  Now if only I had aqquired any understanding from all of my reading.  :(

---

### Post by blackhole54 on 2007-11-15
In the event this may help somebody ...

Hitachi provides a tool for some of its hard drives that is available for download [here]("http://www.hitachigst.com/hdd/support/download.htm#FeatureTool").     Images are available both for bootable floppy and bootable CD.   (The CD refused to exit gracefully but the adjustment still worked.)  This tool works on my Pangolin's HDD (HTS541080G9AT00) and possibly drives in other System76 products.  With it you can set the APM parameter that will persist across resets and power cycles.  After I set the value, the Pangolin then had this value after booting, so apparently my Pangolin BIOS does not touch this setting.  YMMV.  Of course, you will have to make the determination whether setting the value this is way is what you wish to do.  After boot, you can still change the parameter with **hdparm** as before.

---

### Post by ubuntu_demon on 2007-11-15
> **blackhole54 said:**
> In the event this may help somebody ...

Hitachi provides a tool for some of its hard drives that is available for download [here]("http://www.hitachigst.com/hdd/support/download.htm#FeatureTool").     Images are available both for bootable floppy and bootable CD.   (The CD refused to exit gracefully but the adjustment still worked.)  This tool works on my Pangolin's HDD (HTS541080G9AT00) and possibly drives in other System76 products.  With it you can set the APM parameter that will persist across resets and power cycles.  After I set the value, the Pangolin then had this value after booting, so apparently my Pangolin BIOS does not touch this setting.  YMMV.  Of course, you will have to make the determination whether setting the value this is way is what you wish to do.  After boot, you can still change the parameter with **hdparm** as before.

Most of these kind of tools are included on the Ultimate Boot cd-rom. Be sure to look up which tool you need.

IMHO people should only use these kind of tools if they are very heavily affected (their Load_Cycle_Count will reach it's lifetime way before 3 years of harddisk lifetime) and the unofficial ugly fix doesn't work for them for some strange reason.

Let's use this thread for communication with system76.

Let's use this thread support regarding the Load_Cycle_Count issue:
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by blackhole54 on 2007-11-15
> **ubuntu_demon said:**
> Let's use this thread for communication with system76.

My rationale was that my concern with this matter relates to the System76 systems I bought, I was relating this tool to those systems with the expectation that my experience would probably generalize to at least some (maybe many) other System76 systems, and I was describing how the BIOS of my System76 system interacted (i.e., didn't interact) with the value set by this tool.  If this forum was still hosted by System76 (as it was originally) instead of being moved to UbuntuForums, I would think my post would have been quite appropriate.  So I reasoned it would be appropriate here.  I still think so.

I stated that people would have to decide for themselves whether using this Hitachi tool to set the default APM value was apropriate for them.  I used it so that I wouldn't have to worry about this issue with each different distro I run on the machine.  (I am far from satisfied that I understand the underlying issues.  I do wish we would hear from System76 R&D about their perspective on this.)  Realize that I purchased computers with Linux presinstalled so I could feel confident that the hardware would work with Linux.  Ubuntu just happened to be the distro that was installed.  (Although System76 did add some nice touches.)

EDIT:  I had the additional reasons for buying a preinstall to support a company that was preinstalling and to knowing that none of my money was going to support Microsoft.

---

### Post by ubuntu_demon on 2007-11-16
> **blackhole54 said:**
> My rationale was that my concern with this matter relates to the System76 systems I bought, I was relating this tool to those systems with the expectation that my experience would probably generalize to at least some (maybe many) other System76 systems, and I was describing how the BIOS of my System76 system interacted (i.e., didn't interact) with the value set by this tool.  If this forum was still hosted by System76 (as it was originally) instead of being moved to UbuntuForums, I would think my post would have been quite appropriate.  So I reasoned it would be appropriate here.  I still think so.

I stated that people would have to decide for themselves whether using this Hitachi tool to set the default APM value was apropriate for them.  I used it so that I wouldn't have to worry about this issue with each different distro I run on the machine.  (I am far from satisfied that I understand the underlying issues.  I do wish we would hear from System76 R&D about their perspective on this.)  Realize that I purchased computers with Linux presinstalled so I could feel confident that the hardware would work with Linux.  Ubuntu just happened to be the distro that was installed.  (Although System76 did add some nice touches.)

EDIT:  I had the additional reasons for buying a preinstall to support a company that was preinstalling and to knowing that none of my money was going to support Microsoft.

Okay sure. 

If you use a tool to set your apm to 254 because you can't use hdparm for some reason you have to realize that your harddisk head won't park even while on battery (parking the head protects your disk from bumps and lowers the temperature and power).

---

### Post by blackhole54 on 2007-11-16
> **ubuntu_demon said:**
> If you use a tool to set your apm to 254 because you can't use hdparm for some reason you have to realize that your harddisk head won't park even while on battery (parking the head protects your disk from bumps and lowers the temperature and power).

True.  But that is also true with the "ugly fix."  However, with my *Load_Cycle_Count* already over 600,000 after 10 months, I consider my situation critical.  At least until I understand more.   And as  I noted in my first post, I can't see any noticable change in power consumption.  I would say at most 1 watt out of 20.  (BTW, in the 20 days since I changed the APM value to 254, my *Load_Cycle_Count* has gone up less than 300.)

---

### Post by ubuntu_demon on 2007-11-21
> **blackhole54 said:**
> True.  But that is also true with the "ugly fix."  However, with my *Load_Cycle_Count* already over 600,000 after 10 months, I consider my situation critical.  At least until I understand more.   And as  I noted in my first post, I can't see any noticable change in power consumption.  I would say at most 1 watt out of 20.  (BTW, in the 20 days since I changed the APM value to 254, my *Load_Cycle_Count* has gone up less than 300.)

My unofficial ugly fix includes instructions to also use /etc/acpi/battery.d/99-hdd-spin-fix.sh which should set your apm to 128 (or another value) when switching to battery but sadly not when booting from battery (you still have to do that manually).

my unofficial ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Debian also uses a "hdparm -B 254" style fix in it's newest acpi-support see :
[http://ubuntuforums.org/showpost.php?p=3811236&postcount=458](http://ubuntuforums.org/showpost.php?p=3811236&postcount=458)

---

### Post by ubuntu_demon on 2007-11-22
I have improved the "unofficial ugly fix" thanks to blackhole54 who told me I could use *on_ac_power*. see : [http://ubuntuforums.org/showpost.php?p=3817920&postcount=491](http://ubuntuforums.org/showpost.php?p=3817920&postcount=491)

---

