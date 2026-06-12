---
title: "RAID and Server Hardware"
date: 2012-09-12
forum: Server Platforms
---

### Post by LeChacal on 2012-09-12
Hello,

I am looking to build a home file server with about 6 1TB drives in RAID 6. I have work exsperence with hardware RAID controls and don't really want to go through the exspense and headaches of dealing with one. So I am going to use Linux software RAID.

My question is what kind of overhead should I expect to need to implament such a system? Another way of asking, would an old P4 do the job or do I need a new i7 to handle this job?  I have read veraus tests but they don't seem to offer any really good advice or baseline for me to go off of. If I have missed anyone I am open to reading them.

The server would be used for storing a large picture files asseced from photoshop, storing backups of other systmes, intranet web server, and occasional torrent grabber/host for when I find a new OS that I want to play with.

Also I am still looking at hardware, motherboards, CPUs, etc. So if anyone has suggestions that would be greatly apprciated. My goal is something small, lower power I can put in the home rack.

Or if you just have any other suggestions that you think might be better, I have already read into ZFS and decided against that on BSD/Solaris.

Thank you

---

### Post by darkod on 2012-09-12
I have something similar based on AMD Athlon Neo NL36 (I think that's the official CPU name). I am completely happy with it but I use less transfer than what you described.

Depending on your view, I guess you can go with one of the latest Atom or AMD equivalent CPUs. Usually they would come together with the board, so look out for the board spec if there is something special you need.

---

### Post by LeChacal on 2012-09-12
darkod, thanks for the response. The Neo looks like the predecessor to AMD Fusion (Atom competitor), If you don't mind, when you do a large file write what kind of system usages are you getting? I ask because every review/benchmark I have read shows every chip running at 100% usages for large writes which I feel is strange. I have actually been looking at the AMD Fusion line as an option, that is why I ask.

---

### Post by darkod on 2012-09-12
If you tell me what's the best way to look, I might do a short test later. Do I just fire off the copy and open top?

Since I connect with ssh to mu headless server, how can I have in the same terminal top and do the copy command?

---

### Post by LeChacal on 2012-09-12
Depending on how you have ssh setup you can open to connections for the same user, so you would have two terminal windows open allowing for top (or 'watch cat /proc/loadavg') on one and copy on the other. If you aren't allowed two connections then I would use screen, it allows you to have multiply "screens" it is hard for me to explain well, it is like the multiply tty you have when sitting at a terminal and you press ctrl+(alt)+F2-F6.
I would greatly appreciate the information.

---

### Post by darkod on 2012-09-12
Wow, I learned something new. Two separate putty sessions actually worked (I'm on windows right now).

I used mv to move a 370MB folder from my ubuntu server to a network disk WD My Book World over 100Mb network. I still haven't upgraded to Gb.

The info in top regarding the mv process was steady during the move with 5% CPU and 0.1% MEM.

Does that help?

---

### Post by lukeiamyourfather on 2012-09-12
I would not purchase six 1 TB drives to use in RAID 6 configuration. Two 4 TB drives in RAID 1 configuration would be much easier to setup and have less overhead compared to RAID 6 with software. Less power, space, and time to setup as well. Also RAID is not backup, so if you're looking at RAID to prevent data loss look elsewhere. RAID is just to keep things running in the event of a hard disk failure. A better option might be to have one 4 TB disk in one machine (the server) and another 4 TB disk in another machine (as backup) that synchronize once a week or whatever.

---

### Post by CharlesA on 2012-09-12
In a mirrored setup, you can lose one drive and be fine, but if you have one server with a single 4TB drive and another mirrored once a week, you could potentially lose up to a week of data.

Personally, I used my server for file storage and VMs, the extra throughput I get from RAID5 vs single disk is worth it for me.

---

### Post by LeChacal on 2012-09-12
darkod, thank you for the more real world information, it is useful. The tests I was reading were using a benchmarking program so I feel the program was more for finding the limits not showing real world.

lukeiamyourfather, I am very confused by your statements, the point of having RAID 6 was so I could have 2 drives fail and still have the data while new drives are being repopulated. Plus the girlfriend is a employed photographer and stores large amounts of photos that change often, so a single large drive failure with week old backups isn't acceptable, she has already had that happen and it wasn't fun. For other vitally important things I have other off sit backups in place, I understand what the uses of RAID is and proper backup procedures.

CharlesA, when you say that you use it for VMs are you running a VM server or just storing the VM drive files on the server and running them on another machine? Also are you seeing the RAID 5 read performance benefits over ethernet or is the array local to the machine? I wasn't expecting to see any read benefits because of bottlenecks else where.

---

### Post by rubylaser on 2012-09-12
> **LeChacal said:**
> darkod, thank you for the more real world information, it is useful. The tests I was reading were using a benchmarking program so I feel the program was more for finding the limits not showing real world.

lukeiamyourfather, I am very confused by your statements, the point of having RAID 6 was so I could have 2 drives fail and still have the data while new drives are being repopulated. Plus the girlfriend is a employed photographer and stores large amounts of photos that change often, so a single large drive failure with week old backups isn't acceptable, she has already had that happen and it wasn't fun. For other vitally important things I have other off sit backups in place, I understand what the uses of RAID is and proper backup procedures.

CharlesA, when you say that you use it for VMs are you running a VM server or just storing the VM drive files on the server and running them on another machine? Also are you seeing the RAID 5 read performance benefits over ethernet or is the array local to the machine? I wasn't expecting to see any read benefits because of bottlenecks else where.

I used to run a (10) disk mdadm RAID6 array on a AMD 4600X2 (about as powerful as the microserver processor) and had no problem saturating gigabit while maintaining very reasonable loads (half of one core at the most).  Personally, I wouldn't use 1TB drives anymore (unless you have them laying around and they're free).  I'd at least do 2TB drives, because they seem to be at the best price point.

Also, with a professional photographer using the array, you'll be very surprised how quickly 4TB of usable space goes just with RAW photos, and Photoshop edits.  Just my family photo library is 1.4TB alone.  If you want to store home movies, videos, tv shows, music, etc, that 4TB will go FAST :)

If you want any help getting it configured, I think [my tutorials]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") are pretty easy to follow.  

In CharlesA's example, I believe he uses Virtualbox on his fileserver, so the vms are stored locally.  Accessing them over even gigabit would be a bottleneck compared to even 1 modern SATA hard drive.  If you have any other questions, please feel free to post, myself or others will be happy to try to answer them.

---

### Post by CharlesA on 2012-09-12
> **rubylaser said:**
> 
In CharlesA's example, I believe he uses Virtualbox on his fileserver, so the vms are stored locally.  Accessing them over even gigabit would be a bottleneck compared to even 1 modern SATA hard drive.  If you have any other questions, please feel free to post, myself or others will be happy to try to answer them.

Yeah, I access them locally, and the performance of running them off the RAID array is way better than off a single disk. IO wait is way down.

---

### Post by lukeiamyourfather on 2012-09-13
> **CharlesA said:**
> In a mirrored setup, you can lose one drive and be fine, but if you have one server with a single 4TB drive and another mirrored once a week, you could potentially lose up to a week of data.


Hard disk failure is one of many ways data can be lost. For example accidental deletion of a directory could result in loss of ***everything*** which is a lot more than a week of work. I say again, RAID is not backup.

> **LeChacal said:**
> 
lukeiamyourfather, I am very confused by your statements, the point of having RAID 6 was so I could have 2 drives fail and still have the data while new drives are being repopulated. Plus the girlfriend is a employed photographer and stores large amounts of photos that change often, so a single large drive failure with week old backups isn't acceptable, she has already had that happen and it wasn't fun. For other vitally important things I have other off sit backups in place, I understand what the uses of RAID is and proper backup procedures.


I'd still use two large disks in RAID 1 instead of many small disks in RAID 6 (for the reasons already mentioned). Glad to hear you have a backup routine in place because that's something people often overlook and think that RAID is good enough backup.

---

### Post by CharlesA on 2012-09-13
> **lukeiamyourfather said:**
> Hard disk failure is one of many ways data can be lost. For example accidental deletion of a directory could result in loss of ***everything*** which is a lot more than a week of work. I say again, RAID is not backup.

Never said it was a replacement for backups. I have my array backed up to an external drive daily. ;)

Drive failure is always a risk and it is a good idea to ensure you have a good backup and to test that backup before you actually need it.

---

### Post by rubylaser on 2012-09-13
I would still use RAID6 + backup for home storage.  The cost would be almost exactly the same as a (2) 4TB disk RAID1, it would have more storage space, could survive two disk failures. Also, when the disks are spun down, as they would be most of the time, the power consumption difference is negligible (a few watts). Here's an example.

**RAID1 w/** [4TB disks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145592"):  ~$300 x 2 = $600. 4TB usable space, can survive 1 disk failure, can't be easily grown without pooling another array via LVM, mhddfs, etc (another layer to troubleshoot if an issue arrises).
**RAID6 w/** [3TB disks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148844"):  ~$150 x 4 = $600. 6TB usable space, can survive 2 disk failures, and can easily be grown with mdadm in the future.

Obviously, in either case, you NEED a backup system in place for your irreplaceable items.

---

### Post by lukeiamyourfather on 2012-09-13
> **rubylaser said:**
> I would still use RAID6 + backup for home storage.  The cost would be almost exactly the same as a (2) 4TB disk RAID1, it would have more storage space, could survive two disk failures. Also, when the disks are spun down, as they would be most of the time, the power consumption difference is negligible (a few watts). Here's an example.

**RAID1 w/** [4TB disks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145592"):  ~$300 x 2 = $600. 4TB usable space, can survive 1 disk failure, can't be easily grown without pooling another array via LVM, mhddfs, etc (another layer to troubleshoot if an issue arrises).
**RAID6 w/** [3TB disks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148844"):  ~$150 x 4 = $600. 6TB usable space, can survive 2 disk failures, and can easily be grown with mdadm in the future.

Obviously, in either case, you NEED a backup system in place for your irreplaceable items.

Good point, you said it better than me in your previous post about not using 1 TB drives.

---

### Post by CharlesA on 2012-09-13
> **rubylaser said:**
> I would still use RAID6 + backup for home storage.  The cost would be almost exactly the same as a (2) 4TB disk RAID1, it would have more storage space, could survive two disk failures. Also, when the disks are spun down, as they would be most of the time, the power consumption difference is negligible (a few watts). Here's an example.

**RAID1 w/** [4TB disks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145592"):  ~$300 x 2 = $600. 4TB usable space, can survive 1 disk failure, can't be easily grown without pooling another array via LVM, mhddfs, etc (another layer to troubleshoot if an issue arrises).
**RAID6 w/** [3TB disks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148844"):  ~$150 x 4 = $600. 6TB usable space, can survive 2 disk failures, and can easily be grown with mdadm in the future.

Obviously, in either case, you NEED a backup system in place for your irreplaceable items.
Good example. I would definitely not use 1TB drives, when you have 2 or 3TB drives out there.

I'm using 2TB drives on my array and haven't had any issues (yet), but I do have backups and I have spare disks in case one goes out on me.

---

### Post by SeijiSensei on 2012-09-14
Buy a good UPS.  There is nothing worse for a server than an unexpected power outage while you are writing some large file.  I use APCs and the [apcupsd]("https://help.ubuntu.com/community/apcupsd") daemon to manage the UPS. I have the predecessor model to [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101492") across the room from me here.

---

### Post by CharlesA on 2012-09-14
> **SeijiSensei said:**
> Buy a good UPS.  There is nothing worse for a server than an unexpected power outage while you are writing some large file.  I use APCs and the [apcupsd]("https://help.ubuntu.com/community/apcupsd") daemon to manage the UPS. I have the predecessor model to [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101492") across the room from me here.
Huge +1. Nothing worse than losing power and then losing data.

---

### Post by kgatan on 2012-09-14
> **CharlesA said:**
> Yeah, I access them locally, and the performance of running them off the RAID array is way better than off a single disk. IO wait is way down.

Raid 5 does not improve IO performance, only data throughput. It gives you the same IO as a single disk since each access has to be done to all disks. 
Only way to mprove IO access time is to use Raid 1 or 10.

---

### Post by CharlesA on 2012-09-14
> **kgatan said:**
> Raid 5 does not improve IO performance, only data throughput. It gives you the same IO as a single disk since each access has to be done to all disks. 
Only way to mprove IO access time is to use Raid 1 or 10.
RAID 5 is still stripped, so you do have a little increase in performance compared to a single disk.

In any case, the VM are running faster now that their virtual drives are on the array as opposed to the single drive.

---

