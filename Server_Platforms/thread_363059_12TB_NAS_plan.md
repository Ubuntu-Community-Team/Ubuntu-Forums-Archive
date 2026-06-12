---
title: "12TB NAS plan"
date: 2007-02-16
forum: Server Platforms
---

### Post by jml75 on 2007-02-16
Hello all,

I'm writing here because I'm planning to build a NAS storage server. But I was wordering about a few things and would like share my questioning and get your advises, tips and maybe expirence about this.

**_Here is what I plan to buy first for hardware:_**

1 x Supermicro 3U rackmount model SC836TQ-R800V
1 x Tyan Tomcat n3400B (S2925) model S2925G2NR
1 x AMD Opteron DC model : 1210
1 x Kingston 1G DDR2 ECC model : KVR800D2E5K2/1G
1 x AMCC 3Ware RAID controler model : 9650SE-16ML
4 x Seagate Barracuda ES 750GB model : ST3750640NS (as a starter more to be added)

The rackmount chasis provides the ability to hold up to 16 drives but for budget reasons, I'm going to start with 4 and plan adding more disks as time goes by so it will eventually be at around 12TB using 16 disks of 750GB each.

Since the 3ware 9650SE-16ML RAID controler supports RAID 6, I chose to build the NAS server using this level of RAID.

Then, the OS will be probably an Ubuntu Server 6.10.

**_Here are my questions:_**

- What would be a good implementation for the partition scheme?
- Should I make just one big array that increases in size as I add disks or devide it in smaller arrays?
- Should I use LVM?
- Also I read that the maximum size of a ext3 partition is of 4TB, how would I overcome that?
- Is there a better FS than ext3 to do this?
- Is 1 GB of Ram enough?
- Should I look for a faster CPU the one I'm buying is a dual core 1.8 Ghz?
- I'm building this server for a mixed Linux, Mac, Windows environment. Should I use NFS or Samba?
- Should I run Ubuntu Server in 64bit or 32bit mode?

Thanx in advance for your time and help!

Have a nice one!

Jonathan

---

### Post by LotsOfPhil on 2007-02-16
I have a friend who recently did something similar. He went with FreeNAS.

I trust his opinion a lot, so my advice to you is look into FreeNAS instead of Ubuntu.

---

### Post by maxamillion on 2007-02-16
> **LotsOfPhil said:**
> I have a friend who recently did something similar. He went with FreeNAS.

I trust his opinion a lot, so my advice to you is look into FreeNAS instead of Ubuntu.

I am a die hard debian/ubuntu fan but I must too advise you use FreeNAS, its solid and will make your NAS life much easier ... and FreeBSD is a solid system on its own anyways :)

---

### Post by jml75 on 2007-02-16
Thanx you two for the tip. Can FreeNAS do hardware raid to?

Still, i'd like some advices on doing what I want to do with Ubuntu Server so I can try both and make up my mind.

Thanx!

---

### Post by maxamillion on 2007-02-16
> **jml75 said:**
> Thanx you two for the tip. Can FreeNAS do hardware raid to?

Still, i'd like some advices on doing what I want to do with Ubuntu Server so I can try both and make up my mind.

Thanx!

Yes it can, Hardware raid isn't a problem for FreeNAS

---

### Post by jml75 on 2007-02-16
Thanx all for your replies but what about your linux experience?

Also any opinion on the mobo, should I get a Tyan or a Supermicro mobo?

Thanx in advance!

---

### Post by jml75 on 2007-03-28
Well, it's kind of sad to see so few where interested to share their thoughts on this issue...

Thanx for telling me about freenas but this is not what I want.

I want to do this with Linux and i'd really appreciate some help with this.

Any one?

Thanx!

---

### Post by Brazen on 2007-03-28
> **jml75 said:**
> Well, it's kind of sad to see so few where interested to share their thoughts on this issue...

Thanx for telling me about freenas but this is not what I want.

I want to do this with Linux and i'd really appreciate some help with this.

Any one?

Thanx!

FreeNAS is BSD, so not far off from linux.  With all that data though, you need to be VERY mindful of data integrity, so I really really think you should go with LTS editions of Ubuntu ONLY.  Plus, once you get it set up, you don't want to have to do a risky version upgrade every 6 months.  Current LTS edition would of course be Ubuntu 6.06 Dapper Server.

Personally, I would go with Ubuntu Dapper Server over FreeNAS, and use Webmin for a web interface.  Also, I would get one harddrive that is not in the RAID array just for installing the OS on, and then put your file shares on the raid.

- What would be a good implementation for the partition scheme?

This varies greatly depending on what you are going to do with your NAS.  I would suggest leaving about 10-20% of your volume unpartitioned though so you can create snapshots.

- Should I make just one big array that increases in size as I add disks or devide it in smaller arrays?

I would create one big RAID 5 array.  Keep buying your disks in sets of 4, creating new 4-disk arrays and add the array to the LVM volume.  If you want to go with bigger than 4-disk arrays, just keep in mind the optimal size for RAID 5 arrays is 5-8 disks.  At some point (soon), you will also want to invest in a an extra disk to assign as a global hotspare for the arrays.

- Should I use LVM?

Absolutely.  You'll have to have LVM to combine multiple raid arrays into a single volume (as mentioned above), make snapshots, and some other neat features.

- Also I read that the maximum size of a ext3 partition is of 4TB, how would I overcome that?

The maximum size of an ext3 partition is 32 TB.  The maximum size of an XFS partition is 8 Exabytes.

- Is there a better FS than ext3 to do this?

I would use XFS.  It is faster (which may not really have much effect over networked shares), stable (unlike ReiserFS), and has some extra features (some especially useful features for snapshots).

- Is 1 GB of Ram enough?

It should be.  You can always add more later.  The thing I have noticed with our Samba server is, no matter how much RAM I assign to it (it's a VM, so easy to change RAM), it always uses like 80% of the total due to caching.

- Should I look for a faster CPU the one I'm buying is a dual core 1.8 Ghz?

As long as you don't install a GUI on your system, and only have it do file shares, your processor is going to be plenty.

- I'm building this server for a mixed Linux, Mac, Windows environment. Should I use NFS or Samba?

You can use both.  NFS is much faster than Samba (inherit to the SMB protocol, not to Samba).  Also NFSv4, has been problematic for me; I stick to NFSv3.  I use Samba for our Windows clients and NFS for linux clients

- Should I run Ubuntu Server in 64bit or 32bit mode?

I would run 32bit mode, just because I haven't tried 64bit so I can't attest to it's reliability.  From what I'm hearing, 64bit is now just as easy and reliable as 32bit, but I have not had a need for it, and your setup will not get any advantages from 64bit unless you think you will need more than 4GB of RAM in your file server (highly unlikely for a file server).

---

### Post by jml75 on 2007-03-30
Thanx a million Brazen!

I'm glad you answered!

I will analyse your infos and keep you posted when I'll start to play with the server in a week or so.

Also, do you have a preference between RAID 5 and RAID 6? the controller i bought seems to be faster in RAID 6 than RAID 5, I get extra protection because 2 disks per array can fail but I also loose more space... Especially if I do 4 different 4 disks arrays...

Thanx alot again!

---

### Post by Brazen on 2007-04-01
> **jml75 said:**
> Thanx a million Brazen!

I'm glad you answered!

I will analyse your infos and keep you posted when I'll start to play with the server in a week or so.

Also, do you have a preference between RAID 5 and RAID 6? the controller i bought seems to be faster in RAID 6 than RAID 5, I get extra protection because 2 disks per array can fail but I also loose more space... Especially if I do 4 different 4 disks arrays...

Thanx alot again!

In the past, I have researched and compared the various raid levels and always came up that Raid5 worked best for me, so any more I don't consider anything other than (anti-)Raid 0, Raid 1, or Raid 5.

I don't remember anything about Raid 6, but you say 2 drives can fail, so what are the chances, out of 4 or 5 drives, that 2 are going to fail at the same time?  Having a global hotspare can also give you a little more protection with Raid 5 so if one drive fails, as long as the hotspare has a couple hours to integrate into the array and second drive can later fail.  For extremely rare, freak occurances, like 2 drives failing within a few hours, is what backup tapes are for.  If you have 4 arrays, than you can still have 1 driver in each array fail with Raid 5.

But that is just my decission.  You've evidently already looked into the raid types and depending on the quality of your hardware and how important it is not to lose the few hours of data since your last backup, Raid 6 may be right for you.  But I will tell you, Raid 5 is definately the most popular.

---

