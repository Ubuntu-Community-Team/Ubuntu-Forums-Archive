---
title: "Methods used to multiple operating systems."
date: 2014-10-04
forum: Ubuntu, Linux and OS Chat
---

### Post by WanderingAlbatross on 2014-10-04
Many of us have multiple operating systems we use of Linux.  One of the challenges of working with this is constantly updating our data.  Reinstalling involves migrating a lot of things.  What do you do to migrate to a new operating system?

I like to maintain a separate partition outside of my OSes to save all my files I plan on keeping longer than the operating system.  It includes documents, videos, installation ISOs, etc.  When I install the same program in at least two operating system, I then delete it's folder in the OS's home directory, and create a symbolic link to this partition.  I find this is a good way to keep consistency across different OSes.

A while ago I had attempted to use the same home partition for more than one operating system and that was a disaster.  

Of course, rolling releases don't have that trouble as much as others do.  Still, in the even of a meltdown, it is good to have everything out of harm's way.

I have found it useful to do this symbolic linking with browsers, email clients, Orage, Gnucash (which is really just a matter of where you save), etc.  The hardest one is Dropbox, but even that is possible.

Any thoughts?

---

### Post by sudodus on 2014-10-04
I have a ***data*** partition for personal files (documents, pictures, video-clips ...) and I back it up separately. Then it is possible to run simple and independent installed systems and live systems and have my personal data available.

Furthermore, I have one 'production system' or 'work-horse', which is running Ubuntu 12.04.5 LTS. I do not bother to tweak the other systems much, they are only for testing.

---

### Post by santosh83 on 2014-10-04
Second sudodus. I have a separate partition for all my personal data like documents, images, videos and downloads. In fact it's actually a 500Gb external HDD permanently attached to the desktop. The desktop itself has only an old 40 Gb IDE drive, but since I store all my data on the external HDD, this is sufficient space for just the system and programs. I used to do multiple OS side-by-side on several partitions but these days I've no time/energy for that. If I want to try another OS concurrently, I'm thinking I'll take the VirtualBox route, despite the performance hit that'd imply.

But the more important issue as far as data safety goes is duplication or lack of it. If all your data is on a single drive, or cloud, then there's always the risk that a drive crash or cloud provider going under could jeopardise all your data. Duplication is essential. Preferably in geographically separated places. To that end I'm going to duplicate all my personal files on a second external HDD which will get synced to the main one every few days or a week. Although I don't have the means to separate them geographically (thus a local disaster could wipe out all my data, but then again, it's likely it'd wipe me out as well! ;-) ), but at least this way I'm insured against sudden HDD failure.

By the way, I think trying to use the same physical instances of a program (or programs) across many OSes can be tricky. Mainly cause library dependencies could vary from system to system, as well as text formats and so on. Some programs also insist on being at certain places in the FS and won't start from an external drive or a separate data partition. My external HDD is also formatted as NTFS for interoperability with Windows. I wonder if Linux programs can live on it? Linux implements several file permission mechanism which can't be done on NTFS.

So far I've been content with just one OS. If I'm interested enough in future, as I said, I'd consider using VirtualBox instead of actual side-by-side install, to save myself a lot of unnecessary work.

---

### Post by WanderingAlbatross on 2014-10-04
I agree about data backup.  I use an external HDD as well for backup, and a program based on rsync to do it.  I don't personally like all this cloud stuff.  I would rather risk my data being in my geographical place than off in some unknown hands for protection.

I've actually never had a problem with a program switching libraries.  If they change the way they do things, they will tend to keep the same data.  While the settings for the user remains in the home drive, the data generated is what usually ends up on the common drive.  Even the drastic changes in a program like Firefox has done okay on one laptop that has stable Debian and constantly changing Arch.

---

### Post by Bucky Ball on 2014-10-04
I go symlinks. Install your operating system, let /home be a directory inside the / partition. Delete the directories inside /home like /Videos, /Documents, etc. and instead create symlinks to the data partition. You also don't need separate /swap partitions for your Linux install. They will all happily use the same one (as you are only running one OS at a time). 

You will find symlinks explained and the syntax to create them [HERE]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979"). Good luck and hope that gives some clues ...

Basically, think of it like this:

ln -s 'location to link to' 'name of symlink'

So, for example and replace with your details:

```
ln -s /mnt/data/Documents /home/username/Documents
```

Hope that makes some sense. ;)

---

### Post by TheFu on 2014-10-04
I have a mix of different installed OSes on different machines and inside virtual machines. I only dual boot portable systems and do that very rarely.
Using symlinks is workable, but I prefer to use NFS when that is an option and mount storage to the same location.  I rarely have symlinks from my HOME - just not needed in my situations.

I've had a shared HOME before, but not since all the different DE explosion, which I think is what is causing your issues.  Using a pure WM, not a DE should allow the shared HOME to work better. Part of the issue is that different systems have different applications installed - so different menus are needed per HOME ... I guess.

I don't use the cloud - at least not somebody else's computer.  I have my own private cloud (not running owncloud) that is on systems I control and only accessible with a VPN. HTTPS is broken, so that isn't really a viable access method for privacy. I think people [putting their data on someone else's computer is just crazy]("http://www.networkworld.com/article/2228050/opensource-subnet/cloud-computing-is-careless-computing-and-chromeos-pushes-people-into-it-says-open.html"). Once it is out - it is not under your control.

As to email - I run an IMAP email server, so all my clients see the same views. Plus my data isn't stored somewhere else (though most people don't seem to care an force me to give up privacy by using gmail). The server does all the automatic folder management for me and moves messages where I want them base on rules. Every client sees the messages in the same place, extremely great. Can't imagine ever going back again.  Also love having different calendars, but having access to them from anywhere in the world.

---

### Post by PondPuppy on 2014-10-05
Similar for me -- important data lives on the desktop machine running Ubuntu (Win7 dual-boot), backed up to an external HDD. All my machines are multi-boot, but I take care to transfer any important files to the desktop system. Therefore the distros on the laptops can be updated or re-installed without angst; there's nothing on them I can't afford to lose. One of these days I'll set up a home server, but it will be a newbie's learning experience and right now I don't have the time.

I use cloud storage for a few trivialities -- essays I found interesting, quotes, gear lists, useful cli commands, that kind of stuff.

---

### Post by WanderingAlbatross on 2014-10-05
I see, you go with an external hard drive, (and this discussion is quickly heading toward a backup discussion), but on the actual machine you don't have another partition.

Windows certainly adds complication because it can't read EXT filesystems.  I like using symbolic links to make use of the same data on multiple operating systems.  If you bring yourself to change the file system of a separate partition to one that windows can read it might mess up symbolic linking.  I don't know if you can symbolically link to an NTFS.  I know NTFS doesn't support symbolic links.  I will try to experiment with it.  At any rate, I have booted Windows three times since I've had my newest laptop, so I hadn't even thought about linking Windows in to the mix.  It would be interesting to see if you could use the exact same data from Windows and Linux to run your main programs.  There are many Linux programs that also have a Windows version.  At lease last time I looked they did. :grin:

---

### Post by sammiev on 2014-10-05
I just import my data as required as I do so many installs of many OS. I can do a full install and transfer all data in 30 to 40 mins.

---

### Post by Mike_Walsh on 2014-10-09
> **WanderingAlbatross said:**
> Many of us have multiple operating systems we use of Linux.  One of the challenges of working with this is constantly updating our data.  Reinstalling involves migrating a lot of things.  What do you do to migrate to a new operating system?

I like to maintain a separate partition outside of my OSes to save all my files I plan on keeping longer than the operating system.  It includes documents, videos, installation ISOs, etc.  When I install the same program in at least two operating system, I then delete it's folder in the OS's home directory, and create a symbolic link to this partition.  I find this is a good way to keep consistency across different OSes.

A while ago I had attempted to use the same home partition for more than one operating system and that was a disaster.  

Any thoughts?

I guess my setup is similar to many others' on here. Everything important is stored on an external HDD, including a special folder just for regular system backups. That way, it can be accessed by any of my OSs, at any time. 

Like you, I've recently experimented with sharing a /home partition among more than one OS. I wouldn't say it was a disaster; by and large it seemed to work fairly well. The only slight case of cross-contamination is the fact that each OS tends to store your individual settings as hidden .config files within your home folder, so I guess, certainly with the 'buntu 'flavours ( i'm currently sharing a /home partition between Ubuntu & Lubuntu), there's the possibility of things not behaving themselves QUITE as expected. I have noticed icons from each OS appearing on the other one's desktop; but since I have very few anyway, it's not really a problem.

As far as TheFu's observation goes:-

> [COLOR=#000000]I've had a shared HOME before, but not since all the different DE explosion, which I think is what is causing your issues. Using a pure WM, not a DE should allow the shared HOME to work better. [/COLOR][COLOR=#ff0000]Part of the issue is that different systems have different applications installed - so different menus are needed per HOME [/COLOR][COLOR=#000000]... I guess.[/COLOR]

I don't have quite such a problem there, as I have as near as possible an identical application list in every OS; that way I can carry on with what I'm doing without a break, regardless of which OS I happen to take a fancy to on the day.

I've just last night done a full install of Kubuntu to a 64 GB SanDisk CruzerBlade flash drive. I briefly considered linking THAT to the /home partition, but it would have defeated the object of having a self-contained, fully mobile OS that I can take with me anywhere I go. Home folder storage space is NOT a problem... ;)

Regards,

Mike.

---

### Post by endlessinstant on 2014-10-09
I gave up using internal drives as my primary storage drives some time ago.  I've had to many situations where my systems crashed and retrieving the data from an internal drive was going to be...annoying at the least.  I'm fairly obsessive-compulsive but I tend to give my data copied on an external storage drive, Google Drive, and a set of SD cards.   I like SD cards for movies and music because they are easy to swap and transport and newer cards offer plenty of speed and storage for keeping a decent amount of media on them.   They are not the safest medium however, especially since I travel with them frequently, so their use requires good backup practices.   

I usually toss low-capacity SSDs in my internal bays now, enough for the OS and some apps to keep me going.   64 GB is "plenty" for what I do but 128s are starting to get nice and cheap so I will probably switch eventually.

Oh and keeping my data backed up like that makes it nice for all the OSes I use.   I've got Android 4.4, iOS 8, OS X Mavericks, Windows 7, Debian Wheezy, Xubuntu 14.04, and Chrome OS all running on systems that I regularly use.   I'm very noncommittal when it comes to what OS I want to use, even from day to day, LOL! It's lovely to be able to pop an SD card into any of these systems and be able to pull all of my data.  Most tedious device is probably my iPad since I have to plug that in the old fashioned way instead of just using a card.

---

### Post by Mike_Walsh on 2014-10-09
THAT is a neat idea. I must confess, I hadn't thought about using SD cards. Part of the reason I like the SanDisk CruzerBlades (I have 4 of them, in various capacities) is because for a USB drive, they're about the smallest, lowest profile it's possible to get.

With the exception, of course, of the 'nano' drives that are becoming popular...

Regards,

Mike.

---

