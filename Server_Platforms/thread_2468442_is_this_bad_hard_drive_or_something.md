---
title: "is this bad hard drive or something"
date: 2021-10-29
forum: Server Platforms
---

### Post by kustomjs on 2021-10-29
As anybody seen this error before?

It also seems like the whole system is in read only file format even if I am logged into root I cant make any changes.

[ATTACH=CONFIG]289391[/ATTACH]

---

### Post by TheFu on 2021-10-29
Could be anything.

Make good backup.

Attempt to run fsck on all the file systems.

Check the SMART data for each physical storage device.

Expect the disk to completely fail - no read at all - very soon.

---

### Post by carini on 2021-10-30
Seen similar messages on VM with a corrupted VMDK disk underneath. Is this a physical machine?

---

### Post by kustomjs on 2021-10-30
yes it was a physical machine with SSD drive on it and no VM so I had to make a whole new machine on different hard drive so I just wanted to know if its done for because I was able to get into the hard drive when I use ubuntu desktop and grab the files and I am just wondering if there was a way to repair the system or is it toasted?

---

### Post by TheFu on 2021-10-30
Check the SMART data on the drive.  [https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T).

---

### Post by carini on 2021-10-30
Can you copy your disk with dd on another SSD? (you can start from a live USB)

---

### Post by TheFu on 2021-10-30
> **carini said:**
> Can you copy your disk with dd on another SSD? (you can start from a live USB)

On a failing disk, **ddrescue** would be a better choice. Also, be certain that the sector alignment on both drives is the same. Misaligned sectors makes storage work harder.  Though with SSDs, it probably doesn't matter to performance. On HDDs, it could be a 30% performance hit.

---

### Post by kustomjs on 2021-10-30
> **TheFu said:**
> Check the SMART data on the drive.  [https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T).

the hard drive didnt have that when I tried it its on SSD adata su630 drive

---

### Post by CharlesA on 2021-10-30
> **TheFu said:**
> On a failing disk, **ddrescue** would be a better choice. Also, be certain that the sector alignment on both drives is the same. Misaligned sectors makes storage work harder.  Though with SSDs, it probably doesn't matter to performance. On HDDs, it could be a 30% performance hit.

Agreed. Always create a log file when using ddresuce too.

> **kustomjs said:**
> the hard drive didnt have that when I tried it its on SSD adata su630 drive

It should have some SMART data.

You should be able to read it via smartctl if you have the smartmontools package installed.

```
sudo smartctl -a /dev/sda
```

It should output something similar to this (which is one of the SSDs on my server):

```
Model Family:     OCZ Intrepid 3000 SSDs
Device Model:     OCZ INTREPID 3600
Serial Number:    xxxxxxxxxxxxxxxxxx
Firmware Version: 1.4.7.7
User Capacity:    800,166,076,416 bytes [800 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Runtime_Bad_Block       0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       33785
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       111
190 Temperature_Celsius     0x0000   047   075   000    Old_age   Offline      -       47
```

---

### Post by bunny9000 on 2021-10-30
Can you see files and not access them? Sounds like a permissions issue.

---

### Post by kustomjs on 2021-10-30
I was finally got the server back up from read only system but I do believe the disk is failing so any pointers to make a full image back up with all my files in place so I can move it to my VM machine before this SSD fails.

---

### Post by MAFoElffen on 2021-10-30
Just read your PM.

Agreed with TheFu and CharlesA.

smartctl is not a default app and needs to be installed. Is part of the smartmon-tools package. I know TheFu uses this tool a lot. So do I.
```

sudo apt install smartmontools

```
Then do a few things to use it
```

sudo smartctl -i /dev/sda  # Will check if the drive is SMART capable
sudo smartctl -s on -d ata /dev/sda # will enable SMART in it's BIOS
sudo smartctl -d ata -a /dev/sda  # will run a complete detailed overall-health self-assessment test

```
I forget the server hardware you are running on... I don't remember if you run drives behind a RAID controller.

If so, if you could please mention what brand and model the RAID controller is, because you then need to tell smartctl to look "beyond" the RAID controller... just by adding an additional other argument to the command for that.

If you want to run extended tests or run SMART monitoring in the background, adding the results to your syslog, then smartd is a good choice, is in that same package and is a good daemon service to do that.

---

### Post by kustomjs on 2021-10-30
I tried to install smartctl noting happens so I want to create the whole image off this hard drive and move it to my VM machine I am currently upgrading it from 18.04 to 20.04

---

### Post by Bashing-om on 2021-10-30
correction:

Not  to intrude but the package is one worded:
> 
sysop@2004x-c:~$ apt policy smartmontools
smartmontools:
  Installed: (none)
  Candidate: 7.1-1build1
  Version table:
     7.1-1build1 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) focal/main amd64 Packages
sysop@2004x-c:~$


-Just to keep the record straight-

---

### Post by MAFoElffen on 2021-10-30
@Basing-Om 

Thank you for the catch. Been on the "metric" work-week lately.

---

### Post by Bashing-om on 2021-10-30
MAFoElffen :D

It's that muscle memory ya got to watch for :P

---

### Post by TheFu on 2021-10-31
I usually type the name of the program, then if it isn't installed, bash will tell me the possible package names with it.  Then I install the package and run the command.  On minimal OS setups, bash doesn't say the name of the package, that when it is time to do an **apt search**. I'm lazy, so I type just enough.  smart wasn't sufficient to get a short list, so I added a few more characters ...
```
$ apt search 'smartmo*'
Sorting... Done
Full Text Search... Done
hobbit-plugins/focal,focal 20191218 all
  plugins for the Xymon network monitor

libmatch-simple-perl/focal,focal 0.010-1 all
  simplified clone of smartmatch operator

smart-notifier/focal-updates,focal-updates 0.28-6~ubuntu20.04.1 all
  graphical hard disk health status notifier

[COLOR="#008000"]smartmontools[/COLOR]/focal 7.1-1build1 amd64
  control and monitor storage systems using S.M.A.R.T.
```

So ... **smartmontools** is the package name and perhaps the smart-notifier could be useful too?  I've not used the GUI thing, so I don't know.  Servers don't have GUIs.

For how to use it, the manpage is THE way to know.  There are also a number of posts in these forums with examples.
I run weekly "short" tests and monthly "long" tests on all my drives. It is automated in a script, though I think smartmon has some settings to do it cleaner.  I can create a bonehead bash script faster than learn yet another odd way to have SMART data.  My script puts the reports into a directory  (~/SMART/ on each system) and I keep 6 months of those reports, since the way to tell if a disk is going to fail soon is to see the critical numbers in those reports change over time.  A little sdiff or meld can make it clear what is changing from week to week.

And there's also **logwatch** which will see and SMART events (failures) in the system logs and include those in the daily reports.  I only look at the SMART reports when logwatch points out some issue, but if I don't have the data already, it could be much too late.

---

### Post by MAFoElffen on 2021-10-31
You can set up smartd as a daemon with it's smartd.conf file... It will  monitor and send the events to the sys.log. Yes, that is a more of  pre-emptive kind of thing. 

Now that it is suspected as bad... Better to use smartctl now, to see if, and how bad it is.

---

### Post by kustomjs on 2021-10-31
I am actually going take this old hard drive and clone it to new hard drive once I get my hard drive cloning docking station tomorrow. Thanks for who all helped

---

### Post by MAFoElffen on 2021-10-31
Like I said in PM... Here is mine. I have found it invaluable: [Thermaltake BlacX Duet]("https://www.amazon.com/Thermaltake-External-Enclosure-Docking-ST0014U-D/dp/B01J4XNLN6/ref=asc_df_B01J4XNLN6/?tag=hyprod-20&linkCode=df0&hvadid=416694317409&hvpos=&hvnetw=g&hvrand=12026523109180899877&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033428&hvtargid=pla-521906074929&psc=1&tag=&ref=&adgrpid=94693386435&hvpone=&hvptwo=&hvadid=416694317409&hvpos=&hvnetw=g&hvrand=12026523109180899877&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033428&hvtargid=pla-521906074929")
It has made things much easier for what I have to do sometimes. Mine is a few years old. There is faster ones out there now...

I think TheFu has a 4-Drive USB Dock...

My next investment for customers is getting a good USB3.1 NVMe enclosure to image NVMe drives on failed systems. (onsite from my service laptop)

---

### Post by TheFu on 2021-11-01
Actually, I own a BlacX Duet too, but it is USB2/eSATA. Probably 10+ yrs old.

My 4 disk devices are all external arrays - eSATA or infiniband connected. The eSATA one is hot swapable, though I don't really open the case.  The infiniband one is just the connection and I wouldn't recommend anyone actually seek that out. OTOH, the connection is screwed in-place and that part has been been any issue.

---

