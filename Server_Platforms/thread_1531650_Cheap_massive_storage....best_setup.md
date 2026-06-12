---
title: "Cheap massive storage....best setup?"
date: 2010-07-15
forum: Server Platforms
---

### Post by grantemsley on 2010-07-15
I have a file server to store all my movies ripped from DVDs and old VHS, recorded TV shows, music, etc.  The entire collection keeps growing - it's currently over 3TB.  I'm out of space again.

I currently have 2x1TB drives, and 2x1.5TB drives.  The 1st TB of all 4 form a 3TB usable raid5 array, and the 2x500GB on the other drives are used for additional non-raid storage.

I basically have a shoestring budget for upgrading.  I have another 1TB drive, and plan to buy another 1.5TB drive.  That gives me a total of (3*1+3*1.5)= 7.5TB storage.

The problem is keeping it all organized.  If I set up the drives individually, I constantly have to move things around to load balance the free space on the drives.  If I set them all up in RAID, I either lose everything to a single drive failure (raid 0 or lvm concatenating) or I lose a full drive worth of space (raid5).

I don't need redundancy for this.  I can rip it all from the original media again if I have to.  What I really want is a way to have it all show up as 1 drive, and spread files out between the drives automatically.  But, in the event of a disk failure, only lose the data that was actually stored on that drive.

Windows home does this - it shows you all the drives as 1, and balances the data across all the drives.  Each drive has it's own seperate partition and filesystem, but the OS makes it look like 1.

Is there anything like that on linux?

If not, how would you go about setting the drives up (RAID, filesystem choices, etc)?


If you didn't want to read that wall of text (sorry):
[LIST]
[*]I have 3 1TB drives, 3 1.5TB drives
[*]I need as much space as possible (Raid5 is out)
[*]Don't care about SOME dataloss, but don't want to lose EVERYTHING if a drive fails
[*]Want it to show up as 1 drive, so I don't have to juggle files around
[/LIST]


Any advice would be great!  (I think what I really need is more money...)

---

### Post by CharlesA on 2010-07-15
I don't know of anything outside of LVM (I think) that can do that, but you'd lose all data if one drive failed.

It would probably be easier to use Windows Home Server for what you want, since that's how it works: Just add a bunch of drives and it'll expand the "storage pool."

I've not used mdadm, but I *think* you can set it up to use 1 TB from each drive in a RAID 5 array. That won't give you as much space but it's something.

My home server is running 3 x 2TB drives in a RAID 5 array. I've only got 4TB (ish) of usable space, but for the moment that is all I need.

---

### Post by YesWeCan on 2010-07-15
This is an off the wall thought. It might not be sensible. What if you created a directory somewhere and added symbolic links to all the files on all the separate disks to it (you could do this in a shell script to save time). Then all the files would "appear" to be in a single directory. Then, unlike using LVM if one storage disk breaks you just end up with some dead links, and unlike using RAID you don't waste any space.
I'm fairly new to linux so I would be interested if this is a dumb idea or not. :)

---

### Post by gr4nf on 2010-07-15
You should check out FreeNAS:

[http://geekyprojects.com/nas/build-your-own-nas-using-freenas/](http://geekyprojects.com/nas/build-your-own-nas-using-freenas/)

which should let you add drives whenever you want to, and access any and all of them from an http gui on any box on the LAN.

---

### Post by arrrghhh on 2010-07-15
Is there anyway to apply that FreeNAS concept to Ubuntu?  I run a lot of services on my Ubuntu Server, and I really like having them :D  I'd prefer to not be limited to what FreeNAS offers...

---

### Post by grantemsley on 2010-07-15
The symbolic links idea is similar to what I have now...I have one directory with symlinks to all the other drives, and share just that folder with samba. At least that way, I can move things around between drives and just update the symbolic links, nobody else knows the difference.

However, it still requires me to go in frequently and move things around as drives start to get full.

I've looked quite a bit at FreeNAS and similar setups.  ZFS pools can use the full capacity of the drives and show up as one...but my understanding is a single drive failure means losing the entire pool.

I guess I could switch my server to WHS...but I HATE running windows servers.

---

### Post by grantemsley on 2010-07-15
Actually, this: [http://code.google.com/p/greyhole/](http://code.google.com/p/greyhole/) looks a lot like what I want...except for the giant disclaimer saying its beta and might eat all your files, and that it will only work through samba.

---

### Post by gr4nf on 2010-07-15
If drive failure is an issue, FreeNAS supports (i think) RAID 0, 1, 5, and 10. A single drive failure wont cost you any data, but you will have to replace it.

@arrrghhh: FreeNAS is a working linux distro, and it already supports SQL, FTP, SSH, and a number of other services.

---

### Post by YesWeCan on 2010-07-15
"...but I HATE running windows servers" No - don't turn to the Dark Side...:o
Greyhole looks like just what you need, if it is reliable. It is like a librarian that stores and/or duplicates your files and creates symbolic links to them.
This would make a good DIY project if you are familiar with Java programming. The algorithms would be pretty simple.
I think Charles is right to cite LVM and you'd need to run your logical volumes on top of a redundant RAID array. LVM lets you add physical volumes to your logical volumes quite easily and grow your directory across disks. I don't think LVM will do load balancing per se.

---

### Post by arrrghhh on 2010-07-15
> **gr4nf said:**
> @arrrghhh: FreeNAS is a working linux distro, and it already supports SQL, FTP, SSH, and a number of other services.

Do I have all the flexibilities of Ubuntu tho?  I also use rtorrent, Apache, WebKeePass (VERY important to me), MPD, just to name a few...

My understanding is the system is based on BSD... which is **NOT** linux, and which would limit me in what I can do with the above services.  Sure, you may be able to hack the crap out of it to get them to work, but then what happens during an upgrade?

I'd rather stick to Ubuntu if I could.  I know it, and I've setup a very robust and powerful server.  Just looking at my space running out as well, and wondering what the best solution is.  Perhaps in my case mini-LVM's would be best, as currently I break TV shows out into a 1tb drive and Movies into a 1tb drive... I could just have two LVM's, one for Movies and one for TV shows...

I'd still have the problem with drive failure however.  Hrm.

---

### Post by grantemsley on 2010-07-15
Would something like aufs or unionfs be able to do something like this?  I'm not too familar with them, but it looks possible maybe...

---

### Post by grantemsley on 2010-07-15
Anyone have any experience with this?

[http://manpages.ubuntu.com/manpages/lucid/man1/mhddfs.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/mhddfs.1.html)

---

### Post by CharlesA on 2010-07-15
> **grantemsley said:**
> Anyone have any experience with this?

[http://manpages.ubuntu.com/manpages/lucid/man1/mhddfs.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/mhddfs.1.html)

Not used it, but it sounds like it would work for what you want to do. :)

---

### Post by arrrghhh on 2010-07-15
Interesting, looks like it is tied to the FUSE driver...

---

### Post by CharlesA on 2010-07-15
I'd probably make seperate mount points in a folder and then share the folder the mount points are in.

---

### Post by grantemsley on 2010-07-15
> **CharlesA said:**
> I'd probably make seperate mount points in a folder and then share the folder the mount points are in.

That's what I do now - the problem is if the contents of one of those folders fills the drive it is on...you then have to start shuffling things around to balance it out again, which gets to be a lot of effort in my situation.

The mhddfs system looks to be pretty much exactly what I was after!  I'm surprised I hadn't found it until now.  Will take some testing, but it looks like it will merge the space on all the drives, and a drive failure only loses the files actually stored on that device.

---

