---
title: "What online backup service do you use?"
date: 2014-12-14
forum: The Cafe
---

### Post by PartisanEntity on 2014-12-14
I would be interested to see what the most popular online backup services are for Ubuntu/Linux users.

Please feel free to add your recommendations if I have missed them in the poll.

If you do make a recommendation, please list no more than 5 reasons in bullet form as to why you think that service is great.

Thanks :)

---

### Post by /ADM on 2014-12-15
Spideroak

1. Client side encryption
2. Zero knowledge on the server's end
3. Windows, Mac, Linux clients
4. Easy to use and doesn't get in your face
5. It's just awesome :)

But I don't use it as a backup, I use it to store all files.  When I want something I download it, edit it and sync it back.  I only have a 32GB SSD for this reason.  My drive contains 'nothing'.  Except IntelliJ for Java stuff :)

---

### Post by linuxyogi on 2014-12-15
I use dropbox and spideroak. I prefer local backup instead of cloud coz my Internet connection is pretty slow. I have backedup up some important data to spideroak but the client is not even installed. I use dropbox mainly to sync the Keepass database between my tab and PC. Before choosing dropbox I tried btsync but I was facing all kinds of weird permission issues.

---

### Post by linuxyogi on 2014-12-15
@[**[COLOR=#000000]/ADM[/COLOR]**]("http://ubuntuforums.org/member.php?u=1926482")

The only thing that I don't like about Spideroak is the fact that it while linking it makes separate profiles each time. Meaning if you sync multiple devices each will have its own file/folder hierarchy. This seems very inconvenient to me.

---

### Post by /ADM on 2014-12-15
> **linuxyogi said:**
> @[**[COLOR=#000000]/ADM[/COLOR]**]("http://ubuntuforums.org/member.php?u=1926482")

The only thing that I don't like about Spideroak is the fact that it while linking it makes separate profiles each time. Meaning if you sync multiple devices each will have its own file/folder hierarchy. This seems very inconvenient to me.

For me this is a great thing.  I would hate to navigate a windows structure on Linux.

---

### Post by Mauricio_Prinzlau on 2014-12-15
Hey!


Good selection of providers in your poll. I think those are the most popular services online. However, not all of the provider listed above support Linux. Also it depends a lot on what you want to accomplish. As you specifically asked for online backup I would recommend CrashPlan. CrashPlan backs up very well and there are a lot of settings you can play around with. SpiderOak is a good solution if you also plan to sync your files across multiple devices. However I have heard that their backup is able slow. For the other providers I guess it will be difficult to find a client that runs on Linux.

---

### Post by mastablasta on 2014-12-15
> **linuxyogi said:**
> @[**[COLOR=#000000]/ADM[/COLOR]**]("http://ubuntuforums.org/member.php?u=1926482")

The only thing that I don't like about Spideroak is the fact that it while linking it makes separate profiles each time. Meaning if you sync multiple devices each will have its own file/folder hierarchy. This seems very inconvenient to me.

if you sync you put it in "the hive"

otherwise owncloud ftw. but I still thing it needs to be more secure and even easier to configure (e.g to use https by default and to offer client side encryption in an easy way). also annoying part is it is not ment as backup which means you need to tweak it or you another service pushing backup to your server (Adeca, luckybackup, rsync, rdiff...).

---

### Post by Dragonbite on 2014-12-15
I've been tempted to use Crashplan, and then thought of an idea of using (paying) for the 1 TB Dropbox account and carving out the first level of folders for each person in the family. Each person gets selective synching with their folder only, but also there is a server (with > 1 TB space) which synchronizes with the ENTIRE dropbox account so it backs up everybody's files.

This way 
[LIST=1]
[*]The 1 TB is shared (we're not really going to use that much for a while)
[*]Nobody has to be synchronized with anybody else's account (selective sync)
[*]There is a local copy in case of dropped Internet connection (server copy)
[*]Updated files could be pulled from the faster local server than the Internet (sync-over-lan)
[*]It is duplicated in the Cloud, in case of major disaster (dropbox.com account)
[*]Files could be accessible via the browser if necessary (dropbox.com) 
[*]Each person would have their files stored in 3 places : local system, server and cloud
[*]If Dropbox "poofs" out of existence then so long as it doesn't send the delete command, the files are not lost (just turn off Dropbox clients)
[/LIST]

It isn't ideal, I know, but does cover a lot of bases.  My problem is backing up Linux and Windows systems without having to do 2 different means.  Also, the important (wife's) Windows system is Windows Home, which means it cannot backup over the network which is why something with its own cross-platform client looks interesting.

Meanwhile, most of my stuff is synchronized with Copy (250GB for free) but I am still not 100% sure about them.

---

### Post by user1397 on 2014-12-15
i have dropbox, box.com, mega, and google drive.  don't really use any except google drive, and just for important document backups really.

---

### Post by Dragonbite on 2014-12-15
I was actually taking a moment to look at alternatives and if somebody could make a OneDrive client for Linux (maybe along the lines of Grive since Google is *cough* *cough* not coming out with something) then  I think that would be preferred because then files don't have to be converted to be able to edit them online (like when I am at work).

---

### Post by PartisanEntity on 2014-12-15
Thanks very much for all the feedback so far.

I would be interested in an online backup solution that offers affordable packages for high capacity users. I would need around 1TB.

Just out of interest, are any of Amazons products a viable option for something like this? They seem to have massive amounts of storage avaulable? I am just not sure if it is suited for home users?

---

### Post by user1397 on 2014-12-15
I'm curious OP, why did you not include other popular services like dropbox, google drive, onedrive, etc?  Or are the ones in the poll for another purpose than general cloud storage/backup?

A bit confused :(

---

### Post by PartisanEntity on 2014-12-16
> **ubuntuman001 said:**
> I'm curious OP, why did you not include other popular services like dropbox, google drive, onedrive, etc?  Or are the ones in the poll for another purpose than general cloud storage/backup?

A bit confused :(

I did not add them actually because I do not see them as dedicated backup services. I see the ones you listed as file syncing tools. I don't for example see a use case where I would backup 1TB snapshot of a machine to dropbox or google drive.

Are these services being used like that?

---

### Post by Dragonbite on 2014-12-16
> **PartisanEntity said:**
> I did not add them actually because I do not see them as dedicated backup services. I see the ones you listed as file syncing tools. I don't for example see a use case where I would backup 1TB snapshot of a machine to dropbox or google drive.

Are these services being used like that?
They aren't really backup devices. The file synchronization and cloud storage method is rife with potential issues (somebody breaks into your account and hits "delete", once you log in you find your files slowly disappearing, etc.).  Plus the cloud storage method does not protect against corrupt and infected files unless detected within the service's "rollback" period.

The list contains more "point in time" backups, where once you run the backup you have your files as they are in that point in time.  

The advantage of this is you may be able to use incremental backups and store multiple versions of a file in case you accidentally overwrote your file by saving another with the same name an absent-minded clicking "yes" to overwriting the file.  Once the computer synchronizes, it is now gone.  With point-in-time backups you could possibly revert to a time before you goofed!

I forgot to add to my TB Dropbox concept having another server and drive and run a point-in-time backup copying the contents from the Dropbox-attached director to another drive. 

I have only been adverse against the point-in-time backups because I don't know how to restore, in all honesty, and how much it reverts or destroys in the process.

---

### Post by Mike_Walsh on 2014-12-17
I'm like linuxyogi; I prefer local backup (a 1 TB Seagate USB 'Expansion' external HDD), although I do use Google's 'Drive', which I access either through the browser or the Ubuntu 'Grive' client. This is more for file syncing, so that when I visit any family, or mates, I can pull up anything I specifically want to share.

Regards,

Mike.

---

### Post by kevdog on 2014-12-19
Why specifically do you need an online solution?  Why not run a homespun computer with ssh where you could back up things for example like rsync?  I know this seems very low tech, but its platform independent.  Other important documents and things you could use dropbox, Google drive, etc.

---

### Post by Dragonbite on 2014-12-19
> **kevdog said:**
> Why specifically do you need an online solution?  Why not run a homespun computer with ssh where you could back up things for example like rsync?  I know this seems very low tech, but its platform independent.  Other important documents and things you could use dropbox, Google drive, etc.

Biggest advantage of online backups is in case of catastrophic disasters (flooding, house fires, nuclear explosion, etc.).

I like the idea of local AND online, so if something happens to the online service you have the local available, and if something mentioned above happens (god forbid) then there is the online version you can recover from.

---

### Post by PartisanEntity on 2014-12-20
> **Dragonbite said:**
> Biggest advantage of online backups is in case of catastrophic disasters (flooding, house fires, nuclear explosion, etc.).

I like the idea of local AND online, so if something happens to the online service you have the local available, and if something mentioned above happens (god forbid) then there is the online version you can recover from.

Yup that is the reason why I am looking into online backups. Just in case (God forbid) something happens here at home.

I currently have a home server that the other machines in the house backup to. But I would like an online and offsite backup for the server itself.

My current setup is as follows:

Machine1 & Machine2 -> home server (RAID10) -> external usb drive

And what I would like is: 

Machine1 & Machine2 -> home server (RAID10) -> (external usb drive) & (online, offsite and encrypted backup)

At the moment I am leaning towards trying Crashplan because they are the only ones it seems who do not charge for a set amount of space, and I need something in excess of about 800GB.

---

### Post by kevdog on 2014-12-20
I looked into Crashplan last night.  Tell me if I'm wrong - but this just work with a folder sync -- correct?

I personally seem to be more interested in a remote backup server offering rsync, ssh capabilities.  I admit the one's I looked at all were a set fee per month with the fee proportional to the amount of storage space you need.  One program I'm really interested in using is called obnam.  Obnam is capable of performing point in time backups and restoring individual files from any point in time or just restoring the entire collection.  It works with sftp.  The files to be backed up and the repository can be on different computers from the computer running the obnam executable -- both the source and destination files can be accessed via sftp.  In addition all the files can be stored encrypted using gpg as the backend.  The remote repository can be mounted as a local drive so files can be viewed.  This functionality works even with an encrypted archive where the files are mounted and keep read as if they were unencrypted.  A simple cp command can then be used to pick individual files out of the archive if only wanting to get older versions of files.  The mounting process uses fuse utility -- which unfortunately is sometimes buggy but seems not be a major negative.  

I'm curious to any other providers you may know of providing off-site backup with ssh,rsync access.

---

### Post by PartisanEntity on 2014-12-20
> **kevdog said:**
> I looked into Crashplan last night.  Tell me if I'm wrong - but this just work with a folder sync -- correct?

I have not looked in detail at Crashplan, but as far as I know, syncing between machines is one of the features they offer among others.

Spideroak does the same, and subjectively seems to have a more robust security and privacy minded setup but at the moment they offer $10/month for 100GB with $10 more for each 100GB. Spideroak might be the safer option now that I think about it, and in such a case I would select out of 800GB just about 100GB of files and folders that I feel are a priority to backup.

As an altnerative, I wonder if Amazon S3 Storage would be something worth it? If one could set up rsync to sync files to an Amazon bucket?

---

### Post by rewyllys on 2014-12-21
I'm now in the 3rd year of using CrashPlan to backup my Linux desktop and my wife's Windows 7 desktop.  

CrashPlan handles both OSes very nicely, is very user-friendly, and charges a reasonable amount for the 2TB of storage that our two systems require for backup.

I've restored files perhaps 10 times during our 2+ years with CrashPlan, and in every case the restoration was easy and quick (the speed being helped by the fact that our ISP, Grande Communications, has since last February provided us with 1 gigabit/second service).

---

### Post by Andika_Demas_Riyan on 2014-12-23
crashplan seems good to me.. but i rather prefer offline backup.. well i understand of the disaster probability mentioned by OP, but i think we still need offline backup no matter what.

---

### Post by rewyllys on 2014-12-23
> **Andika_Demas_Riyan said:**
> crashplan seems good to me.. but i rather prefer offline backup.. well i understand of the disaster probability mentioned by OP, but i think we still need offline backup no matter what.
I agree with you, and I also use LuckyBackup to keep a daily synchronized backup to my desktop.

Also, one of the options offered by CrashPlan is to maintain the backup of your files on the computer of a relative or friend of yours whom you trust completely.

---

### Post by michael-piziak on 2014-12-23
Great post.

If users could also comment on whether or not there are any free high storage online backup websites, that would be much appreciated.
Seems like most allow 5 GB or so for free.
Update:  I'm looking at "Adrive" now - it has 50 GB for free.  Downside is the free account is not encrypted.
Update 2:  Adrive.com wouldn't recognize my Java in 2 different browsers, but it did allow me to use a non-Java upload option.
                I'm sending 25 GB to it now.  Another downside is that it is very slow (about 240 KiB/second).  Also, it forced me to select files, not a folder.
Update 3:  I canceled the upload.  Takes way too long.  One would have to do this overnight as they slept.

---

### Post by sffvba[e0rt on 2014-12-25
I use Dropbox, Mega and Spideroak (got unlimited for $150 a year) :D

---

### Post by LiberaTek on 2014-12-25
I use mainly Dropbox and Mega, but I've been more inclined to Mega lately because of its security features and free space offered.

---

### Post by mikodo on 2014-12-28
I don't use an online backup service, but I have been reading about this one:

[rsync.net]("http://www.rsync.net/products/index.html")

Maybe someday, with a [OpenSSH Server]("https://help.ubuntu.com/lts/serverguide/openssh-server.html") ...

edit: I am thinking of just a small amount of backed up data though. Maybe, just 2 GB. Large volumes of data would be pricey.

---

### Post by Kurt_Alan on 2015-01-05
Some years ago I used Mozy for a couple of years until I learned their dirty secret.  One day I chose to create a physically separate backup to an external hard drive utilizing Mozy. I thought I'd then lock up that drive in my file cabinet.  That's when I discovered that if the Mozy software does not perceive a dynamic connection to the storage drive, that a countdown of 30 days will begin before the data is permanently wiped from the Mozy servers while I am still paying monthly for my account.  What The Heck? <------Polite.  So I quit them.

Then I discovered the difference between dynamic storage (e.g. Carbonite) and static storage (e.g. Dropbox). I now only use static storage X three sets: Dropbox, Google Drive, external hard drive.  All locations maintain the same data set.

Everything that is time constrained I simply place in folders and date.

---

### Post by Sasha_Aderolop on 2015-01-06
Currently, I'm a Backblaze subscriber. Personally, I find Backblaze easiest to use, quicker to back up, and less of a hog on my computer's resource than other services.

---

### Post by mastablasta on 2015-01-07
does mega have any client? or still only web based?

---

### Post by Dragonbite on 2015-01-07
> **mastablasta said:**
> does mega have any client? or still only web based?

Looks like there is a Linux client sync program [https://mega.co.nz/#sync]("https://mega.co.nz/#sync")

If you use that, can you let me know how "heavy" the client is?  I'm trying to find which clients synchronize the easiest, without taking a lot of resources constantly checking, scanning and indexing.

---

### Post by Habitual on 2015-01-07
S3

---

### Post by jacob55 on 2015-01-08
I mainly use [CloudBacko Pro]("http://www.cloudbacko.com"). It is best backup solution for backing up Microsoft exchange server, VM-ware, Hyper-V, lotus notes, oracle database, MySQL, Window system and many more. You can also check this software for backup.

---

### Post by PartisanEntity on 2015-01-08
> **Habitual said:**
> S3

That sounds interesting, can you elaborate a little. What setup do you have? Also if you don't mind me asking, what price range is Amazon S3?

---

### Post by Habitual on 2015-01-08
> **PartisanEntity said:**
> That sounds interesting, can you elaborate a little. What setup do you have? Also if you don't mind me asking, what price range is Amazon S3?

Sure, I use the s3cmd (in the repos) to mount my s3 buckets
[URL="http://aws.amazon.com/s3/pricing/"]Pricing
[/URL][Getting Started With Amazon S3]("http://aws.amazon.com/s3/getting-started/")

Edit: The free Tier is good for 1 year but has some limitations on storage (I think it's 20G) See the DOCs.

Hope that helps.

---

### Post by PartisanEntity on 2015-01-10
> **Habitual said:**
> Sure, I use the s3cmd (in the repos) to mount my s3 buckets
[URL="http://aws.amazon.com/s3/pricing/"]Pricing
[/URL][Getting Started With Amazon S3]("http://aws.amazon.com/s3/getting-started/")

Edit: The free Tier is good for 1 year but has some limitations on storage (I think it's 20G) See the DOCs.

Hope that helps.

Thanks very much for your reply, do you encrypt locally before you upload any of your backups?

Theoretically I could use built-in backup feature in Ubuntu and point to an S3 bucket?

If I am not mistaken, Amazon charges you separately for both uploading and downloading, correct? The reason I ask, is because optimally I would want to backup about 800GB of data (several computers plus several snapshots). I can imagine that this will become quite pricey.

---

### Post by mikodo on 2015-01-10
I want to thank PartisanEntity, for starting this thread. It has prompted me to look into different online backups, (which I never have done).

In the next month with my rebuilt computer, I want to back up my mission critical stuff with [Tarsnap]("https://www.tarsnap.com/"). Then, I can do incremental backups daily, as need be.

I have ordered portable drives to use to save my media stuff away from home, for disaster recovery of the rest.

---

### Post by Habitual on 2015-01-12
> **PartisanEntity said:**
> do you encrypt locally before you upload any of your backups?I do not.

[QUOTE=PartisanEntity]Theoretically I could use built-in backup feature in Ubuntu and point to an S3 bucket?[/QUOTE] I guess? There are lots of s3-aware client packages out there, some provide nice GUIs. 

[QUOTE=PartisanEntity]If I am not mistaken, Amazon charges you separately for both uploading and downloading, correct? The reason I ask, is because optimally I would want to backup about 800GB of data (several computers plus several snapshots). I can imagine that this will become quite pricey.[/QUOTE] Only if coming in from a different region. See the Billing section of the [FAQ]("http://aws.amazon.com/s3/faqs/#billing_anchor")
"Some prices vary across Amazon S3 Regions and are based on the location of your bucket". US-EAST is the most economical.
I use the ec2-create-snapshot utility provided by the [API tools]("http://docs.aws.amazon.com/AWSEC2/latest/CommandLineReference/command-reference.html"). These snapshots are created in the same region so there is no charge for data in or out for this procedure.

Hope that helps.

---

