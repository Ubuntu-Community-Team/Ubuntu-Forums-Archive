---
title: "Do you have a seperate home partition? If not: Why not?"
date: 2011-11-19
forum: The Cafe
---

### Post by Bazon on 2011-11-19
I have always one and loving it! Even after a fresh install, all files and settings remain! :-)
I wonder why this isn't a default setting / why not everybody uses one.
What are the reasons for that?


PS:
Of course, for different OS versions, I don't share the home partition. Or, to be more precisely: I don't share the whole home partition! I only share the fixed folders for files via "bind" in the /etc/fstab, e.g.:
```
/mnt/sda5/bazon/Downloads	/home/bazon/Downloads	  none  bind  0  0
```
That way, files are always shared between different OS versions, but settings aren't.

I love linux flexibility! :-)

---

### Post by Elfy on 2011-11-19
Most - in fact the majority - of my data is in another partition - all I ever need to keep from my /home when I reinstall is a few of the config folders - so no point for me to have it seperate.

---

### Post by BigSilly on 2011-11-19
> **forestpiskie said:**
> Most - in fact the majority - of my data is in another partition - all I ever need to keep from my /home when I reinstall is a few of the config folders - so no point for me to have it seperate.

I don't tend to keep config files personally. I have found in the past that if software is updated then old config files can cause issues. 

I have a separate partition for my personal stuff, but I don't have a separate home partition. I just drag and drop around to backup what I want to keep onto a separate partition and an external drive, and restore whatever I need to use directly into my current home folder from my separate partition.

---

### Post by lovinglinux on 2011-11-19
Yes. I  can't live without it.

---

### Post by Elfy on 2011-11-19
> **BigSilly said:**
> I don't tend to keep config files personally. I have found in the past that if software is updated then old config files can cause issues.When I say few - I mean 3 :) firefox/tbird and xchat - not had any issues with those personally.

---

### Post by BigSilly on 2011-11-19
> **forestpiskie said:**
> When I say few - I mean 3 :) firefox/tbird and xchat - not had any issues with those personally.

Yeah of course. I suppose I'm a bit old fashioned in that I just move files around as and when. Maybe I should try a separate home partition, but I sort of already feel that I have one in a way.

---

### Post by Elfy on 2011-11-19
> **BigSilly said:**
> Yeah of course. I suppose I'm a bit old fashioned in that I just move files around as and when. Maybe I should try a separate home partition, but I sort of already feel that I have one in a way.

Possibly we are talkign at cross purposes here - what I mean is that I copy/move those few to new installs as and when I need to :)

But it is possible that I'm just rambling too ;)

---

### Post by BigSilly on 2011-11-19
> **forestpiskie said:**
> Possibly we are talkign at cross purposes here - what I mean is that I copy/move those few to new installs as and when I need to :)

But it is possible that I'm just rambling too ;)

No I get you. It's me that's rambling. Sorry. :D

---

### Post by Elfy on 2011-11-19
It'll be watching Burnley and Leeds on the BBC ...

---

### Post by odiseo77 on 2011-11-19
I have a /home partition and a huge NTFS partition where I store all my data (this one is shared between Debian, Windows and Ubuntu).

---

### Post by fatality_uk on 2011-11-19
Does my C:\ drive count? :D

---

### Post by CharlesA on 2011-11-19
I don't have a separate home partition, mostly cuz I'm lazy and I don't want to mess with it.

Plus I keep a backup of said home folder on my RAID array (and external media)

---

### Post by Perfect Storm on 2011-11-19
Voted Yes, though I have my stuff on different partitions.

sda (ext4)
/boot
|- /<root>
|- /var (reiser)
|- swap
|- /home
|- /games

sdb (ext4)
/storage
/multimedia

---

### Post by obithius on 2011-11-19
I don't because,though I've been using ubuntu happily for about 2 years,I wouldn't have a clue as to why I should or how.

---

### Post by CharlesA on 2011-11-19
> **Artificial Intelligence said:**
> Voted Yes, though I have my stuff on different partitions.

sda (ext4)
/boot
|- /<root>
|- /var (reiser)
|- swap
|- /home
|- /games

sdb (ext4)
/storage
/multimedia

Nice way to do it.

I've got got mine set up like so:

sda
/

sdb
/array

Like I said, lazy. :D

---

### Post by Elfy on 2011-11-19
> **obithius said:**
> I don't because,though I've been using ubuntu happily for about 2 years,I wouldn't have a clue as to why I should or how.

Then I'd say that there is no need to :)

---

### Post by Plumtreed on 2011-11-19
I guess it is important to have a /home partition when you are inclined to change distros. No I don't usually use a /home partition.

*Why not?,*I don't see the value in having a /home partition when I just upgrade as changes occur.

I do have a separate /home partition on a eeePC 701 but that is to extend the disk size to include an 'external' ssd......sumthin peculiar to the 701 cos of the small capacity!

..be interesting to hear why others consider a /home partition worthwhile:P

---

### Post by Old_Grey_Wolf on 2011-11-19
I don't have a separate /home partition. I don't need to. I have multiple partitions or VMs.

I install two versions of a distro or two different distros using multiple partitions or VMs. When I find a version or a distro I want to use; then, I copy the needed /home data from one to the other. Then I delete the unneeded partition or VM.

I also use deja-dup just in case.

---

### Post by Copper Bezel on 2011-11-19
I do, just for the security of knowing I can install the OS if I want to upgrade or if something goes horribly awry with a minimum of fuss. It's also just nice to *know* that my user and system data are separate.

It's really useless and entirely psychological, and it was not fun when I ran out of space on / during an application install that one (*or three*) times and had to start deleting icon themes from a TTY to free up enough space to authenticate into Gnome.

But it's neat and I like it, and it's easier than migrating data back into a fresh install, so it saved me a step in the upgrade to Natty and Oneiric. (I didn't want to trust the upgrade process through the package manager for these two releases.)

---

### Post by MG&amp;TL on 2011-11-19
Sometimes I can't be bothered. Typically I never dual-boot that often, and it's easier to use the nice easy installer when I'm installing something new. (although I can of course use the manual installer).

And if you're meant to back your stuff up anyway, what's the point?

Also what if you install a load of programs but have no documents, or vice versa. Sure you can change it, but then it's advisable to back up again...

just my 2p.

(and yes, I have had separate /home partitions before, so you can't say I'm too lazy to do it.)

---

### Post by BrokenKingpin on 2011-11-19
No, mainly because I store all my files on my file server.

---

### Post by oldos2er on 2011-11-19
Yes, I tend to use different home partitions for different iterations of Ubuntu though. I mostly keep separate Music and Video partitions, since those are the largest disk-space-wise.

---

### Post by KingYaba on 2011-11-19
Nope. One hard drive for Linux, one hard drive for Windows, and one for storage. No partitioning schemes. I like it simple.

---

### Post by jjex22 on 2011-11-20
Not any more - I still use windows and bsd so I need a partition neutral to all - so it's formatted to FAT32 - there's litterally nothing of my data in my home directory, when I set up I always point programs at equivalent folders on the data partition.

When I started out, I followed a guide to create a classic linux install of partitions for
/
/boot
/usr
/var
/temp
/home

But when I upgraded to 10.04 and (as i'd been an experimenting noob) decided to do a clean install - accidentally let ubuntu do a default install and noticed that it didn't effect my performance at all, so the only benefit was security and I decided that for my usage it was an acceptable level of risk, so then there was just the root partitions for a year.

Now I use BTRFS instead of EXT4 and just add those directories to subvolumes, except for a boot partition obviously.

---

### Post by ilovelinux33467 on 2011-11-20
Yes. Mainly because when I install Mageia or Fedora it will automatically set up a seperate home partition for me.

---

### Post by tersogar on 2011-11-20
If it is your main computer it will be illogical not to have a home partition. After a clean install not only the data but even the favorite list and the podcast on my Rhythmbox  was there.

---

### Post by Plumtreed on 2011-11-20
> **tersogar said:**
> If it is your main computer it will be illogical not to have a home partition. After a clean install not only the data but even the favorite list and the podcast on my Rhythmbox  was there.

It may be more logical to do an 'upgrade' rather than a clean install......especially if it is your main computer!

---

### Post by szymon_g on 2011-11-20
i have 2 disks raid10 array.
there are two partitions on each disk:
150 mb /dev/md0 /raid0/ for /boot
rest for /dev/md1 and, on the top of it i created lvm2 - which lets me to set sizes of "partitions" /so data in, let say, /var wont eat everything/.

i find this solution much better than "just" simple partitions- i can always easily add new disks! (shame that ubuntu livecd doesn't support lvm/raid)

---

### Post by stinkeye on 2011-11-20
No.
I run two installs of ubuntu ...the latest and the previous release.
Keep music, movies podcasts bups etc on separate disk. 
When I am happy with the stability of the latest release
I copy over my ~/.opera folder and then other configs as needed.
Then the previous release install is overwritten with the latest beta release.
...and around it goes.

---

### Post by Tibuda on 2011-11-20
yes, I have drive C: for the OS and apps and drive E: for my documents, media and more stuff.

---

### Post by fantab on 2011-11-20
No, I don't use a separate /Home. I use a Linux Data Partition to store all my data.

Also I don't believe in carrying those configurations and preferences from one Installation to another. And I always do a clean, fresh installation- never upgrade.

---

### Post by CharlesA on 2011-11-20
> **Copper Bezel said:**
> I do, just for the security of knowing I can install the OS if I want to upgrade or if something goes horribly awry with a minimum of fuss. It's also just nice to *know* that my user and system data are separate.

That's a good idea, actually. I wonder how much "leftovers" I would have to deal with if I just copied my entire home folder from my server to a clean install of a newer version (12.04, when it comes out.)

---

### Post by effenberg0x0 on 2011-11-20
- / is on SSD01
- /home is on 2x SATA3 HDD RAID 1
- vmware VMs are on SSD2
- $home/backup has all the important stuff incrementally updated every hour. Twice a day cron+rsync sends it to NAS (8xSATA3 HDD RAID6).

Having a separate home partition has helped a couple times. Most .files can be disregarded, but some are worth keeping. These are regexp'ed to $home/backup.

---

### Post by muep on 2011-11-20
No, because I should have a backup of /home contents in any case.

When I have a backup, I can just use it to restore my /home contents after a fresh install.

---

