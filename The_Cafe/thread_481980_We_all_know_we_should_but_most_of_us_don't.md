---
title: "We all know we should but most of us don't"
date: 2007-06-23
forum: The Cafe
---

### Post by ixus_123 on 2007-06-23
What's your backup / redundancy method?

Currently I have bought a D-link 323 NAS running 2 500GB western digital disks in a RAID 1.

I also have an external 320GB USB drive that I plan to set up a weekly backup to.

It's only recently I specifically budgeted for redundancy / backing up my data but I have so much stuff on my computer now it seems really stupid not to.

So what's your solution and if you have none perhaps you should

---

### Post by karellen on 2007-06-23
simply write cds as I don't have much stuff that it's really so important and that cannot be replaced easily

---

### Post by azkehmm on 2007-06-23
A real man don't make backup... he cries instead :)

---

### Post by eentonig on 2007-06-23
Music; movies and Photo's are daily rsync'd to an external HD.

Off Course, if the house burns down, I'm still screwed. But at least HD crash wont screw me (again).

---

### Post by Erik Trybom on 2007-06-23
I backup important documents to my own private space on the university servers.

---

### Post by peterbrewer on 2007-06-23
I have my laptop mirrored onto my media centre and backups of most of my media.

---

### Post by Skrynesaver on 2007-06-23
External hardrive
A tgz of find -mtime 1 daily except Sunday when it does tgz s of /home /etc /var

---

### Post by energiya on 2007-06-23
Made myself a backup script and I just copy the resulting archieve on another hdd or CD.

---

### Post by Obor on 2007-06-23
Not the best solution but I use my 60GB ipod to backup all my important bits (mostly photos)

---

### Post by bobbocanfly on 2007-06-23
I backup my Apache Htdocs every 3 hours to a USB pen drive. When i get the file server set up properly ill so a daily media backup to that

---

### Post by PatrickMay16 on 2007-06-23
I back my files up onto CD-Rs and DVD-Rs, and an external hard disk... mainly the external hard disk.

---

### Post by daynah on 2007-06-23
I back up manually... As in, I copy and paste the folders that I keep my stuff in to two other harddrives (a laptop and an external; they can't all fail at the some time!) and I copy like tomboy and KMyMoney files also (I have a list to back up). If something goues wrong, it's an excuse for a clean install.

I do this because, though I have made back ups of the whole system like in the tutorials, I never had to empliment them and... well, I dunno if I trust something I've never done. What if I typed it wrong? I don't know... I also tried a backup program but it had no gui, so I assumed the defaults were rational. Whatever, I had my normal backup. The dumbthing backedup by the comp including its own backups and a few days later there wasn't enough room to log me in!

Nope, I like seeing my file, in the decompressed format I can easily open them in. That way I know they are there...

---

### Post by PartisanEntity on 2007-06-23
I use rsync to copy my home directory to an external hard disk, nice thing about it is that after running it for the first time it only copies changes.

---

### Post by keithweddell on 2007-06-23
To start, I'm using RAID1 to guard against HD failure.  Then I wrote a script to rsync home, samba shares, email, music, pictures and configs every night to a spare HD.  I rotate 7 daily snapshots and automatically back up to dvd one a week.  A little paranoid but barring house fire I 've got most things covered.


Keith

---

### Post by juxtaposed on 2007-06-23
I don't have enough other hard drive space to backup the stuff on my 500GB hard drive :(

---

### Post by beercz on 2007-06-23
I use [rsnapshot]("http://rsnapshot.org/") to automatically backup with cron my stuff onto a separate server, daily.

Superb utility.

---

### Post by macogw on 2007-06-23
Once I don't need my spare HDD for experimentation (submitting bugs on why the heck Ubiquity segfaults with Feisty), it'll be a nightly rdiff-backup, I think.  I used to do dd if=/dev/sda of=/dev/sdb, but now I think I'd like rdiff because it means I'll end up with a bit of a CVS/SVN (pick one) effect.  The problem is finding the time of night when I'm least likely to be online (and then somehow remember not to have it go if I'm using it...maybe I could make the script check to see if Firefox is running before it remounts as read-only...)

---

### Post by FuturePilot on 2007-06-23
I don't have one:o Maybe I should.
Though if there is something important I might put multiple copies on a few USB drives.

---

### Post by blah blah blah on 2007-06-23
I don't back-up.

> **daynah said:**
> ...they can't all fail at the some time!...

yes they can

---

### Post by HotShotDJ on 2007-06-23
I rsync my home partition to an external hard drive every week or so.  Also, every month (or before making any major changes to my system), I boot using a livecd and use partimage to take a snapshot of my root partition and store the image on an external hard drive.

---

### Post by Happy_Man on 2007-06-23
All my important stuff is on my NTFS partition (formerly used, now not so much). Sure, I have my photos and music copied over for increased efficiency, but it's all there if I need it. That's enough backup for me.

---

### Post by VChief on 2007-06-24
I kinda do it lazily. Once a week, I just tar up my home folder and throw it on my external. I'm getting a laptop before I start school this fall. With that one, I'm going to write a script that automatically backs-up my files on my desktop whenever I start up and shutdown at home so that my laptop's always backed-up (I'm kinda clumsy at times and worry about jacking up my laptop).

---

### Post by puppy on 2007-06-24
All documents/music/videos/pictures etc and critical files incrementally backed up to a NAS (Network Attached Storage) device which hangs off my router in another room nightly via a CRON job :D

---

### Post by mips on 2007-06-24
I have two identical drives and two identical size /home partions. I mirror my /home to /home2.

---

### Post by notwen on 2007-06-24
I use mondo and backup my /home partition and my media HDD every month.

---

### Post by justifier on 2007-06-24
Music is all cpyed on about 3 differnet machines. Saves network (and server) overload (i dont buy machines there all reclaims) when everyone is streaming music at once etc. We are a high net traffic family. School work etc. Is jsut a gamble if it goes it goes.  HTML another copy genrally. Not that important tho. So thats it really. Other stuff isnt important enought to backup or i ahve copys on CDs. Oh and the music collection is also on CDs. That was a mission ripping 20Gigs of CDs

---

### Post by joe.turion64x2 on 2007-06-24
To prevent any Linux failures (you know, you can always screw your installation) I hold the important data in my laptop in a separate partition mounted under my home folder so I can easily retrieve the data using the other Linux I have installed in the laptop.

Besides my desktop holds a copy of most of my data. In addition to that I have redundant backups in CDs and DVDs (I record 2 backup DVDs a year), and soon will have an external hard drive to make another backup copy (and synchronize easily the laptop and the desktop).

The data that is being edited is in my 512MB USB flash drive.

Joe.

---

### Post by xpod on 2007-06-24
I usually have one up to date back up cd lying around......otherwise known as an Ubuntu cd.:D
I really dont have anything on the pc i worry about.
I dont even make dvd`s to watch anymore,not since connecting the tv.....i do have a second copy of that xorg.conf if that counts mind you.:D

---

### Post by rax_m on 2007-06-24
I backup randomly to an external hdd.. mostly when I think there's some new and important files I've created. I.e. I've actually done some work for a change ;)

Thinking of using the rsync solution..
does anybody know if it matters whether the backup partition has to be of a particular filesystem?
My data is stored on a FAT32 (yuk!) and the backup drive is NTFS..

---

### Post by ThinkBuntu on 2007-06-24
I keep a backup of my Home directory on my iPod. I update this weekly, and it's about 6GB. Contains all the essentials (FTP logins, Email), plus the usual docs, etc.

---

### Post by Nekiruhs on 2007-06-24
Full images of a 250 GB HD to a 50 GB partition using Acronis True Image Workstation. I Also do the same for my other 250 GB drive with Kubuntu on it, only to a 20 GB partition.

---

### Post by bclark on 2007-06-24
I just write custom scripts to tgz stuff up and send curl it to another server and run it as a cron job.

---

### Post by ivesjd on 2007-06-24
I'm working on getting rsnapshot working to my remote server.

---

### Post by x0as on 2007-06-25
Anything important is burnt onto dvd/cd.  Music, videos etc can easily be replaced.

---

### Post by diskotek on 2007-06-25
cd's & dvd's.. but i would like to have 500gb WD external thing.

---

### Post by Matakoo on 2007-06-25
Call me paranoid...but this is what I'm doing on my home-machine.

/home is a RAID1-mirror (software-raid but still)
I also use rsync to keep a mirror on a NAS-drive. Or rather, I would if I could get Ubuntu to talk to a Freecom NDAS-enabled-drive.  I know it should be possible, but I haven't succeeded yet.

Then I'm also using a  tapedrive for the most important stuff.  Probably not necessary, especially if I get the NDAS-thing working, but I have the drive and I might as well use it.

---

### Post by qpieus on 2007-06-25
Daily cron job to rsync /home and /etc to my file/print server.

---

### Post by Ozor Mox on 2007-07-10
I now use rsync to make regular backups to my external hard drive of all my files which I keep in one folder on my desktop.

Does anyone know if I can use rsync if the external hard drive is formatted as FAT32 instead of ext3, or if I need to do anything differently?

---

### Post by Dragonbite on 2007-07-10
> **azkehmm said:**
> A real man don't make backup... he cries instead :)And Cry I have done!

---

### Post by DJ_Max on 2007-07-10
> **azkehmm said:**
> A real man don't make backup... he cries instead :)
Ditto

But I just got my laptop, and haven't realized I don't backup. Maybe I should....

---

### Post by lhomme on 2007-07-12
For now its just the external HD.  I've thrown the idea around of someday getting another external HD just for backups, putting it inside a fire resistant safe and drilling 2 holes for power and USB.  
If I get really ambitious someday I might look into a wireless network storage device, put that in the safe (maybe a hole for the antenna to poke though) and stuff the whole thing somewhere fairly safe in the house (garage?)

---

### Post by Warpnow on 2007-07-12
I use gmail for my small stuff like documents, images, ect

For bigger things I burn them to DVDs usually.

---

### Post by frrobert on 2007-07-12
I backup my office  laptop and desktop to a 2nd hard drive on the desktop, which is backed up to an external HD, which I store in a fire safe when not in use.

---

### Post by dada1958 on 2007-07-12
I rsync my home folder with the one on my file/webserver every day, in the background with a cron job ...

---

