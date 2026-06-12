---
title: "ntfs or ext3 for samba?"
date: 2008-05-25
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-25
I posted a wek ago asking this question and was told that it should be in ext3 if the drives connected to a ubuntu server.
It made sense but I've now found his article and it says 'drives for staorage ould be ntfs' in so many words.
So which is it? If it's NTFS does that mean ubuntu is using the NTFS-3g project for writing? Although this seems very good writing  1-2 gb files might cause issues.
Here the link -  [http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

---

### Post by koenn on 2008-05-25
> **garethsimpsonuk said:**
> I posted a wek ago asking this question and was told that it should be in ext3 if the drives connected to a ubuntu server.
It made sense but I've now found his article and it says 'drives for staorage ould be ntfs' in so many words.
So which is it? If it's NTFS does that mean ubuntu is using the NTFS-3g project for writing? Although this seems very good writing  1-2 gb files might cause issues.
Here the link -  [http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

The only reference to ntfs I saw in that guide is
"This Home File Server ***can*** work with hard disks formatted in NTFS. So **when you need or want to move the hard disk into a new computer,** they are accessible by Windows and most Linux operating systems."
This has no bearing on accessing **shares** from Windows or Linux computers, because they'll access the shared files through smb, not ntfs or ext3 or whatever filesystem you want to use.

---

### Post by HermanAB on 2008-05-25
Samba translates the disk file system into a network file system.  I suggest that you use Ext3 or JFS on the disk since those are more efficient than NTFS.

---

### Post by garethsimpsonuk on 2008-05-25
Ok yea I ill go with ext3 i have a 500gb usb ntfs drive with a lot of important stuff on so is it ok to plug that in via usb and share it? the ide drives totalling around 300gb will be ext3 (what about 4, is it stable?)
It does say right at the start what I mentioned but the links down so I can't quote it. It's right at the beginning.
Thanks

---

### Post by jrusso2 on 2008-05-25
Personally I would not use EXT 3 for anything as it seems the most failure prone.  I have been using a combination of JFS and XFS lately with JFS for / and XFS for /Home.

---

### Post by koenn on 2008-05-25
> **garethsimpsonuk said:**
> 
It does say right at the start what I mentioned but the links down so I can't quote it. It's right at the beginning.
Thanks
The link in your post has a syntax error - you can see it in the code.
try this one : [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by garethsimpsonuk on 2008-05-25
oh yea lol not wiv it 2day, fixed it and yes you were koenn right, it doesn't say it should be in NTFS. 
JRusso2 the guides I've got say there isn't as much community support for JFS and it may not have a very long shelf life due to some legal issues, my server is just for my home office so I think ext3 will be ok. Plus it doesn't complicate things anymore for me lol. 
The only thing I hate about linux is the permission setup. If only there was a basic setting for a layman (i kno i kno, then it would be unsafe like windows). 
All I want to do is set up an account for each family member, and give them all there own space on disk which they can write to. Let everyone read my NTFS USB drive (but no write) Then create a separate group for full rights to business docs, which only me and another family member can write to.
Shall I do it with home directories? id prefer for them all to have an equal share on another disk away from the os.
Anyone wanna give me any pointers? I've bin messing about with all this for weeks now. (which aint a bad thing cos i've learnt loads) 
N e ways if anyones got a simplified way of doing all this i'd be grateful

cheers

---

### Post by articpenguin on 2008-05-26
how does jfs have legal issues? You are right about jfs not having community support. It is maintained by one guy who works on it part time.

---

### Post by windependence on 2008-05-26
> **jrusso2 said:**
> Personally I would not use EXT 3 for anything as it seems the most failure prone.  I have been using a combination of JFS and XFS lately with JFS for / and XFS for /Home.

This is YOUR experience not the experience of most users. Yes, XFS is faster on large files BUT it only saves metadata when journaling so it's actually not as safe as EXT3. YMMV.


-Tim

---

### Post by articpenguin on 2008-05-27
all the filesystems in linux by defualt journal metadata.

---

### Post by NateMan on 2008-05-27
Ntfs support in linux seems to work very well, but I personally used to share a 500gig ntfs drive over a linux server and it was nothing but problems (occasionally would loose connection and then have to be forced in a very rough way to unmount). It may be better by now, as that was some time ago. I would however try to figure a way to back up the 500gig and redo it as an ext3 drive. Ext3 has never given me so much as a hiccup so I would have to say it is very stable. I even use it on my 1.5TB raid5 array. I do believe if I was going larger than that I would use xfs.

---

### Post by garethsimpsonuk on 2008-05-27
Even though I don't wanna do it I think you're right. The drive sometimes comes with me to plug in other boxes (usually windoze) so I will have to sacrifice that feature (or maybe carry round an Ext3 driver for windoze, any ideas on one?)

---

### Post by NateMan on 2008-05-27
Yes there is a good ext3 driver for windows. I put a tiny vfat partition containing the driver on my external drive and used ext3 for everything else. Give me a sec and I'll find a link...

---

### Post by NateMan on 2008-05-27
And here is your link.... [http://www.fs-driver.org/](http://www.fs-driver.org/) Hope that will help you out.

---

### Post by garethsimpsonuk on 2008-05-27
Cheers I'll check it out

---

