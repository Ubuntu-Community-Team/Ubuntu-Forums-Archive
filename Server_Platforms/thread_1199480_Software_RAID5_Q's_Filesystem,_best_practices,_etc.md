---
title: "Software RAID5 Q's: Filesystem, best practices, etc."
date: 2009-06-29
forum: Server Platforms
---

### Post by Plecebo on 2009-06-29
I am getting ready (the hardware is in the mail) to build a NAS to house my files. Included in the hardware is 6x 1TB drives that I was planning to setup in a RAID5 array. I'm fairly new to raid and would appreciate any help/information anyone can offer. 

I will be using the NAS device to server up movies (.iso archives of dvd's mostly), music (flac and mp3 files), photos (a lot of raw files 15 MB + each) and some other random documents. 

My questions are three fold: 
[LIST=1]
[*]Is using the 6 drives in 1 RAID5 array a mistake?: Should I be looking to break it up into a few smaller arrays? I have an 8 bay drive enclosure that will house the drives ([http://www.newegg.com/Product/Product.aspx?Item=N82E16816111051](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111051)) and a SATA/eSATA expansion card that will connect the enclosure ([http://www.newegg.com/Product/Product.aspx?Item=N82E16816132018](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132018)) This should give me room to add 2 more drives to the enclosure and bump my storage a bit more if need be. Anyone see a red flag where I might be mis stepping significantly? 
[*]What File system to use for this NAS? My immediate thought was to use ext4, but I'm not finding ANY information about using ext4 on a raid array. That makes me a bit nervous, but it could be because its not been "stable" for a super long time. Is ext4 a bad idea? Given the use I ran down above would XFS be a better choice? I really like the idea of ZFS, but not in its current state (fuse/opensolarus/bsd only). 
[*]How long, roughly, am I looking at for building the array? I've heard this can take quite a long time (days or even worse, weeks). I have some time off coming up that I would like to set aside for the project, just wondering what kind of time I'm looking at spending waiting for the array to build. 
[/LIST]


Thank you very much in advance for any information you may be able to provide.

---

### Post by Plecebo on 2009-06-29
No feedback huh?

---

### Post by lmlypfan on 2009-06-29
Not sure if i can help, but at least this will bump the thread. 

I have an ubuntu 9.04 headless server running mdadm for RAID5 over 3 1TB drives. The drives are formatted in ext3. I use SAMBA and NFS to share my folders. 

I don't see any problem with using RAID5 with 6 drives. I would think that configuration would be preferred over splitting it into 2 separate arrays.  

My 3TB array assembled in a matter of hours from what I remember. 

Are you using Ubuntu for your NAS, or FreeNAS, or something else?

Are you using hardware or software RAID?

---

### Post by grantemsley on 2009-06-29
A couple things:

- That enclosure already includes a PCIE 1x card to go with it.  The other card you linked probably won't work - most inexpensive (<$150ish) don't support port multiplier (1 port, multiple drives).  Make sure they are compatible.

- I'd use XFS.  ext4 is too new to have much info on, as you discovered. XFS works very well for large files, and if the majority of your stuff is going to be DVD isos, I'd stay with XFS.

- Building the array will take DAYS.  However, the array will be usable while it is building, it just won't have any redundancy yet. You can monitor it's progress in /proc/mdstat.  The array will be a bit slower while it is building, but still fully usable.  By default, it rebuilds very slowly so it doesn't have much impact on performance.  There is a setting you can tweak to make it rebuild faster (at the cost of slowing down anything else using the array)...I forget what it is, but it shouldn't be hard to find.

- Make sure you have smartmon installed and occationally check the smart status of your drives - any that show reallocated sectors should be replaced immediately.

- Always remember that RAID is not a backup solution.  It only prevents you from losing things if a drive fails. It doesn't help against data corruption, filesystem damage, accidental deltion, etc.  I have basically the same setup as you are talking about for my home server.  The DVD isos, tv shows, etc don't need to be backed up as far as I'm concerned, but make sure you keep backups of photos and other irreplacable data.

---

### Post by sloggerkhan on 2009-06-29
With 6+ drives, maybe see if you can swing RAID 6? See: [http://n0tablog.wordpress.com/howtos/software-raid-6-on-debian-etch-micro-howto/](http://n0tablog.wordpress.com/howtos/software-raid-6-on-debian-etch-micro-howto/)
Likewise: [http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page) may be useful.

I think if the port multiplexer works properly you should be able to put all 6 or 8 drives into a RAID 6 configuration. 

Personally, I think you should either go for 1 RAID 6 or 2 four drive raid 5s. With 6 or 8 drives and you purchasing and using all the drives from the same date, with distributed use, I think it is likely that more than one will start to fail about the same time, hence why I think with that many drives you should allow for 2 failures. 

Also key, when you get your drives, run SMART tests on all of them immediately. It would be unusual, in my experience, for 6 drives to all pass out of the box. If any don't pass perfectly out of the box, return that particular drive for replacement. If a new drive has SMART errors, my experience is that it's unlikely to last even a month. 

Likewise, when constructing your array, you will get marked performance benefit from setting chunk sizes to be at least 256K (especially if you have lots of large files), the default is way too low.

My experience is that formatting your md device ext4 is fine, the reason it's not mentioned much is that it is the successor to ext3, which is what all the tutorials/instructions will use because ext4 only stabilised very recently. 
There's very little difference in setting up an ext4 partition from an ext3 one. I don't think there is anything wrong with xfs as a filesystem, but it is a filesystem that you should look up the proper parameters for formatting instead of using defaults, it will make a big difference. I'd look up for sure that whatever file system you choose can be grown easily should you add more disks.

---

### Post by Plecebo on 2009-06-30
> **grantemsley said:**
> A couple things:

- That enclosure already includes a PCIE 1x card to go with it.  The other card you linked probably won't work - most inexpensive (<$150ish) don't support port multiplier (1 port, multiple drives).  Make sure they are compatible.

- I'd use XFS.  ext4 is too new to have much info on, as you discovered. XFS works very well for large files, and if the majority of your stuff is going to be DVD isos, I'd stay with XFS.

Thanks for pointing out the incompatibility. I was aware that it came with a card, but it is only a 1x card, and if I was going to be running 8 drives off this thing streaming HD Video and Audio then the bandwidth might have become an issue. I got this card instead, PCI Express x4 and 4 port eSATA. [http://www.newegg.com/Product/Product.aspx?Item=N82E16816151058](http://www.newegg.com/Product/Product.aspx?Item=N82E16816151058) 

The benefits of xfs sound great, but I keep hearing about the issues with power loss and recovery. How pressing are those issues? Is it that the corruption only happens if there is a crash during a write procedure? If that is the case I could probably live with that. mostly because i'm not likely to be creating content on the server, it will be on the client. 

> **grantemsley said:**
> 
- Building the array will take DAYS.  However, the array will be usable while it is building, it just won't have any redundancy yet. You can monitor it's progress in /proc/mdstat.  The array will be a bit slower while it is building, but still fully usable.  By default, it rebuilds very slowly so it doesn't have much impact on performance.  There is a setting you can tweak to make it rebuild faster (at the cost of slowing down anything else using the array)...I forget what it is, but it shouldn't be hard to find.

- Make sure you have smartmon installed and occationally check the smart status of your drives - any that show reallocated sectors should be replaced immediately.


That is a huge relief. I was picturing me waiting around for 3 or 4 days waiting for the array to build, when in reality that would not be happening. I should just ensure that I keep the source data while it is rebuilding... check!. 

Thanks for the tip on smartmon, I'll definitely make that part of my implementation.

The backup thing goes without saying, luckily only a portion of it is irreplaceable (some music that I no longer have CD's for, and personal data), so I'll backup just those items. 

@sloggerkhan re: Raid 6

I have considered Raid 6, my budget is blowing up on this project and I was hesitant to go to 6 without knowing how much video space I'll need. Though thinking about it The cost of drives is low, perhaps I'll go 6 and just plan on getting another drive in a few weeks. 

Thanks for the tip about the chunk size, I was hoping to get some suggestions relating to that.

---

### Post by windependence on 2009-06-30
A)  I see no problem with one array if you are using hardware RAID.

B)  You don't have to go exotic (and in fact probably shouldn't) on file systems. If it was me I would stick to EXT3. You are going to get a significant performance boost because of the number of spindles you have so it's not necessary to hot rod the box

C)  There are tons of people now suggesting RAID 6 because of a bunch of blogs on the internet. IMHO it's not necessary especially if you have physical acces to the box. You will be able to see a drive failure no problem. In actual practice in the enterprise we still use RAID5 almost exclusively.

-Tim

---

### Post by mr.propre on 2009-06-30
Choosing an file system is separated from RAID. In fact you can chose more then one File system and partition your RAID the way you like.

Personal I would chose one of the HDD as a Hot spare in case the system fails and you aren't around, in that case you have almost the same security of RAID 6 but cheaper and faster. RAID 6 isn't widely supported and as far as I know it's almost never used.

---

### Post by Plecebo on 2009-06-30
> **windependence said:**
> A)  I see no problem with one array if you are using hardware RAID.

B)  You don't have to go exotic (and in fact probably shouldn't) on file systems. If it was me I would stick to EXT3. You are going to get a significant performance boost because of the number of spindles you have so it's not necessary to hot rod the box

C)  There are tons of people now suggesting RAID 6 because of a bunch of blogs on the internet. IMHO it's not necessary especially if you have physical acces to the box. You will be able to see a drive failure no problem. In actual practice in the enterprise we still use RAID5 almost exclusively.

-Tim
Thanks for the info. 
A) My setup will be software raid probably using either the latest Ubuntu server release, or the latest LTS release. I couldn't justify the cost of the hardware controller, especially one for 8 (for now) drives. 

B) EXT3 is my trusty sidekick in other words? I do like the idea of the speed of XFS especially with larger files (which is primarily going to be what I'm transferring), but I have no real world experience with xfs, and don't feel I could install a test bed and get any kind of idea how reliable it is in just a few days. From what I understand, the main issue with XFS is that it doesn't always recover gracefully from a non graceful system reboot. What would be great, and what I've not been able to find, is under what conditions does this happen? Is it only when the FS is writing data and looses power? Also how deep do the troubles go, is it limited to one or two files? At the moment I'm at a tossup between the two FS's. As I understand they are both supported in Kernel. 

C)Thanks for the real world use information. I like the idea of RAID 6, but not if it is going to cause more trouble down the road. I can understand your point about RAID 5 use in the enterprise, but I'm not an enterprise (yet!) and my datacenter is not manned 24x7. I'd hate to go away for a week and find my raid array crashed because I hadn't had another drive in time before a 2nd crashed. Given the fact that I'm using consumer grade hardware (drives) purchased from the same retailer around the same time (I know two strikes) it is something that I should probably be thinking about. 

@mr.propre I like the idea of a hot spare. Curious, does it have to rebuild the array when one disk fails and it starts to use the hot spare? In that case it could be rebuilding for quite a while, and I'd be vulnerable to drive failure during that time. 

Thanks to everyone for the great information. I'll be doing the build this weekend, so it is nice to get things hammered out ahead of time.

---

### Post by sloggerkhan on 2009-06-30
My reason for thinking RAID 6 to be useful is that, first of all, it should be supported by mdadm software raid, which IMO, is the only way to run RAIDs that doesn't have serious downsides for home users.

Likewise, as poster pointed out, when buying all drives in a batch, the odds on simultaneous failure are much higher.

So I think either having the live spare or going RAID 6 are very good ideas.

Likewise, in enterprise, your RAID would have backups. Home users generally can't afford to have backup RAID arrays. So for a home environment, extra redundancy is more important.

And yes, if you use a spare, the spare will automatically be added to the array on another drive failing/dropping. It will say that it is resyncing or some such. It shouldn't take as long as the initial build, but it will still take a while.

---

### Post by ian dobson on 2009-06-30
Hi,

I have a 3 x 2Tb array and it took about 14 hours to rebuild while recording several programs (MythTV)

I'm using ext3, ext4 is still too new for me.

Don't forget RAID isn't a replacement for good backups. I have a forth 2Tb drive that I use for backups of important data.

Regards
Ian Dobson

---

### Post by Plecebo on 2009-06-30
> **ian dobson said:**
> 
I have a 3 x 2Tb array and it took about 14 hours to rebuild while recording several programs (MythTV)

Which of the 2TB drives did you use? I am using the 1TB WD Green Power drives, which now that I am researching more might not have been the best choice. 

I think I'll try the ext3 option and see if I run into troubles with bandwidth. With 6 drives, and only one GB Ethernet port I am thinking it probably won't be an issue.

---

### Post by windependence on 2009-06-30
Don't forget that with softraid, you cannot boot from the raid device because it will not have been created until after the boot. You should have your boot info on either a separate drive (preferred) or a separate partition. 

-Tim

---

### Post by ian dobson on 2009-06-30
> **Plecebo said:**
> Which of the 2TB drives did you use? I am using the 1TB WD Green Power drives, which now that I am researching more might not have been the best choice. 

I think I'll try the ext3 option and see if I run into troubles with bandwidth. With 6 drives, and only one GB Ethernet port I am thinking it probably won't be an issue.

WD Green Power (WD20EADS).

Bandwidth shouldn't be a problem. I've recorded 4 HD programs at the same time onto the RAID5 array no problems.

I actually have 2 RAID partitions setup on the 3 RAID drives. The first partition is only about 20Gb RAID1 for boot and the rest is setup as a RAID5. I'm using mdadm/onboard SATA ports rather than an seperate controller card.

Regards
Ian Dobson

---

### Post by joec22 on 2009-07-25
Placebo, did that card work?  I mistakenly purchased the 1300 internal and it doesn't work with latest ubuntu.  I can't find any non-raid card with 4 ports that works.  

Joe

---

### Post by windependence on 2009-07-25
Try something based on the silicon image 3512 chipset. Sabrent is one I know of that makes a card, try the SBT-SRD4. Very cheap too!

It's a RAID card, but you simply set it up in non-RAID mode.

-Tim

---

### Post by joec22 on 2009-07-25
I'm looking for pci express, something that can run 4 drives and work with ubuntu.

---

### Post by fjgaude on 2009-07-25
> **joec22 said:**
> I'm looking for pci express, something that can run 4 drives and work with ubuntu.

Seems most folks have had look success with the 3ware products and linux/ubuntu:

[http://www.3ware.com/](http://www.3ware.com/)

Give the link a study and see what you think... lots of adapters to go over. I'm sure you can find a used one on e-bay. <smile>

---

### Post by joec22 on 2009-07-25
Thank you.  I'm glad to hear something works in pci-e, but I was hoping not to pay for the hardware raid.  It may be my only option though.

---

### Post by Plecebo on 2009-07-25
> **joec22 said:**
> Placebo, did that card work?  I mistakenly purchased the 1300 internal and it doesn't work with latest ubuntu.  I can't find any non-raid card with 4 ports that works.  

Joe

Hello Joe, 

No the Areca card never worked for me under Ubuntu. I did get the card to work under Red Hat after installing drivers, but then had trouble with my nic because the current version of RH (CentOS really) did not have drivers for the NB chipset on my MB. I tried the card in: 

[LIST]
[*]RHEL - Really CentOS, but I tried the newest version, with the issues listed above.
[*]Open SUSE - The newest version. The documentation claims this card supports SUSE, but I could not find drivers for it, and the distro never picked up the drives 
[*]Ubuntu - The documentation makes no mention of Ubuntu, so I wasn't surprised that it never worked. I tried installing the Debian drivers that come on the disk and could never get them working at all. They were from a few Kernels ago, but it appeared to install ok. (I don't even know if that sort of thing is possible). 
[/LIST]

I ended up returning the Areca ARC-1300-4E and got the SANS DIGITAL HA-DAT-4ESPCIE, and I'm very glad I did. 

It works beautifully without any drivers under Ubuntu server 9.04 x64 (only version I tested it with). as it is a 8x pci-express card it is significantly faster then the 1x card that came with my enclosure. 

It costs slightly more then the Areca, but you don't even have to install drivers. On newegg.com the description says "Windows only" but that applies only to the raid modes, not the port multiplier functionality. 

Hope that is helpful to your quest, and sorry for the late reply.

For those interested my system is up and running. I did end up going with 8x 1TB drives (6 of the green power drives and 2 of the RE3 raid drives). I had some trouble with the GP drives slipping into error recovery mode and being seen as failed drives to the mdadm process. I found this post [http://www.hardforum.com/showthread.php?p=1034376807]("http://www.hardforum.com/showthread.php?p=1034376807") that details how to enable a Time Limited Error Recovery (TLER) mode, which is enabled in the raid (RE3) drives. I purchased the RE3 drives before I found this post, else I would have just had 8 of the Green Power drives. 

Ironically all the Green Power drives passed SMART testing (A flippin miracle I know) however, one of the RE3 drives failed and so was sent back for RMA. 

I did end up going with a raid 6 array mostly because I purchased the drives very close together and am affraid that they might start failing quickly once they start going seeing as how they are all consumer drives. 

I also dropped in an Intel nic and upgraded my network to gigabit speeds which has made my network transfers much faster.

---

### Post by sloggerkhan on 2009-07-27
Congrats on your setup. I have to say I never really though about 100megabit ethernet being too slow until I transfered most of a 700 (750 base ten) gigabyte hard drive to RAID across my lan...

---

### Post by fjgaude on 2009-07-27
Plecebo, you are using **mdadm** for the raid6? External drives to your case? With two cards?

---

### Post by Plecebo on 2009-07-27
> **fjgaude said:**
> Plecebo, you are using **mdadm** for the raid6? External drives to your case? With two cards?

Correct, I use mdadm for the raid6 array. 

I have the 8 drives in an external 8 bay esata enclosure ([http://www.newegg.com/Product/Product.aspx?Item=N82E16816111051](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111051)) connected to my server via the 1 esata card with 4 esata ports that I mention above. 

So 1 8x pci-express card with 4x esata ports. Connected to my enclosure (this uses 2 x esata connections for the 8 drives). 

Hope that clears things up a bit. 

I'd be glad to post benchmarks if anyone has a how to on doing so.

---

### Post by fjgaude on 2009-07-28
Very good... here's a simple quick test for throughput:

```
time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
```

Run it when logged into the array in a terminal. 

Here's my normal test using **hdparm**:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

Let us know how it all goes. Thanks!

---

### Post by Plecebo on 2009-07-28
> **fjgaude said:**
> Very good... here's a simple quick test for throughput: 
...

Let us know how it all goes. Thanks!

Here are the results: 
```
sudo time dd bs=1M count=1000 if=/dev/zero of=/mnt/raidarr/1000M.bin
[sudo] password for plecebo: 
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 4.43635 s, 236 MB/s
0.01user 2.83system 0:04.92elapsed 57%CPU (0avgtext+0avgdata 0maxresident)k
80inputs+2048000outputs (0major+525minor)pagefaults 0swaps

```

and 

```
sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   7166 MB in  2.00 seconds = 3584.88 MB/sec
 Timing buffered disk reads:  832 MB in  3.01 seconds = 276.21 MB/sec

```

Are those numbers acceptable for my type of setup? Could I get a performance improvement with some tweaking? 

Thanks for the input.

---

### Post by fjgaude on 2009-07-31
That performance is okay, but with your array I'd think the thru-put should be twice what you are getting.

All your drives are less than two years old, eh?

You might better results with raid10, eight drives.

---

### Post by Plecebo on 2009-07-31
> **fjgaude said:**
> That performance is okay, but with your array I'd think the thru-put should be twice what you are getting.

All your drives are less than two years old, eh?

You might better results with raid10, eight drives.

They are all brand new drives. Most of them (6) are the WD 1TB Green Power drives. Which are not optimized for use in a RAID array. I enabled the TLER options on those drives, so they don't drop out of the array, but I would not be surprised if there were other hurdles keeping me from getting the best results. 

The other two drives are WD 1TB RE3 drives, which are intended to be used in a RAID array. 

There are a lot of places I could be experiencing bottlenecks with my setup though, and some further testing would need to be done in order to see where the bottlenecks lie. 

For now the dual redundancy of the Raid6 leaves me feeling mostly safe. Lucky for me most of the data is not critical, and doesn't need to be backed up. 

That being said, I wouldn't mind experimenting a bit with tuning mdadm or some file system parameters to see about bringing my numbers up a bit. 

fjgaude: Thanks for the information :)

---

### Post by sloggerkhan on 2009-07-31
I get ```
 /dev/md0:
 Timing cached reads:   2644 MB in  2.00 seconds = 1322.27 MB/sec
 Timing buffered disk reads:  750 MB in  3.00 seconds = 249.76 MB/sec

```
On my 4 disk RAID 5.
I suspect my read speed may be limited by my motherboard's bus/datapaths, but not 100% sure.

---

### Post by fjgaude on 2009-07-31
Well, sloggerkhan, your read speed should be about three times one drive in a four-drive raid5 array. Your low cache reads are from your relatively slow memory and CPU. They don't seem to be much of a bottleneck though. Likely your read speed would top-out at about 300MB/sec with late model drives.

My drives are only 70BM/sec each so I'm good. Yours likely 110!

---

