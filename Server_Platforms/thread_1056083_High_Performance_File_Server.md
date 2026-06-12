---
title: "High Performance File Server"
date: 2009-01-31
forum: Server Platforms
---

### Post by _2009 on 2009-01-31
Hi,

I'm new here and to Ubuntu, so please go easy!

Firstly I apologise if this has been covered before, but as technology is changing so quickly I though it would be better to start a thread with my exact requirements.

I'm building a new file server for my company and have decided on Ubuntu as the OS. This will be my first system build with Ubuntu, so I thought I'd come here for some OS set-up & hardware advice.

The file server needs to provide high read/write performance of file sizes up to 200mb to 20+ windows clients, possibly act as a ftp server.

The bulk of the clients are in a dedicated render farm and when they start a new job the server will get hit with a lot simultaneous requests for the files required by the job, which would be around a Gig of small and large files.

I plan to have all the data on a raid 5 array with 4 x 250 GB SATA II disks that I have already. Can anyone suggest a mobo/network/storage combination that would meet our needs?

I've heard that Samba may be the main bottleneck when dealing with windows clients, but don't fully understand why, so I'm open to suggestions of how to overcome this.

Can anyone suggest a tried and tested nightly backup procedure on Ubuntu?

Money is the final consideration in these uncertain times, so I'm looking to do it all for under $400 if possible?

If I've been unclear, please let me know where and I'll try and explain myself better.

Thanks in advance for your help.

_2009

---

### Post by HermanAB on 2009-01-31
OK, here is a reality check for you.

A file server doesn't need much computing power, since the bottleneck is the network itself.  Consequently, you need not worry much about your server choice - any old thing with one or two gigabit ethernet ports will do. 

You should be more concerned about your backup strategy.  RAID5 is overkill, since one can get enormous disk drives.  Two 1 TB disk drives in a RAID1 software mirror setup is most probably good enough for what you want to do.

For backup, I would use a couple more 1TB disk drives on USB ports.  Carry one with you so that you always have one off-site.  That is good enough to get started.  However, ensure that the drives are encrypted, so that you have security with data at rest.

You should look at both ease of use and efficiency.  FTP is more efficient than Samba, but it would be inconvenient for the users when compared to Samba.

When building a reliable system, always use a UPS.

Hope that helps!

Herman

---

### Post by unixeducation on 2009-01-31
> Can anyone suggest a tried and tested nightly backup procedure on Ubuntu?

I can try to help you here; I use rdiff-backup to pull nightly incremental backups from several servers to a centralized backup box. There's a good tutorial on setting this up here: [http://arctic.org/~dean/rdiff-backup/unattended.html]("http://arctic.org/~dean/rdiff-backup/unattended.html")

It works great as an unattended backup solution when you properly set up SSH keys to allow for passwordless logins. I typically follow this approach with small files servers I set up; I have a second box that only serves as a backup machine, basically another rig with a lot of disk space.

---

### Post by _2009 on 2009-02-01
Thanks for the replies so far.

unixeducation, I'll check that out when I'm up and running.

HermanAB, or anyone else: Is it possible to increase bandwidth with a multi-port network card?

Thanks,
_2009

---

### Post by sanemanmad on 2009-02-01
AS far as increasing bandwidth, that can only be accomplished really with better hardware. However you can utilize your network limitations efficiently by using multiple network cards.. > any old thing with one or two gigabit ethernet ports will do. 

And that is all, I assume your workplace has some set of switches/Routers in place to manage load balancing/Routes etc..

---

### Post by _2009 on 2009-02-01
We've got a gigabit switch connecting all the machines.

> **sanemanmad said:**
> However you can utilize your network limitations efficiently by using multiple network cards..

I've no idea how I'd go about this on Ubuntu. Can you point me in the right direction or elaborate on this?

Thanks,
_2009

---

### Post by sanemanmad on 2009-02-01
Well if this machine is going to be a dedicated server that handles simultaneous connections, consider adding a 2nd NIC to reduce the amount of traffic at once.

Here is a snippet of my > /etc/network/interfaces file.

```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0
broadcast 10.0.0.255
network 10.0.0.0

```

I have changed my network settings for my own privacy, however it gives you an idea of how to setup this up.

Thus enabling you to break up traffic, maybe one for FTP and another for SAMBA? I dunno, that is a decision left to you.

---

### Post by magawake on 2009-02-01
> 
I'm new here and to Ubuntu, so please go easy!

Firstly I apologise if this has been covered before, but as technology is changing so quickly I though it would be better to start a thread with my exact requirements.

I'm building a new file server for my company and have decided on Ubuntu as the OS. This will be my first system build with Ubuntu, so I thought I'd come here for some OS set-up & hardware advice.

Good Choice. Perhaps, Debian is also a good alternative. 



> The file server needs to provide high read/write performance of file sizes up to 200mb to 20+ windows clients, possibly act as a ftp server.

The bulk of the clients are in a dedicated render farm and when they start a new job the server will get hit with a lot simultaneous requests for the files required by the job, which would be around a Gig of small and large files.

> I have something very similar to this at my University. 

I plan to have all the data on a raid 5 array with 4 x 250 GB SATA II disks that I have already. Can anyone suggest a mobo/network/storage combination that would meet our needs?

I've heard that Samba may be the main bottleneck when dealing with windows clients, but don't fully understand why, so I'm open to suggestions of how to overcome this.

Can anyone suggest a tried and tested nightly backup procedure on Ubuntu?

Money is the final consideration in these uncertain times, so I'm looking to do it all for under $400 if possible?

If I've been unclear, please let me know where and I'll try and explain myself better.

Thanks in advance for your help.


I recommend you to look at a cluster filesystem such as Lustre. You will need atleast 2 or 3 boxes, but the performance will be impressive. See if you can covert one of your Windows boxes into a fileserver. Your biggest bottle neck is going to be I/O especially if its random, therefore I suggest you to take a look at this configuration.

HTH.

---

### Post by r m h on 2009-02-01
In my experience, for the fastest I/O rates, set up a RAID5 array with as many disks as you can (more spindles are good).

I have always had great results with Supermicro mainboards and 3Ware RAID cards.  My business partner has had great results with Supermicro mainboards and HighPoint Rocket RAID cards as long as the RocetRAID cards use hardware RAID, not software RAID.

Size the disks according to your end-result array size goals and the maximum filesystem size your OS can handle (64 bit OSs rock here).

For instance, I recently setup a database server with SATA II disks - a 2x250 RAID1 (mirror) OS array and a 6x250GB RAID5 + hot swap array for the database and file share, using a 64K stripe size.  Of that 6 disk RAID5 array, 5 were the 1TB array and the 6th was the hot spare.

Using SAMBA, I have achieved a sustained write rate of 80+MBps to this RAID5 array over a Gbit network from an smbmounted Linux host (do note that you will not achieve as high a throughput with Windows in the mix - funny, that).  YMMV (and there's LOTS of variables in this mix).

Do note that SATA II, while way cheaper than U320 SCSI 15000 RPM disks, is still slower than said U320 SCSI disks in an equal configuration.

I'd opt for more spindles with smaller capacity over fewer spindles with higher capacity any day based on my real-world testing.

---

### Post by RobinGopher on 2009-02-02
I find myself in a similar situation.

 At work, when our old Windows 2000 Pro 'File/Mail Server' started throwing up errors on its single IDE hard drive, I quickly knocked up a CenOS box running Samba & Scalix. This system run on desktop hardware with software raid on a RocketRAID 1640 (crap) card. However the demands of fileserver (heavily used by our accounts package that uses a fileshare for 3 users) and Scalix are mutually incompatible. One requires frequent read/write access to lots of small files, while the other reads quite large ones.

The plan is now to split those roles and move SAMBA to its own machine and maybe even do some real networking stuff like have a domain controller, LDAP shared with the Scalix box etc.... Picking the hardware however is hard. People keep talking about avoiding FakeRAID, PCI-X is both retiring and only found on expensive Workstation or Server boards, PCI-E cards are a bit slow coming to market, and identifying HARDware RAID cards is not easy. 

After lots of searching I came to the conclusion that for those on a budget there are 2 cards that do Hardware RAID,use PCI-E as you might find on a good desktop board, and don't cost $1000's: LSI MegaRAID 8704 or the Adaptec 3405. Both of these also take SAS drives so you could start with come cheap SATAII drives like WD Black's and migrate to 15K RPM SAS ones later when you have more budget. Based mainly on personal preference I was looking @ using an Asus P5Q series mobo and a cheap Core2Duo. A bigger budget might take you towards a Supermicro/Tyan Mobo but they are much harder to source to the DIY'er.

One feature I noticed on some p5q models was the ability to TEAM up the networking ports, combined with a suitable switch this could give a 2gbit link to your fileserver. But I am unaware if this feature is BIOS level or OS enabled.

Any thoughts from anyone wold be great!!!

---

### Post by HermanAB on 2009-02-02
Well, before spending a ton of money, spend an hour to set up a cheap 'desktop' server and see how it goes first.  You will likely find that it is good enough.  You don't have all that many people and people never do the same thing all at the same time, so the load will be naturally distributed.

Cheers,

Herman

---

### Post by Poleh on 2009-02-02
Contrary to some of the opinions mentioned above I would suggest you look to configure up a RAID 10 array for disk performance. This has the benefit of striping performance (RAID 0) with protection for the entire array on another set of disks (RAID 1/mirroring). Naysayers will decry this due to the fact that it needs double the disks due to the mirroring (4 minimum) but with the cost of disk as cheap as it is I don't see this as a problem. I would also suggest you look at SAS drives rather than SATA as they will perform significantly quicker.

You will find however that the network will be your bottleneck, especially if multiple clients will start requesting files/information at the same time. To combat this I would look to have multiple (2+) GB NICs and bond them into a single interface. However to get this working at it's best you need to have switch assisted bonding whereby you bond the NICs on the server to act like a single NIC, but you also have a switch that allows you to bond the ports into a single virtual interface so that all the clients see is one 4GB interface (for example).

Again, this is viable as NICs are relatively cheap but you might have to shell out to get a layer 2/3 switch to get the port bonding done.

Hope this helps...

---

### Post by RobinGopher on 2009-02-02
Raid 10 is nice even on a game PC, But commonly held opinions on many forums etc almost always suggest RAID5 for fileservers & Raid 10 for servers running things like Scalix (which specifies it in the manual). However all types of RAID and their best uses are described in detail on the websites of almost any Vendor and/or Wikipedia. One I know of to avoid is RAID3 as found recently on cards from XFX.

However going back to the original post, the requirements were to deliver big files Fast and backup with $400 and 4 hdd's. I think we would need to know what else they have?

Managed / Smart Switch - or Dumb?
Any spare machines hanging about for testing before committing? (and salvage)
What is the existing backup strategy?
Is there a remote site for a secure off site rdiff/rsync?
Have you read about/Considered LVM snapshots?
Total data size? Backups to DVD or pendrive are frowned on by many, but they are very cheap and easy, zip, burn, take home.
Can your files be compressed and by how much?
What is the value of your Data? (if it's worth lot's $400 wouldn't even buy you a tape drive)

My server solution costs up @ about £600GBP in rack form. Compared to what you might buy from Dell or HP this is a bargain (1/3rd perhaps).[Yes that is by choosing a horribly cheap case but hey..]

Our backups are done nightly to Tape on a Freecom Dat72 (rebadged HP drive). To make it user friendly to use I use Yosemite Tapeware Basic (Not yet tried it on ubuntu tho') which came with the drive. This is point - click easy, which is always a boon when everything is new to you. A 6 Tape rotation means you don't need to spend a fortune on those either, although they are 10 times cheaper than our old Travan NS20 tapes were.

Once you have something up running and working, make a copy. If disaster strikes, working out what you had done/tweaked all over -not fun.

---

### Post by _2009 on 2009-02-03
> **Poleh said:**
> I would also suggest you look at SAS drives rather than SATA as they will perform significantly quicker.

The sole reason for the new file server is to replace a Dell 2650 with 5 U320 10K SCSI disks (bought on ebay) because the disks are noisy as hell. We're only a small 2 man company, the server sits in the corner screaming away all day and we can't take it any more!

> **Poleh said:**
> To combat this I would look to have multiple (2+) GB NICs and bond them into a single interface. However to get this working at it's best you need to have switch assisted bonding whereby you bond the NICs on the server to act like a single NIC, but you also have a switch that allows you to bond the ports into a single virtual interface so that all the clients see is one 4GB interface (for example).

Again, this is viable as NICs are relatively cheap but you might have to shell out to get a layer 2/3 switch to get the port bonding done.

I like the sound of this. But we're using [_this unmanaged switch_]("http://www.netgear.com/Products/Switches/DesktopSwitches/GS116.aspx?detail=Specifications") at the moment. What sort of money are we talking about for a switch capable of bonding and do you have a suggested make/model?

> **RobinGopher said:**
> Managed / Smart Switch - or Dumb?

See above.

> **RobinGopher said:**
> Any spare machines hanging about for testing before committing? (and salvage) 

No spares for testing. The only salvage we have available are the 4 SATA II disks mentioned earlier and a LSI Logic Megaraid PCI-X controller, spec  can be found [_here_]("http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sata/megaraid_sata_3008x/index.html").

> **RobinGopher said:**
> What is the existing backup strategy?

Full backup of our data to a removable SATA drive. We alternate 2 disks so we always have a copy off-site.

> **RobinGopher said:**
> Is there a remote site for a secure off site rdiff/rsync?

Nope.

> **RobinGopher said:**
> Have you read about/Considered LVM snapshots?

I just read the wiki and it sounds slow? Might be overkill when we aren't serving a database?

> **RobinGopher said:**
> Total data size? Backups to DVD or pendrive are frowned on by many, but they are very cheap and easy, zip, burn, take home.

Up to 300 GB in a full backup.

> **RobinGopher said:**
> Can your files be compressed and by how much?

Compresses to around 70% of the original size. 230 GB became 160 GB last night.

> **RobinGopher said:**
> What is the value of your Data? (if it's worth lot's $400 wouldn't even buy you a tape drive)

It's our livelihood. That said I've found tapes expensive & unreliable in the past, especially with auto-loaders. Have things moved on?

> **HermanAB said:**
> You don't have all that many people and people never do the same thing all at the same time, so the load will be naturally distributed.

2 workstations, 12 render slaves. The slaves are the hogs when they start a new job, they all request the same files at the same time. Usually around a gigabyte of data needs to go to each slave.

Something I forgot to mention in my initial post is domains & DHCP. Do domains exist on Linux? Could this server, running Ubuntu, be a domain controller and manage DHCP for us?

Thanks again for all of your invaluable advice.

_2009

---

### Post by Poleh on 2009-02-03
I am putting my system architect hat on now, forgive me :)

1. If this data is your livelihood then you need to spend the money to protect it properly.

2. SAS drives don't have to be noisy, and they come in small 2.5" form factors now as well. However it may be cheaper for you to get 4 SATAII drives and RAID10 them for performance

3. Managed switch recommendations - not really, any decent brand name will do so ask your local IT shop for something from Cisco, D-LINK, NetGear, etc. (chime in here guys). It depends on where in the world you are and what the local availability of stuff is like.

4. Ubuntu cannot BE a domain controller (i.e. this is a Microsoft tech) but it can JOIN an existing domain. I ask you why you NEED a domain controller? This is normally just a microsoft authentication thing, not for anythin specific. LDAP could be an alternative but that's quite advanced (IMO).

Are you just wanting something to act as a logon server and manage file permissions? If so then you can do that without a domain on Linux.

5. Yes Ubuntu (and indeed all Linux) servers can act as a DHCP server (and DNS etc.). These are not functions soley of active directory but come as part of what it provides.

Hope this helps.

---

### Post by HermanAB on 2009-02-03
Hmm, Ubuntu *can* be a domain controller, but you need to read the Official Howto at the Samba web site and set it up yourself.

Cheers,

Herman

---

### Post by _2009 on 2009-02-04
> **Poleh said:**
> 1. If this data is your livelihood then you need to spend the money to protect it properly.

2. SAS drives don't have to be noisy, and they come in small 2.5" form factors now as well. However it may be cheaper for you to get 4 SATAII drives and RAID10 them for performance

3. Managed switch recommendations - not really, any decent brand name will do so ask your local IT shop for something from Cisco, D-LINK, NetGear, etc. (chime in here guys). It depends on where in the world you are and what the local availability of stuff is like.

4. Ubuntu cannot BE a domain controller (i.e. this is a Microsoft tech) but it can JOIN an existing domain. I ask you why you NEED a domain controller? This is normally just a microsoft authentication thing, not for anythin specific. LDAP could be an alternative but that's quite advanced (IMO).

Are you just wanting something to act as a logon server and manage file permissions? If so then you can do that without a domain on Linux.

5. Yes Ubuntu (and indeed all Linux) servers can act as a DHCP server (and DNS etc.). These are not functions soley of active directory but come as part of what it provides.

This is all good stuff.

1. I hear what your saying but I think my budget is still adequate to protect our data when using a redundant array and our current backup strategy. Unless I'm mistaken?

2. Again trying to reuse the 4 SATA disks we have lying around to keep costs down.

3. In the UK so should be able to get something.

4. You can tell I'm new here. But HermanAB seems to disagree?
The main reason for the domain was a central place to administer user accounts.

5. That's good news.

Thanks,
_2009

---

### Post by Poleh on 2009-02-04
> **_2009 said:**
> 
4. You can tell I'm new here. But HermanAB seems to disagree?

Ja, I am also a bit of a linux n00b and I learn something about it every day :)

---

### Post by bksouder on 2012-03-04
So how did this all turn out.  No one ever comes back with updates, gotcha's, I never should have added used disks because they are so cheap and one failed on us, how things are going a few years later, and how the updates went through the years.

---

### Post by sffvba[e0rt on 2012-03-04
*Old thread **closed**.*


404

---

