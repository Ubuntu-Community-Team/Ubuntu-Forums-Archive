---
title: "[SOLVED] How do I create a backup image of my server?"
date: 2007-12-02
forum: Server Platforms
---

### Post by Alt69 on 2007-12-02
Hi, now that I have a “working version” of my server, I would like to back it up. I am long time user of Nortons Ghost for my laptop. I like Ghost so much that I am holding off upgrading to their new “Go Back “ feature for as long as I can. It allows me to create a compressed image and I can generally have my laptop back up and running with everything on it, OS, patches, email, files, etc. in about 45 minutes. 

Is there something similar that I can do with Ubuntu that will allow me to save a working “snapshot” of my server? I know that as I as start to play with it, I will blow it up and don’t want to have to rebuild it from scratch again.  

If someone can point me in the direction of a method, utility out there can accomplish this, that would be much appreciated.

thanks

---

### Post by MJN on 2007-12-02
I've used [G4L]("http://sourceforge.net/projects/g4l") (*Ghost For Linux* ..) in the past and it seems to work well for exactly what you want to achieve. 

Since my server is now up-and-running I've moved towards more of a backup/recovery strategy and have changed to a higher filesystem-level way of working so there could well be better alternatives to G4L available now.

Mathew

---

### Post by Alt69 on 2007-12-02
Hi, if you don't mind me asking, what do mean by a higher filesystem and would you mind sharing your backup/recovery startegy?

Ideally, i would like to be able to backup the server without having to take it off-line, but not sure what options are out there and if the cost factor is an indicator of reliabliity.

---

### Post by pcormack on 2007-12-02
I have used Partimage in work and it is also very good.

More info: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by MJN on 2007-12-02
> **Alt69 said:**
> Hi, if you don't mind me asking, what do mean by a higher filesystem and would you mind sharing your backup/recovery startegy?

I meant I don't do a low level image backup but rather something that works at the filesystem level i.e. copies the files as-is to another location. This enables me to exclude certain bits from being backed up, pluck out individual files from the backup etc. It also means the backup exists in a format completely independent from the application that made it i.e. I could restore it using whatever tool may be appropriate for the circumstances at the time. There is also the possibly irrational comfort of me having the backup stored as as many pieces (files) as there are on the source - I would not sleep easy with my 'personal' files wrapped up in a single file - 'eggs in one basket' and all that.

I use rsync but there are a million-and-one equally good similar tools. The strategy itself is a relatively straightforward nightly/weekly/monthly backup to a remote USB drive (the weekly backup also being mirrored offsite). One of the reason I like rsync is it is equally suited to backing up locally as it is backing up over the Internet - and for both purposes it provides various optimisations (the most notable of which is only having to transfer the bits of the file(s) that have changed in order to stil create a full mirror at the other end).

I only mentioned it to explain why I am no longer using G4L - it's because my circumstances have changed as opposed to me disliking G4L (or that type of tool).

A filesystem-level backup strategy would probably not be the most suitable solution for you as, given a multi-partition setup, you would need to handle the creation/restoration of the partitions (and filesystems) separately before restoring your files back to them. It's doable of course but you can't beat whacking in a bootable image disc to get your machine back if you've meddled too much!

Mathew

---

### Post by Alt69 on 2007-12-02
Hi thanks for all the info. It looks like  I have some investigating ahead of me to find the right approach. 

I already have a SystemRestore CD with the Partimage on it, so I will test it out in the short term.

thanks again for the quick responses. 


cheers,

---

### Post by HermanAB on 2007-12-02
If you have a spare disk drive, plug it in and use dd to duplicate the first one.

Otherwise, use NFS to mount a drive on another machine and use rsync to periodically back up certain things.

---

### Post by Alt69 on 2007-12-18
Hi, I ended up uisng G4L to at least get a base image. Worked well. Of course I made some changes and restored from the newly created image just to make sure it worked.

Now I make changes, and lot at longer backup strategies.

thanks everyone for you suggestions.

cheers.

---

### Post by psusi on 2007-12-18
> **HermanAB said:**
> If you have a spare disk drive, plug it in and use dd to duplicate the first one.

Otherwise, use NFS to mount a drive on another machine and use rsync to periodically back up certain things.

You do NOT want to use dd because the backup drive will have to be at least as large as the source ( and any additional space is wasted ), and it will take AGES to complete as it will copy everything, including the free space.

Another advantage of using rsync or tar over a full system image is that you can do daily incremental backups that go quickly because only the changed files need backed up, and you can extract individual files from the backups rather than having to restore the entire thing in one go.

---

