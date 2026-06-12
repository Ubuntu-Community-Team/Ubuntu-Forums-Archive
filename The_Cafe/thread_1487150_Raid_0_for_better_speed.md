---
title: "Raid 0 for better speed?"
date: 2010-05-18
forum: The Cafe
---

### Post by McRat on 2010-05-18
I always thought raid was only for data redundancy.

But somebody posted that it's good for speed.

Anyone have experiences or thoughts on Raid 0?

---

### Post by Zyrtec on 2010-05-18
RAID 0 is fast, but you're liable to major data loss if you don't have proper backup. RAID 0 is like striping the disks, so for a 2 Disk RAID 0 array, a 2 byte file would have byte 1 on Disk 1, and byte 2 on Disk 2. If Disk 1 fails, the array fails. So yeah, it's fast, but if one of your hard drives die, you're screwed.

RAID 5 is popular because it is a good mix of reliability and speed. The only drawback is that it requires 3 drives to have a raid 5. In this case, it spreads data across all the drives... for a 3 byte file with a 3 disk RAID 5, for example, bytes 1 and 2 would be on disk 1, bytes 2 and 3 would be on disk 2, and bytes 1 and 3 would be on disk 3. This way, if there is a disk failure, the data is still retrievable. 

Hope that makes sense.

---

### Post by undecim on 2010-05-18
> **Zyrtec said:**
> RAID 5 is popular because it is a good mix of reliability and speed. The only drawback is that it requires 3 drives to have a raid 5. In this case, it spreads data across all the drives... for a 3 byte file with a 3 disk RAID 5, for example, bytes 1 and 2 would be on disk 1, bytes 2 and 3 would be on disk 2, and bytes 1 and 3 would be on disk 3. This way, if there is a disk failure, the data is still retrievable. 

That's not quite right. The way you are describing, the data exists twice and uses twice as much space.

RAID 5 uses one disk for parity, which lets you use the other two for data storage, but if one of the disks goes out, the third can be rebuilt form the other two. It works by uses the XOR function.

The XOR function will return 0 if two bits are the same and 1 if two bits are different. For example, if you had 3 1-bit drives in a RAID 5 and two of them had the data "0" and "1" the third one would be 0 XOR 1, which is "1".

But that won't speed your system up any more than a RAID 1 will, which increases read speed, but decreases write speed, because in both cases, there are two sources to read data from, and two places data has to be written to.

The reason RAID 0 is faster is because it's set up like Zyrtec explained, it can read and write data twice as fast, because it only has to read/write half as much data to each disk, and is using them both simultaneously. But, that also means you only need one of them to go out in order for the whole thing to fail.

---

### Post by Zyrtec on 2010-05-18
I thought RAID 5 was distributed parity? It uses all the disks for storage, and can rebuild a replaced disk.



Edit: Yeah, I looked it up to make sure. I was just trying to explain it in a basic way, but the way it really is:  Disk 1 has byte 1, and parity with Disk 2. Disk 2 has byte 2, and parity with Disk 3. Disk 3 has byte 3, and parity with Disk 1.

It's not taking up twice as much space. The amount of storage for a RAID 5 is (n-1)*S  where n is the number of drives, and S is the total amount of space.

---

### Post by NMFTM on 2010-05-18
How fast is RAID0 if you don't have an actual RAID controller and are just using the harddrive controller built into your motherboard? In my case, JMicron.

---

### Post by McRat on 2010-05-18
I think only two motherboards I own have on-board RAID.  Best I can figure, you need to load the included Windows software to make it work after turning it on in BIOS.

So for Linux and this M/B, I don't think it's going work that way.

---

### Post by Xbehave on 2010-05-18
> **McRat said:**
> I think only two motherboards I own have on-board RAID.  Best I can figure, you need to load the included Windows software to make it work after turning it on in BIOS.

So for Linux and this M/B, I don't think it's going work that way. bn
AS i understand it there are 3 types of raid
1) Software raid, fully supported by Linux but limited to the number of HDD you can physically connect to your motherboard
2) Hardware raid, because linux is popular is server space, raid cards are apparently well supported (I'm not popular in server space so i don't know how true this is)
3) Fakeraid, a physical adaptor with a bit of logic but all the heavy lifting is done by the windows only driver

---

### Post by CharlesA on 2010-05-18
Fakeraid is also called software raid, since it uses the chipset on the mobo for most of the processing (along with the CPU and RAM).

Linux would see fakeraid the same as a regular HW raid card.

---

### Post by NMFTM on 2010-05-18
> **McRat said:**
> I think only two motherboards I own have on-board RAID.
Unless you spent several hundred dollars for really high end motherboards, what the mobo manufactures advertise as "RAID" is actually fake raid. It uses hard drive controllers instead of actual RAID controllers.

---

### Post by cariboo on 2010-05-18
I had data corruption problems with FakeRaid on one of my motherboards, I'd go with software raid only, if you don't have a stand-a-lone raid card.

There are quite a few threads in [Sever Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") comparing FakeRaid to software raid, if you want to do some research.

---

### Post by tgalati4 on 2010-05-18
Write speed is roughly double for RAID0.

A typical fast SATA drive (such as a WD Raptor) can write 77 MB/sec.  With striping of two drives you can get ~150 MB/sec.  The data bus can probably push 3000 MB (3 GB/sec) so RAID0 can measurably increase speed for video or music editing.  The reliability would be cut in half so you need a decent backup strategy.  RAID5 is somewhat slower because of the parity calculation and extra parity writing.

You have to measure the speeds on your own hardware to determine the improvement.  You can use the hdparm command:

sudo hdparm -tT /dev/sda1

---

### Post by CharlesA on 2010-05-18
I thought SATA II could only have a max throughput of 3Gb/sec.

Where were you getting 3GB/sec?

---

### Post by Shining Arcanine on 2010-05-18
> **McRat said:**
> I always thought raid was only for data redundancy.

But somebody posted that it's good for speed.

Anyone have experiences or thoughts on Raid 0?

RAID 0 was designed for throughput at the expense of everything else rather than speed. You can get higher sequential reads and writes with it, but latencies and small random operations are terrible with it. You are better off with a solid state disk.

---

### Post by McRat on 2010-05-19
> **Shining Arcanine said:**
> RAID 0 was designed for throughput at the expense of everything else rather than speed. You can get higher sequential reads and writes with it, but latencies and small random operations are terrible with it. You are better off with a solid state disk.


Thanks!

---

### Post by tgalati4 on 2010-05-20
True, SATAII is rated for burst speed of 3 GigaBits per second, but server motherboards can move RAM to the processor much faster: 3 GigaBytes per second.

Run memtest and see what your RAM and cache speeds are and compare them to your hdparm (hard disk speeds).

---

