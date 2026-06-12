---
title: "What's your backup strategy (if any)?"
date: 2007-11-04
forum: The Cafe
---

### Post by FG123 on 2007-11-04
Do you do regular backups?
What media do you backup onto?
What content do you backup?
Do you use any backup software or just burn a folder?

For me, about once a month or whenever I'm feeling worried, I'll do a backup of the latest important changes to my critical files. This includes my thesis, new photos, other documents, etc. I already have a backup of the majority of important content so I only create DVDs of anything new or changed I don't want to lose. I don't bother backing up movies/music unless it's really worthy, since they're mostly expendable.

I ask because I read on another forum how someone recently built a new system and somehow managed to perform, in his words, "a RAID arrays disk stripe going wrong". Result: a whole terabyte of data lost! Not that it would all have been worth backing up, but it's gotta suck when all that content disappears in a flash. :mad:

---

### Post by lyndaj70 on 2007-11-04
I have an external hard disk I use to keep my main backup files on, and occasionally when I'm feeling paranoid I will burn it all to DVD, sorting it into categories (music, photographs -- sifting out the space hogs to burn separate).

Whenever I am considering any changes to a system, I transfer it all to that hard disk "just in case:.

I keep text files with my important bookmarks, etc, so I don't have to worry about compatibilty between proggies....

Take care!
~L

---

### Post by FG123 on 2007-11-04
Yeah, I should probably also mention, being a recent Windows convert, that my regular style of backups (ie. burn stuff directly to DVD) might not be so suitable in Linux. I don't believe the file format used in CDs/DVDs has support for symbolic links for example, stuff I'd want to preserve.

I suppose in those cases, an external HD formatted with a suitable format would be more appropriate in Linux now.

---

### Post by p_quarles on 2007-11-04
I make occasional backups of important data to CD/DVD, but this happens maybe twice a year. My main backup method is to use rsync to mirror my main data directory to a loopback disk image on my home server. I do this about once a week or so, just to be on the safe side.

---

### Post by Depressed Man on 2007-11-04
I backup any important files onto an external hard drive monthly. I also have most of them on my laptop (and mirrored onto another hard drive in the system). So besides my external there's always two other places to find it.

---

### Post by RandomJoe on 2007-11-04
Timely question - it's been a long while since I did any...

I have several stages of backup that I can (and used to regularly) do.  

The first "online" stage is rsync to my server in the back room.  It has 1TB RAID5, so even if a drive fails (which has happened in the past) I can fix it and not lose my data.  At this level I back up the entire system, makes it easy to "re-image" the computer if needed and I'm right back to the point the backup was made.  

The fun part, I've used this method as a way to comfortably experiment with another distro, if I didn't like it or just wanted to go back I could rsync the backup onto the reformatted drive and with just a little work (primarily making sure the bootloader was happy) I was back up and running.

Second is a set of USB/Firewire external drives.  Problem here is that I've outgrown them!  I have to think long and hard about what's important when using them.  I really should buy some larger drives to put in them.

Third, of course, is DVDs - I'll burn my most important documents to one periodically and store the DVDs in a fire safe.  Offsite would be better, but I haven't done it yet...

I used to have the rsync automated - just ran periodically, or whenever my laptop was on the home LAN.  I should get that set back up again!

---

### Post by PriceChild on 2007-11-04
I back up my encryption keys to my phone and media player which I carry all the time, keeping revocation certs around also. I don't have anything else important as any work is on paper.

---

### Post by tempusfugit on 2007-11-04
If i have enough new stuff to burn on a dvd i do that, thats all
if i need to reinstall windows i dont care, with ubuntu, havent made any back up yet, but have nothing to back up actually, only programs and i could install them in minutes back from synaptic or add aplication.

---

### Post by DutyDuty on 2007-11-04
Send things to myself on GMail. It's such a wonderful device.

Of course, nothing giant. But the point is there.

---

### Post by -grubby on 2007-11-04
I back up all my documents (i.e. bookmarks,office files,etc...) to my flash drive. Comes in handy A lot

---

### Post by bruce89 on 2007-11-04
> **FG123 said:**
> I don't believe the file format used in CDs/DVDs has support for symbolic links for example, stuff I'd want to preserve.

Thanks to [Rock Ridge]("http://en.wikipedia.org/wiki/Rock_Ridge"), this is not the case. (to clear up, POSIX things work)

---

### Post by Compucore on 2007-11-04
I have a external tape back up that I can easily hook up to my computers over here. The tape back up machine that I am using is a 12/24 gigabyte tape back rom Seagate. Which suites me fine over here. And can be used on either windows or linux. At least it is compatable for what I need to do with it. Using DAT-3 tapes. And I have about 50-60 spare tapes that I got for free and tested to make sure that they will work on my machine over here. 

Compucore

---

### Post by cyclefiend2000 on 2007-11-04
i have all my music on an external harddive. which needs to be upgraded since my collection is starting to test the limits of the harddrive. 

all our photos are backed up to dvd currently, but i would like a better method of backup for them. that is the main thing i worry about. all the other stuff could be replaced. i have been searching for an online photo storage, but i havent found one i like.

---

### Post by jeffjohn on 2007-11-05
Can someone tell me the scripts or Apps to SAVE my system files to a bootable disc, please.  In Windows I use Autostreamer.

thanks jeffjohn

---

### Post by Phil Airtime on 2007-11-05
Every so often, I drag media and important files to a "server" on the network, which is actually an old first-generation Mac Mini I used for my desktop until it got too slow. To save power, the "server" is off unless I'm putting files onto it or retrieving them from it. I also keep a lot of smaller files such as documents on a USB stick. I don't have any sort of "backup strategy", but it means I'll lose very little if my comuter goes all breaky on me. I don't upgrade my Ubuntu, though, so it's unlikely.

---

### Post by runningwithscissors on 2007-11-05
At the moment it's only a cronned rsync job. I'll set RAID up when I can be arsed.

---

### Post by Scruffynerf on 2007-11-05
Basically home folder in ext3 to ntfs partition on same HDD (not really a backup, considering that if the drive dies, then "><") (operating systems are on a different drive btw).

Weekly backups to DVD of home folder.

---

### Post by OrangeCrate on 2007-11-05
I use a standard install, with just a few minor modifications like auto login, appearance preferences, etc. All of my email is web based (gmail), and my OOo documents are backed up on a USB stick. My upgrade from 7.04 to 7.10 borked about half way through, so I just downloaded and installed a new copy of 7.10, and was up and running again within minutes.

---

### Post by asimon on 2007-11-05
I use [dar]("http://dar.linux.free.fr/") for my backups. I have a special backup partition where I store the backup files and from time to time I burn them on DVD+RW. I always keep the last 3 backups on DVD. I do a full backup once a week but being lazy I burn them on DVD quite infrequently, which is bad.

The backups include my whole home directory minus some svn checkouts I have from serveral projects (which sum up to several GB) but are easy to download again. Of course I also exclude stuff like ~/.cache/ (Tracker's cache is nearly a GB big too).

---

### Post by WinterWeaver on 2007-11-05
I have my Home folder on a seperate partition, so when I want to format and reinsall anything, I just remount it. Nice way to keeps settings for apps etc, bookmarks mail etc :)

For a more long term backup solution, I write any files and folders which I wish to keep onto DVD.

I also have minor things on my USB stick, which is usually with me.

Thats about it ^_^

WW

---

### Post by william_nbg on 2007-11-05
I wrote a simple shell script which:

Backups to another HD
Deletes older backups
Backups only what I want
Saves permissions 
tar format

Originally, I had set for a crontab, but I hate it when I'm working and it starts backing everything up and I'm wondering, "what the hells going on with my systems?"

---

### Post by beercz on 2007-11-05
I backup daily using rsnapshot

Superb tool, it's all automated (via cron), is safe, secure, reliable and very fast and I don't have to worry.

Uses rsync over ssh to make incremental backups of data, hard linking to previously backed up unchanged files, and copying over new/modified files, thus making it very fast and very efficient.

I get my backup system to write log files and uses scp to copy the log files to my client machine so I can check the backup.

My backup of around 70Gb of data takes about 15 minutes to complete.  (The first time I ran it took a lot longer as it had to copy everything , subsequent backups copy only new or modified files).

I have a grandfather, father, son backup system.

Been using it for years, never failed.

BTW rsnapshot is currently changing maintainers, so the site is temporarily down.

---

### Post by meg23 on 2007-11-05
My backup strategy is proactive. Don't mess with grub or the partitioner. Don't copy and paste anything into the terminal that you don't understand. Don't upgrade to Gutsy. And last but not least, don't fix something that is not broken.

---

### Post by OffHand on 2007-11-05
I use rdiff-backup in combination with a cron job. It backups my whole /home folder to a seperate drive.

---

