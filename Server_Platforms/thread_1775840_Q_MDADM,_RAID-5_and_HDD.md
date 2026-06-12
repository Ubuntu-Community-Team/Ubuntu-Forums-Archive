---
title: "Q: MDADM, RAID-5 and HDD"
date: 2011-06-05
forum: Server Platforms
---

### Post by Krupski on 2011-06-05
Hi all, got a few quick questions if I may...

I'm running Ubuntu 11.04 64 bit server with five 1TB drives setup in a RAID-5 array under MDADM, yielding about 4TB. Works like a charm.

(By the way, the drives are Western Digital "Caviar Black" 1 TB SATA drives).

My first question concerns RAID-5. It seems to me that I can keep on expanding the array by simply adding more hard drives (I've experimented with up to 8 so far).

My question is, if a RAID-5 array is N+1 drives (the extra being used for RAID purposes), how can I keep expanding the array and still have it work?

The larger N is, the smaller percentage of space is available for the RAID housekeeping data. WHY DOES IT WORK???

Next question... has anyone ever had an INTERMITTENT hard drive?

One of the drives in my array recently "died" (MDADM took it offline and trying to look at it with CFDISK yielded an error - " FATAL ERROR: Cannot open disk drive").

So I bought a brand new replacement drive and before I replaced it, I fired up the server again to make absolutely sure which PHYSICAL drive had died so that I didn't pull the wrong one.

Surprise... the drive was working! So I ran some S.M.A.R.T. tests on it (using smartctl) and the drive tested perfectly - "Raw_Read_Error_Rate 0" and everything else OK.

So I kept the new drive in the box, not even opened and the server ran fine for weeks.

Then the same drive "died" again. Same thing, it came back to life and SMART said no errors.

Has anyone ever run into a drive like this? It plays dead, then works, then does it again?

I did replace the drive this time, and I also ran a full test on the flaky drive with the manufacturer's software (a detailed test that took over 4 hours to run) and the drive tests 100% good!

What the heck is going on here???

Any ideas or info will be greatly appreciated.

Thanks!

-- Roger

---

### Post by YesWeCan on 2011-06-05
> **Krupski said:**
> My question is, if a RAID-5 array is N+1 drives (the extra being used for RAID purposes), how can I keep expanding the array and still have it work?

The larger N is, the smaller percentage of space is available for the RAID housekeeping data. WHY DOES IT WORK???
Hi there. The RAID "extra" are parity blocks that are spread across all the drives. The idea is that RAID5 protects against a single drive failure and keeps the minimum parity required to do this. The amount of parity reduces as a % of drives because the amount of 1 drive reduces as the % of drives. Common sense is that the more drives you have the less protection (of all your data) you have and that is true. RAID5 can recover from 1 drive failure if and only if all remaining drives are perfectly readable. Cold comfort if you have a lot of drives.

RAID5 is not the safest, especially the more drives you add. This is because if you lose a drive all the other drives have to be entirely failure-free in order to regenerate the missing drive data. The more drives the higher the odds of a second failure. RAID6 is considerably safer and consumes 2 drives worth of parity blocks. RAID1 and its variants are safest as a rule because they mirror rather than use parity.

---

### Post by Krupski on 2011-06-06
> **YesWeCan said:**
> Hi there. The RAID "extra" are parity blocks that are spread across all the drives. The idea is that RAID5 protects against a single drive failure and keeps the minimum parity required to do this. The amount of parity reduces as a % of drives because the amount of 1 drive reduces as the % of drives. Common sense is that the more drives you have the less protection (of all your data) you have and that is true. RAID5 can recover from 1 drive failure if and only if all remaining drives are perfectly readable. Cold comfort if you have a lot of drives.

RAID5 is not the safest, especially the more drives you add. This is because if you lose a drive all the other drives have to be entirely failure-free in order to regenerate the missing drive data. The more drives the higher the odds of a second failure. RAID6 is considerably safer and consumes 2 drives worth of parity blocks. RAID1 and its variants are safest as a rule because they mirror rather than use parity.

Thanks for the reply!

I've had a total of four single drive failures over the life of the file server, and thankfully the RAID saved me each time. No data was lost.

The original reason that I built the server was to hold ripped DVD and BD disks. No, I don't pirate! But I have three kids and you know what happens to a DVD when kids get a hold of it.

So I buy a movie, rip it to the server and then put the original away in a safe place... finally watching the movie over the house intra-net.

At 7 to 8 GB per disk (and 25 to 50 GB for blu ray), you can see that the server fills up quick.

I also run a small message board on the server (although that takes up very little space).

As I began to run out of room, I added another hard drive. At first I thought I could ONLY have 3 drives as RAID-5, so I planned to make a second array, then JBOD together /dev/md0 and /dev/md1.

Then, I asked around and was told I could have as many drives as I wished and it worked... but then I wondered HOW it could work if the percentage of space available for RAID-5 parity blocks decreased.

As you can see by how I use the server, I NEED 4 or more terabytes of space. The box is already maxed out with 5 physical drives (only 5 SATA ports on the mobo - plus one eSata in the rear). My next option is to start over and use 2TB drives instead (yielding an 8TB array).

I really can't afford to "waste" the space by using RAID-6 (or RAID-1), although I do agree with you that either one is much safer than what I'm doing. If I lose more than 1 drive at a time, the data is history.

Lastly, do you have any thoughts on the mystery hard drive that plays dead? Ever see something like that before? I have not.

Thanks again for the reply!

-- Roger

---

### Post by ian dobson on 2011-06-06
Hi,

For my backup array (3x2Tb wd drives) I'm using a port multiplier card. The card has 1 port upstream (to motherboard) and 5 sata ports for harddisk.

As long as your sata port supports sata port multipliers, you can attach up to 15 drives to each motherboard sata port. Under linux each drive looks like a normal drive.

Port multiplier cards cost about 100$, abit more than a sata card but if you don't have a pci(-e) ports free it's a possible solution.

Regards
Ian Dobson

---

### Post by YesWeCan on 2011-06-06
> **Krupski said:**
> Lastly, do you have any thoughts on the mystery hard drive that plays dead? Ever see something like that before? I have not.
Not really. The closest I have experienced to those symptoms was due to a bad SATA cable connector.

---

