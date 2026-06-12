---
title: "Trying to resolve some issues with my Ubuntu 16 Media server!"
date: 2016-10-10
forum: Server Platforms
---

### Post by rogert9ri on 2016-10-10
first, of I've been running Ubuntu for several years now with little to no difficulty and the performance has been great! I recently started noticing some issues with streaming media. I have been experiencing some significant buffering and freezes during some play back. The buffering and freezing is not consistent, ie I can stream older files with no issues, just about ALL newer media is problematic.  I think I might be experiencing intermittent drive problems but cant' really figure out the log files. I hope someone with more experience then I can guide me a bit. 

System Description: Ubuntu 16.04LTS, 7 sata drives, sda through sdg setup as 3 RAID1 Volumes (~7TB).

I check the kern.log file and find these lines:
Oct 10 14:47:50 Mizar kernel: [ 9124.433646] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 frozen
Oct 10 14:47:50 Mizar kernel: [ 9124.434322] ata2.01: failed command: SMART
Oct 10 14:47:50 Mizar kernel: [ 9124.434988] ata2.01: cmd b0/da:00:00:4f:c2/00:00:00:00:00/10 tag 0
Oct 10 14:47:50 Mizar kernel: [ 9124.434988]          res 40/00:01:01:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 10 14:47:50 Mizar kernel: [ 9124.436390] ata2.01: status: { DRDY }
Oct 10 14:47:50 Mizar kernel: [ 9124.437123] ata2.00: hard resetting link
Oct 10 14:47:50 Mizar kernel: [ 9124.753651] ata2.01: hard resetting link
Oct 10 14:47:56 Mizar kernel: [ 9130.274097] ata2.00: link is slow to respond, please be patient (ready=0)
Oct 10 14:47:59 Mizar kernel: [ 9133.074371] ata2.00: SATA link up 6.0 Gbps (SStatus 133 SControl 330)
Oct 10 14:47:59 Mizar kernel: [ 9133.074387] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
Oct 10 14:47:59 Mizar kernel: [ 9133.106787] ata2.00: configured for UDMA/133
Oct 10 14:47:59 Mizar kernel: [ 9133.131218] ata2.01: configured for UDMA/133
Oct 10 14:47:59 Mizar kernel: [ 9133.131238] ata2: EH complete

I know this appears to be a SATA link failure, but have replaced the sata cables a number of times to check. The odd time I also see ata5 failing also!
Changing cables appears to have made no change.

What is really confusing is the kern.log is also filled with this;
Oct 10 19:16:17 Mizar kernel: [25232.807032]  sdg:
Oct 10 19:21:19 Mizar kernel: [25534.522003]  sdf:
Oct 10 19:21:19 Mizar kernel: [25534.542207]  sdg:
Oct 10 19:26:29 Mizar kernel: [25844.885345]  sdf:
Oct 10 19:26:29 Mizar kernel: [25844.911125]  sdg:
Oct 10 19:26:29 Mizar kernel: [25844.912364]  sdg:
Oct 10 19:31:39 Mizar kernel: [26155.152850]  sdf:
Oct 10 19:31:39 Mizar kernel: [26155.191083]  sdg:
Oct 10 19:36:40 Mizar kernel: [26455.562249]  sdf:
Oct 10 19:36:40 Mizar kernel: [26455.626174]  sdg:
Oct 10 19:41:50 Mizar kernel: [26765.794257]  sdf:
Oct 10 19:41:50 Mizar kernel: [26765.828418]  sdg:
Oct 10 19:43:19 Mizar kernel: [26854.863766]  sdf:
Oct 10 19:43:19 Mizar kernel: [26854.887760]  sdg:

SMART reports no problems on any drives!, Badblocks reports ZERO blocks on all drives. nmon shows nothing that stands out.
Any idea? or direction?  I am still trying to test to see if these messages get logged at same time as media freezes.
Any help would be greatly appreciated.

---

### Post by TheFu on 2016-10-11
Get those backups ready. What sort of RAID1? HW, SW, Fake?  Could be the disk controller failing. Swap some of the cables around at the controller connection point and see if the problem follows the cable swaps.

When I had ATA5 errors, it was the HDD.  Swapped in a new one and everything got faster again.  Plus it was my last Seagate, so a good cause for celebration.

---

### Post by rogert9ri on 2016-10-12
It's a software RAID1. I notice the failed ATA's every time on bootup and occasionally throughout the logs at different times.  Going to buy NEW cables today to try tonight.  
The other sections of the kern.log file are still a mystery. I can't figure out why the kernel would be reporting just the last 2 drives with no details!! just      
Oct 10 19:43:19 Mizar kernel: [26854.863766] sdf:   
Oct 10 19:43:19 Mizar kernel: [26854.887760] sdg:    

sdf and sdg are on SATA 5 and comprise md2. Drives sdf,sdg (Western Digital's) are the most recent pair added to the system. I get the odd errors about SATA 5 failing but not as frequently as ATA2 (containing Seagate Barracudas). More of a mystery are these two lines that get repeated for hundreds of lines in the log! and making the kern.log quite large, (hundred megs!+)  and only started in last few weeks.        Media from earlier (likely stored on ATA2 appears to play fine!), its the recently stored media that causes issue and are likely on the later drives. Would be nice to find a way to locate a file on a physical drive in an LVM array!

I have used smartctl to check each and every drive and ALL report passed and I see no CRC errors, I have noticed that sometimes it can take several seconds before smartctl reports from some drives, not everytime but frequently, not sure if normal but no errors. APCI is turned off, the drives never spin down. Badblocks test report 0 blocks on all drives. mdadm reports all RAID units are clean. SMART is active on all drives, no faults are being posted from either SMARTMON or MDADM. 

If no other process is complaining about drives, why and what is the kernel reporting ! a bug!      Hope to do some more tests tonight to see if the ATA's fail during media playback causing my video freezing and buffering, looks like it can take several seconds for the ATA to recover, so it sounds about right for the delay, should not be a problem as my media boxes cache a couple hundred megs at time, but apparently the entire system stalls during the ATA reset!

---

### Post by rogert9ri on 2016-10-18
Well... (Thanks TheFu) Fixed part of the problem by replacing one of the drives, even though it passed all SMART, so lesson learned, SMART is not so SMART!!! Still a bit perplexed about the kernel dumping the following:

Oct 10 19:43:19 Mizar kernel: [26854.863766] sdf:   
Oct 10 19:43:19 Mizar kernel: [26854.887760] sdg:    

My logs fill up with them, no issues at all with these drives, and the Kernel report is cryptic... Any Clues?

---

