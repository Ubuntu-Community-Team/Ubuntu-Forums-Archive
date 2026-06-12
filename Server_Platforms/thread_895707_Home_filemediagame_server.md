---
title: "Home file/media/game server"
date: 2008-08-20
forum: Server Platforms
---

### Post by alecz20 on 2008-08-20
I am planning to build and install a server in my house.

What I need the server to do:
- host and share files (via Samba) to both Windows and Linux machines
- stream media, possibly some encoding (via MediaTomb probably)
- host Dedicated Server games (such as Battlefield 2)
- possibly provide storage for whatever my family members need (such as video editing that requires large amount of HDD space)

I know that generally the hardware requirements for servers are lower than those of desktops, but given the fact that I want have lot's of HDD space (over 1 TB) and be able to encode, and host a game server simultaneously, I figured I might want a better hardware setup. So I am currently considering the following:

- Intel Pentium D 2.8 GHz (dual core CPU)
- 2 - 4 GB RAM
- PCI (express) Gigabit Network card (not sure about the brand yet)
- 1 x 150 GB Raptor (10k RPM) for OS, Swap, Game server partition. Probably 100 GB for the game server partition, rest OS+Swap.
- 1 x 1 TB HDD for movies and other large files (what FS should I use?)
- 1 x 500 GB HDD for music, pictures, possibly internet cache. I might add another 500 GB and make RAID 1 (again, what FS?)

I plan to install Ubuntu 8.04.1 Server Edition 32-bit, but I am not sure what other options I would need besides SAMBA. I don't want to complicate myself with APACHE, DNS, PHP, MySQL and all that, as I barely know what they are.

My questions:
1) Is this hardware overkill or not enough?
2) Should I have different file systems? (small files vs large files)
3) Is the Raptor HDD going to help if it hosts the OS, Swap, and a game server partition?
4) Is there a better option than MediaTomb for media sharing? (My greatest concern is with photos, where MediaTomb does not seem to keep the disk directory structure of dates/albums)

5) Any other comments/suggestions are appreciated.

Thanks,

Alex.

---

### Post by frego on 2008-08-20
If you want to use more than 2GB of RAM, I believe you still need a 64bit system.  Can someone else verify this is true?  I haven't kept current; did a new kernel change this?

With the price of AMD X2 chips now, they're a steal.  I'm using a AMD 64 3800+ in a similar role right now.  I opted to put in the 4GB of RAM and boy am I glad I did!  It doesn't take  much processor to serve up files, but the encoding and in my case, running VMWARE with multiple OS images running at once, the processor speed and RAM really comes in handy.  

The other specs sound fine to me.  I probably would go with a server grade board with scsi onboard and setup a hardware raid to mirror the system disks if you want to get fancy.  But I don't think the 10K drive is worth the money as you gain a bit of speed at the expense of a shorter life on the drive.  And in a server, you definitely want to build it with longevity in mind.  That's also why I'd recommend not going with a consumer grade motherboard.  The server grade will cost you more initially, but you should get a lot longer life out of it.

As far as file system, I like ext3 or JFS.  You might also consider LVM for your media storage array.

---

### Post by troutbum13 on 2008-08-20
My personal opinion is that hardware has reached a point where people tend to overbuild machines. I have a home sever of older parts and it works great, and is rock solid. I am using an older abit board with onboard gigE lan, a prescott 3 GHz CPU that runs wicked hot, 2 gigs of RAM, 35 GB raptor for / drive and 4 500 GB WD using LVM for pulled storage. I run samba for my wife (only windows machine in the house) and NFS for serving to linux. I use SSHD and apache for serving sessions and a small web page. I also like webmin for admin tasks for the server 

to anser your questions, I think the hardware you have depends on if you are really going to encode/decode on the server. My preference would be to use my more powerful desktop machine for heavy tasks and keep the sever hardware light.

I use XBMC for media playback, and it basically handles any format you can throw at it, so server side is limited to serving files.

IMO the raptor is not going to make that big of difference

+1 on ext3 and I use LVM and it is very scalable for a home server solution.

good luck.

---

### Post by alecz20 on 2008-08-20
Regarding the 32 vs 64 bit. I read on this forum that the 32-bit server Edition supports PAE which should allow up to 64 GB or RAM to be used.

The reason I mention the Pentium D, is because a friend of mine wants to get rid of it, so I can get a REALLY good price for it. He also sells the Raptoor for $160 CAD, so I thought it would be a nice deal.

I suppose you were suggesting LVM so that I can make a larger partition out of smaller ones. I do not think this is really my intention... I heard that some file-systems are better with smaller files, while other are better with larger files, hence the 1 TB & 500 GB disks. If that's not the case then I might go with LVM to get a huge partition.

I want to be able to stream to a PS3 so encoding would need to be done on the server whenever necessary. I do not know if XBMC can do that, I'll have to look into it.

---

### Post by troutbum13 on 2008-08-21
sounds like you have a plan.:)
LVM will work as you have suggested, but it also makes your file system scalable. I mention it because you talked about this machine serving media, LVM lets you add pooled space to existing directories as needed. As your media directory gets full you can add physical disks and just increase the pooled storage, JBOD style...as for transcoding software I have little experience withit but people speak highly of tversity

---

### Post by alecz20 on 2008-08-24
Thanks for the LVM tip. Sounds interesting.

> **troutbum13 said:**
> 
...as for transcoding software I have little experience withit but people speak highly of tversity

**If only there was a Linux version for tversity!** Also I plan to run without a Desktop Environment, so I need some Command Line option.

I just tested MediaTomb from my laptop, and it works flawlessly, without any transcoding. The new firmware for the PS3 has DivX/ Xvid support.

I still have to see how MediaTomb handles pictures...

---

### Post by fido777 on 2008-08-25
My recent post [**http://ubuntuforums.org/showthread.php?t=892692**]("http://ubuntuforums.org/showthread.php?t=892692") may be of some help.  I use a RAID5/LVM setup, and I'm quite happy with it.

---

