---
title: "Help with Storage Server setup"
date: 2007-10-11
forum: Server Platforms
---

### Post by phylae on 2007-10-11
Hi,

I am trying to set up a Storage Server for my home/home office. I am about 99% sure I will use Ubuntu for the O/S, but I am hoping to get some advice before I start buying hardware and installing things.

I currently have two computers on my home network: a laptop with Ubuntu and a desktop with Windows XP. I would like to put most files onto a storage server so that I only have to worry about backing up, sharing, and security for one machine.

There are four main types of files that I will want to store on this machine: pictures, music that I have recorded, video from my HD camera and source code for the web applications I am developing. Essentially anything that I have created. It is VERY important that I don't lose any of this because I can't replace it.

I will probably also use the server to store documents, backup emails, run a development database, and run subversion. The last two might be within a virtual machine (so that it will be easy to move to another server when I've outgrown the first one). All of these are secondary uses.

Because I have two computers on the network that need to read/write the above mentioned file types, I would very much like to have these files stored on the server, not just backed up on the server. Also, I will occasionally have people visiting with their laptops and they will need access to some stuff on this server too. Most likely visitors will have Mac OS X or Windows XP. Vista and various Linux distros are possible but not likely (for the forseeable future).

I think I should start with about 1TB of space. However, I would like the ability to upgrade to at least 2TB in the future. (Yeah, that HD video cam takes up a lot of space!)

My budget is a MAX of $2000 CAD (yes I am in Canada). However, I would very much like to get started for less than $1000 CAD.

My biggested dilemma is, **what kind of RAID should I use**? I like the idea of RAID-6. That way if a drive fails, I can still feel safe and I don't need to immediately rush out and buy a new hard drive. However, there seems to be a huge price jump to get RAID-6, so maybe it is overkill.

Then there is software RAID. I have heard that this can use different drive sizes. Is that true? If so it might make upgrading cheaper. I have also heard that it is slower. How much slower is it? If I am already getting a speed boost from RAID striping then I should still be faster than a standard hard drive, right?

I have a few other quesitons too: 

What is the recommended file system for this kind of setup? I like the (reported) reliability of XFS, but I haven't used it before. Does it work well with Ubuntu?

How much RAM should I get? I know the database (likely MySQL, possibly PostgreSQL) can hog RAM, but I won't be using it very often.

Should I get all 64bit hardware?

Any recommendations for other hardware: motherbaord, hard drives, case, fans.

One last note, it would be *nice* if the machine was fairly quite since it will be on all the time--in my living room. :)

Thanks in advance.

---

### Post by HermanAB on 2007-10-11
My tuppence worth:
Use RAID1 (2 drives mirrored).  
Software RAID is good, not slower at all.
Get at least 2GB RAM if you want to run virtual machines.
For more than 2GB you need to install a different kernel.
Use JFS, since XFS is buggy lately.  JFS is efficient and fast, very similar in performance to XFS.
Don't use Ext3, since it wastes gigabytes of disk space due to excessive overhead (about 7.5%)
64bit is good for a server, but not really any better than 32bit.
Do get a UPS.

Cheers eh,

Herman

---

### Post by phylae on 2007-10-11
Thanks for the answer!

I'm definitely going to get a UPS. I have been very happy with the APC one that I have for my desktop, so I'll probably get another one of those.

I've never heard of JFS before (yeah, I've been using Windows too long). I did some quick research and it looks interesting. I actually meant to say ZFS in my original post, not XFS. Is anyone successfully using ZFS on Ubuntu?

---

### Post by elvis on 2007-10-12
RAID6 is available now through Linux software RAID.  This is highly recommended for small home/office servers.  True hardware RAID controllers are rcommended where high speeds are required and you have LOTS of users.  But for 50 or fewer users, linux's own MD RAID system performs very well.

Do be aware that database write performance on RAID5 or 6 volumes isn't that great.  This applies more so to large databases (multi-GB databases with many simultaneous users).  In that instance, RAID10 is recommended.  But again, for small home/office or private development use, RAID5/RAID6 is fine.

On any RAID system, A UPS is mandatory.  The biggest killer of data is a power outage in the middle of a striped write.  And don't scrimp either - get a fully online UPS (not a switching UPS).  Yes, they are more expensive, but how much is your data worth to you?

> **phylae said:**
> I've never heard of JFS before (yeah, I've been using Windows too long). I did some quick research and it looks interesting. I actually meant to say ZFS in my original post, not XFS. Is anyone successfully using ZFS on Ubuntu?
ZFS is not available natively on Linux due to license incompatibilities.  Currently if you want ZFS on a host, Solaris is your only option.

For file servers 1TB and up, I use the following:

1) Linux MD RAID to build my RAID sets

2) Linux LVM on top to manage my volumes, and allow me to grow volumes at a later date

3) XFS file system - the best performance file system for large volumes hosting large files.

This combination allows me to manage my volumes easily, and expand my storage at a later date (without needing to format and repartition) should I need it,  All three are well documented on their respective websites, and on multiple HOWTO sites.  Let Google and the man files be your guide.

One final piece of advice - have a good backup strategy.  RAID **IS NOT** a replacement for backup!

RAID is there to prevent the inconvenience of failed hardware only.  RAID will not protect you against user error like accidental file deletion, or file system errors.  The only way to recover from those is to look to a recent good backup.

Your options here are nearly unlimited.  You can go the whole hog and have twin servers that rsync their contents daily.  You can go tape.  You can go USB/firewire removable hard disk (my recommendation for small home/office setups with a limited budget).  You can go DVD-R if you have a small file system.  It doesn't matter, as long as you have SOMETHING.

---

### Post by ChrisQ on 2007-10-14
anyone care to walk me through how to grow a current raid array? I've got a raid 5 setup with 4 300 GB sata drives and I want to replace them with 500 GB drives. THe partition on it is reiser 3.6, thanks.

---

### Post by elvis on 2007-10-16
> **ChrisQ said:**
> anyone care to walk me through how to grow a current raid array? I've got a raid 5 setup with 4 300 GB sata drives and I want to replace them with 500 GB drives. THe partition on it is reiser 3.6, thanks.

First things first: back up all your data.  That goes without saying.

RedHat have an excellent guide up on growing RAID5 sets via physical drive-replacement:

[http://www.redhat.com/magazine/022aug06/departments/tips_tricks/](http://www.redhat.com/magazine/022aug06/departments/tips_tricks/)

The last line in the example shows how to resize an ext2/3 file systems.  "man resize_reiserfs" will tell you how to do this with ReiserFS.

For me personally, I would rather set up a second RAID set, test it for a few days, and then rsync all the data across.  But I'm a paranoid kinda dude.

---

### Post by ChrisQ on 2007-10-16
I would too, just nowhere to put it.

---

### Post by phylae on 2007-10-17
Thanks elvis!

Your comments are really helpful. I've got the server up and running. I decided to test out an old machine I had and it seems to be running well enough for now. It is amazing how fast things run on Ubuntu when you don't have a GUI. 

At the moment I only have a 20GB IDE hard drive in the machine, but my new 500GB SATA drives and the SATA conroller should arrive on Friday. Then the real fun will begin.

By the way, I bought an APC Back-UPS RX1300 for about $200. I really liked the previous APC UPS I bought. It never gave me any troubles, even though electricity in my house is not very stable. How do I tell if my new UPS is fully online or switching?

Thanks again

---

### Post by elvis on 2007-10-17
> **phylae said:**
> By the way, I bought an APC Back-UPS RX1300 for about $200. I really liked the previous APC UPS I bought. It never gave me any troubles, even though electricity in my house is not very stable. How do I tell if my new UPS is fully online or switching?

Well for starters, the manual will tell you what type it is. :)

Usually the price is an indication too.  I haven't seen a fully online UPS for under about US$500 or so.  I know a lot of people will baulk at that sort of money, but if the safety and integrity of your data is important to you, prevention is better than few.

The difference is a fully online UPS (or "always active" UPS) powers your system from the UPS battery constantly.  Any power surges or dips are absorbed by the battery and protection circuit, and your system always gets clean power no matter what.

A switching UPS (or "offline" UPS) feeds power to your system direct from the mains.  If there is a power fault (either a spike or a dip) large enough to trigger the circuit, it will switch over to battery.

Now, 9 times out of 10, this switching occurs fast enough.  But occasionally, it doesn't.  Likewise, if the surge (or dip) just happens to occur at a point when the AC waveform is at a high (or low), it may go unnoticed by the UPS.

This can not only damage equipment, but for RAID it can mean that cached data does not get written fully to the disk, resulting in data corruption.

I've seen this occur first hand - I administrate about 40 sites for a particular retail chain who all had switching UPSes in their shop fronts (to save money over fully online units).  They suffered quite a lot of equipment damage and data destruction before they finally bit the bullet and started upgrading their UPS units.  In all stores where the upgrade occurred, the problems disappeared.

But back on topic....

I can't find an online product manual for the model you mention above.   But the series of UPSes it belongs to are all home/small-office units, which are 99% of the time switching UPSes. 

You need to look at something like the more expensive Smart-UPS series for fully-online units.

---

