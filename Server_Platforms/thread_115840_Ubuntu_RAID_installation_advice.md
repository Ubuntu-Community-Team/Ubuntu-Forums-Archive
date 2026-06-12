---
title: "Ubuntu RAID installation advice?"
date: 2006-01-11
forum: Server Platforms
---

### Post by juicybananahead on 2006-01-11
Hi everyone,

In the near future I'm going to set up a home server (mainly to be used for SMB fileserving and SFTP but I'm considering running a MythTV backend on it) and I want to use software RAID to provide some protection against hard drive failure. There are two options I'm considering:

1) 2 x 250 GB SATA drives in a RAID 1 config (250 GB storage)
2) 3 x 250 GB SATA drives in a RAID 5 config (500 GB storage)

Has anybody had any experience setting up a similiar system? I'm wondering how easy it is to install Ubuntu and create one of these configs. How would LVM fit into the scheme of things? Also, can anybody suggest an appropriate partitioning scheme?

All advice will be gratefully received!

// juicy

---

### Post by spade_shark on 2006-01-12
> In the near future I'm going to set up a home server (mainly to be used for SMB fileserving and SFTP ...Good idea.  Start there with a Raid 5 if you can.  The easiest would be a single smaller drive to boot and root and the option #2 as the Raid 5 /var storage.  Look at partions with XFS or JFS.  Larger files will take around a minute to delete with ext3, and seconds with XFS / JFS.  Stop here and think about the next step!  I did and still am for a year now ;)  This is my setup...and why I did it.  The above setup leaves you an incredibly stable, reliable, flexible, etc. storage solution.  Not a lot of horse power required to run this solution.  (Modest PIII with 512 ram and a fast nic or two.)  This will run till the cows come home.  You can move data around download / upload isos.  Always on and the wife's files are always available too;)  

MythTV skews this idea quickly.  How many front ends do you want? started with one, now two?  Are you recording in mpegII or HDTV.  Need more CPU and RAM too...more GB of space would'nt hurt either!  How about upgrading to a GB lan.  AH!  (at least that is what I told the DR. in therapy last week).  The myth drives are always crunching something, removing adds, transcoding, encoding, sometimes coding... deleting, adding, and don't forget multipling.
  
I ended up with a P4 front/back RAID0 w/two mpegII tuners.  The kids shows can be dumped down to a dvd and tossed into any player or pc / or those car mobile units.  I found I save very little to HD but rather move to DVD...but that is just me.  Next month it may change :D  I just bought an external SATAII enclosure...if I quit going to IT therapy, I could save enough money to buy a 500gb drive for it.  Add that changes all the rules again.  I am happy to post partions configs whatever you need, are'nt we all.  Just some food for thought(s).  And yes, sorry, I know TMI (2muchinfo).

---

### Post by juicybananahead on 2006-01-12
[QUOTE=spade_shark]Good idea.  Start there with a Raid 5 if you can.  The easiest would be a single smaller drive to boot and root and the option #2 as the Raid 5 /var storage.  Look at partions with XFS or JFS.  Larger files will take around a minute to delete with ext3, and seconds with XFS / JFS.  Stop here and think about the next step!  I did and still am for a year now ;)  This is my setup...and why I did it.  The above setup leaves you an incredibly stable, reliable, flexible, etc. storage solution.  Not a lot of horse power required to run this solution.  (Modest PIII with 512 ram and a fast nic or two.)  This will run till the cows come home.  You can move data around download / upload isos.  Always on and the wife's files are always available too;)  

MythTV skews this idea quickly.  How many front ends do you want? started with one, now two?  Are you recording in mpegII or HDTV.  Need more CPU and RAM too...more GB of space would'nt hurt either!  How about upgrading to a GB lan.  AH!  (at least that is what I told the DR. in therapy last week).  The myth drives are always crunching something, removing adds, transcoding, encoding, sometimes coding... deleting, adding, and don't forget multipling.
  
I ended up with a P4 front/back RAID0 w/two mpegII tuners.  The kids shows can be dumped down to a dvd and tossed into any player or pc / or those car mobile units.  I found I save very little to HD but rather move to DVD...but that is just me.  Next month it may change :D  I just bought an external SATAII enclosure...if I quit going to IT therapy, I could save enough money to buy a 500gb drive for it.  Add that changes all the rules again.  I am happy to post partions configs whatever you need, are'nt we all.  Just some food for thought(s).  And yes, sorry, I know TMI (2muchinfo).[/QUOTE]

Hi Shark,

Thanks for the reply - as far as I'm concerned there's no such thing as too much information! Anyway, I suppose I should clarify one or two things. First of all, maybe I shouldn't have mentioned MythTV. That's a project that's a bit further down the line than the samba/sftp server.  No HDTV broadcasts over here in the UK so I'd eventually be hoping to use a DVB-T card. The only reason I mentioned it was that I know that MythTV recorded video is an absolute space-hog so I thought that maybe it might be best to co-locate the backend and the fileserver, rather than saturating the network during a record from a separate backend to a samba mount on the fileserver. So... forget about MythTV for the moment.

 I've done a little digging around and apparently it's a bit of trouble to boot from a RAID config, so I might take your advice and pick up a cheap SCSI drive on ebay to boot from. However, I guess what I'm asking is, how easy is it to setup software RAID5? I think the Ubuntu installation lets you pick RAID1 or RAID0 but I can't remember RAID5 being on the list.

// juicy

PS My advice is to ditch the therapy and buy the 500 GB drive!

---

### Post by dustyculler on 2006-01-12
I can't speak for Raid5, but I've set several Breezy systems up using software Raid1 and they've worked great so far.

I just created three identical partitions on each drive setting them to be used as raid partitions, went into the Raid setup to mark each set of partitions as being part of a Raid1 array, then set the Raid partitions up to be /boot, swap, and /.

I haven't seen any problems booting from the Raid array, although I can't honestly say if it would still boot if either of the drives went down since I haven't tested that.

If you're thinking about setting Mythtv up in the future, SCSI probably wouldn't give you the space to do much with it.  I've got a Mythtv system I setup to test it out with a small 80GB drive and it fills up so fast I feel like I have to check it every day, deleting shows so I can make sure I don't run out of disk space.

---

### Post by jackdaw on 2006-02-03
I recently built a RAID 1 server with a hot spare, so three 80gb drives total. The only issue i had was if the first drive is unplugged (to simulate failure) it will not boot, as grub does not write the boot info to the second drive. To fix this, do 

grub
grub>device (hd0) /dev/hdb
grub>root (hd0,0)
grub> setup (hd0)

(of course your drives may be different)

then it will boot to either drive and come up normally. then the spare drive replaces the failed drive after all data is transferred.

a good raid how to (where I got the info above) is available at 
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

hope this helps...

---

