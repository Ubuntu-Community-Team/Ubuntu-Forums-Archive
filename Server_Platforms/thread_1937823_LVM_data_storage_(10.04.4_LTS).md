---
title: "LVM data storage? (10.04.4 LTS)"
date: 2012-03-08
forum: Server Platforms
---

### Post by Drak3 on 2012-03-08
So, I have a relatively simple network file server set up, and I'm looking to expand my storage.  (current storage drive is 70+% full)  I've more or less settled on LVM because striping makes me extremely paranoid, and I dont need crazy access speeds.

My question is, does LVM have any sort of distributions leveling?  Basically, I want to know if LVM will fill the hard drives sequentially, or if it will choose which drive to write files to.  Ordinarily I wouldn't care, but i'm not using up space too rapidly, which could mean one drive is full and another is barely being used.

the answer doesn't really affect my decision to use lvm, but it'd be nice to know before i drop money on more drives.

Ive tried google, but i'm either missing obvious things, or nobody has bothered to say much about it.  If anyone has any info, that would be awesome.

---

### Post by darkod on 2012-03-09
As far as I know, it is not using it evenly. I don't know if it's literary sequential, but don't expect it to be even at all.

But... there are ways to set up LVM with actual striping, so that it literary does write 50-50 (on two disks). I believe it can work on more than two disks too.

I have seen that used on SSDs to simulate raid0 because the raid0 will not use trim, so someone has figured out that lvm striping will do the same job as raid0 striping and at the same time use trim on a SSD.

The topic was from the OCZ forums... if only I could find the link... :)

EDIT: Found it. It's for a SSD but adjust it for your needs, the lvm section still applies.
[http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux)

---

### Post by Drak3 on 2012-03-10
thanks, i thought it would most likely be something resembling sequential.  though in my case sing SSDs with striping would be overkill to the max!  in the end, the network is the ultimate bottleneck.

---

### Post by darkod on 2012-03-10
Well, even for a home file server I would never put it on raid0 (or this striped lvm). With the amount of data even home users have these days (photos, videos, etc), I would actually consider a raid with redundancy. Not sure what you are planning to do, I would use raid1 at least.

That way if one disk goes, you still have time to replace it with a new one and the array keeps going.

Again I say, depending what you plan to do, but you can consider something like raid1 with lvm on top of it. So in future you can create one more raid1 array and extend the lvm to include it.

---

### Post by Drak3 on 2012-03-10
im actually planning on getting 3 more hard drives.  1 to expand storage, and the other 2 either for backup or raid1, not sure which.  still have to work on means of backing up if i dont go raid1

---

### Post by rubylaser on 2012-03-10
+1 for RAID + a backup for critical items at a minimum (family pics, home movies, etc).  Personally, I'd suggest mdadm with a RAID5 to start.  You can migrate to a RAID6 down the line as you add drives.  Also, there's no need for LVM unless you want to span across multiple md devices as darkod had mentioned.

---

### Post by Drak3 on 2012-03-10
i refuse to do striping, lol, so raid 0,5,6 or any flavors of striping are out for me.  i could tolerate raid1, but if i have a current backup, raid1 would be of little use to me.  plus my whole goal was to have multiple drives appear as one.

in any case i still have to figure out how to backup 4TB of data using 2TB drives, but that would be a different thread altogether...

---

### Post by rubylaser on 2012-03-10
Then, I'd just suggest you use [mhddfs]("http://romanrm.ru/en/mhddfs").  That way losing a disk won't cause the lose of all of the data in your logical volume.

I'm not sure why you're against RAID5/6 as that's an effective way to maximize storage space while still having redundancy, but it's your data, so it's your choice.

---

### Post by Drak3 on 2012-03-10
i was unaware that lvm would suffer from that drawback.  mhddfs looks quite attractive.  i dont suppose you have any recommended reading on it?  (i'm not finding  whole lot with google.

---

### Post by rubylaser on 2012-03-11
There's really nothing amazing or dangerous about mhddfs :) There really isn't much to Google as that page I linked to covers everything from what it does to how to set it up.  Just build a Virtualbox virtual machine and try it out, it's really simple, although not blazing fast because it's a layer sitting in front of each of your hard disks.

Basically, all of your hard drives contain their own filesystems, so you can either view the data on each one individually via it's mount point, or as a whole through it's virtual mhddfs mount point.

---

### Post by Drak3 on 2012-03-11
i may have been convinced, lol.  i just have 2 main questions:

[LIST=1]
[*]about how much of a speed hit could i expect? and,
[*] would the individual volumes still be accessable?  (if they are, then backups become stupid easy)
[/LIST]

i may try a VM later, but if you have answers now, gigitty!

---

### Post by rubylaser on 2012-03-11
> **Drak3 said:**
> i may have been convinced, lol.  i just have 2 main questions:

[LIST=1]
[*]about how much of a speed hit could i expect? and,
[*] would the individual volumes still be accessable?  (if they are, then backups become stupid easy)
[/LIST]

i may try a VM later, but if you have answers now, gigitty!
1. I've only been able to get about 45MB/s across the network via scp or NFS to an mhddfs share.  This is still much faster than most consumer grade NAS devices, but slow compared to what I'm used to.

2. Yes, the individual drives are all accessible because they need to be mounted prior to mhddfs making it's virtual mount, so backups have just become easy.  Also, it doesn't span files across two drives, so you don't have to worry about parts of a file being on different drives.

Please do try it out in a VM, so you can really understand how it works.  Even try setting up a backup for it, and try restoring the backups.  It's always a good idea to test everything before you actually deploy and rely on something :)

---

### Post by Drak3 on 2012-03-18
Well, I believe I am in your debt good sir!

mhddfs is working excellently so far.  there is actually one little curiosity ive noticed; file transfer speed within the server is on par with the individual disks, but the transfer speed over the network is about half of what it was before, but its still >10MB/s in most cases.  not a complaint, just interesting--internally little to no speed penalty, externally not so much...

---

### Post by rubylaser on 2012-03-18
No problem :)  I'm glad you got it setup and working.  I haven't seen speeds that low, but it would depend on what protocol you're using to transfer with.  NFS will be much faster than CIFS/SAMBA.

---

### Post by Drak3 on 2012-03-19
I actually discovered that my partitions on the new hard drives were misaligned (dont know HOW I managed to do that), and after fixing that, and restoring, the transfer is about where is was before; >20MB/s.  I mostly just use samba for streaming.  For major uploading and downloading I usually use sftp.

---

