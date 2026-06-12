---
title: "Strange behaviour makes me think of a virus."
date: 2020-06-19
forum: Security
---

### Post by snorretik on 2020-06-19
Okay so I think I have contracted a virus... in my network as well... I have tried to install clamav to see if it picks up something. However it's still going on. Just now Software Center just disappeared, and in general ubuntu is either really slow... or being weird at log in and shut down. And now the disappearance of Software Center. It was still there a couple of minutes ago and now searching activities it doesn't find anything.

Further more, for a longer time already all my devices have weird window flashes as if something briefly passes by and I got increasingly worried about all of that. Also, sometimes Ubuntu takes a really long time to shut down.

When it was being really weird it reported problems as well and sent the error reports. So it should at least get logged for the developers.

However that's no fix. I did mess with wine for a while before all of this started, because I wanted to be able to read an ebook in Linux however that failed. I don't know if it's related but it said somewhere that that could be a real culprit. Also did some SSH with github but shouldn't have been a problem.

I'm just looking for advice on what I can do if there is a virus present in my network/system. This is because some of the problems have switched to my old laptop with Ubuntu as well. So it did go across to other PC's.

On my main PC it is set up as Dual Boot. But Windows is doing fine as far as I can tell. I've got professional virus software on Windows as well so if it turned up there I *would* have a place to turn to. However it's not available for Linux and I don't know what to do if it's related to that.

Any suggestions?

---

### Post by EuclideanCoffee on 2020-06-19
Without a virus scan, it's hard to say. There aren't a lot of known malware, but that doesn't mean there isn't any malware.

eBooks have a reputation for carrying malware. I recommend reinstalling your operating system, as that would likely take care of any configurations changed and give you a fresh new operating system.

---

### Post by snorretik on 2020-06-20
I reinstalled my operating system on my laptop already, and the first thing I did with it was install clamav and run it. It appeared as if there was a problem with updating clamAV though, through the GUI clamtk, because the buttons messed up and overlapped eachother. But then I did a "freshclam" and it should have been updated. It didn't find anything.

There was one other thing, on my windows pc a "cd" was found, even if I don't have a cd drive installed in the hardware at all. I tried some stuff on it, scanning, "destroy it" (an option of Avast), didn't work. Then I just ejected it, and it didn't pop up anymore. But I don't know what it does if Ubuntu sees a cd pop up.

I'm giving you all the details in the hope that there might be a lead in it.

However I don't know what more I can do than reinstalling OS and scanning it with clam. And it seems as if it's still present. Or could this disappearance of Software Center just be a bug? Maybe a simple fix?

---

### Post by TheFu on 2020-06-20
I'd assume a hardware failure first.  A failing disk or disk controller can cause the behavior you've described. Check that first.  Look in the logs (/var/log/*) and use smartctl or Gnome-Disks to check the SMART data for badness.

As for the video issues - a loose cable or failing PSU or failing GPU can cause that. So can improper GPU drivers. Stay with the drivers provided through Canonical's ubuntu-drivers program.

Assuming zero HW issues, which I'm unconvinced about still ... 

When you look at your versioned backups, do you see any new files or changes to existing file owners, groups or permissions that don't make sense?

Doubt you have a virus. Sounds more like a rootkit. There are scanners for root kits, but for those to be effective, run them from a flash "try ubuntu" boot device.  ClamAV searches for Windows viruses, not Linux.  WINE is good enough for some Windows viruses to get in. If you remove WINE or just don't run any WINE programs, that should end any Windows viruses.  I'd just move the WINE-PREFIX to a different location while testing that hypothesis.

Jumping to other systems could just be coincidence.  Over the last 3 weeks, I've had 3 HDDs failing. They were completely disconnected events, but if I were superstitious, I'd think some relation existed.  Yesterday, got a warning about another HDD having SMART errors. Is that connected?  Nope. It is just a 6 yr old HDD nearing end of life.

I'm not saying there aren't Linux viruses, but usually those don't happen. A worm or rootkit is much more likely. Linux systems are most useful as C&C (command and control) for huge botnets.

---

### Post by snorretik on 2020-06-20
Okay, I found that a program chkrootkit can check for those. However it appears it's not as simple as "try Ubuntu" and then sudo apt install chkrootkit. Cause it can't find it. Do I have to somehow include it on the USB I'm booting from?

It continues doing all kinds of weird stuff by the way. Now also before logging into Windows.

---

### Post by deadflowr on 2020-06-20
Most likely need to enable the universe repository.
Steps would be
```
sudo add-apt-repository universe
sudo apt update
sudo apt install chkrootkit
```

---

### Post by snorretik on 2020-06-20
Okay thanks, I was able to run both chkrootkit and rkhunter. Now it gave me some results:
- Chkrootkit seems like it hasn't found that much. Two suspicious files/directories, I wrote them down. And at some point it says "Warning: Possible LKM Trojan installed". And nothing deleted it says. However I don't really know what to look for. But it didn't have obvious "infected" flags.
- Rkhunter was also run. It has a system checks summary. It says it checked 142 files. Found 1 suspect file. Then Rootkit checks, checked: 477, possible rootkits: 6.

I copied the whole terminal window. I was told to run cat as well and that displayed the log file I believe. Copied that with it. So I've got the whole record I guess. But I don't know what to look for or how to fix the issues. There's a lot of documentation on it but that's going to take a really long time. If anybody can explain to me clearly what to do with this info or how to actually fix this I would really appreciate it. And prevent this from happening again.

Edit:
@TheFu, I wasn't keeping versioned back ups as far as I know. I had some important files backed up and that was it. When this is over I'll consider doing something like that.

---

### Post by TheFu on 2020-06-20
*Try Ubuntu* booting uses an overlay file system. This is handy in that the iso cannot be compromised assuming it came from a reputable source and the signature has been cryptographically validated.  in 20.04 that happens automatically.

But the environment won't remember anything installed after a reboot.  So you'll need to enable a repo, install some root-kit scanners, run those and clean up whatever they find.  When you reboot, those installs and repo changes are lost.

i still think  there is a HW problem.  Did you look at the logs?  Did you look at the HDD SMART data?

All the root-kit scanners are known for false positives.  The fix is to wipe the disk and restore from backups prior to the issues happening.  Daily, automatic, versioned, backups, "pulled" by another system, are the #1 security technique for all Unix-based OSes.  Don't use network storage that the client machine can access, since then the infected client can destroy all the backups too.  The backup server needs to "pull" the backups and not allow any clients direct access in.

Backups have all sorts of uses.  This morning a 20.04 weekly patch went very wrong here and left me without any kernels.  After 30 minutes trying to fix it, i gave up and wiped the machine, did a fresh install and restored my backups from last night into it. Took 30 min.

Nobody can tell you how to prevent stuff from happening without knowing what you did.  i haven't used AV on any desktop systems since about 2012 when my last contract that mandated professional liability insurance ended. 

Update: i don't do high risk behaviors like allowing javascript to run from most websites or allowing any flash or java. Don't use social networks at all. My Windows systems are never used online except to do non-email and non-browser things.  Not everyone can make these choices.

---

### Post by snorretik on 2020-06-20
Lol I tried typing it down but I think it became too much information. The first reaction I had is that because I have a relatively new PC I didn't mind reinstalling the OS etc. I had a couple of files that I wanted. And then I did a full factory reinstall.

So actually if I could wipe in the same way you did I would be glad to. Makes it a lot less complicated. But I have heard that there is possible malware that hides on your network. Then I wouldn't know what to do anymore. But as you said it could be a coincidence. 

Edit: I didn't check for hardware yet. So I'll do that now.

Edit 2:
There is something going on though. Which I wanted to try and solve with a factory reset. It's a few partitions I can't seem to delete or do anything at all with. And I do remember having tinkered with some online guide in the partitioning when trying to install Ubuntu. Afterwards it was no longer necessary because it recognized the Windows OS and could install next to it. But at first it didn't detect it yet. Yeah there's all kinds of stuff that could've gone wrong now that I think of it... there's other stuff too. Like it freezing my pc until I changed some BIOS settings to legacy. 

Anyway, when I go to var log there's crosses there on 3 directories and 3 files. I don't know if that's good. Also when I boot Ubuntu from my USB it does disk checks and it says it finds 1 problem and that "it could result in errors".

---

### Post by ajgreeny on 2020-06-20
The problem found when booting your USB means there is a problem in that USB live system, not necessarily in your installed system, and may have nothing to do with your installed OS, unless, of course, it is the same USB medium you used to install your OS.

---

### Post by snorretik on 2020-06-20
Yeah it is. Both on the Dual Boot and the laptop. Which would explain the "jump".

---

### Post by snorretik on 2020-06-20
Okay so it's still not without trouble. This is the first time it didn't start with errors. However while updating some small stuff a gray screen flashed before my eyes "Oh no something went wrong". And I got logged out. Couldn't shut down the system anymore. Had to force it off. Turned it on again... and it seemed stable for a while. But now this laptop takes an age to shut down as well. Which is what the initial problem was with the Dual Boot PC. Keeps nagging about a keychain as well and I don't particularly trust that.

Not really happy about this stuff...

---

### Post by TheFu on 2020-06-20
Hardware failure...   look at the log files.

---

### Post by EuclideanCoffee on 2020-06-20
I think this is a hardware failure too.

Try ```
 dmesg | grep error 
```

Sometimes things pop out, and I can fix them immediately.

---

### Post by snorretik on 2020-06-21
It only shows one line but I'll paste it in here.

[    1.681620] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro

I'm going to do some reading on how to read and interpret the log files.

---

### Post by TheFu on 2020-06-21
> **snorretik said:**
> It only shows one line but I'll paste it in here.

[    1.681620] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro

I'm going to do some reading on how to read and interpret the log files.

That line just shows that sda2 has mount options. The "errors" that grep found was part of the mount options, not actually an error.  
I'd NOT be very surprised if there were 50+ errors in the logs.  Even normally working systems will have errors because determining which CPU family is being used shows up and causes errors.  I'd look using something like this:
```
$ egrep -i 'erro|warn' /var/log/*g
```
May need to pipe it through a PAGER. 

There is probably a "*Log Viewer*" somewhere in the menus if you're using any Desktop Ubuntu flavor.

Have you looked at the SMART data for the disks yet?

---

### Post by snorretik on 2020-06-21
Right, I found a log viewer. It has an "important" tab, and I can go back to yesterday evening and see what the logs were.

There are just a few, for yesterday evening:
Under Security it says "Failed to start GNOME Shell on X11". 
Then under Other it says "Failed to start Wait until snapd is fully seeded."

Then through all the subsequent sessions there is a:
"System Bluetooth: hci0: unexpected event for opcode 0xfc2f"
"Other dbus: wpa_dbus_property_changed: no property SessionLength in object /fi/w1/wpa_supplicant1/Interfaces/0"
"System Initramfs unpacking failed: Decoding failed"

I checked Smart, there is an option to do a self test. I did a short one, an extended one. They both succeeded. And the conveyance gave me an error "not supported".
And all the assessment values are OK.

And I did your command but that flooded my screen with all kinds of errors and warnings so that was a bit too much. I can do it again with additional info on what to look for but right now it doesn't seem very useful. Oh right I did look for what a pager is. Could do that more thoroughly so that's something I could still do.

Edit: Right, and there still is an option to use the Snap Store. Which is identical to the Software Center. So that's no longer a problem. I didn't know about that.
So I'm going to continue on my laptop and see if it can stay stable for a while. And if something happens I know I can use that log viewer utility and see if anything popped up under "important".
Still want to know what caused the gray screen... but if from now on it can stay stable for a while perhaps I can start installing some programs on it again.

---

### Post by TheFu on 2020-06-21
SMART data without raw values is almost worthless.  The "OK" is often lies.  

"conveyance" isn't something I've seen in SMART.

Rather than interpreting data, please copy/paste it here and wrap that output in "code tags" as we do for all terminal commands and output. Why? Because most output has columns and when they don't line up as we see in a terminal, it is hard to read/understand.

Perhaps some other cook can be more helpful than I?

---

### Post by snorretik on 2020-06-21
Okay so I think this is what you want to see:

```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-37-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     KINGSTON RBU-SC100S37128GD
Serial Number:    50026B725114E750
Firmware Version: S8FM06.9
User Capacity:    128.035.676.160 bytes [128 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Jun 21 20:49:53 2020 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  255) seconds.
Offline data collection
capabilities:              (0x1b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (   2) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0013   100   100   050    Pre-fail  Always       -       0
  7 Unknown_SSD_Attribute   0x000b   100   100   050    Pre-fail  Always       -       0
  8 Unknown_SSD_Attribute   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       9724
 10 Unknown_SSD_Attribute   0x0013   100   100   050    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0012   100   100   000    Old_age   Always       -       3316
168 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       3
170 Unknown_Attribute       0x0003   100   100   010    Pre-fail  Always       -       288
173 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       6226083
175 Program_Fail_Count_Chip 0x0012   100   100   010    Old_age   Always       -       0
187 Reported_Uncorrect      0x0012   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0012   100   100   000    Old_age   Always       -       23
194 Temperature_Celsius     0x0023   035   035   000    Pre-fail  Always       -       35
196 Reallocated_Event_Count 0x0002   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000b   100   100   050    Pre-fail  Always       -       0
218 Unknown_Attribute       0x000b   100   100   050    Pre-fail  Always       -       0
233 Media_Wearout_Indicator 0x000b   100   100   000    Pre-fail  Always       -       7796
240 Unknown_SSD_Attribute   0x0013   100   100   050    Pre-fail  Always       -       0
241 Total_LBAs_Written      0x0012   100   100   000    Old_age   Always       -       5191
242 Total_LBAs_Read         0x0012   100   100   000    Old_age   Always       -       2800
244 Unknown_Attribute       0x0002   100   100   050    Old_age   Always       -       95
245 Unknown_Attribute       0x0002   100   100   050    Old_age   Always       -       163
246 Unknown_Attribute       0x0002   100   100   050    Old_age   Always       -       3966180
250 Read_Error_Retry_Rate   0x0002   100   100   050    Old_age   Always       -       6554

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%         3         -
# 2  Extended offline    Completed without error       00%         0         -
# 3  Short offline       Completed without error       00%         0         -

Selective Self-tests/Logging not supported
```

Edit:
Conveyance is also mentioned here:
[URL="https://wiki.archlinux.org/index.php/S.M.A.R.T."]https://wiki.archlinux.org/index.php/S.M.A.R.T.
[/URL]It's one of the 3 tests it can do.

Edit 2:
Lol and Software Center just popped back again. This is so weird. Now snap store is gone. It seems to be either one though, which is good enough.

---

### Post by EuclideanCoffee on 2020-06-22
I think you should try reopening this thread in a hardware support forum.

I believe the issue is related to hardware, and there can be plenty of troubleshooting done there.

If you find a virus, the real thing you can do is reformat, as there really isn't a good way to help you clean your PC remotely on a forum.

---

### Post by snorretik on 2020-06-22
Well, it got worse. Yesterday it spread to my TV. It was flashing black and back again like 3 times every 5 seconds for about a minute. Then I turned it off and turned the whole media box off (which does TV and internet in one). Now today turning it back on it seems normal again and the flashing is gone. But yesterday to me that was a signal that it was definitely a form of malware.

So I contacted Avast, they can only guarantee safety for Windows, and not the modem/tv or anything related to Linux.

And next time it happens I can contact my internet/tv provider.

So I myself don't think it's hardware. I had problems on both my Dual Boot PC and then the laptop. Then I saw screens flashing by on both my Android Phone and Android tablet. And then the TV stuff. So yeah if that changes things for you guys let me know. But if I can't solve this some other way I'm going to prepare to stick to Windows.

---

### Post by EuclideanCoffee on 2020-06-22
This appears to be a network security question.

This community forum assists in "Questions about security in Ubuntu and the official flavours."

Though I believe many users here have years of professional experience, network administration really isn't simply Ubuntu.

When your router has been attacked, we can assist with suggestions, but that support lands with your ISP and network administrator.

You're better off looking for support from a general security or network focused board, which there are many on the net.

---

### Post by TheFu on 2020-06-22
> **snorretik said:**
>  
So I contacted Avast, they can only guarantee safety for Windows, and not the modem/tv or anything related to Linux.
 

That's just funny.  Avast cannot guarantee anything.  A/V is, at best, 50% effective. There have been studies by security professionals. Running the top 20 A/V programs on a Windows system only finds 80-90% of **known** viruses.

We're getting to a place that "ghosts" are the most likely answer from the problem expansion.  People who believe in ghosts are much more likely to see ghosts when they look.  Someone has to be specifically targeting you for this sort of stuff and few people would have the skills to do it.  That means some organization wants to drive you crazy. Is that likely?  

Getting a virus on Linux is extremely unlikely.  
Getting a virus on Windows is behavior dependent.
Do you have a router?  Is it patched at least monthly?  Is it still supported by the vendor?  If not, then some "bad people" may have complete access to your LAN and might have come in to accomplish something specific. Would they have a reason to bother?  
Do you use Windows on the internet?  Do you do other high-risk activities?  Is your smartphone connected to your LAN?  Is your wifi using a trivial password? Do your neighbors know with wifi password?  How else might some virus or "bad person" gain access to your LAN?

I'm back to the loose video connector or failing power supply types of issues.  Is the power to your house solid? Can you see the input voltages?  

My systems are on UPSes. I know that right now the incoming power is 60hz and 121V. The UPSes condition the power to be 120V at 60Hz.  One is using 128W and the other is using 90W of power.  There are 5 computers connected, 2 routers, 3 switches, a 4-port KVM, 2 external disk arrays and a cable modem all going through those UPSes.  

Had 3 HDDs fail in the last 3 weeks, about a week apart. They were mostly really old and didn't completely fail, but one was under 4 yrs old, so that one was just a not-so-great lifespan situation. I watch the SMART data monthly, but create reports for all disks weekly.  I saw the errors growing on these disks over time.  Your SSD does indeed seem fine.  SSDs aren't like spinning disks.  When they fail, they just stop working. Sometimes we'll get lucky and the SSD will go into read-only mode for a month before it dies completely. I've seen both happen.  Dead without warning and read-only for a few months before dying.  Same for flash storage (USB/SDHC/microSD).

A laptop does have some key presses that happen without anyone touching it at all.  Probably a pinched keyboard connector or some faulty key input contacts. It has been doing that for a few years. I jiggle the key and it stops for about a month. Today it was the down-arrow. Usually it is the 'd' key.  That's just a 10 yr old laptop with an issue, not a virus.

No ghosts here. ;)  But I doubt I can convince someone else.

---

### Post by daveginboav on 2020-06-22
Could sophos be of any use to you?
[https://www.fosslinux.com/2852/how-to-install-sophos-antivirus-software-in-ubuntu.htm](https://www.fosslinux.com/2852/how-to-install-sophos-antivirus-software-in-ubuntu.htm)

---

### Post by snorretik on 2020-06-25
I will look into Sophos, thanks.

As far as Avast goes with guaranteeing stuff, it's the same as insuring yourself from storms doesn't stop the storms from coming. Once I got a virus on my Windows PC, Avast has to do their part of the deal and get to work on it. I expect them to do the work when things go wrong. Not prevent it from happening altogether. That's a difference.

---

### Post by TheFu on 2020-06-25
An excerpt from the Avast software license if you have the paid Assurance Plan:

> 13.8.2. If you request Vendor’s assistance under the Assurance Plan, and if you and your Device qualify for assistance under Section 13.8.3, **Vendor will use commercially reasonable efforts to assist you to remove the viruses or other Malicious Code affecting your Device.** You hereby acknowledge, accept and agree that **Vendor’s efforts may not be enough to remove certain viruses or other Malicious Code from your Device**, and that Vendor, in the course of providing service, may alter, **delete or corrupt data** on your Device, change Device settings, or otherwise interfere with the proper operation of your Device.

Avast/AVG damaged their reputation when they were caught selling user and system data in 2019. That doesn't matter to everyone. Google and Mozilla removed their browser addons from their "stores" over it.  Seems google only approves when they do the spying. ;)

---

### Post by snorretik on 2020-06-26
Right. I wanted to add a bit saying "insurance companies try to get out of certain costs as well", which is true. So I know it's probably still going to be an issue if something happens. However you can't first sell something and then talk your way out of it through all kinds of legal trickery. Cause that would just be deception in the end. If that's what it all boils down to, it doesn't hold in court. And you just need to prove it. I'm convinced about that... but the only real test would be if it actually happens and is important enough. They sell it by using "commercially reasonable". That's the key thing there, if it wouldn't have included that it would be nonsense.

I didn't know about their reputation though.

Edit:
I guess if it's a really professional attack reasonable will at some point be a problem.

---

### Post by snorretik on 2020-06-29
@ EuclidianCoffee

Could you perhaps point me in the right direction when looking for other boards? I'm not finding the boards you referred to.

---

### Post by EuclideanCoffee on 2020-06-29
Maybe Reddit or StackOverflow?

---

### Post by snorretik on 2020-06-29
Right, the big ones. I'll give them another go, thanks.

---

