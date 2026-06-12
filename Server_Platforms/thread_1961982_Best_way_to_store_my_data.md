---
title: "Best way to store my data"
date: 2012-04-20
forum: Server Platforms
---

### Post by 337Manni on 2012-04-20
Hi all.

I am after some advice regarding the best way to store my data.
Some info…

I have a HTPC with the following HDDs
HDD 1 - 150GB Sata 2 - Windows 7 (80GB) & Windows XP (60GB)
HDD 2 - 80GB IDE - Ubuntu 11.10
HDD 3 - 2TB Sata 3 - Films, TV Shows…
HDD 4 - 2TB Sata 2 - Documents, Music, Pictures, Backup Programs…

Also a Netbook with 160GB - Ubuntu 11.10

I would like to backup my data and would like to know your views on how’s best to do this.
I have considered building a homemade NAS, moving my 2x2TB HDDs and with additional HDDs implementing a RAID 5 setup for my media (Films, Music & Pictures). My Documents would be sync’d with the Cloud and both my HTPC (Win7) and Netbook (Ubuntu 11.10).

Can anyone advise on a better solution than this?

What is your current setup / goal regarding your storage setup?

---

### Post by Dngrsone on 2012-04-20
Sounds like a good paln.  I'd also recommend some off-site storage of at least the really important stuff-- if a plane falls on your home, then you've lost your computer *and* your backups, neh?

---

### Post by collisionystm on 2012-04-20
> **Dngrsone said:**
> Sounds like a good paln.  I'd also recommend some off-site storage of at least the really important stuff-- if a plane falls on your home, then you've lost your computer *and* your backups, neh?

That would never happen in a million years! Oh... wait.

[http://www.huffingtonpost.com/2012/04/06/virginia-beach-jet-crash-video_n_1408673.html](http://www.huffingtonpost.com/2012/04/06/virginia-beach-jet-crash-video_n_1408673.html)

---

### Post by 337Manni on 2012-04-20
Ha, if that did happen I think my data would be the last thing on my mind.... but at least it would be safe!

With my Documents sync'd with two PC's and the cloud the important stuff is pretty safe.
If I lost all the media files it would be a pain to gather and reorganise back onto my PC's, but I have most of the originals (Original DVD's, Photos on social networks...) so it would just be a matter of time.

One issue I can see is me filling up the limited amount of data I can store on the cloud. I think Ubuntu One is 5GB free at present. I was above this before a recent clear out of old files, at about 3.5GB for now.

I'm also a little unsure about the best storage for my media. I've read a lot about RAID a few years ago. Most I've forgot about, ha. Reading recently I had come to this conclusion:

RAID 5, Slow? If I lose a HDD then the rebuild could cause my RAID to fail.
RAID 6, Additional HDD for redundancy
RAID 10, Quicker performance, quicker rebuild of RAID as just copies a HDD, Less storage from same amount of HDD's (Half?)
I have also just found out about ZFS, RAIDz and RAIDz2 and like the sound of this. Need more reading though.

Just a little confused as to the best solution for my needs?


I would prefer software RAID over hardware:
1. If hardware card fails I would have to get same, or risk losing data?
2. Cheaper,

Which software / OS would you recommend?

Originally thought I'd use Ubuntu, but now leaning towards FreeNAS.

---

### Post by rubylaser on 2012-04-20
> **collisionystm said:**
> That would never happen in a million years! Oh... wait.

[http://www.huffingtonpost.com/2012/04/06/virginia-beach-jet-crash-video_n_1408673.html](http://www.huffingtonpost.com/2012/04/06/virginia-beach-jet-crash-video_n_1408673.html)

+1 for the great comment.  That made me laugh.

---

### Post by Dngrsone on 2012-04-20
I'd say FreeNAS as it's leaner, but I haven't had success with it, myself.

Of course, I have issues with the hardware I was trying to use it on... [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by 337Manni on 2012-04-20
Have you used ZFS? Do you have any opionions on it?

Do you know of any good reads on the subject? Only just started looking

---

### Post by rubylaser on 2012-04-20
> **337Manni said:**
> Ha, if that did happen I think my data would be the last thing on my mind.... but at least it would be safe!

With my Documents sync'd with two PC's and the cloud the important stuff is pretty safe.
If I lost all the media files it would be a pain to gather and reorganise back onto my PC's, but I have most of the originals (Original DVD's, Photos on social networks...) so it would just be a matter of time.

One issue I can see is me filling up the limited amount of data I can store on the cloud. I think Ubuntu One is 5GB free at present. I was above this before a recent clear out of old files, at about 3.5GB for now.

I'm also a little unsure about the best storage for my media. I've read a lot about RAID a few years ago. Most I've forgot about, ha. Reading recently I had come to this conclusion:

RAID 5, Slow? If I lose a HDD then the rebuild could cause my RAID to fail.
RAID 6, Additional HDD for redundancy
RAID 10, Quicker performance, quicker rebuild of RAID as just copies a HDD, Less storage from same amount of HDD's (Half?)
I have also just found out about ZFS, RAIDz and RAIDz2 and like the sound of this. Need more reading though.

Just a little confused as to the best solution for my needs?


I would prefer software RAID over hardware:
1. If hardware card fails I would have to get same, or risk losing data?
2. Cheaper,

Which software / OS would you recommend?

Originally thought I'd use Ubuntu, but now leaning towards FreeNAS.
How much data are you trying to store (including plans for future growth)? And, how important is each part of it to you?

FreeNAS is easy to setup, but if fast network speed is your goal, it's implementation of ZFS is not as fast as ZFS on Solaris 11/Openindiana.  I prefer to use Openindiana  v28 pool (so it's portable to other OS's in the future if I choose to export it) + the napp-it web gui, it makes managing ZFS arrays pretty easy.

Ubuntu + mdadm would work great as well.  But, if 30-40 MB/s across a gigabit connection is fine for you, then FreeNAS is pretty hard to screw up :)

---

### Post by rubylaser on 2012-04-20
> **337Manni said:**
> Have you used ZFS? Do you have any opionions on it?

Do you know of any good reads on the subject? Only just started looking

I have used ZFS both at home and work.  It works great, but it is VERY RAM hungry even without deduplication enabled.  I'd plan on a minimum of 8GB if you want good transfer speeds (I have 16GB in my home server, luckily RAM is super cheap). 

Here's a couple things to get you started.
[ZFS the last word in file systems]("http://hub.opensolaris.org/bin/download/Community+Group+zfs/docs/zfslast.pdf")
[http://constantin.glez.de/search/node/zfs]("http://constantin.glez.de/search/node/zfs")
[http://napp-it.org/]("http://napp-it.org/")

---

### Post by 337Manni on 2012-04-20
At the moment I have:

1.8TB of Video's,
52GB of Music,
12GB of Pictures,
3.5GB of Documents (Maybe more when I correctly organise them)
5GB of USB Pen Drive Backups
5.5GB of Backups from important folders from my PC to my family's which I maintain.

For ease of maintanance I also would like to backup my OS HDD, and possibly my familys (Hav'nt yet found the best solution for this, bet thats another topic).


As the main PC is a Media centre (HTPC) I record TV to it so the video's would grow quickly.

I am thinking of using 4 x 2TB HDD's at first. Then I would grow this as needed, possible in sets of 4 x 2TB?

Speed wise, I'm not after the fastest solution out there. My wish is to stream HD contents from the NAS to one of the PC's.
Currently only one PC is streamed to at a time, but this could change to two/three as my family grows.

I am in the process of installing a gigabit network. I have a Switcher and have ran in all the cables. They just require connecting to a backbox as and when the rooms are decorated.


I will have a good read of those links, thanks.

---

### Post by anonymouschief on 2012-04-20
> **337Manni said:**
> At the moment I have:
1.8TB of Video's,
52GB of Music,
12GB of Pictures,
3.5GB of Documents (Maybe more when I correctly organise them)
5GB of USB Pen Drive Backups
5.5GB of Backups from important folders from my PC to my family's which I maintain.


For personal stuff, that is, my computer at home. I do not want to waste so much of my system's resources with complex, and lengthy backup schedules as they do at work. I see that all your stuff, except for the videos, would fit in an external 1TB hard disk. I would advise that you backup what you can you cannot replace or data you cannot deal with if you lost. I backup all my documents on a drop box account. I also have a free 50GB Box account

If you have the resources for a complex backup scheme, then i recommend that you add a second NIC on every computer that acts a a media server, get a good gigabit switch and connect those new NICs to the switch and then build a NAS that is quick, and connect the NAS to that switch. Separate your backup data from your internet/wifi data to reduce the ACK noise. I am only suggesting.

---

### Post by collisionystm on 2012-04-20
I would just buy this. Its 3tb

[http://www.amazon.com/Seagate-FreeAgent-GoFlex-External-STAC3000102/dp/B005IA844G/ref=sr_1_2?s=electronics&ie=UTF8&qid=1334942371&sr=1-2](http://www.amazon.com/Seagate-FreeAgent-GoFlex-External-STAC3000102/dp/B005IA844G/ref=sr_1_2?s=electronics&ie=UTF8&qid=1334942371&sr=1-2)

---

### Post by kgatan on 2012-04-20
A few more alternatives if you want ZFS,
 
Nexenta Stor CE
A NAS based on Solaris which is free up to 18TB.
Its supposed to be almost as fast as Open Solaris.
All configs are made through web gui.
 
 
ZFSGuru
A FreeBSD nas with web gui. Havnt tried it my self.
 
 
FreeBSD 9
v.28 ZFS

---

### Post by CharlesA on 2012-04-20
> **collisionystm said:**
> I would just buy this. Its 3tb

[http://www.amazon.com/Seagate-FreeAgent-GoFlex-External-STAC3000102/dp/B005IA844G/ref=sr_1_2?s=electronics&ie=UTF8&qid=1334942371&sr=1-2](http://www.amazon.com/Seagate-FreeAgent-GoFlex-External-STAC3000102/dp/B005IA844G/ref=sr_1_2?s=electronics&ie=UTF8&qid=1334942371&sr=1-2)
I've got a couple of those for backups and they have worked wonderfully.

---

### Post by collisionystm on 2012-04-20
> **CharlesA said:**
> I've got a couple of those for backups and they have worked wonderfully.


At work I have a buffalo 4TB station with Raid 10. Its attached to a nix box that just rsnapshots all of my servers everynight and dumps them onto it. I keep 2 weeks of backups on it.

I then have a 2nd offsite backup. Its a nix box with a 2tb usb drive attached that just holds the most recent day of the 2 week backup.

So far its worked great.

---

### Post by CharlesA on 2012-04-20
> **collisionystm said:**
> At work I have a buffalo 4TB station with Raid 10. Its attached to a nix box that just rsnapshots all of my servers everynight and dumps them onto it. I keep 2 weeks of backups on it.

I then have a 2nd offsite backup. Its a nix box with a 2tb usb drive attached that just holds the most recent day of the 2 week backup.

So far its worked great.
Nice set up.

I have everything at home sync to my server and then just back up the server's RAID 5 array to an external drive daily. I probably get around 9 months worth of daily backups before I need to start clearing them out.

Of course they are incremental backups using hardlinks, so each one doesn't take up much space if nothing has changed.

---

### Post by dharmavir on 2012-04-22
I think other people on the post tried explaining it well but here is another post which might help you on the same topic with much detail:

[http://blogs.digitss.com/apache/mod_proxy-mod_vhost_alias-to-host-multiple-domains-on-web-server-and-running-apache-iis-together/](http://blogs.digitss.com/apache/mod_proxy-mod_vhost_alias-to-host-multiple-domains-on-web-server-and-running-apache-iis-together/)

---

### Post by rubylaser on 2012-04-22
> **dharmavir said:**
> I think other people on the post tried explaining it well but here is another post which might help you on the same topic with much detail:

[http://blogs.digitss.com/apache/mod_proxy-mod_vhost_alias-to-host-multiple-domains-on-web-server-and-running-apache-iis-together/](http://blogs.digitss.com/apache/mod_proxy-mod_vhost_alias-to-host-multiple-domains-on-web-server-and-running-apache-iis-together/)

Maybe you linked to the wrong page?  This article is about Apache vhosts.  The OP was talking about a way to backup his data.

---

### Post by 337Manni on 2012-04-22
Thanks all for your reply&#8217;s!! I didn't expect so many so soon. Defiantly the best forum on the web in my eyes!

@rubylaser
Glad you posted that, I was confused by the link ha!

@anonymouschief
Where did you get a free 50GB account? I would be very interested in this for my Documents, USB Drives & Backups.

I  want to build a NAS for a few reasons.
1. I love tinkering with PC's
2. The satisfaction of using my own home made one
3. I can make it expandable, and upgrade components in future if needed, or my goals change.

A few months ago I won a cheap 3U 12bay Enclosure on an online auction site. It came with a Intel S845WD1-E Mother Board, a 3Ware 8506 SATA RAID Controller. I only really bid on this for the enclosure, and didn't know about the MB, CPU, RAM, Controller..... as these weren&#8217;t listed and so was a pleasant surprise. I would gladly upgrade the internal hardware if needed.

After reading I'm leaning towards using ZFS. I believe that:

RAIDz - similar to RAID 5
RAIDz2 - similar to RAID 6
Striped Mirrored Vdev&#8217;s - similar to RAID 10


Which one would you recommend for my situation?

If I started out with 4/6 HDD's, could I add another HDD later and increase the RAID, or would I have to add another 4/6 HDD's?

---

### Post by rubylaser on 2012-04-22
> **337Manni said:**
> Thanks all for your reply’s!! I didn't expect so many so soon. Defiantly the best forum on the web in my eyes!

@rubylaser
Glad you posted that, I was confused by the link ha!

@anonymouschief
Where did you get a free 50GB account? I would be very interested in this for my Documents, USB Drives & Backups.

I  want to build a NAS for a few reasons.
1. I love tinkering with PC's
2. The satisfaction of using my own home made one
3. I can make it expandable, and upgrade components in future if needed, or my goals change.

A few months ago I won a cheap 3U 12bay Enclosure on an online auction site. It came with a Intel S845WD1-E Mother Board, a 3Ware 8506 SATA RAID Controller. I only really bid on this for the enclosure, and didn't know about the MB, CPU, RAM, Controller..... as these weren’t listed and so was a pleasant surprise. I would gladly upgrade the internal hardware if needed.

After reading I'm leaning towards using ZFS. I believe that:

RAIDz - similar to RAID 5
RAIDz2 - similar to RAID 6
Striped Mirrored Vdev’s - similar to RAID 10


Which one would you recommend for my situation?

If I started out with 4/5 HDD's, could I add another HDD later and increase the RAID, or would I have to add another 4/5 HDD's?

Box.net ran a promo a little while ago for anyone that connected an IOS device to their service. You can read about it [here]("http://lifehacker.com/5849795/get-free-50-gb-of-storage-for-life-on-boxnet++if-youre-an-iphone-ipad-or-ipod-touch-user").  They are still offering it to people with Android devices though.

You are correct in your RAID comparisons, although ZFS is not susceptible to the write hole that exists in traditional RAID5/6 of copy on write.  The whole write must complete or it's all rolled back. 

If you go with ZFS, you can expand the pool by adding more vdevs. So, if you started with a 4 or 5 disk vdev, the best way to expand would be to add another matching vdev, but you can add anything you want to the pool to expand.  [This post ]("http://constantin.glez.de/blog/2010/01/home-server-raid-greed-and-why-mirroring-still-best")mentions using mirrors for the added flexibility, but at home, I use raidz2 to maximize my storage space while still being able to survive losing two disks.

---

### Post by 337Manni on 2012-04-22
Had a quick look ion the site but I can't find 50GB free for Android.



Ignore that! I've found it. It's on selected Android devices, unfortunately not mine. Will keep my eyes open though.

---

### Post by 337Manni on 2012-04-22
I've read that RAID z performs better that RAIDz2 and that Striped Mirrored Vdev’s outperforms them all.
Is that correct?

---

### Post by rubylaser on 2012-04-22
> **337Manni said:**
> Had a quick look ion the site but I can't find 50GB free for Android.



Ignore that! I've found it. It's on selected Android devices, unfortunately not mine. Will keep my eyes open though.

It's [LG Android devices]("http://blog.box.com/2011/11/50-gb-free-on-all-lg-devices-and-new-android-features/").

---

### Post by rubylaser on 2012-04-22
> **337Manni said:**
> I've read that RAID z performs better that RAIDz2 and that Striped Mirrored Vdev’s outperforms them all.
Is that correct?

RAIDz arrays will have higher throughput in terms of a single request with the same number of disks (raidz slightly faster than raidz2).  Mirrors will support more IOPS than a raidz array, because each mirror is able to respond individually rather than the raidz array that acts like one device.  For home use, raidz2 is the best imho, and is still VERY fast when you have around (6) spindles.

---

### Post by 337Manni on 2012-04-22
Thanks for your help.

In real world terms, if in the future I streamed video from this NAS to three/four different PC's which RAID would I benifit from?

---

### Post by rubylaser on 2012-04-22
> **337Manni said:**
> Thanks for your help.

In real world terms, if in the future I streamed video from this NAS to three/four different PC's which RAID would I benifit from?

I use raidz2 at home with (9) 2TB drives and have no problem streaming 1080p streams to all 3 of my XBMC frontends at the same time.  I'd use raidz2 for the guarantee that I could lose 2 disks and still have a functioning RAID set.

---

### Post by 337Manni on 2012-04-22
Thats promising that theres a real world example.
I was torn between ZFS RAID 10 and RAID2z, but I'll prob go for RAIDz2 now that I know that.

I also like the sounds of OpenIndiana that you mentioned.

Just so I can confirm, once I have the RAIDz2 setup, if the OS HDD, motherboard or other hardware should fail, I can move the RAIDz2 HDD's to a new setup, reinstall OpenIndianaor or another OS with the same or higher  version of the pool and my RAID should be up and running again?

---

### Post by 337Manni on 2012-04-22
what would the hardware requirments be for OpenIndiana? On there FAQ it says:

Disk space: Recommended size is 7GB. A minimum of 3GB is required.  Memory: The minimum requirement is 512MB. Recommended size is 768MB.

On other sites I have seen Min 4GB RAM.

May I ask the specs of your hardware?

---

### Post by rubylaser on 2012-04-22
> **337Manni said:**
> Thats promising that theres a real world example.
I was torn between ZFS RAID 10 and RAID2z, but I'll prob go for RAIDz2 now that I know that.

I also like the sounds of OpenIndiana that you mentioned.

Just so I can confirm, once I have the RAIDz2 setup, if the OS HDD, motherboard or other hardware should fail, I can move the RAIDz2 HDD's to a new setup, reinstall OpenIndianaor or another OS with the same or higher  version of the pool and my RAID should be up and running again?

Yes, this will work exactly as you describe.  And, I would install the napp-it frontend, it makes it MUCH easier to manage if you've never used ZFS / Solaris before. Napp-it is dead simple to install to...
```
wget-O - www.napp-it.org/nappit | perl 
```

Once installed, just browse to your machine's ip on port 81 and log in :)

---

### Post by rubylaser on 2012-04-22
> **337Manni said:**
> what would the hardware requirments be for OpenIndiana? On there FAQ it says:

Disk space: Recommended size is 7GB. A minimum of 3GB is required.  Memory: The minimum requirement is 512MB. Recommended size is 768MB.

On other sites I have seen Min 4GB RAM.

May I ask the specs of your hardware?

The more RAM you have the faster ZFS will be.  Frankly, I'd spend more on RAM than I would on anything else in a ZFS system.  The base install + all other packages I've installed is using 5.6GB on my OS drive. I did a text install (no GUI) of Openindiana and run a version 28 pool so it's portable to other OS's that support ZFS.

I have a [AMD 4600+ X2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103749") (this is a pretty old processor by today's standards) with 16GB of RAM (personally, I would say 4GB should be the minimum, but with RAM as cheap as it is, I'd really go for 8 or even 16GB myself).  I use an IBM m1015 flashed with LSI IT firmware for my HBA (my motherboard only has 4 SATA ports).  I use aIso use dual port Intel gigabit NICs lag'd together.  have (2) 160GB 2.5" laptop drives in a ZFS mirror for my root filesystem. I have (9) 2TB hard drives that are a mix of Hitachi 5K3000's and Seagate ST2000DL003's.  On my machine I get sequential write speeds of 525MB/s and reads of 632MB/s, so it's more than fast enough for home use :)

---

### Post by 337Manni on 2012-04-23
I'm impressed.
As I thought I will have to purchase a replacement Motherboard, CPU & RAM. Just double checked the spec's of mine and it only supports a max of 2GB RAM ha.
I would like one that can support 12 SATA + 1 or 2 OS HDD so I can Mirror.
I've also read that some OS's support installation to a Compact Flash card connected via a CF to IDE convertor, and that this gives better performance.
Do you know if OpenIndiana can support SATA expansion cards? I was thinking if I got a Motherboard with say 8 or 10 SATA I could purchase one of these:

[http://www.scan.co.uk/products/2-port-lycom-pe-115-sata-iii-6gbps-low-profile-pci-e-20-host-adapter](http://www.scan.co.uk/products/2-port-lycom-pe-115-sata-iii-6gbps-low-profile-pci-e-20-host-adapter)
[http://www.scan.co.uk/products/lycom-pe-116-6g-sata-iii-2ports-plus-ata-133-1port-low-profile-pcie-20-host](http://www.scan.co.uk/products/lycom-pe-116-6g-sata-iii-2ports-plus-ata-133-1port-low-profile-pcie-20-host)
[http://www.scan.co.uk/products/highpoint-rocket-620-%28r620%29-2-channel-internal-pci-e-v2-x1-to-sata-6gb-s-non-raid-controller-card](http://www.scan.co.uk/products/highpoint-rocket-620-%28r620%29-2-channel-internal-pci-e-v2-x1-to-sata-6gb-s-non-raid-controller-card)
[http://www.scan.co.uk/products/highpoint-rocket-640l-lite-4-internal-port-hdd-controller](http://www.scan.co.uk/products/highpoint-rocket-640l-lite-4-internal-port-hdd-controller)


When you say "I also use dual port Intel gigabit NICs lag'd together", what do you mean by Lag'd? Is this a way of getting twice the bandwidth to the switcher by sending the data down two separate Ethernets?:p

---

### Post by rubylaser on 2012-04-23
> **337Manni said:**
> I'm impressed.
As I thought I will have to purchase a replacement Motherboard, CPU & RAM. Just double checked the spec's of mine and it only supports a max of 2GB RAM ha.
I would like one that can support 12 SATA + 1 or 2 OS HDD so I can Mirror.
I've also read that some OS's support installation to a Compact Flash card connected via a CF to IDE convertor, and that this gives better performance.
Do you know if OpenIndiana can support SATA expansion cards? I was thinking if I got a Motherboard with say 8 or 10 SATA I could purchase one of these:

[http://www.scan.co.uk/products/2-port-lycom-pe-115-sata-iii-6gbps-low-profile-pci-e-20-host-adapter](http://www.scan.co.uk/products/2-port-lycom-pe-115-sata-iii-6gbps-low-profile-pci-e-20-host-adapter)
[http://www.scan.co.uk/products/lycom-pe-116-6g-sata-iii-2ports-plus-ata-133-1port-low-profile-pcie-20-host](http://www.scan.co.uk/products/lycom-pe-116-6g-sata-iii-2ports-plus-ata-133-1port-low-profile-pcie-20-host)
[http://www.scan.co.uk/products/highpoint-rocket-620-%28r620%29-2-channel-internal-pci-e-v2-x1-to-sata-6gb-s-non-raid-controller-card](http://www.scan.co.uk/products/highpoint-rocket-620-%28r620%29-2-channel-internal-pci-e-v2-x1-to-sata-6gb-s-non-raid-controller-card)
[http://www.scan.co.uk/products/highpoint-rocket-640l-lite-4-internal-port-hdd-controller](http://www.scan.co.uk/products/highpoint-rocket-640l-lite-4-internal-port-hdd-controller)


When you say "I also use dual port Intel gigabit NICs lag'd together", what do you mean by Lag'd? Is this a way of getting twice the bandwidth to the switcher by sending the data down two separate Ethernets?:p

Personally, I would skip the CF to IDE adapter as you'll be running ZFS on the root OS and that would probably be pretty hard on a CF card.  Also, I think it would be slower in your use case, so just use an old hard drive or laptop drive or small SSD as the OS drive.  If you tell me what your budget is and what hardware you currently have (case, PSU, etc), I'd be happy to put together what I would use for parts.

Yes, Openindiana / Solaris supports adding SATA Expansion cards, those are what I referred to as HBAs (Host Bus Adapter).  The card I mentioned I use works great.  It can be had for around $60-$70 on eBay and can connect up to 8 hard drives.  That card is the [IBM m1015]("http://www.ebay.com/sch/i.html?_nkw=ibm+m1015&_sacat=0&_odkw=ibm+m1015&_osacat=0").  A cheaper option, but one that doesn't support drives larger than 2TB is the [IBM BR10i]("http://www.ebay.com/sch/i.html?_nkw=ibm+br10i&_sacat=0&_odkw=ibm+m1015&_osacat=0"). Those can get as cheap as $30 on eBay.  You do need to make sure that your card is supported in Solaris. I would HIGHLY recommend one of the two cards I listed as they both work very well and will allow the connection of 8 hard drives via [SFF-8087 forward breakout cable]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116097"), something like this.

I would flash either of those two cards with IT firmware to ensure that the hard drives are passed start through to the OS.  Here's the [m1015 directions]("http://www.servethehome.com/ibm-serveraid-m1015-part-4/"), and the [BR10i]("http://www.servethehome.com/flashing-intel-sasuc8i-lsi-firmware-guide/") (this is basically the same card as the Intel SASUC8I so don't be confused by them only mentioning the Intel card in those directions).

LAG is IEEE 802.3ad, and it allows you to aggregate NICs into a group.  This is good for both redundancy and can support streaming a gigabit speeds to multiple clients at once.  You will not see 2x gigabit speeds to one client though.

---

### Post by 337Manni on 2012-04-23
I like the idea of using two NIC's LAG'd together. One of the concerns I had was if several clients connected to this NAS in the future, that the performance would be hit.

I didn't think I'd go down the route of CF, just wondered if it was worth considering for performance.

I already have 2 x 80GB IDE HDD's I can use for the OS.
I have a 12bay enclosure with 2 additional internal 3.5" bays, all with caddies and SATA cables
It came with a redundant power supply.
3Ware 8506 PCI-X 12Port SATA RAID Controller (Only supports an array of up to 2TB)
24 Port GB Switcher
Wireless N ADSL Router


Just really need:
CPU
RAM
Motherboard
and depending on MB a HBA.
2TB HDD's
I do have 2x2TB HDD's in my HTPC, but thinking about it I will need to keep these as they have the data on them. I'll have to setup the RAIDz2 and move the data from these to the NAS then.


I tend to shop on [www.ebay.co.uk](www.ebay.co.uk) for a bargain or [www.scan.co.uk](www.scan.co.uk)

I don't really have a budget in mind.
I would just like a system capable of supporting 12 Sata HDD'S
The OS on 2xHDD's Mirrored (IDE or SATA), or even 1x SSD if it helps performance.

I have thought of installing Ubuntu with MythTV as a backend, so looked at PCIe ports for TV tuners in future, but I think I will setup my main HTPC for this and just leave this as a NAS with OpenIndiana.

---

### Post by rubylaser on 2012-04-23
If you ever wanted to virtualize Ubuntu and Openindiana on ESXi, I would be purchasing hardware that supports VT-D.  Here's what I would buy.

**[MOBO]** [SUPERMICRO MBD-X9SCL-F-O]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182251")
**[CPU]** [Intel Xeon E3-1230]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115083")
**[RAM]** [Kingston 8GB (2 x 4GB) KVR1333D3E9SK2/8G]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139262") x 2, so 16GB RAM total.

This is a great mix of budget and power while giving you lots of room to expand in the future. But, doesn't have an IDE heads on the motherboard, so that would rule out your older IDE drives.  Your OS isn't going to be slow on any of those setups, but I'd be using a ZFS mirror if you can swing it.  Your data array will be doing all of the work, so don't blow a bunch of money on an OS hard drive.

Otherwise, you could go with something like an Intel [G620]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116399") + [GIGABYTE GA-Z68A-D3H-B3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128502&Tpk=GIGABYTE%20GA-Z68A-D3H-B3") + [RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231315").  This is definately cheaper, but is missing features like ECC memory support, IPMI KVM, VT-D, and AES-NI support if you ever want to switch to Solaris and run ZFS encryption.

---

### Post by anonymouschief on 2012-04-23
> **337Manni said:**
> 
@anonymouschief
Where did you get a free 50GB account? I would be very interested in this for my Documents, USB Drives & Backups.


I signed up to Box from a Blackberry Playbook. Here is the page that details the promos, they are valid till December, 2012: [https://support.box.com/entries/20768867-box-50-gb-promotion-faqs](https://support.box.com/entries/20768867-box-50-gb-promotion-faqs)

---

### Post by 337Manni on 2012-04-26
How would I go about virtualizing Ubuntu and Openindiana on ESXi? I’ve never heard of ESXI before.
Would this allow me to run Ubuntu + MythTV backend and Openindiana at the same time?
Could I install TV tuners in this system?
If so it sounds like a perfect solution!:P


Thanks for taking the time to spec out a system.
I have a case which supports an E-ATX board, I feel that a mATX Motherboard is limiting my expandability in the future if I can install TV tuners and other hardware. I would be happy to spend more if it gave me a perfect setup, which is upgradable in the future (More PCIe ports, greater memory in the future).

> **rubylaser said:**
>  This is definately cheaper, but is missing features like ECC memory  support, IPMI KVM, VT-D, and AES-NI support if you ever want to switch  to Solaris and run ZFS encryption.     

What would these be used for? Excuse my ignorance, but apart from ECC Memory I've never heard of these before.

---

### Post by rubylaser on 2012-04-26
[ESXi]("http://www.vmware.com/products/vsphere-hypervisor/overview.html") is a VMware Virtualization Hypervisor.  If you've never used virtualization before, this would be a bit of a stretch for you.  Here's a[ document]("http://www.napp-it.org/doc/downloads/all-in-one.pdf") that covers that concepts.

This board is a very stable, and would support (3) IBM m1015's + a TV tuner if you'd like (or use a USB tuner as another option).  If you have a VT-D enabled CPU, you can pass through devices directly to the virtual machine.  This is required for some things to work properly.  If you went this route, you'd pass through the m1015's to the Openindiana box and pass through the tuner card to Ubuntu for it's [Mythbackend]("http://www.gossamer-threads.com/lists/mythtv/users/494903").  I'm not sure what else you'd want to put in there, so I still think this is a fine platform for your needs.

You can get 32GB of RAM in this motherboard if you go with 8GB DIMM's. Kingston makes a kit that's perfect for this board (KVR1333D3E9SK2/16G).

To describe all of those acronyms in depth would take some time, but here's the summary:
1. IPMI - gives you KVM over IP.  This allows you manage the server remotely (including entering the BIOS, powering off/on, etc).  For a home user this probably isn't super useful, but it is nice for remote powering on.

2. VT-D - I described passing through cards above, and you'd need VT-D or AMD's Vi technology to do this. Wikipedia describes VT-D like this, *"An input/output memory management unit (IOMMU) enables guest virtual machines to directly use peripheral devices, such as Ethernet, accelerated graphics cards, and hard-drive controllers, through DMA and interrupt remapping." * That is a pretty good description of it's features.

3. AES-NI - Are Intel's Advanced Encryption Standard Instructions. Intel describes this as, *"used to accelerate the performance of an implementation of AES by 3 to 10x over a completely software implementation."*  The main benefit of this would come if you ever wanted to encrypt your ZFS pool.  This would allow all of the encryption to happen in hardware making it much faster (you'd need a pool version of 30, which would require the use of Solaris 11, and would not be portable to other Operating Systems at this point.  I've avoided using pool version 30 for this reason).

---

### Post by 337Manni on 2012-04-26
I will look into VMware, thanks!

The MBD-X9SCL-F-O mATX board you mentioned is hard to get in the UK. I can only find it for as low as £130 ($210) and they all seem to be out of stock.

I was thinking if I got an ATX or E-ATX board, I would have more PCIe ports for 2/3 TV tuners (Don't like USB tuners), 2x NIC's, 1x HBA and other options I may have in the future.


I can see VT-D being useful. IS this just a CPU or CPU+Motherboard feature I should look out for?
I don't think I would use AES-NI though. I can't see a reason I would want to encrypt the ZFS Pool.
The IPMI, I'm not sure about. The NAS would be on 24/7, or I would look at using wake-on-LAN to turn it on, and a command to power it down if possible? I take it Openindiana  could still be managed with Napp-it without IPMI? It would only be if I put Ubuntu on it I would use it?

I will have to do more reading when I get chance. I have to save up for the hardware yet so there’s no rush.

Thanks for all the info so far!!

---

### Post by rubylaser on 2012-04-26
VT-D needs a motherboard + CPU combo, so you do have to watch out for it. Yes, Napp-it doesn't rely on IPMI at all, they are completely unrelated.  If you're not going to run Ubuntu in a second virtual machine and just make it an Openindiana fileserver, then you don't even need to worry about VT-D processors/motherboards.

---

### Post by 337Manni on 2012-11-15
Just an update.
  
  Since last posting I’ve been reading into ESXI and VM’s and it has made me stream several long term projects into one. I originally set out to build a NAS then later a media server then CCTV DVR. I’m now looking to build an All-In-One Server/NAS. My aim is to have:
  
  **[B][B]ESXI **as the base layer[/B][/B]
  
  **[B][B]Open Indiana VM**[/B][/B] for controlling my NAS
  NAS - RAIDz2 using 4 x 2TB HDD
  
  **[B][B]Ubuntu VM**[/B][/B]
  MythTV Installed for a backend Media Server
  Zone Minder Installed for CCTV system (DVR)
  
  Hardware wise I’m looking at the following:
  
  **PCIe Cards**
  NIC Card - Silicom PEG6i - 6 x GB Ports
  DVR Capture Card - LinkDelight 4 Port
  HBA - 8 Port Sata/SAS Controller
  DVB-T2 HD Tuner - BlackGold BGT3650 Quad DVB-T2 / T
   
  **HDD’s**
  6 x 2TB Seagate ST2000DM001 HDD’s (RAIDz2)
  1 x 60GB OCZ Agility 3 SSD (For VM’s)
   
  **Motherboard -** Supermicro X9DR7-LN4F (More than likely this one….)
  **CPU’s -** 2 x Intel Xeon E5-2603 - 4 Cores, 1.8Ghz, 10MB Cache, 80W
  **RAM -** 4 x Kingston KVR1333D3S4R9SK2/8G (32GB Total)
   
   
  What do you think? Can you see any problems I may have with the hardware… Any improvements…
   
  I intend to put the VM’s on one or two SSD’s for performance and back them up to the RAIDz2.

---

### Post by 337Manni on 2012-12-03
I have more questions ha.
   
  1. On the X9DR7-LN4F can the LSI 2308 SAS controller be put / flashed into IT mode?
   
  2. If not is this a problem for OpenIndiana?
   
  3. If I store my media on the RAIDz2 that OpenIndiana controls, and use Ubuntu with MythTV for a media backend to stream media from the RAIDz2 to other PC’s on my LAN, to which VM do I pass the NIC to, Ubuntu, OpenIndiana, both?
   
  4. What size PSU would you recommend and any particular brand / model?
   
  5. I’m sure I’ve read somewhere that with RAIDz2 6 or 10 disks are preferred. Is this true and why? I would like to start with 4 disks and add 4 at a time due to cost, but will use sets of 6 disks if there is a valid reason.
   
  6. Anyone got any tips / hints or guides for my project?

---

### Post by rubylaser on 2012-12-03
> **337Manni said:**
> I have more questions ha.
   
  1. On the X9DR7-LN4F can the LSI 2308 SAS controller be put / flashed into IT mode?
   
  2. If not is this a problem for OpenIndiana?
   
  3. If I store my media on the RAIDz2 that OpenIndiana controls, and use Ubuntu with MythTV for a media backend to stream media from the RAIDz2 to other PC&#8217;s on my LAN, to which VM do I pass the NIC to, Ubuntu, OpenIndiana, both?
   
  4. What size PSU would you recommend and any particular brand / model?
   
  5. I&#8217;m sure I&#8217;ve read somewhere that with RAIDz2 6 or 10 disks are preferred. Is this true and why? I would like to start with 4 disks and add 4 at a time due to cost, but will use sets of 6 disks if there is a valid reason.
   
  6. Anyone got any tips / hints or guides for my project?

Yes, the LSI 2308 can be [flashed to IT mode]("http://lime-technology.com/forum/index.php?PHPSESSID=3af811881c623ce4d495f32108dce302&topic=12767.msg121130#msg121130"). 

I don't have time to answer all of these now, but you will see a performance gain by using the optimal number of disks in a raidz2 array.  Here's the reasoning...

> As i understand, the performance issues with 4K disks isn&#8217;t just partition alignment, but also an issue with RAID-Z&#8217;s variable stripe size.
RAID-Z basically works to spread the 128KiB recordsizie upon on its data disks. That would lead to a formula like:
128KiB / (nr_of_drives &#8211; parity_drives) = maximum (default) variable stripe size
Let&#8217;s do some examples:
3-disk RAID-Z = 128KiB / 2 = 64KiB = good
4-disk RAID-Z = 128KiB / 3 = ~43KiB = BAD!
5-disk RAID-Z = 128KiB / 4 = 32KiB = good
9-disk RAID-Z = 128KiB / 8 = 16KiB = good
4-disk RAID-Z2 = 128KiB / 2 = 64KiB = good
5-disk RAID-Z2 = 128KiB / 3 = ~43KiB = BAD!
6-disk RAID-Z2 = 128KiB / 4 = 32KiB = good
10-disk RAID-Z2 = 128KiB / 8 = 16KiB = good

That being said, I ran a (9) disk raidz2 and could read/write to the array on the box at ~500-600MBps, so that's not too bad :)

---

### Post by Toriku on 2012-12-04
I have a few hard drives in my computer dedicated to videos, music and media, and one NAS server in my house with the same content, I plan to consolidate it into one homebuilt NAS server, and then sync it with a mates that I will help him build, that way we both get off site storage in the form of each others NAS; it will also help with storage for a few of our projects we are sharing files on already over dropbox... 

 I think NAS servers are a brilliant idea, it also means my housemates can store media on there as well, making one master collection of all our entertainment, and I can view it on a Boxee or similar media center device (not decided on what yet)

 Got a mate that wants one too? you could both get the mutual benefit of the security of an off site security system that way

---

### Post by 337Manni on 2012-12-07
Thanks all!

@rubylaser

Brilliant news about flashing the LSI controller! :D
I will read into it when I get chance. Thanks for the link.

The example you quoted about the 4K disks is the same thing I read. Before they listed the formulas they said that 6 / 10 disks are preferred. I couldn't understand why as 128kb still fits nicely over a 4 disk RAIDz2 setup.


@Toriku

Unfortunately I don't know anyone who wants to build / use a NAS.
Great idea though. All my important data is backed up off site, but the more backups the better.

Have you spec'd out a server yet, or are you using all your current hardware to build one?
How do you plan on syncing each other’s contents? I'm curious as this may be handy for backing up my family's PC's to my NAS.

---

