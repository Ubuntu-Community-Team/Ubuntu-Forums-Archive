---
title: "[SOLVED] Reconstructing RAID1 takes many days"
date: 2008-12-29
forum: Server Platforms
---

### Post by bronkeydain on 2008-12-29
I have this weird problem. I am reconstructing 1 (of 2) RAID 1 drive. However it reconstructs at around 100K/sec and will take 30.000 minutes which is about 3 weeks. I know this process is slow but should take hours rather than weeks.

The drives are both IDE 160GB. I have tried them on the same IDE channel and a separate channel. I have set /proc/sys/dev/raid/speed_limit_min to read 5000, but it was not even getting the default 1000K/sec anyway. 

There are no errors in /var/log/messages
I just wonder if anyone has idea's where to look next?

---

### Post by bronkeydain on 2008-12-29
I forgot to mention this is software RAID, I set it up using mdadm. 

When I set it up using the same drives 2 it worked like a charm. I have deliberately broken the RAID for testing purposes, but with the intention to start using RAID for my data once I have tried my recovery scenario.

---

### Post by fjgaude on 2008-12-29
I can't say if I can be of any assistance, but maybe this link will help:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Many seem to have troubles with mdadm raid1.

---

### Post by Cracauer on 2008-12-29
That's definitely not normal. Linux md spanks the monkey out of hardware RAID controllers in the rebuild speed.

Let me guess, you have them both at the same IDE channel? Don't do that.

Also make sure DMA is active.

Post `dmesg`, please.

---

### Post by bronkeydain on 2008-12-31
Thanks for your replies.

I have 3 HD's, the system disk, and the mirrored data RAID disks.
I have tried putting the disks on a separate channel (but one sharing the IDE channel with the system disk). I have put them together and I have installed a RAID hardware card which I used in IDE mode so I had the system on the 1st IDE, 1 RAID disk on 2nd IDE and the other RAID disk on the IDE of the RAID card. 

No matter what I do I get the same result. I have even tried to use a Live CD (Clone ZIlla, it uses DD command) to clone the 2 drives to see what speed I would get (again on the same or separate IDE channels). Whatever I do I get a max throughput of 120K/sec

I think this might be a hardware issue and not a RAID problem. Investigating further, which might take a while with the new year celebration coming up.

---

### Post by Cracauer on 2008-12-31
OK, do this:

cstream -T10 -i /dev/hda -n16g -o-
then
cstream -T10 -i /dev/hdc -n16g -o-

and note throughput. Insert correct devices.

Then do them both at the same time. 

If you had good throughput alone and it collapses when doing both at the same time you have a channel independence problem.

---

### Post by fjgaude on 2009-01-01
Testing is a good idea.

Try one drive at a time with **hdparm**:

```
sudo hdparm -tT /dev/hda
```

Also for /dev/hdc. This will show the overall speed of drive, memory, and CPU.

---

### Post by bronkeydain on 2009-01-01
Thanks again for helping guys.

```
hdparm -tT /dev/sdb

/dev/sdb:

Timing cached reads:     2 MB in 17.70 seconds = 115.70 kB/sec
Timing buffered disk reads:    2 MB in 15.73 seconds = 130.17 kB/sec
```


```
hdparm -tT /dev/sdc

/dev/sdc:
Timing cached reads:   754 MB in  2.00 seconds = 376.31 MB/sec
Timing buffered disk reads:  164 MB in  3.03 seconds =  54.09 MB/sec
```


It seems one of the drives is the problem. I have also tried Cracauer's cstream commands, they told the same story. When I ran the test on both disks at the same time there was no difference. I will run a HD test using UBCD (Ultimate Boot CD).

---

### Post by fjgaude on 2009-01-01
One of the drives is very fast, the other normal. The cached memory/CPU looks very slow, not normal.

Here's mine:

4x raid5 Samsungs, CPU at 3.6GHz:
/dev/md32:
 Timing cached reads:   18182 MB in  2.00 seconds = 9103.61 MB/sec
 Timing buffered disk reads:  540 MB in  3.00 seconds = 179.75 MB/sec

I know I have a very fast box but the cached runs should be over 1000 MB/sec for modern systems.

---

### Post by bronkeydain on 2009-01-01
Weird as both drives are identical (Seagate 160GB ST3160021A).

Are you saying this might be a CPU or memory problem?

---

### Post by Cracauer on 2009-01-01
I think I asked that before but don't remember:

DMA on?

---

### Post by fjgaude on 2009-01-01
I guess I'm saying I've never seen a cached memory/CPU come out as low as yours. Yes, Likely some issue here. As asked, is DMA on?

The more I study your hdparm results the more I'm convinced there is surely something wrong. Notice the difference between the two drive results. Strange!

---

### Post by cariboo on 2009-01-01
This may have something to do with your problem:

> To allow for two drives on the same cable, IDE uses a special configuration called master and slave. This configuration allows one drive's controller to tell the other drive when it can transfer data to or from the computer. What happens is the slave drive makes a request to the master drive, which checks to see if it is currently communicating with the computer. If the master drive is idle, it tells the slave drive to go ahead. If the master drive is communicating with the computer, it tells the slave drive to wait and then informs it when it can go ahead. 

If you could make both drives a master and set your boot drive as a slave and still boot , you should see faster speeds.

Jim

---

### Post by bronkeydain on 2009-01-02
Thanks again everyone for your input.

DMA is on.
I have had both disks as master on separate channels. 

Even the Seatools HD test (on Ultimate Boot CD) was still on 0% after 45 minutes. It was not frozen but incredibly slow.

I have to admit that this machine was build from left over parts so possibly some part is faulty. But when I assembled it I have run hardware tests on the CPU and memory.

But if it is a CPU or RAM issue, I find it strange it only happens on this specific disk. Unfortunately my time to check this is sparse (kids, don't have them! lol). But I would like to try to reformat the disk and also try it in another machine. I will report back.

---

### Post by Cracauer on 2009-01-02
Did you exchange cables and ports?

---

### Post by bronkeydain on 2009-01-02
I have used 4 different IDE cables and also on IDE1 and IDE2, and on the PCI RAID card.

Something else I have noticed... the problem is intermittent! I am copying some files of before reformatting the drive and the first 30 or 40 GB have copied in no time, and now it is very slow doing the last 30GB (these last files are all CD and DVD ISO images, maybe it is struggling with large files?). So far for 2 days everything ha been slow so I don't understand why those other files copied so fast.

Also, my CPU is on 99% solid whilst copying, so once more this shows some relation with the CPU.
Why would it only affect this HD I wonder, could it be that the software raid somehow slows it down? (This disk witht he problem is the only drisk in the array now).

Anyway as I said I will reformat the drive, try it, and also connect to it another machine and report back later.

---

### Post by fjgaude on 2009-01-02
During copying your CPU shouldn't be used at 99%. There is something this drive is doing to hog the CPU cycles. A new drive is indicated! <smile>

---

