---
title: "How would you go about saving and restoring your root directory?"
date: 2013-02-05
forum: Server Platforms
---

### Post by Roasted on 2013-02-05
I have Ubuntu Server 12.04.1 running. The OS is split up on a 500 GB HDD.

20 GB = /
Remainder = /media/primary_drive

I want to back up the root partition only. My intention is to capture that partition and have it be restore-able to another drive. 

Scenario 1 = Root HDD dies. Install a new HDD of any size that's larger than 20 GB, whether it be 40, 160, 320, 1 TB, etc. Restore the image, boot up, everything just works.

Scenario 2 = In time, I want to replace the HDD with an SSD. I want to install the SSD, restore the image, boot up, and everything just works.

I'm just a little unsure of how to go about this and what the best solution is. Some discussions with other users has kind of ruled out "DD" from the equation due to DD being block level, and my intention of someday going to an SSD kind of nullifies that. Is Clonezilla Live my best bet? Can CZ Live restore singular partitions (like / in my case) and bingo, it boots up fine? Or should I result to some sort of CLI command, like cp or tar?

Overall, just curious what you guys use and what you recommend. Need some more food choices on the table before I pick the main course.

---

### Post by TheFu on 2013-02-05
The file system used would impact which imaging tool was used.  EXT4 is not well supported.  Ext2 and EXt3 are well supported by partimage and will only store actual data. I've used dd and ddrescue more than a few times when moving to new HDDs, but with all the migrations from 512b sector disks to 4K sector disks, I don't see this as a viable option anymore.

OTOH, why use an image at all?  Use any backup tool and just exclude everything under /media from the backups.  I use **rdiff-backup**, but Deja-Dup, Duplicity, Duplicati, or even rsync can easily do what you need.  Automatic, versioned, backups are **critical for data security** even if you never lose any files.

Another alternative is not to bother backing up the OS and apps at all. Just backup the settings, data, and keep a record of the installed apps using **dpkg --get-selections > file.out**.  When you need to restore, install the base OS like normal, then use **dpkg --set-selections < file.out **torestore the apps.Simple.Image backups are for Windows, not Linux, IMHO.

---

### Post by Roasted on 2013-02-05
Thanks for the insight. I currently have my entire /etc directory getting tar'd nightly and backing up, since after all the vast majority of my configs exist there. Doing this just got me curious that it'd be nice to have a ready-to-go image to plop on a drive and get going in an instant if need be. I know what you're saying that imaging is typically a Windows thing, but if it can be done here, it would still undoubtedly be helpful.

---

### Post by TheFu on 2013-02-05
You can image any HDD using clonezilla or partimage. The compression will just be dumb, unlike with ext3 and ext2 where the compression will be file-system aware. Basically, dumb means every bit gets added to the image AND the restore since it uses `dd` internally.

We all need backups, so why not have backups be your normal recovery method?  Why have something "special" for some other reason?  Backups are extremely space and time efficient.  No reason to use** tar** anymore.

---

### Post by Roasted on 2013-02-05
What would you personally use for backups? I'm currently using rsync to synchronize raw data to another drive (external HDD). I'm actually prepping a Raspberry Pi now to be in another area of the house and run 24/7 to handle this job. That way my "backup" isn't directly attached to the server. This has always been my preferred method since rsync works beautifully to local USB drives or remote servers in the house/state/country. Plus it's relatively easy to whip up a bash script to run nightly via cron.

I understand the whole backup mentality and I understand that imaging may not always be the conventional backup method for Linux, but then this question comes to mind in which I'm curious what your answer would be. Let's say you want to do a drive migration, where you want your current server off of the current drive and installed to a new drive. How would you go about doing that? Just back up /var, /etc, and whatever else and then do a fresh OS install, then bring the configs back over?

Thanks for your insight!

---

### Post by TheFu on 2013-02-05
I use **rdiff-backup**.
I have restored using it multiple times.  Restored 1 file or entire OSes.

I've written about this on my blog.jdpfu.com multiple times, including techniques for non-full system backups (doing the settings and data only method).  I've used that too AND restored 100% successfully.

rsync is not usually the best tool for backups. It is a fine tool to mirror disks AFTER the file system has been built.  Again, why have 2 solutions - mirror and backup.  If you don't trust your backups that much, then you need a different backup method, right?

---

### Post by Roasted on 2013-02-05
I guess I'll have to do some reading on rdiff-backup. I'm not entirely sure why rsync wouldn't work if what I want is an identical copy of what's on the server vs my desktop. After all, rsync is crazy fast, and it sure does the job, hence why I never had a reason to look elsewhere. I'm reading through some documentation now so we'll see what we come up with. So far through a quick test I did here on my system I see that rdiff-backup creates a folder entitled rdiff-backup-data, which I assume is some sort of database related mapping files. We'll see what happens. Thanks for the insight!

EDIT - I'm seeing that rdiff-backup requires you to be root in order to retain permissions, whereas rsync can retain permissions via the -a flag, assuming you have ownership of the data. This could be a deal breaker, as I surely won't be doing any sort of backups as root on my client systems to my server. They run as regular users, or they don't run at all.

EDIT II - But then again, if the users have ownership of the data, would they not retain permissions by default? Or would that still require root?

---

### Post by TheFu on 2013-02-05
> **Roasted said:**
> I guess I'll have to do some reading on rdiff-backup. I'm not entirely sure why rsync wouldn't work if what I want is an identical copy of what's on the server vs my desktop. After all, rsync is crazy fast, and it sure does the job, hence why I never had a reason to look elsewhere. I'm reading through some documentation now so we'll see what we come up with. So far through a quick test I did here on my system I see that rdiff-backup creates a folder entitled rdiff-backup-data, which I assume is some sort of database related mapping files. We'll see what happens. Thanks for the insight!

EDIT - I'm seeing that rdiff-backup requires you to be root in order to retain permissions, whereas rsync can retain permissions via the -a flag, assuming you have ownership of the data. This could be a deal breaker, as I surely won't be doing any sort of backups as root on my client systems to my server. They run as regular users, or they don't run at all.

And my response:
> rsync is not usually the best tool for backups. It is a fine tool to  mirror disks AFTER the file system has been built.  Again, why have 2  solutions - mirror and backup.  If you don't trust your backups that  much, then you need a different backup method, right?

If you want to backup a complete system, then you must use root.  Normal users do not have permissions to read every file, period.  Heck, there are files under /etc/ that most users cannot read.  Further, you don't need the actual "root" account, but a "root-equivelant" is necessary.  That means any account with a uid of zero (0).  Further, if you need to automate this - and any backup that isn't automatic is a failure in my book - then you'll want to use ssh-key-based credentials.  The backup server should be very far from the internet and it should "pull" the backups from client machines. It also means that client machines do not need credentials to connect back to the backup server.

I've done backups and disaster recovery for a living for over a decade. There is not 1-size-fits all solution, but for a small office or home with fewer than 5 systems, the options I provided above blow away what a straight rsync provides.  Almost every backup tool on Linux will be based off librsync, so don't worry about efficiency of network or storage.

Lastly, I think you misread the rdiff-backup information. There are many complexities around permissions and rdiff-backup does handle those better than most other simple-to-restore-without-a-special-program choices.  TOH, rdiff-backup is not perfect.

---

### Post by Roasted on 2013-02-05
Ya know, I didn't even realize I was blurring the lines of different backup uses as I typed my response. To clear the air, this thread was created in an effort to see how I can back up my root directory of my server in an effort to port it to a different hard drive in the event the OS drive fails. But as I typed my response, I was already beginning to think about how I'd use rdiff-backup with the client systems, which currently rsync their home directory over SSH to their specified destination on my server, which is normally /media/storage/username. It was in THAT instance that I was like, whoa, root = bad news. But if they're rdiff'ing data they own, that kind of negates the root talk I would think.

I'll read into this a bit more. It certainly seems to have its purpose. I just need to do some testing and see how it operates to really get a grasp of it.

---

### Post by TheFu on 2013-02-05
> **Roasted said:**
> EDIT II - But then again, if the users have ownership of the data, would they not retain permissions by default? Or would that still require root?

I think you are confusing ownership and permissions.  Sometimes permissions **includes** ownership.  Please read some more.

rdiff-backup is not just a linux tool. You can store data from Linux on NTFS partitions too. Since NTFS doesn't support UNIX-style permissions, ... metadata needs to be stored.

If you think that using **rsync -p** will retain permissions (bits, owner and group) when run as a normal user and mirroring files owned by a different user, then I think you are confused. It cannot work that way.  rsync has other issues - like when the permissions bits change over time. How is that maintained?  It isn't .

Here is the rdiff-backup man page summary:
>  rdiff-backup is a script, written in python(1) that backs up one direc&#8208;
       tory  to  another.  The target directory ends up a copy (mirror) of the
       source directory, but extra reverse diffs are stored in a special  sub&#8208;
       directory of that target directory, so you can still recover files lost
       some time ago.  The idea is to combine the best features  of  a  mirror
       and  an incremental backup.  rdiff-backup also preserves symlinks, spe&#8208;
       cial files, hardlinks, permissions, uid/gid ownership, and modification
       times.
Seems like it handled everything you are concerned about to me.  Man pages are fantastic things.

---

### Post by Roasted on 2013-02-05
I understand. It's looking more and more like it would be a wise alternative. The more I read about it the more I get the backup vs mirror implementation. The only thing I'm a little gray on is the actual restore process yet. Perhaps you can correct me where I'm wrong, but in my little localized test, what I'm seeing is that rdiff-backup does a mirror for source to destination, but the contents of rdiff-backup-data is where the "backup" feature comes in, whereas it's otherwise just a mirror. Okay fine, I'm just trying to figure out the process behind restoring a file. 

Example...

HelloFriend.odt on desktop. rdiff-backup runs and synchronizes it to my server under /media/storage/jason. I open HelloFriend.odt on my desktop, select all, delete, save, and rdiff-backup runs again. The empty HelloFriend.odt is now on my server, BUT the older version containing text should be accessible... somewhere. A bit more reading and a few test drives and perhaps I'll swap it out tonight for the real deal.

---

### Post by Roasted on 2013-02-05
I tried to refrain from responding here, but after all of the Google links turned purple from searching and the man page began yielding no additional responses, here I am.

I've figured a lot out, as I understand now that I can restore specific incremental backups by specifying the particular backup found when I run rdiff-backup -l /path/to/backup/directory, then running rdiff-backup -r 2013-02-05T16:40:30 /path/to/backup/directory, for example. 

The part I'm lost at that's sending me into an absolute rage is the fact that I want to back up only specific directories. With rsync, I simply say:

rsync -a /home/jason/Documents /home/jason/Music /home/jason/Pictures /media/external_hdd, and presto, Documents, Music, and Pictures all sync to my external hard drive. But doing *that* with rdiff-backup is not clicking with me no matter how many times I read examples and directions. 

So, question: How exactly would one back up multiple directories? Let's say we're using the above example... Documents, Music, Pictures, and the backup destination is /media/external_hdd. What would I do?

EDIT - On top of that, I'm trying to do this over SSH. I'm getting the error that "Destination directory exists, but does not look like a rdiff-backup directory." If I use --force, it works, but the disclaimer saying that it could destroy the contents is sketchy. Eh?
CANCEL EDIT - I had a hidden file that was in that directory, so it wasn't 100% empty. Rdiff was warning me that I could damage that data by running the backup. Durp durp... (leaving this here for future users)


EDIT II - Some testing has kind of revealed exactly what I would have to do, but I'm left with one simple question. I created a list.txt file in /usr/local/bin, and then ran the following command:

rdiff-backup --include-filelist /usr/local/bin/list.txt --exclude '**' /home/jason /home/jason/destination

The contents of list.txt are:
/home/jason/source1
/home/jason/source2

It didn't take anything else in my home directory. Not music, pictures, documents, nothing. Just source1 and source2. This is good! This is what I wanted. So we're all good... however... it doesn't seem to be taking the CONTENTS of source1 and source2. It just takes the parent directories and that's it. On the flip side of the coin, if I do a regular rdiff-backup /home/jason/source1 /home/jason/destination, it works fine and takes the contents. It's something about this include file that isn't flying, and I can't crack it...

EDIT III - Seems as if I need to do --include-globbing-filelist, not just --include-filelist. Now it takes the contents. Nice! Some light reading indicated that globbing is a way of lumping together wildcards, or something of that nature. Sort of like this:

> 
For example, to list all the JPEG and GIF files that start with either "ab" or "def" you could do:

  $ ls +(ab|def)*+(.jpg|.gif)


Of course you could also do this without extended globbing:

  # ls ab*.jpg ab*.gif def*.jpg def*.gif

Source - [http://www.linuxjournal.com/content/bash-extended-globbing](http://www.linuxjournal.com/content/bash-extended-globbing)

The only other question I have is... if I want to do the --remove-older-than command, can I do that on one directory, or must it be done on all sub directories? Or should that be done on the client system?

Example - all backups are stored in /media/storage/user. Can I run rdiff-backup --remove-older-than 5D /media/storage and have it take care of fred/frank/bob/dave in one shot, or must I run them individually, like so:

rdiff-backup --remove-older-than 5D /media/storage/fred
rdiff-backup --remove-older-than 5D /media/storage/frank
rdiff-backup --remove-older-than 5D /media/storage/bob
rdiff-backup --remove-older-than 5D /media/storage/dave

OR, should I run it along with the client machine? Example:

rdiff-backup --include-globbing-list /usr/local/bin/includelist.txt /home/jason jason@192.168.1.10::/media/storage/jason
rdiff-backup --remove-older-than 5D jason@192.168.1.10::/media/storage/jason

---

