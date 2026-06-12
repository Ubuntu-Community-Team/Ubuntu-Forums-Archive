---
title: "Server Hard Drive Setup"
date: 2008-10-06
forum: Server Platforms
---

### Post by Lul2x on 2008-10-06
Hi, I currently have a 80GB hdd in my computer. I want to install Ubuntu server on it and later add two 750GB drives setup in software RAID 1. 

I was thinking of  storing all the files for my webserver on my 80GB drive with daily backups to the RAID drives and use the two 750GB drives for file storage and sharing among my other network computers. Does this sound good or would you guys suggest a better setup?

If anyone could lead me to a tutorial explaining how to add software RAID after ubuntu has been installed, that would be great. Thank you!!

---

### Post by Masuran on 2008-10-06
I would create my /var, /home, /usr and /tmp partitions on the first 750Gb drive and enable raid1 mirroring to the second 750Gb drive. Create your / partition on the 80Gb drive and mount your partitions as needed. 

When creating your /var on the first 750Gb disk, you don't need to make daily backups. The raid setup will make sure you don't loose any data. 

A HOWTO on software raid [can be found here]("http://tldp.org/HOWTO/Software-RAID-HOWTO.html").

---

### Post by Lul2x on 2008-10-06
Thanks for the input. I take it this would require me to have all three drives at the time of install. Unfortunately I only have the 80GB drive at the moment and will be getting the 750GB drives in a couple weeks. Is there anyway to install ubuntu on the one drive first and get my webserver setup and then add the other two later? Or is this just not practical?

Thanks.

---

### Post by lykwydchykyn on 2008-10-06
> **Lul2x said:**
>  Is there anyway to install ubuntu on the one drive first and get my webserver setup and then add the other two later? Or is this just not practical?

Thanks.

Absolutely; I would probably do it the way you described, but really there are some other things to think about:

 - How many users are going to be accessing this system?  If you have multiple users, and you want their data separate, then it makes the most sense to mount your raid volumes at /home and just use standard home directories for sharing.  If it's just you, you might want to mount them at /srv instead for your web and other data directories.

 - How much data do you have initially?  Is it going to be impractical to move it later?
 
 - Is this a multipurpose setup or just for your web server?

Basically, the reasons you want to partition are:
 
 - To put hard limits on the growth of a file system (to keep users from tanking the whole OS, for instance)
 - To add security (you can add flags like nosuid or noexec to user data filesystems to keep malicious scripts from being executed)
 - To use a different filesystem format for different areas (reiserfs or jfs might be more appropriate to a certain application than ext3)
 - To keep data distinct from system files, so for example if you want to upgrade or migrate to a different distro without destroying your current install, you can use the same data partitions while adding a new system partition.
 - To keep related files from getting too spread out on the disk.

I've never honestly felt the need to break a hard drive into more than /home and /var or maybe /srv, depending on the application.  But I'm not a master UNIX admin either.

---

### Post by Lul2x on 2008-10-07
Wow, that`s a lot to think about...

The purpose of the server is to:
1) host my personal website/blog
2) act as a file server where I can store documents, pictures, music, movies, etc
3) act as a print server

For the most part, it will just be me accessing the server. On occasion, I may have others in the house connecting to watch a movie or listen to music, but they will not be storing files on it. Am I able to limit their permissions for certain directories of mine without having to give them their own user account? And, will this influence how I set up my partitions? They will be connecting from Windows machines.

I appreciate the help as I`m pretty new at this. Thanks again!

---

### Post by lykwydchykyn on 2008-10-07
Generally speaking, a website and blog don't take up much space.  Unless you're dishing out huge media files or something, you probably won't need more than a few hundred MB for a website tops (that's assuming lots of pictures).  So I would reserve your 750's for personal files.  You can set pretty specific read/write permissions on any directory, you don't need to worry about partition structure for that.

---

### Post by Lul2x on 2008-10-07
Thanks.

I've done some more reading and it seems I was mistaken to want to use RAID as a backup method. Instead, I think I will do this setup:

-because I am not receiving my 750GB drive for a couple weeks and I really want to install Ubuntu now, I will setup the OS on a 500GB drive that I have first, and then move /home to the 750GB drive later (now I'm only getting one 750 hdd).

-once my personal files are moved to the 750GB drive, I will use the 500GB drive for backup of my important files (both from the 750GB drive and local network computers). I know it is not the best idea to store backup on the same computer, but I just don't have another one around with the storage capacity (and I decided to setup this server so I wouldn't need a NAS box.)

-I have always stored my webserver files in /home/me/server. Are there any potential problems with this. If so, where should I put it?

What do you guys think of this setup? Any input is appreciated. Thanks.

---

### Post by lykwydchykyn on 2008-10-07
You have a lot of big hard drives laying around, why not invest $20 - $50 or so on a USB or NAS enclosure for one of them, and back up to that?

RAID is not so much a backup strategy in my mind as it is a high-availability thing.  I guess in certain conditions a mirrored drive will protect you if you have a drive go bad out of the blue.  But it doesn't help you if you get hacked, or some incompetent user deletes everything, or if your box gets zapped by lightening and goes belly up.  Backing up to a separate device at regular intervals does give you this.

As for your files location, it doesn't really matter.  Putting them in /srv is a convention of sorts, though ubuntu defaults to /var/www for some reason (see [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)).  I have put them in /home before, just to consolidate data in one directory/partition.  I never saw the reasoning behind putting in in /var, personally.

As for you proposed setup, it makes me want to cry to think you're going to use a 500 GB drive for the root.  10GB is more space than any server's root directory will ever dream of using.  If it were me, I'd stick the smallest reliable drive I have in there for the root fs, then save the big drives for backups or a rainy day.

---

### Post by Lul2x on 2008-10-07
Alright. With consideration to all your suggestions and given the hard drives that I have right now, I have made my decision!

I am going to install ubuntu server on my 80GB. Initially, /home will be located there as a separate partition simply because I don`t have my 750GB drive yet. I will move it to the larger drive later using this tutorial -- [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I will then connect a 500GB drive via an external enclosure. This is where all my backups will go.

The only annoyance is what to do with the remainder of the 80GB once I move /home to the 750GB drive. It would be nice if I could span /home across the two drives, but from what I`ve read this isn`t easily done. I`m sure I`ll think of something.

What do you think of the final setup?

---

### Post by lykwydchykyn on 2008-10-08
Sounds like what I'd do.  If you have other Ubuntu computers on the network, you can always use some of that 80 GB to create a local apt mirror.  That will save you some network bandwidth and speed up updates.  Just an idea.

---

### Post by Lul2x on 2008-10-08
Wow, it turns out that the drive I thought was an 80GB was actually 200GB :). With it being in my server for so long, I never really checked much!

More good news; I've installed ubuntu server with LAMP and have my website back up and running already (with the exception of my gallery, but I think it should be wrinkled out soon)!

I don't have anymore ubuntu boxes, but I'm sure I'll find a use for this extra space. I can't wait to get SAMBA going!!

Thanks for all your input lykwydchykyn.

---

