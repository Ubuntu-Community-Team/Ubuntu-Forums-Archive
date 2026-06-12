---
title: "[SOLVED] Partitioning the server - need help with all this space!"
date: 2008-04-16
forum: Server Platforms
---

### Post by garfonzo on 2008-04-16
Hiya,

I'm going to be setting up a Ubuntu server in the next few weeks and I'm trying to decide how to partition the whole thing. The purpose of the server is for my household LAN. 

These are the comps:
1 Desktop - Ubuntu
1 Laptop - WinXP
1 iBook - OSX (maybe)
1 Desktop - WinXP (maybe)

- [COLOR="Red"]I'm reasonably convinced to not do this --> [/COLOR]Was considering mapping each comp's 'home' or 'My Documents' folder on the server, not locally for data security. 
- I want a large partition for misc. files and media (pics, music, movies) that everyone can read/write.
- I want to back up all files on the server with rsync.

Now, this is what the server has:
- One 20GB ide hard drive 
- One 320 GB ide hard drive
- One 320 GB ide hard drive in a USB enclosure.

So I'm not sure exaclty how to partition everything (I know it is somewhat subjective) but was looking for advice/tips. I was thinking that the USB hard drive could be used only for backups (sort of mirror the internal 320 with rsync). So, how would you partition this and with what type (ext3, NTFS,??)?

Thoughts?
Tips?
Should I really map "Home folders" / "My Docs" to the server?[COLOR="Red"] <-- Probably not[/COLOR]


Cheers,

Garfonzo

---

### Post by chewearn on 2008-04-16
I would like to address a single part of your post only.  At work, I used to carry a laptop with "My Documents" folder mapped to a network drive.

It's a *pita* because:

1. the network drive was not 100% up time, so occasionally you can't find your data when you most need it.

2. if I'm not in the office and can't connect to the office network, I loose access to "My Documents".  I have to always remember to make a local copy of my files before carrying the laptop outside.

3. some applications will lock-up when I access the "Open" dialog; sometimes, windows explorer crashed.

I presumed mapping linux home directory to the network might have similar issues.

---

### Post by garfonzo on 2008-04-16
> **AstalaVista said:**
> I would like to address a single part of your post only.  At work, I used to carry a laptop with "My Documents" folder mapped to a network drive.

It's a *pita* because: 

I'm not really sure what a pita is (outside of the ones I eat ;))...but I get your point. Those are all worries I had, actually. The other thing I was thinking of doing was just setting up a scheduled backup system where the server rsynced all files from each computer's 'home' directory to the server as a backup. Then the frustrations you mentioned are no longer. Thanks for the tip!

Anyone have ideas for the partitioning part?

---

### Post by ginge6000 on 2008-04-16
Surely if you have My Documents on a network drive you can make the folder available offline if you're using a laptop?  Then you will have them all the time.  Also it depends on the quality of your LAN as to whether things are likely to hang.

---

### Post by garfonzo on 2008-04-16
I did some hunting around the forums and found [[COLOR="RoyalBlue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=756192&highlight=partition&page=2") which has some tips on partitioning a 20GB hard drive for the OS with the second drive for /home.

What if I do as has been suggested in that thread:
20GB hd0:
18GB = / 
2GB = swap

320GB hd1:
Full Disk = /home

320GB hd3 (external HD):
Full Disk = ??? (rsync backup drive)

So lets say I set it up like above, if I want to make a directory that is for all users to store music, pics, and movies in (read/write access for all) where would that directory go? It doesn't seem right that it would go inside the /home directory does it? 

I guess what I'm asking is, where in the file system do I put miscellaneous directories that all users can access? Should I make a pretend user whose /home directory only has directories intended for network sharing?

---

### Post by tcpankon on 2008-04-16
My advice would be to take the 20Gig drive and partition as follows:

```

7Gig / parition
2 Gig /var parition
1 Gig Swap
10Gig /home

```

Explanation:  You really shouldn't need more than 5 Gig in your / partition the only thing that should be stored here is various config files.

I would use /home exclusively for user specific docs...keep all your large file collections (music,movies,etc) separate

keeping /var separate will prevent a log file from getting out of hand and filling your / partition.  There can be serious problems if your / partition fills up completely, specifically you may run into a problem of not being able to boot the system.

For the second disk (320Gig)
Use the entire partition as a ext3 partition mounted to /mnt/data.  Create subdirs under this mount point for music, movies, etc

I would then change ownership of the /mnt/data directory to something owned by your user with a users group that contains all of the users you want to have read/write perms.

Example: 
```

sudo chown bob:users /mnt/data -R
sudo chmod 775 /mnt/data -R

the edit /etc/group and add a 'users' group that has all the users you want to have read/write permissions

``` 

You could also split up the 320Gig between home and your data, but that is all personal preference.

Hope that helps

---

### Post by garfonzo on 2008-04-16
> **tcpankon said:**
> My advice would be to take the 20Gig drive and partition as follows:

```

7Gig / parition
2 Gig /var parition
1 Gig Swap
10Gig /home

```


Given that this will be a server, is there any reason to have a /home much larger than, say, 1GB? Really, no users will be logging in and saving files to the server in their home directory. All files saved by a user onto the server will be somewhere in the "Media" directory, not a home directory. For that matter, what will be in the /home directory since this is a server (I know it needs to be there, but for what?)?

> **tcpankon said:**
> 
I would use /home exclusively for user specific docs...

You mean files a user would want to save for themselves or user specific config files?

> **tcpankon said:**
> 
For the second disk (320Gig)
Use the entire partition as a ext3 partition mounted to /mnt/data.  Create subdirs under this mount point for music, movies, etc


So a second hard drive inside the comp (not an external USB one) is normally located in /mnt ? (It’s been a while since I’ve worked with Linux)

> **tcpankon said:**
> Hope that helps

It helps a lot! Thanks!

---

### Post by tcpankon on 2008-04-16
> **garfonzo said:**
> Given that this will be a server, is there any reason to have a /home much larger than, say, 1GB? Really, no users will be logging in and saving files to the server in their home directory. All files saved by a user onto the server will be somewhere in the "Media" directory, not a home directory. For that matter, what will be in the /home directory since this is a server (I know it needs to be there, but for what?)?  

If it is strictly a file server and you want everyone to save to the "Media" directory, then I would say that no, there is no real reason to worry about creating a /home partition.  it's useful on a desktop install since you can reinstall the OS and keep all of your desktop settings since they are stored in /home.

So if you feel you don't need a home partition, and depending on how much RAM you have, do a Gig of swap, 2 at max. a 2 Gig /var partition and the rest to /.

> 
You mean files a user would want to save for themselves or user specific config files?

I was referring to a file a user would want for themselve, word docs, or whatever.


> 
So a second hard drive inside the comp (not an external USB one) is normally located in /mnt ? (It’s been a while since I’ve worked with Linux)


It can go anywhere you want to put it, you simply need to create the directory for it to be mounted to.  For example you could mkdir /data and do a 

```

mkdir /data
chown bob:users /data -R
chmod 775 /data -R
mount /dev/sdb1 /data.
``` 

That will create a /data directory, change your user to the owner with rwxrwxr-x permissions, and finally mount the first slice of your second sata disk to /data

 Just make sure you don't try to mount it over a directory that is used :)


> 

It helps a lot! Thanks!

No Problem

---

### Post by garfonzo on 2008-04-16
> **tcpankon said:**
> 
[the second hard drive] can go anywhere you want to put it, you simply need to create the directory for it to be mounted to.

Interesting. So, I can set it up like so:

2GB = /swap
2GB = /var
1GB = /home
Rest = / 


Then, just make a directory in / called "Media" and another called "Backup" or something, and just mount the 320GB internal and 320GB external hard drives to those directories? Then, for all intensive purposes, it will be as if the two drives are each just another directory within the file system? 

I guess I was confused/worried about how to "attach" the other two bigger drives to the OS so they would all play nice. I like the 'slickness' of having the drives mounted to a directory. I suppose, however, that I'll need to create a script that is run on start-up so that the "media" and "backup" drives are mounted at boot, or does the OS take care of that automatically?

I'm slowly remembering why I liked Linux.

---

### Post by tcpankon on 2008-04-16
You will have to add a line into /etc/fstab to mount the drive on boot, fairly straightforward

```

/dev/sdb1        /data           ext3       defaults         0        2

```

Again, i wouldn't even bother creating a separate /home partition.  put that extra 1Gig in your /var or / partition.  It will by default create a /home directory, it will just be part of the root filesystem.

And yes, each disk will just look like another directory in the filesystem.

Hope that helps clear it up

---

### Post by garfonzo on 2008-04-16
Yes that does clear it up. That was exactly the info I was looking for. 

Cheers!

Garfonzo
:)

---

