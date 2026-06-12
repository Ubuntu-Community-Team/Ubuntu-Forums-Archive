---
title: "Best way to share docs between desktop and laptop?"
date: 2019-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2019-10-24
I'm curious what others do. I'm not crazy about using a service like Dropbox or Google Drive because of security concerns so I still just copy and carry what I need on a flash drive. I also carry only what I need so very little (if any) sensitive info is in danger of theft or loss, and I'm especially cautious when I must use public wifi (going as far as switching off Bluetooth altogether). As I said I'm just curious what others do. Sometimes new tricks are the best tricks :D

---

### Post by Bashing-om on 2019-10-24
kansasnoob; Hey -

I am aware of some old tricks:
Have you seen:
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

SimpleHTTPServer for in-house works a treat :)

[INDENT][INDENT]more ways to skin a cat
[/INDENT][/INDENT]

---

### Post by uRock on 2019-10-25
At home, it depends on the file size. I usually use SFTP for small files, but a USB drive for anything large or needed outside the LAN.

---

### Post by sdsurfer on 2019-10-25
I use samba and local networking for all local file transfers. I can connect to our Windows network computers as well as the desktop and laptop, both on Ubuntu 18.04. The windows computers can log on to shared Ubuntu directories as well.

---

### Post by TheFu on 2019-10-25
NFS on the same LAN, though I use rsync and Nextcloud that way sometimes.  Also use Plex, Calibre for the stuff they do well.

Off the LAN, over the internet, there are many, many, different solutions. I use most of them.[LIST]
[*]rsync
[*]scp/sftp
[*]sshfs
[*]NextCloud files/audio/video/photos
[*]Plex Server for media / audio/video/photos (using ssh SOCKS proxy; no plex account needed)
[*]Calibre Server for ebooks
[/LIST]

For nextcloud to be accessible, I require either an ssh SOCKS proxy or full VPN connection.  On a laptop running Linux, the SOCKS proxy is much easier.  For android devices, the full VPN is easier.  I barely use nextcloud for file stuff.  It is too heavy and too slow for my purposes.  I like knowing that files are actively being transferred and have a reasonable time for when that will complete.  Nextcloud could work if I left my android devices in sync mode overnight, I suppose.

For media files on the LAN, I usually use a DLNA client that can 'download' the files.  My portable devices are never considered system-of-record storage.  

Nothing on any portable device is important, nor is it unencrypted.  IMHO, all portable devices need strong encryption.  I came to that choice after seeing a friend have 2 unlocked, no-password-needed smartphones stolen in 2 days on a trip to Europe.

To have off-line reading materials, I use something called wallabag. It is like a read-it-later webapp which a browser addon can sent to and grab a story for reading later, removing all the cruft.  Then there is an android client that can sync all the stories down for reading on trips or in waiting rooms.  Mark a story as read or deleted and the next sync will do the same on the server.  It is very handy.  I don't allow the wallabag server to be accessed over the internet ... without a ssh SOCKS proxy or full VPN.

About 95% of the time, I use rsync if NFS isn't available and sometimes I'll use rsync over NFS mounts.

If you have openssh-server setup on the "server", then any Linux client can use the default filemanager on that machine and use a URL like "sftp://{hostname.local}" to access the file system on the server with drag-n-drop. So, my hadar server would be accessed using sftp://hadar.local .... this makes all sorts of assumptions about avahi working.  You can always use the IP address in the URL.   Also, any ssh-keys will be used, if they are available, so you won't be asked for a password except to unlock the key.  And ssh when used with keys is considered secure enough for use over the internet.  2 minutes to setup, 10 yrs of better security and convenience.  ssh keys need to be replaced from time to time.
If it isn't obvious, ssh-keys work for any ssh-based connection, so ssh, sftp, scp, rsync, x2go, sshfs, and probably 50 others.  vim can use rsync:// URLs to remotely edit files ... which uses ssh, so ssh-keys would be used.

ssh is how Unix systems communicate.  Mastering the use of ssh-keys is a basic skill in the networked world, IMHO.

sshfs is a special-use tool for me.  Suppose I've been working on a script on a machine that has hundreds of module dependencies. If the data files for that script are on another machine and the storage isn't NFS shared, then I'll mount using sshfs and run the scripts.  Sometimes setting up the needed tools on the other systems is just too much hassle, so sshfs to the rescue.   sshfs is slow, so it works for data and audio files, but definitely not for video. It is handy when working in a public library, to stream house music, for example.   I'll also use it at the local LUG meetings to show some of the lesser known capabilities of ssh to newer members.  Freaks them out a little.

---

### Post by oldfred on 2019-10-25
I swiched to NFS for internal transfers PC to PC.
I use flash drives for transfers remote locations, and multiple copies as backups.

I used to use laptop with XP. It seemed every Windows update and back then I did not use LTS, so every 6 month update to Ubuntu, I had to reconfigure Samba.
So I installed Ubuntu on laptop & started using LTS versions as main working install and have as part of my install scripts set up of NFS. And then a script to mount NFS paths & rsync data. 

Some have said SSH would be easier for occasional use.
[https://ubuntuforums.org/showthread.php?t=2326477&p=13498242#post13498242](https://ubuntuforums.org/showthread.php?t=2326477&p=13498242#post13498242)

---

### Post by SeijiSensei on 2019-10-25
> **kansasnoob said:**
> I'm curious what others do. I'm not crazy about using a service like Dropbox or Google Drive because of security concerns so I still just copy and carry what I need on a flash drive.
Have you considered renting a VM in the cloud that you can control?  Linodes start at just [$5/month]("https://www.linode.com/pricing/").

Flash drives are still a good solution though.

---

### Post by zimbuf on 2019-10-26
I have an intel NUC I installed an ftp server on. Have the thing chrooted to a directory with that directory being write-only and the real ftp directory being a subdirectory (to protect against the roaring beast vulnerability, of course).

---

### Post by kurt18947 on 2019-10-26
I don't use this for anything sensitive but for simple stuff a USB flash drive plugged into my router. I'm not sure about security implications of that setup.

---

### Post by Tadaen_Sylvermane on 2019-10-27
I keep all my stuff on my server at home. Everything is shared around the house with autofs mounts over nfs to each machine requiring them. Makes it easy to manage a single script instead of updating it on 3-4 machines each time.

Having a small machine act as a central storage makes life easy, need not be powerful.

For external outside the lan, flash drive. I rarely need to do this though.

---

### Post by MoebusNet on 2019-10-29
I keep my documents synchronized as part of my data backup. I don't keep a central server running on my LAN; I just use an external USB HDD big enough to back everything up. I use Grsync to synchronize my files between my 2 laptops and my backup HDD. *Disadvantage*: I have to make sure that I synchronize the most current file versions to the backup HDD. In my case, not usually an issue since one laptop is just a backup PC anyway. *Advantage*: Because i disconnect the external HDD, it can't be corrupted by external hacking or power surges.

---

### Post by kevdog on 2019-10-29
nfs or samba share?

---

### Post by polvino on 2019-10-30
> **kevdog said:**
> nfs or samba share?
I use samba for this. Two Windows desktops have no issue reading and writing there, and administration is pretty straightforward.

---

### Post by oldrocker99 on 2019-11-19
Personally, I just email, with attachments, to myself. Works just fine, for a **few** files.

A USB thumb drive would likely hold all the files.

Just trying to KISS.

---

### Post by jetsam on 2019-11-19
Sneakernet with a multi-gig usb drive is ridiculously effective.  Cons: the drive fills up with junk.  You have to run around a bit.  Pros: very secure, immune to network attacks when not in use, fully securable if you lock it in a safe or something...  There's really no more secure solution.  It's only a little inconvenient, too, depending on how often you transfer files and how many files at a time.

It's so effective, I've let all my significant network file shares go for a while now.  No matter how good a NAS or file server is, if it's open, it's going to take some maintenance work over time.  I'll get a file server up again soon I'm sure, but you really don't need one unless you need to share work with a workgroup.

On the list to investigate: git.  It has a lot of power, and I want versioning for some content I'm working on.

---

### Post by kansasnoob on 2019-11-19
> **jetsam said:**
> Sneakernet with a multi-gig usb drive is ridiculously effective.  Cons: the drive fills up with junk.  You have to run around a bit.  Pros: very secure, immune to network attacks when not in use, fully securable if you lock it in a safe or something...  There's really no more secure solution.  It's only a little inconvenient, too, depending on how often you transfer files and how many files at a time.

It's so effective, I've let all my significant network file shares go for a while now.  No matter how good a NAS or file server is, if it's open, it's going to take some maintenance work over time.  I'll get a file server up again soon I'm sure, but you really don't need one unless you need to share work with a workgroup.

On the list to investigate: git.  It has a lot of power, and I want versioning for some content I'm working on.

That's basically what I do now, even down to the point of using my gun safe. Backup drives live in tupperware which is then placed in the safe. If the drives are at all subject to static (such as bare physical drives) they're first placed in anti-static bags. And I've actually begun using DVD's more frequently again - not sure WHY. Actually my laptop bag has a slot that's seems to be made for CD's and DVD's so why not?

---

### Post by jetsam on 2019-11-19
There was some saying about a truck full of dvd's beating the internet in a data race...

They work, no excuses needed.  I think they're relatively good archival-ish-wise (?!word!?) if you keep them dry and dark, too.

---

### Post by kansasnoob on 2019-11-20
> **jetsam said:**
> There was some saying about a truck full of dvd's beating the internet in a data race...

They work, no excuses needed.  I think they're relatively good archival-ish-wise (?!word!?) if you keep them dry and dark, too.

DVD's are very easy to label, flash drives not so much. Markers smear, labels peel, etc. I tried actual tags at one point (affixed with small slip rings) but that defeats the compact aspect of flash drives.

---

### Post by yetimon_64 on 2019-11-20
> **kansasnoob said:**
> DVD's are very easy to label, flash drives not so much. Markers smear, labels peel, etc. I tried actual tags at one point (affixed with small slip rings) but that defeats the compact aspect of flash drives.

Dvds sure are convenient, but are you aware of the potential for [[COLOR=#0000ff]--disc rot--[/COLOR]]("https://en.wikipedia.org/wiki/Disc_rot") (Wikipedia info link in blue) over time? I only mention this to you as I recently pulled out some of my old win98 backup sets only to find 2 of the 4 discs in a set were no good any more. They were stored in good conditions, dark cool and dry etc, but after about 18 years of storage were no longer any good and were totally unaccessible. Having 2 discs affected by disc rot lost the whole backup set unfortunately.

Luckily I had read about the potential for such problems back then and any important files are still backed up on my magnetic media (SATA hard drives). If you intend to keep data over prolonged periods of time I would advise against optical media like dvds from personal experience here. If you only need a means of quick storage for transfer purposes optical media like dvds are very good though, particularly the rewriteable ones.

I have a couple of external SATA docks, one is USB2 and the other USB3, that can plug in either 2.5 inch laptop drives or full size 3.5 inch desktop hard drives. For large transfers or for many files I definitely recommend a USB3 dock for the faster transfer speeds.

I usually have a local samba file network set up for all my devices, 1 laptop and 5 rPi units, with the samba service bound to the ethernet network via the smb.conf files etc; I bind the samba sharing to the ethernet network as my internet access is via an android phone either USB tethered or by wireless. This type of shares network takes quite a bit of initial setting up but once done is pretty good for transfers on a gigabit network with a 5 port network switch here. Though my best/most convenient/easiest way of sharing files/docs here would be via the USB3 dock.

Cheers, yeti.

---

### Post by jetsam on 2019-11-20
> Dvds sure are convenient, but are you aware of the potential for [--disc rot--]("https://en.wikipedia.org/wiki/Disc_rot") (Wikipedia info link in blue) over time? 

Oh, thanks for bringing that up.  I'd actually heard about that before and had forgotten it completely...  

Just anecdotally, I think almost all my now 30ish year old audio cd's play through just fine, barring the lost and damaged ones...  It seems like the aluminum based professional ones are at least decent for archival purposes provided they're handled carefully and the plastic isn't extensively scratched.  I suppose that's tough to ensure in a public collection, though...

...everything degrades with time.  Even stone erodes and gathers lichen.  I've got boxes of old magnetic media from the eight bit days I'm afraid to try to access, for fear of finding out how much of them I've lost already.  Most of them aren't important, but I would like to see that old pirated copy of Karateka working again some day.

---

### Post by uRock on 2019-11-20
I still have CDs and DVDs from the 90s that still work as intended. The only enemy of disks that I have found is scratches, and most of those can be worked out with automotive wax.

---

### Post by yetimon_64 on 2019-11-20
> **uRock said:**
> I still have CDs and DVDs from the 90s that still work as intended. The only enemy of disks that I have found is scratches, and most of those can be worked out with automotive wax.

Yeah, I suspect I may have hit a bad batch or picked a cheap/nasty brand or the like. No scratches showing on these discs and they are backups I'd opened previously many years ago so know they were usable back then but today are had it completely. Probably a pretty rare/unlucky occurence but also unfortunate that I got hit on a backup set.

I do have other dvds/cds from the same era that are still OK as well, just unlucky in this case. When I couldn't simply open the discs in my install I ran photorec over them, the 2 that failed both consistently failed at the same region on multiple attempts to access the data indicating the discs were now faulty.

I suppose if long time storage is not needed and they are only being used for easy/quick transfer of data then the possibility of dvd rot will not be any sort issue for the OP.

**Edit**:
> ...everything degrades with time.  Even stone erodes and gathers lichen.   I've got boxes of old magnetic media from the eight bit days I'm  afraid to try to access, for fear of finding out how much of them I've  lost already.... 
I also don't use floppies for archiving as they can fail as well, probably more so than cds/dvds in my experience. By magnetic media (media is probably a poor choice of wording) I am referring to SATA hard drives only. All my older IDE hard drives that were in use in the very early 2000's are long retired as well with all data transferred over to newer SATA ones. Every so often I have to recover all data off a drive if it is starting to show bad sectors or if it is showing any sign of failure. So even hard drives are not perfect but I tend to pick up on any develloping problem much easier than with either cd/dvds or even with old magnetic floppies. 

It will depend on what the OPs usage is but as I read it the OP is simply using the dvds for transfers not for storage so this aspect may be a bit off the mark on my part (apologies if that is so OP, I don't mean to hijack the thread with discussion on long term storage if that is not involved here. Just mentioned the possibility IF you are also relying on such media for storage purposes as well)

Cheers, yeti.

---

### Post by uRock on 2019-11-20
> **yetimon_64 said:**
> Yeah, I suspect I may have hit a bad batch or picked a cheap/nasty brand or the like. No scratches showing on these discs and they are backups I'd opened previously many years ago so know they were usable back then but today are had it completely. Probably a pretty rare/unlucky occurence but also unfortunate that I got hit on a backup set.

I do have other dvds/cds from the same era that are still OK as well, just unlucky in this case. When I couldn't simply open the discs in my install I ran photorec over them, the 2 that failed both consistently failed at the same region on multiple attempts to access the data indicating the discs were now faulty.

I suppose if long time storage is not needed and they are only being used for easy/quick transfer of data then the possibility of dvd rot will not be any sort issue for the OP.

Cheers, yeti.
That bytes! I only back up pictures to DVD and have a tendency to multiple copies of them, as I don't do versioned backups. I also have external drives with the same data. My pictures are the only data I want to make sure never gets lost.

I don't use disks to transport data, though. It's thumb drive or SFTP.

---

### Post by kansasnoob on 2019-11-21
> **yetimon_64 said:**
> Yeah, I suspect I may have hit a bad batch or picked a cheap/nasty brand or the like. No scratches showing on these discs and they are backups I'd opened previously many years ago so know they were usable back then but today are had it completely. Probably a pretty rare/unlucky occurence but also unfortunate that I got hit on a backup set.

I do have other dvds/cds from the same era that are still OK as well, just unlucky in this case. When I couldn't simply open the discs in my install I ran photorec over them, the 2 that failed both consistently failed at the same region on multiple attempts to access the data indicating the discs were now faulty.

I suppose if long time storage is not needed and they are only being used for easy/quick transfer of data then the possibility of dvd rot will not be any sort issue for the OP.

**Edit**:

I also don't use floppies for archiving as they can fail as well, probably more so than cds/dvds in my experience. By magnetic media (media is probably a poor choice of wording) I am referring to SATA hard drives only. All my older IDE hard drives that were in use in the very early 2000's are long retired as well with all data transferred over to newer SATA ones. Every so often I have to recover all data off a drive if it is starting to show bad sectors or if it is showing any sign of failure. So even hard drives are not perfect but I tend to pick up on any develloping problem much easier than with either cd/dvds or even with old magnetic floppies. 

It will depend on what the OPs usage is but as I read it the OP is simply using the dvds for transfers not for storage so this aspect may be a bit off the mark on my part (apologies if that is so OP, I don't mean to hijack the thread with discussion on long term storage if that is not involved here. Just mentioned the possibility IF you are also relying on such media for storage purposes as well)

Cheers, yeti.

In deed, optical discs are basically assumed to be temporary storage/transfer. Since starting this thread I've also been playing with Bluetooth for copying what I need to my laptop just before heading out and it's both fast and easy. The bottom line is (I think) there are numerous ways to copy data and it kind of comes down to whatever seems most convenient at any given point in time. 

For instance if I use my old netbook (Latitude 2110) I obviously wouldn't use a DVD because it has no optical drive. But then again it's mostly used for automotive work - provides a dandy screen for my endoscope and it's small enough to be convenient. It's also kind of a sacrificial lamb that I don't mind knocking around.

I've actually considered re-purposing an old laptop as a sort of NAS using something like OpenMediaVault. I just haven't had time to play with it. I would think an old Latitude E6400 with a 2.4ghz CPU and 4GB of RAM would be more than sufficient for such a purpose.

---

### Post by kansasnoob on 2019-11-21
> **uRock said:**
> That bytes! I only back up pictures to DVD and have a tendency to multiple copies of them, as I don't do versioned backups. I also have external drives with the same data. My pictures are the only data I want to make sure never gets lost.

I don't use disks to transport data, though. It's thumb drive or SFTP.

I don't have a tape drive to find out but I wonder if my box full of old Tandy cassettes are still readable? That is if the mice haven't eaten them :lolflag:

I was recently asked though if I still had any digital photos of my oldest grandson and found some on old 3.5" floppy discs. I had to piece together a PC using an old floppy drive to find out but they were still perfect so I was able to copy them without problem.

---

### Post by jetsam on 2019-11-21
I suppose anything could be ok, no matter how long it's been since last accessed.  Anybody really serious about archiving old 8 bit material should probably get started at their earliest convenience.  The data sizes are tiny by today's standards.  A really large collection from 1983 would no doubt fit on a thumb drive today.  The transfer job won't get any easier, though.  It can only get harder to access material with each passing year as less and less equipment survives over time.

It's an interesting topic.  The computer museums out there may have some better resources for people with collections to archive...  

Well, it isn't easy to Google the subject it turns out.  "Data archiving," often refers to government data retention requirements...  I haven't found a good resource for the family with a few boxes of floppies from the 80's to preserve.

---

### Post by uRock on 2019-11-21
> **kansasnoob said:**
> I don't have a tape drive to find out but I wonder if my box full of old Tandy cassettes are still readable? That is if the mice haven't eaten them :lolflag:

I was recently asked though if I still had any digital photos of my oldest grandson and found some on old 3.5" floppy discs. I had to piece together a PC using an old floppy drive to find out but they were still perfect so I was able to copy them without problem.

That's awesome!

---

### Post by kansasnoob on 2019-11-21
> **uRock said:**
> That's awesome!

It was fun too :)

There's just something about putting together old hardware and having it work that always results in smiles.

---

### Post by Bashing-om on 2019-11-22
kansasnoob; Hey

I ran across a new one on me:
[https://www.maketecheasier.com/transferring-files-using-python-http-server/](https://www.maketecheasier.com/transferring-files-using-python-http-server/)

Python has a server !

[INDENT]something new all the time - ubuntu ![/INDENT]

---

### Post by him610 on 2020-02-21
@Bashing_om
> 
I ran across a new one on me:
[https://www.maketecheasier.com/trans...n-http-server/](https://www.maketecheasier.com/trans...n-http-server/)

Python has a server !

something new all the time - ubuntu !

This is great stuff. Thanks

---

### Post by kurt18947 on 2020-02-22
Something I haven't seen mentioned in this thread so far -- Mdisc. 

[https://en.wikipedia.org/wiki/M-DISC](https://en.wikipedia.org/wiki/M-DISC)

[https://www.extremetech.com/computing/92286-m-disc-is-a-dvd-made-out-of-stone-that-lasts-1000-years](https://www.extremetech.com/computing/92286-m-disc-is-a-dvd-made-out-of-stone-that-lasts-1000-years)

Even reducing claimed lifetime by an order of magniture the trick would  be in 100 years to find a means to view the Mdisc's contents. Bluray Mdisc wouldn't be cheap but reasonably high capacity. I've had pretty good luck with even store brand DVDs as long as they're stored reasonably i.e. not in a motor vehicle left outdoors. There are also archival grade DVDs available which should be longer lived than commonly available media.

---

### Post by Skaperen on 2020-02-23
i know it's been said already. but you can keep your data safer with encryption.  the more people do this the less interest perps will want to steal our devices for the data.  there will always be an interest in theft for repurpose.  when manufacturers implement a usage lockout mechanism that makes the device useless for non-owners that enable it, we can even reduce repurpose theft.

---

### Post by kevdog on 2020-02-23
And sorry to bring this up -- since not linux related.  However if doing a one to one file transfer -- like desktop to laptop -- Apple's AirDrop by far is hand's down super easy.  This technology has been around for a long time.  I have no idea why a similar easy method such as this can't be replicated for other systems.

---

### Post by linuxyogi on 2020-02-24
I use MEGAsync.

---

### Post by malspa on 2020-02-24
> **kansasnoob said:**
> DVD's are very easy to label, flash drives not so much. Markers smear, labels peel, etc. I tried actual tags at one point (affixed with small slip rings) but that defeats the compact aspect of flash drives.

I use flash drives and email attachments to share files between computers. Yeah, trying to find ways to label flash drives, that's a drawback.

---

### Post by oldfred on 2020-02-24
I tape a small bit of paper to flash drive to label it and then put more tape over top to prevent ink from rubbing off. 
Also have used label maker, but label is just a bit too large even when trimmed a lot.

---

### Post by ajgreeny on 2020-02-24
Something I used in the past to do this was [Transfer-on-Lan]("https://code.google.com/archive/p/transfer-on-lan/downloads").

I can not comment on its security flaws (or not) and I don't really use it any more but it certainly did work pretty well.
It is different from a normal server setup in that one user has to "push" files or folders to the other user, both of whom need ToL installed and running, and must be on the same local network.

---

### Post by mastablasta on 2020-02-25
> **oldfred said:**
> I tape a small bit of paper to flash drive to label it and then put more tape over top to prevent ink from rubbing off. 
Also have used label maker, but label is just a bit too large even when trimmed a lot.


i found that post it note sticks to it more tightly (use the the upper part of the note), then you can wrap it with scotch tape to protect the ink. it works rather well.

---

### Post by kurt18947 on 2020-02-26
SWMBO has a lot of partial sheets of paper. I use those printed on a laser using an 8 or 9 point sans font. Cut the printing out, lay the bit on a desk and pick it up with a bit of clear tape. Stick it to the flash drive in such a way that it's possible to remove the tape/label as required. I've also used the sticky label trick, that works as well and doesn't require a printer.

---

### Post by lammert-nijhof on 2020-03-01
I use ZFS on desktop and laptop and all my data is lz4 compressed. I have ~0.8 TB of compressed data. I synchronize that data weekly from desktop to laptop in ~10 minutes on a 1 Gbps Ethernet link. It kills two birds with one stone, I have the same stuff at home (desktop) and on the road (laptop) and I have another backup. That link is using a cheap 5 port network switch (1 Gbps) in front of my Internet/WiFi router (100 Mbps).
I snapshot my data on the desktop, use ssh, enabling to transfer the receive command to the laptop. The desktop is using an incremental send and it sends only the changed physical compressed records to the laptop. That mechanism is especially useful, if you deal with large files. I sync ~50 Virtual Machines in this way with disk files of 50 MB (Windows 3.0) to 50 GB (Windows 7 or 10).
If you have smaller sub-GB files, grsync (GUI) or rsync (CLI) are good alternatives. They rely on samba or nfs for remote access. They only send the changed files, but basically they would send the files uncompressed. 
I run Ubuntu 19.10 on the desktop and Ubuntu Mate 19.10 on the laptop.

---

### Post by lammert-nijhof on 2020-03-01
I have an easy job, sharing data between Ubuntu 19.10 desktop and Ubuntu Mate 19.10 laptop, since I use ZFS (Zeta File System) on both systems. I snapshot my desktop at least weekly or sometimes daily and use "zfs send | ssh zfs receive" to send the changed info from desktop to laptop. I use a simple two line script per dataset(folder), that I want to send. I use exactly the same commands for sending that Data and VMs to my FreeBSD backup server. Note that ZFS is supported on many other OSes too.

I have ~750GB of Data and Virtual Machines, that I want to sync. I bought a cheap 5 port Ethernet Switch (1 Gbps) to get the weekly transfer below 10 minutes. ZFS only sends the changed physical records and if sender and receiver use e.g. lz4 compression, it sends the data in that compressed format. 

Ubuntu can install the OS on ZFS (lz4 compressed), they call it experimental, but that is only true for the installer, ZFS itself is in use by e.g. SUN-Solaris since 2005. ZFS is rock solid with Ubuntu 19.10 on my Ryzen3 2200G, Ubuntu Mate 19.10 on my i5-2520M and FreeBSD on my 32-bits Pentium IV.

ZFS requires the terminal, but the command language is strong and  consistent. It is the best CLI, I did see since the days of PDP11 and  VAX computers. If you want to go that way, try it out with two VMs in  e.g Virtualbox.

---

