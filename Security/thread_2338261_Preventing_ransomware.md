---
title: "Preventing ransomware"
date: 2016-09-26
forum: Security
---

### Post by Robbyx on 2016-09-26
Assuming  that ransomware can/ will  be made to run on Linux, I have started to backup my important files ie home and my docs with sudo dd if=/dev/sda3 of=/dev/sde2. My intention is to leave the flash drive out of the usb port unless I am doing a backup or restore from it, but I get the following  error message when I try to open sde2 using a file manager:


> Error mounting /dev/sde2 at /media/robins/Image home: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sde2" "/media/robins/Image home"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sde2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


> dmesg | tail
[ 5605.536200] [UFW BLOCK] IN=eth0 OUT= MAC=d0:50:99:19:55:52:8c:10:d4:cd:25:73:08:00 SRC=192.168.1.254 DST=192.168.1.4 LEN=305 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=11376 LEN=285 
[ 5625.556238] [UFW BLOCK] IN=eth0 OUT= MAC=d0:50:99:19:55:52:18:28:61:cd:8f:6d:08:00 SRC=192.168.1.6 DST=192.168.1.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=56977 DF PROTO=TCP SPT=46458 DPT=39440 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 5646.954474] EXT4-fs (sde2): bad geometry: block count 10416896 exceeds size of device (6931712 blocks)
[ 5648.986110] [UFW BLOCK] IN=eth0 OUT= MAC=d0:50:99:19:55:52:8c:10:d4:cd:25:73:08:00 SRC=192.168.1.254 DST=192.168.1.4 LEN=293 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=44577 LEN=273 
[ 5650.625241] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:8c:10:d4:cd:25:73:86:dd SRC=fe80:0000:0000:0000:8e10:d4ff:fecd:2573 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[ 5667.554354] [UFW BLOCK] IN=eth0 OUT= MAC=d0:50:99:19:55:52:18:28:61:cd:8f:6d:08:00 SRC=192.168.1.6 DST=192.168.1.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=56980 DF PROTO=TCP SPT=46458 DPT=39440 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 5686.075131] [UFW BLOCK] IN=eth0 OUT= MAC=d0:50:99:19:55:52:18:28:61:cd:8f:6d:08:00 SRC=192.168.1.6 DST=192.168.1.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=36931 DF PROTO=TCP SPT=46494 DPT=39440 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 5707.163996] [UFW BLOCK] IN=eth0 OUT= MAC=d0:50:99:19:55:52:18:28:61:cd:8f:6d:08:00 SRC=192.168.1.6 DST=192.168.1.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=36934 DF PROTO=TCP SPT=46494 DPT=39440 WINDOW=5840 RES=0x00 SYN URGP=0 


What have I done wrong?

---

### Post by SeijiSensei on 2016-09-26
Are those two devices identically sized?  It doesn't seem so given this error:
```
[ 5646.954474] EXT4-fs (sde2): bad geometry: block count 10416896 exceeds size of device (6931712 blocks)

```

And how would someone manage to inflict a ransomware situation in Linux?  All you'd need to do is reinstall the OS.  It's not like Windows where you typically have no installation media.

---

### Post by ian-weisser on 2016-09-26
Versioned backups maybe preferable - on a very bad day, you might accidentally overwrite your only good backup with a useless encrypted lump.
Also, remember that restoring from backups need to be tested. You need to know that restoring will work on that very bad day.

---

### Post by Robbyx on 2016-09-26
> **SeijiSensei said:**
> Are those two devices identically sized?  It doesn't seem so given this error:
```
[ 5646.954474] EXT4-fs (sde2): bad geometry: block count 10416896 exceeds size of device (6931712 blocks)

```

And how would someone manage to inflict a ransomware situation in Linux?  All you'd need to do is reinstall the OS.  It's not like Windows where you typically have no installation media.

I measured the required destination partition size by taking the used space size from the source and adding a couple of gigs to it. That gave a lot less spare space on the distination than the source but I thought that did not matter. **Are you saying that dd copies the spare space as well as the used area?**

Fram what I have seen on the TV  ransomware encodes all files on the system, even if that is a misunderstanding I assume it goes for all the data files it can find on all drives and I think that is what I have seen today on the TV program discussing it.

---

### Post by Robbyx on 2016-09-26
> **ian-weisser said:**
> Versioned backups maybe preferable - on a very bad day, you might accidentally overwrite your only good backup with a useless encrypted lump.
Also, remember that restoring from backups need to be tested. You need to know that restoring will work on that very bad day.

I had the idea of incremental backups, but how do I do it? I tried a straight copy and paste of the source and a number of presumably transient or special files were not copied and error messages appeared, so I moved on to dd which gave me the errors in the my opening query above. For the home directory backup  what gui would do an incremental backup to the flash drive?

I also considered  Backup (deju dup)  but how do I use it for both regular daily  backups and the separate  special flash drive backup to defeat ransonware?

---

### Post by 1clue on 2016-09-26
IMO dd is not a backup tool, especially on the device level.

Personally I don't do incremental backups OR encrypted backups.

I've been making backups since the early/mid 90s, both for business and private life. I've used  floppies, digital tapes (9-track, DAT, more), CDs, DVDs, BluRays,  Bernoulli drives, you name it. I used all sorts of proprietary software  that was required by whatever media. Up until about 1995 I blindly made  backups and assumed they were good.  In 1995 I had to restore one, and  discovered that my DAT tapes were totally useless. I couldn't get any  data from them, at all. That was a serious awakening.

I went  through a bunch of "offline" media and found fault with most or all of  it. In the end, I think it's best to use a large spinning disk as the storage medium, store files in their natural uncompressed state and then unmount/physically remove the device when the backup is done.  Pardon my rant, but:

In my very strongly held opinion:
[LIST=1]
[*]Backups should be manual enough to be in your face, automated enough to be reliable.
[LIST=1]
[*]Fully automatic backups are ignored until they're needed, and then they're found to be inadequate. 
[*]Sooner or later the directories/files you are backing up becomes obsolete and new, important stuff is not backed up because nobody thought of it. 
[*]It's best IMO to require somebody to do something.  Plug in a drive and start the backup, for example. Make examination of the script and backup sources a part of the human process. 
[/LIST]
  
[*]If it's always online, it's not a backup.
[LIST=1]
[*]Online means susceptible to theft, ransomware, electrical damage, accidental deletion. 
[/LIST]
  
[*]If it's in the same building as your hardware, it's not a backup.
[LIST=1]
[*]If your building burns down or is robbed, you have no backup. 
[/LIST]
  
[*]rsync and similar tools are not backups.
[LIST=1]
[*]They copy current contents but dumbly repeat accidental deletions or modifications. 
[*]They don't keep any sort of history. 
[*]That said, they CAN BE USEFUL in conjunction with a real backup. 
[/LIST]
  
[*]dd is not a backup.
[LIST=1]
[*]dd, especially at the device level, assumes a lot about where the data will be restored. 
[*]This automatically means difficulties when being restored to some other type of device. 
[*]This type of backup also copies dead blocks on the source and destination devices. 
[*]When not used at the device level there are much better alternatives. 
[/LIST]
  
[*]If it's reachable from the Internet, it's not secure.
[LIST=1]
[*]If you can reach it online and your credentials are stored on your box, and your box gets hacked, then your backup can be easily compromised. 
[/LIST]
  
[*]If it's "on the cloud" it's not your data and should be considered to be public, because sooner or later it will be.
[LIST=1]
[*]I shouldn't have to say anything here. The Internet is full of horror stories about private data stored on the cloud. 
[/LIST]
  
[*]If it requires proprietary software or hardware to extract, it's not a backup.
[LIST=1]
[*]If you don't have at least 3 **new** spares of the proprietary device and/or its software in an alternate location, you'd just as well not do a backup. 
[*]If you haven't done a full restore and successfully retrieved your data, then don't count it as a backup. 
[*]You need to keep at least one spare device/software in every location you store backups, disconnected. 
[/LIST]
  
[*]Your uptime is your most valuable asset.
[LIST=1]
[*]Backups should be easily searchable and be able to extract single file easily with minimal training. 
[*]When disaster strikes, you (or your IT staff) are stressed and in a hurry. 
[*]If you're in a business and 300 people can't work because some data is missing, you're paying all those people until the system is back up. 
[*]Spending more money or more time during backups is probably worth it. 
[/LIST]
  
[/LIST]

Here's what I do. It's more expensive than some backup techniques, but it has the advantage of being the most universal, standard format, easily searchable mechanism I can think of.
[LIST=1]
[*]I use git for text files that frequently change and need specific tracking of who did what and when. 
[*]I have a front-loading SATA cartridge that accepts a standard SATA 3.5" drive.  You could also use a USB3 drive, although that's slightly more expensive. 
[*]Buy at least 3 large drives. Buy the biggest drive that is economically feasible.
[LIST=1]
[*]Look at larger and larger drives until the price for the size increase starts to increase significantly. 
[*]Do NOT buy the cheapest drive of a category. 
[*]Cache, greenness and all that do not matter since this is a backup drive which will spend most of its time in a safe, unconnected from the world. 
[*]Speed matters somewhat, it matters more as you need to store larger backups. 
[/LIST]
  
[*]Format with a single large partition.
[LIST=1]
[*]Use something standard and stable as a partition format. 
[*]I use xfs. 
[*]You use whatever makes the most sense. 
[*]Mark the drive with a serial number, not what's on it.  "Backups 201609" for me would be a drive whose first backup happened this month. 
[/LIST]
  
[*]Every backup uses a different drive.
[LIST=1]
[*]The device containing today's backup goes to another site ASAP. 
[*]Hopefully have one or more off-site locations where you store alternating backups in a way that prevents damage from theft, fire, water or other natural disaster. 
[/LIST]
  
[/LIST]
Assuming I mount the drive on /var/backups:


[LIST=1]
[*]Define the list of directories you want backed up each time. 
[*]Clean out unwanted junk each time before the backup begins. 
[*]Get the total size needed for all combined directories. 
[*]Check the backup device for adequate space.
[LIST=1]
[*]Delete an old backup if necessary. 
[*]See below for logic in choosing what to delete. 
[/LIST]
  
[*]As root run a script with something like:
[LIST=1]
[*]export DEST="/var/backups/-`date +%Y$1%m$1%d`/`hostname -s`" 
[*]mkdir -p $DEST 
[*]cp -rax /etc $DEST/ 
[*]cp -rax /home $DEST/ 
[*]export MYSQLDEST="$DEST/var/lib/mysqlbak" 
[*]mkdir -p $MYSQLDEST 
[*]mysqldump ... (see [http://dev.mysql.com/doc/refman/5.7/en/backup-policy.html](http://dev.mysql.com/doc/refman/5.7/en/backup-policy.html)) 
[*]... 
[/LIST]
  
[*]Note that:
[LIST=1]
[*]I DO NOT zip or encrypt anything that isn't normally zipped or encrypted.
[LIST=1]
[*]You may need to make exceptions. 
[/LIST]
  
[*]I keep files in their normal directory within the $DEST space. 
[*]This makes everything extremely easy to search and extremely easy to restore. 
[*]I use -rax which prevents symbolic links from sucking in files from some other directory. 
[/LIST]
  
[/LIST]
Deleting:


[LIST=1]
[*]You generally want to keep one of every so many older backups. 
[*]You want frequent backups for the latest information. 
[*]You want something to show what happened 3 years ago. 
[*]You don't necessarily need to save frequent backups of what happened 3 years ago. 
[*]This means that when deleting you mark one backup per month (or whatever) to be kept. You may have more than one level of deletions:
[LIST=1]
[*]When you get backups that are older than a year, keep the first one every month. 
[*]When you get backups that are older than 2 years, keep the first one every even month. 
[*]At 3 years,  keep one every 4 months. 
[*]Whatever makes sense for your situation. 
[*]At some point you've deleted all the ephemeral backups on the drive (you want to keep everything on the drive), so just throw it in the safe. 
[/LIST]
  
[/LIST]

I've butted heads with other IT professionals over this methodology, but I still say my way is better.

---

### Post by 1clue on 2016-09-26
Sorry, forgot something:

Backup data and settings, not software.

If possible, keep settings on a source control system like git so you know what changes are due to the system upgrade and what changes were made by you.

---

### Post by Robbyx on 2016-09-26
Thank you. My experience is very similar in that I have kept all sorts of backups that have proved to be useless when I have tried to recover files. One was so bad I could not work out where the files were let alone get to the stage of recovering them.

---

### Post by DuckHook on 2016-09-26
@OP

In answer to your title (rather than the body of your text which talks almost exclusively about backups), I would suggest the following:

[LIST=1]
[*]Backups, backups, backups.
[*]Apparmor as many apps as possible but your browser for sure.
[*]Don't run scripting languages like java or flash.
[*]Don't succumb to deplorable security habits like automated login, etc.
[*]Confine as many apps as possible by running them inside containers or VMs.
[*]Don't be stupid. (This last is the single biggest thing you can do to protect yourself. All other techniques don't matter if this one is ignored).
[/LIST]

---

### Post by 1clue on 2016-09-26
My first restore, as mentioned above, was so bad that I could not get any data at all from any of the tapes I'd written. It was just the shock I needed to realize that my "backups" meant nothing, and to undo all the media hype about what backups are really all about. It's important that people understand what's really happening and why it should be done a certain way. It's such a fundamentally simple concept that people don't think it out.

There is so much software out there that will help you "backup your system" or "backup your network" and the reality is that having sane backups requires careful thought and planning no matter what software you use. Adding layers of complexity to it does nothing but cause extra points of failure. When it comes down to crunch time, the simpler the better, and seconds count.

My experience and data loss bit me hard enough that I still rant about it 20+ years later.

SATA drives slide into almost anything.  USB drives attach to almost anything. Partition formats, once stable, are not fluid and therefore readable on anything for decades to come. Who's to say that some ABC company will still be in business when I need my data restored? Who says the device will still be relevant?

The lion's share of what I need to backup is pretty tiny, with respect to work. There are some very large databases though, so that makes a difference. Generally speaking there is a lot of room for backups on a single drive, but you need to rotate those drives out to prevent a single device failure or a single other catastrophic event from eliminating all your backups. This includes my most recent catastrophe for my home setup, accidentally deleting a few years of photos from my backup. It reminded me yet again why you should be careful when using wildcards while removing files.

---

### Post by 1clue on 2016-09-26
> **DuckHook said:**
> @OP

In answer to your title (rather than the body of your text which talks almost exclusively about backups), I would suggest the following:

[LIST=1]
[*]Backups, backups, backups. 
[*]Apparmor as many apps as possible but your browser for sure. 
[*]Don't run scripting languages like java or flash. 
[*]Don't succumb to deplorable security habits like automated login, etc. 
[*]Confine as many apps as possible by running them inside containers or VMs. 
[*]Don't be stupid. (This last is the single biggest thing you can do to protect yourself. All other techniques don't matter if this one is ignored). 
[/LIST]


I agree with most of this, except item 3. 

Java is not a scripting language, it's a compiled language which runs on a VM. As such it's no less safe than anything else running in a VM.

Flash is, unfortunately, inseparable from the mainstream Internet. I'd go without flash if I could do so and still do my job, which includes interacting with others who use Flash.

And in general, scripting languages are here to stay too. JavaScript is an inseparable component of html5. As much as I hate it, it's getting more integrated rather than less integrated.  Local shell scripts exist as integral parts of every version of Linux, and probably every operating system.

Peace.

---

### Post by DuckHook on 2016-09-26
> **1clue said:**
> I agree with most of this, except item 3."Don't run scripting languages like java or flash." &#8594; "Run absolute minimum of scripting languages or any other language." There; fixed it. :D While we are at it, the same admonition applies to PPAs or non-repository apps, though I suppose that is covered under "don't be stupid".

Some people add totally extraneous "stuff" to their computers like squirrels hoarding acorns. What they don't understand is that every such "extra" is another attack vector. One of the best security habits that new users can cultivate is "Keep It Stupidly Simple", which is fundamentally your approach to backups (an approach I completely agree with).

---

### Post by 1clue on 2016-09-26
That I can agree with.

I think in general you're talking about web scripted languages, things that run in a browser. That's certainly an attack vector and easier to get onto a system than much of the other attack vectors. Certainly there is a risk, and also certainly most of these languages are used in day-to-day communications with coworkers. There's a limited amount you can do without crippling yourself. It's a balancing act between security and functionality, and each person needs to understand the issues and make their own decision.

Next IMO would be cross platform documents with built-in scripting languages, like Microsoft Office docs (word, excel, etc) where script functionality is implemented on every platform. Again, it's a balance.

I certainly understand the squirrels analogy. My wife's smart phone is a prime example. I've been trying to teach her about permissions and likely malware, she just doesn't get it.

The counter to the squirrels thing is that in order to function in a certain capacity you need the tools commonly used in that capacity.  At least to the point of data interoperability, but sometimes in the application space as well. The only hard and fast rule that always applies is, "don't be stupid." I have several off-the-reservation apps, as PPAs, as commercially supplied binaries and as compiled source code. I do my research and try to avoid stupidity.

One thing I don't think has been mentioned much in this thread is sudo. Sudo with a password required is risky enough even though sometimes necessary, but sudo with NOPASSWD falls into your "stupid" catch-all.

---

