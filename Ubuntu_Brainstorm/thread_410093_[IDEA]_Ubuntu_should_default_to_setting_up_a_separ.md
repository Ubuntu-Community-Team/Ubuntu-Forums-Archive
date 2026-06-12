---
title: "[IDEA] Ubuntu should default to setting up a separate /home partition"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by viciouslime on 2007-04-15
With a separate home partition fixing a broken ubuntu is never more difficult than sticking the cd in, double clicking install, pressing next a few times and that's that. Your computer restarts and all your documents and settings are loaded as usual. OpenSuSE now defaults to doing this and it makes life so much easier.

It is very easy to do this now in ubuntu, however, without doing this by default, many users simply won't be aware of the advantages... many don't even know what a partition is.

---

### Post by miggols99 on 2007-04-15
I think this is a very good idea. Newbies usually don't want to mess around with partitions due to them being scared that they might lose data.

---

### Post by =0verlord= on 2007-04-15
While it's a great system and I employ it myself, it's a fundamental shift in how the disk is set up and I'm not sure how feasible it is to implement.  Going to a two partition setup that separates data and system requires balancing the available space between them - and that varies greatly between users.  If you can come up with a way to accurately gauge user requirements at install time, I'm all ears.  As an option for advanced users, I can see this as handy but not strictly necessary as they'll usually know how to do it anyway.  I feel like a Gnome dev saying this, but this has a good probability of confusing people and causing unbalanced partitions - even I  have to rebalance mine every once in a while and nondestructive partitioning is *always* dangerous.

---

### Post by plb on 2007-04-15
If I'm not mistaken, debian has this option as well. I also use this method :D

---

### Post by Turgon on 2007-04-15
I like the idea, but overlord has some great points. The worst thing is if the installer makes a / partition thats too small and then the inexperienced first time user runs out of space when he installs quake 4 and unreal tournament 2004. On the other hand, harddrives are getting so big these days that it shouldn't be too much trouble to just make a very big / just to be sure.

But on the other hand, will an inexperienced user that does not know how to make a seprat home partition be able to use the benefits of it?

---

### Post by =0verlord= on 2007-04-15
After thinking about it some more, if someone comes up with minimum system/data sizes and be configurable between those values that would work pretty well.  However, leaving out older hardware by assuming large drive size is not something I like a lot, as laptops and just old machines in general will be screwed.  Food for thought, I'm still ambivalent about the general idea.

---

### Post by Rui Pais on 2007-04-15
In my experience, either with ubuntu as other distros, and with separated home partitions, the / partitions rarely hits the 10G with gnome, kde and an extra light DE (usually i have e17, its' cvs source).

i said a safe choice would be 50/50 for free space till 20G and 10~15G for / and rest for /home for free space bigger then 20G.

Note that due to the fact that linux mount OS always as / and /home that would be full transparent to the newbie user... If he/she don't understand partitions he/she would note the division among two partitions.

---

### Post by viciouslime on 2007-04-15
> **=0verlord= said:**
> While it's a great system and I employ it myself, it's a fundamental shift in how the disk is set up and I'm not sure how feasible it is to implement.  Going to a two partition setup that separates data and system requires balancing the available space between them - and that varies greatly between users.  If you can come up with a way to accurately gauge user requirements at install time, I'm all ears.  As an option for advanced users, I can see this as handy but not strictly necessary as they'll usually know how to do it anyway.  I feel like a Gnome dev saying this, but this has a good probability of confusing people and causing unbalanced partitions - even I  have to rebalance mine every once in a while and nondestructive partitioning is *always* dangerous.

Quite right, but opensuse manages it, maybe we should look at how they do it and copy that. TBH though, I don't see why anyone would need more than say 15gb as a root partition and the rest as home with a small amount for swap, remember this is only default I am talking about, so anyone who did need different would most likely know this and adjust it at install.

---

### Post by aysiu on 2007-04-15
I think it should go as follows:

1. The default should be to create a separate /home, but you should be able to easily choose another option

2A. For the default option, if the hard drive is bigger than 20 GB, and it's a Ubuntu-only installation, 10 GB should go to / and the rest should go to /home

2B. If the hard drive is between 10 GB and 20 GB, and it's a Ubuntu-only installation, 5 GB should go to / and the rest to /home

2C. If the hard drive is less than 10 GB, there should not be a separate /home partition

3A. If the hard drive is bigger than 40 GB and a dual-boot, 10 GB should go to / and the rest to /home

3B. If the hard drive is between 30 GB and 40 GB and a dual-boot, 5 GB should go to / and the rest to /home

3C. If the hard drive is less than 30 GB and a dual-boot, there should be no separate /home partition.

---

### Post by viciouslime on 2007-04-15
> **Turgon said:**
> I like the idea, but overlord has some great points. The worst thing is if the installer makes a / partition thats too small and then the inexperienced first time user runs out of space when he installs quake 4 and unreal tournament 2004. On the other hand, harddrives are getting so big these days that it shouldn't be too much trouble to just make a very big / just to be sure.

But on the other hand, will an inexperienced user that does not know how to make a seprat home partition be able to use the benefits of it?

Personally, I always install games to a folder titled games in my home directory, that way there is one less thing to reinstall when I format. Granted though, if there were to be more than one user wanting to play the game this isn't really a good option, however someone has proposed a shared folder for gutsy gibbon so it could go there...

---

### Post by viciouslime on 2007-04-15
> **aysiu said:**
> I think it should go as follows:

1. The default should be to create a separate /home, but you should be able to easily choose another option

2A. For the default option, if the hard drive is bigger than 20 GB, and it's a Ubuntu-only installation, 10 GB should go to / and the rest should go to /home

2B. If the hard drive is between 10 GB and 20 GB, and it's a Ubuntu-only installation, 5 GB should go to / and the rest to /home

2C. If the hard drive is less than 10 GB, there should not be a separate /home partition

3A. If the hard drive is bigger than 40 GB and a dual-boot, 10 GB should go to / and the rest to /home

3B. If the hard drive is between 30 GB and 40 GB and a dual-boot, 5 GB should go to / and the rest to /home

3C. If the hard drive is less than 30 GB and a dual-boot, there should be no separate /home partition.

That's exactly what I was in the middle of typing, I even had the same options for sizes! You beat me by like 20seconds! lol

But anyway yeh, basically I couldn't agree more, this is exactly how I imagined it. I would've also added that >40GB would be 15GB to / and the rest to /home but numbers could be argued all day, the point is I really think this would be a nice enhancement for the majority of users. It must of course be stressed that it would have to be very easy to NOT do this should you want a different partition layout, however, I don't see that being much of an issue, as it is already very easy TO DO this, it just isn't done by default so lots of users don't know it can be done.

---

### Post by viciouslime on 2007-04-15
> **=0verlord= said:**
> After thinking about it some more, if someone comes up with minimum system/data sizes and be configurable between those values that would work pretty well.  However, leaving out older hardware by assuming large drive size is not something I like a lot, as laptops and just old machines in general will be screwed.  Food for thought, I'm still ambivalent about the general idea.

I also don't like the idea of leaving out older hardware and for this reason anything with a hard drive less than 10gb should default to everything on one partition :) But for the majority of users these days whose machines have hard drives of sizes 200gb+ it would almost certainly be a good thing.

---

### Post by =0verlord= on 2007-04-15
I'm perfectly happy with what you guys have suggested.

---

### Post by viciouslime on 2007-04-15
> **=0verlord= said:**
> I'm perfectly happy with what you guys have suggested.

Good. Now we just need to get the devs behind it... roll on Forum Ambassadors!

---

### Post by rsambuca on 2007-04-15
I'm not opposed to the idea, but personally I never use a separate partition for /home.  I have a separate partition for my media files, documents, etc, but I don't mind setting things up anew with an upgrade or re-installation.  Really, though, how often do you expect a new user to be re-installing and need the saved /home settings anyways?  ie.  how many new casual users will be re-installing if things don't work the first time?  If I got every single person I know to try out ubuntu (and didn't install it for them), maybe one or two would try re-installing if it didn't work the first time.  I think the rest would just say - Oh well, kinda neat, but I like windows.

---

### Post by viciouslime on 2007-04-15
> **rsambuca said:**
> I'm not opposed to the idea, but personally I never use a separate partition for /home.  I have a separate partition for my media files, documents, etc, but I don't mind setting things up anew with an upgrade or re-installation.  Really, though, how often do you expect a new user to be re-installing and need the saved /home settings anyways?  ie.  how many new casual users will be re-installing if things don't work the first time?  If I got every single person I know to try out ubuntu (and didn't install it for them), maybe one or two would try re-installing if it didn't work the first time.  I think the rest would just say - Oh well, kinda neat, but I like windows.

Well they might get hooked on it then a new version will come out and they'll decide to do a fresh install to avoid potential problems. Or.... errrm.... Ok, perhaps reinstalling isn't something done by new users THAT often, but now if they do totally trash X, or whatever and the only help anyone on the forums can give involves using the very scary command line, then they could just reinstall, which they'll be used to doing with windows anyway, only with linux and a separate /home you reinstall and you can't tell you've done so. Everything goes back to being just like it was.....magic :D

That was always the worst thing on windows after its usual 3months-of-use-grinding-to-a-halt-slowdown-for-no-apparent-reason thing it does, reinstalling was fairly straightforward, but you would spend hours stopping it from grouping things on the taskbar, telling it to use firefox instead of IE, etc. etc. and then there's installing programs! <shudders at the memory of it all>

---

### Post by hardyn on 2007-04-15
how does linux do its partitioning?

i run a dual boot system, 2 primary windows parititions and 2 primary linux partitions (/ and swap)  IIRC 4 primary paritions is the limit for an IDE device.  so again, more condidions than just size for determination of disk divy.

I do like the idea, and will probably consider something to this effect on next install, but, it might be a little complicated when considering the total possiblities of hard disk configurations.

2cents.

---

### Post by tom56 on 2007-04-15
I don't think that separate partitions for home is the way to go. What we should be doing is concentrating on making it easier to do backups, thus eliminating the need for a separate home, and preventing problems from occurring after disk failure at the same time.

---

### Post by viciouslime on 2007-04-15
> **tom56 said:**
> I don't think that separate partitions for home is the way to go. What we should be doing is concentrating on making it easier to do backups, thus eliminating the need for a separate home, and preventing problems from occurring after disk failure at the same time.

Why not do both? Lots of people simply don't have space for a backup. if I wanted to back-up now and then wipe completely and reinstall I would need to find someone willing to lend me a 500GB HDD... or burn over a 100 DVDs, aside from the massive amount of time involved, both of these options are clearly unpractical. With many people getting larger and larger HDDs (and filling them) there simply isn't the space to back EVERYTHING up.

---

### Post by PriceChild on 2007-04-15
> **=0verlord= said:**
> While it's a great system and I employ it myself, it's a fundamental shift in how the disk is set up and I'm not sure how feasible it is to implement.  Going to a two partition setup that separates data and system requires balancing the available space between them - and that varies greatly between users.  If you can come up with a way to accurately gauge user requirements at install time, I'm all ears.  As an option for advanced users, I can see this as handy but not strictly necessary as they'll usually know how to do it anyway.  I feel like a Gnome dev saying this, but this has a good probability of confusing people and causing unbalanced partitions - even I  have to rebalance mine every once in a while and nondestructive partitioning is *always* dangerous.> **tom56 said:**
> I don't think that separate partitions for home is the way to go. What we should be doing is concentrating on making it easier to do backups, thus eliminating the need for a separate home, and preventing problems from occurring after disk failure at the same time.

In my opinion having different partitions to mount inside / is better than having all of your eggs in one basket. However I don't believe that an automated installer can decide what is best for the user. A program can't decide whether someone will install lots of apps or have lots of music.

The installer needs to have as little questions as possible and "just work". Those that even half know what they are doing can easily use ubiquity or the alternate installer to create all of these partitions. However for beginners to linux, a single "C:" drive is a perfectly fine and functioning way to work.

---

### Post by aysiu on 2007-04-15
One of the major advantages of a separate /home is the ability to do a new installation and retain your settings and files easily. It's not a matter of anything being wrong with the installation or files needing to be backed up.

For example, there are a lot of Dapper users who want to upgrade to Feisty next week. That's not going to be pretty. They either upgrade from Dapper to Edgy and then from Edgy to Feisty, which will take a *really* long time, even on a broadband connection, or they reinstall Feisty directly... in which case having a separate /home partition comes in handy.

---

### Post by viciouslime on 2007-04-15
> **aysiu said:**
> One of the major advantages of a separate /home is the ability to do a new installation and retain your settings and files easily. It's not a matter of anything being wrong with the installation or files needing to be backed up.

For example, there are a lot of Dapper users who want to upgrade to Feisty next week. That's not going to be pretty. They either upgrade from Dapper to Edgy and then from Edgy to Feisty, which will take a *really* long time, even on a broadband connection, or they reinstall Feisty directly... in which case having a separate /home partition comes in handy.

Exactly! (Thanks!:p)

---

### Post by tom56 on 2007-04-15
> **aysiu said:**
> One of the major advantages of a separate /home is the ability to do a new installation and retain your settings and files easily. It's not a matter of anything being wrong with the installation or files needing to be backed up.

For example, there are a lot of Dapper users who want to upgrade to Feisty next week. That's not going to be pretty. They either upgrade from Dapper to Edgy and then from Edgy to Feisty, which will take a *really* long time, even on a broadband connection, or they reinstall Feisty directly... in which case having a separate /home partition comes in handy.

But when I reinstall I just do a backup, then copy my /home back on to the new system.

I don't think that a separate /home is a bad idea per se, but I'd rather see developer time concentrated on making it easier to do backups. I also don't like the idea of the installer assuming how people will be using their computer and getting it wrong.

---

### Post by aysiu on 2007-04-15
> **tom56 said:**
> But when I reinstall I just do a backup, then copy my /home back on to the new system. And that's what *you* do, and that's fine. Not everyone has the *space* to make a full backup.

> I don't think that a separate /home is a bad idea per se, but I'd rather see developer time concentrated on making it easier to do backups. The two aren't mutually exclusive. > I also don't like the idea of the installer assuming how people will be using their computer and getting it wrong. Then don't use it. It's just a sensible default for new users who might be confused about all these different partitioning options. You can always override it and do manually partitioning.

Anyway, the current installer already does guessing and assuming. That's what the "automatic resize and install Ubuntu in the available space" option does. And if you do a standard Ubuntu installation, it automatically creates a swap partition without asking you any questions.

In case you're not getting it--it's about defaults for inexperienced users.

Advanced or intermediate users can **always** use the *Manually Edit Partition Table* option and have full control over the installation process.

---

### Post by tom56 on 2007-04-15
> **aysiu said:**
> 
Anyway, the current installer already does guessing and assuming. That's what the "automatic resize and install Ubuntu in the available space" option does. And if you do a standard Ubuntu installation, it automatically creates a swap partition without asking you any questions.

But it's not a case of advanced vs. inexperienced user. Here's a crap example off the top of my head.

I'm a pro photographer. I have a 20gig hard drive. Because I'm only using my computer for one or two tasks (browsing the web and editing photos) I don't need much / but I need a big /home for all my photos. However the installer has halved my hard drive space. As an inexperienced user I don't know anything about partitions and assume that the basic Ubuntu install takes 10Gb of space. "Screw this" I think, and go back to Windows.

Like I said crap example, but you get the gist of it.

---

### Post by viciouslime on 2007-04-15
> **tom56 said:**
> But it's not a case of advanced vs. inexperienced user. Here's a crap example off the top of my head.

I'm a pro photographer. I have a 20gig hard drive. Because I'm only using my computer for one or two tasks (browsing the web and editing photos) I don't need much / but I need a big /home for all my photos. However the installer has halved my hard drive space. As an inexperienced user I don't know anything about partitions and assume that the basic Ubuntu install takes 10Gb of space. "Screw this" I think, and go back to Windows.

Like I said crap example, but you get the gist of it.Firstly, if the numbers aysiu and I suggested were used, this user would have a 15GB home partition and his / partition would have to be an absolute minimum of 2.5GB anyway, so he would only be losing 2.5GB of potential space for photos.

Secondly, your case is a very limited one, i.e. it applies to VERY few people, proportionally far more people would benefit from this change. Please remember I am talking about DEFAULT settings here, not your home partition WILL be XGB and your root partition WILL be XGB linux is all about choice, but lots of people get lost in the all the choice available, so good default options are required.

Finally... photos saved in raw formats can often be upwards of 100mb with a decent camera... how many professional photographers have a 20GB hdd? :p

EDIT: Just another quick thought. If it was windows vista you were going back to then you would need a minimum 40gb hard drive and the windows folder on a default vista install is over 15GB!!! This is just a side note, i realise your example wasn't perfect.

---

### Post by tom56 on 2007-04-15
[QUOTE=viciouslime]Finally... photos saved in raw formats can often be upwards of 100mb with a decent camera... how many professional photographers have a 20GB hdd? :p[/QUOTE]

Which is why I said it was a crap example :)

[QUOTE=viciouslime]Firstly, if the numbers aysiu and I suggested were used, this user would have a 15GB home partition[/QUOTE]

[QUOTE=aysiu]2A. For the default option, if the hard drive is bigger than 20 GB, and it's a Ubuntu-only installation, 10 GB should go to / and the rest should go to /home[/QUOTE]

I see that I've misread it now, but even then I'd say that 2.5Gb of wasted space is quite alot on a 20Gb drive. It's 12.5%.

---

### Post by viciouslime on 2007-04-15
> **tom56 said:**
> Which is why I said it was a crap example :)
Hence the ":p" :)

> **tom56 said:**
> I see that I've misread it now, but even then I'd say that 2.5Gb of wasted space is quite alot on a 20Gb drive. It's 12.5%.

It is, which is why this particular photographer would lose out with these new defaults very slightly. However, this is the case with changes made to all default settings. There will never be a setting that satisfies EVERYONE, else there'd be no point in making it a setting.

---

### Post by BungaMan on 2007-04-17
> **aysiu said:**
> I think it should go as follows:

1. The default should be to create a separate /home, but you should be able to easily choose another option


I have a different opinion on that.  I think the majority of people are unfamiliar with partitioning.  If they ever have to reinstall their system they are not aware that they would be able to rescue their home partition and do a complete new install anyway.  It would be a good option for an advanced user to be able to set this but an inexperienced user will only be confused.

But in any case, a separate home partition should be possible during install.  I lost mine a couple of days ago thinking damn if I'd only had it separate.

---

### Post by viciouslime on 2007-04-17
> **BungaMan said:**
> I have a different opinion on that.  I think the majority of people are unfamiliar with partitioning.  If they ever have to reinstall their system they are not aware that they would be able to rescue their home partition and do a complete new install anyway.  It would be a good option for an advanced user to be able to set this but an inexperienced user will only be confused.

But in any case, a separate home partition should be possible during install.  I lost mine a couple of days ago thinking damn if I'd only had it separate.

No they might not be aware that they could do this, but then they could be made aware either as a reply to their post on the forums, or on a wiki page describing ways to recover ubuntu should it suffer major breakage. Without this being the default they might not even be able to access their home folder to back-up their stuff if, say, the X-server dies.

---

### Post by aysiu on 2007-04-17
> **BungaMan said:**
> I have a different opinion on that.  I think the majority of people are unfamiliar with partitioning.  If they ever have to reinstall their system they are not aware that they would be able to rescue their home partition and do a complete new install anyway.  It would be a good option for an advanced user to be able to set this but an inexperienced user will only be confused.

But in any case, a separate home partition should be possible during install.  I lost mine a couple of days ago thinking damn if I'd only had it separate.
Well, that brings up a second point. Rather than scrapping the whole "create a /home partition by default" idea, how about making it so that a reinstallation is able to detect an existing /home partition and, by default, use it instead of reformatting it. (Again, you could always override the default if you did want to reformat the partition.)

It shouldn't be too difficult for the installer to scan the contents of the partition and see if there's anything that looks like a /home directory.

**More about this idea in its own thread**:
[[IDEA]: Auto-detect existing /home partition during installation](http://ubuntuforums.org/showthread.php?t=411871)

---

### Post by BungaMan on 2007-04-17
yes it is, anything to make the total bunch more stable and easy to recover from a loss, got my vote!  This is something that fits the definition of user friendly :)

---

### Post by qamelian on 2007-04-17
> **=0verlord= said:**
> While it's a great system and I employ it myself, it's a fundamental shift in how the disk is set up and I'm not sure how feasible it is to implement.  Going to a two partition setup that separates data and system requires balancing the available space between them - and that varies greatly between users.  If you can come up with a way to accurately gauge user requirements at install time, I'm all ears.  As an option for advanced users, I can see this as handy but not strictly necessary as they'll usually know how to do it anyway.  I feel like a Gnome dev saying this, but this has a good probability of confusing people and causing unbalanced partitions - even I  have to rebalance mine every once in a while and nondestructive partitioning is *always* dangerous.

It's not such a big shift. I can think of several distros that have automatically done this for ages when you allow the installer to automatically handle partitioning for you. I tried one (can't remember which right now) that by default would create separate /, /boot, /home, and /usr/local partitions!

---

### Post by altonbr on 2007-04-22
My votes in. Is there a lunchpad spec for this?

---

### Post by viciouslime on 2007-04-22
> **altonbr said:**
> My votes in. Is there a lunchpad spec for this?

I haven't created on yet, but I will do.

---

### Post by madman91 on 2007-04-22
my vote is in.. gogogogogogo 

This should have been default from 6.06 or earlier...

---

### Post by viciouslime on 2007-04-22
> **madman91 said:**
> my vote is in.. gogogogogogo 

This should have been default from 6.06 or earlier...

Couldn't agree more!

---

### Post by lemsto on 2007-04-23
> **aysiu said:**
> I think it should go as follows:

1. The default should be to create a separate /home, but you should be able to easily choose another option

2A. For the default option, if the hard drive is bigger than 20 GB, and it's a Ubuntu-only installation, 10 GB should go to / and the rest should go to /home

2B. If the hard drive is between 10 GB and 20 GB, and it's a Ubuntu-only installation, 5 GB should go to / and the rest to /home

2C. If the hard drive is less than 10 GB, there should not be a separate /home partition

3A. If the hard drive is bigger than 40 GB and a dual-boot, 10 GB should go to / and the rest to /home

3B. If the hard drive is between 30 GB and 40 GB and a dual-boot, 5 GB should go to / and the rest to /home

3C. If the hard drive is less than 30 GB and a dual-boot, there should be no separate /home partition.

+1

---

### Post by botulismo on 2007-04-23
This is a good idea. When I found myself toying with different distros before I decided on Ubuntu this would have saved me a bunch of time from copying music, photos, videos, papers, and other data over from my backup drive each time I wiped and put a new distro on... Plus this would make it easier for advanced users who prefer doing a fresh install every so often to do just that. It should be presented as an option in the guided partitioning at the beginning. Like "Do you want a separate home partition?" and then present some information like "This makes it easier to save your personal files in the event of a computer crash" or some such... And then be be given an option as to how much space it should occupy. Most beginners, if it were presented like that, would probably opt for it.

---

### Post by apoclypse on 2007-04-23
> **aysiu said:**
> Well, that brings up a second point. Rather than scrapping the whole "create a /home partition by default" idea, how about making it so that a reinstallation is able to detect an existing /home partition and, by default, use it instead of reformatting it. (Again, you could always override the default if you did want to reformat the partition.)

It shouldn't be too difficult for the installer to scan the contents of the partition and see if there's anything that looks like a /home directory.

**More about this idea in its own thread**:
[[IDEA]: Auto-detect existing /home partition during installation](http://ubuntuforums.org/showthread.php?t=411871)

Maybe the migration asssistant can be extended to copy files over form an existing home partition before going ahead with the install. Ubuntu gets upgraded enough that something really has to be done. It gest annoying having to transfer all my files and then having to install all my software from scratch.

---

### Post by tom56 on 2007-04-23
> **botulismo said:**
> ... and then present some information like "This makes it easier to save your personal files in the event of a computer crash" or some such

This is my main problem with this idea. People will misunderstand what a separate /home is for. Having a separate home ***does not*** make it any easier to recover files in the event of the system breaking. That's what backups are for.

---

### Post by altonbr on 2007-04-23
> **tom56 said:**
> This is my main problem with this idea. People will misunderstand what a separate /home is for. Having a separate home ***does not*** make it any easier to recover files in the event of the system breaking. That's what backups are for.

Then it makes it easier to do backups ;)

I found it extremely useful to separate Windows from my Data back when I used it, merely because of all the times Windows crashed. If Windows (or Ubuntu in this case) crashes, then you can us a recovery disk to find your data partition and recover the data. Or you can simply reinstall Windows with absolutely no worry that your data will be lost.

I'd say it makes computing easier (and in some cases, more efficient due to seek times, etc.).

---

### Post by zacinator on 2007-04-23
> Originally Posted by aysiu  
I think it should go as follows:

1. The default should be to create a separate /home, but you should be able to easily choose another option

2A. For the default option, if the hard drive is bigger than 20 GB, and it's a Ubuntu-only installation, 10 GB should go to / and the rest should go to /home

2B. If the hard drive is between 10 GB and 20 GB, and it's a Ubuntu-only installation, 5 GB should go to / and the rest to /home

2C. If the hard drive is less than 10 GB, there should not be a separate /home partition

3A. If the hard drive is bigger than 40 GB and a dual-boot, 10 GB should go to / and the rest to /home

3B. If the hard drive is between 30 GB and 40 GB and a dual-boot, 5 GB should go to / and the rest to /home

3C. If the hard drive is less than 30 GB and a dual-boot, there should be no separate /home partition.
> **lemsto said:**
> +1
+2

---

### Post by aysiu on 2007-04-23
> **tom56 said:**
> This is my main problem with this idea. People will misunderstand what a separate /home is for. Having a separate home ***does not*** make it any easier to recover files in the event of the system breaking. That's what backups are for.
People don't even have to *know* what a separate /home partition is, unless they want to override the defaults and do their own manual partitioning scheme.

This suggestion is made in conjunction with two other Gutsy ideas:

1. To have the installer [recognize and mount without reformatting existing /home partitions by default](http://ubuntuforums.org/showthread.php?t=411871&highlight=home) (again, the default can be overriden)

2. To have the installer [recognize existing accounts with the same name as the "newly created" username and assign the same user id.](http://ubuntuforums.org/showthread.php?t=410584&highlight=home)

If those sensible **defaults** (which can **always** be overridden by advanced users) are in place, no beginner would have to know what a separate /home partition is. This is the same way the swap partition is currently handled. If you tell Ubuntu to erase the whole disk, it'll automatically set up a swap partition for you. You don't have to know what a swap partition is unless you want to.

---

### Post by tom56 on 2007-04-23
> **aysiu said:**
> People don't even have to *know* what a separate /home partition is, unless they want to override the defaults and do their own manual partitioning scheme.

I agree with you there. If this is going to be done by default then I don't want people to be told about it. The person I was quoting was suggesting the installer explain what a separate /home is for. But I think this is an unhappy medium. Either you do it by default or you don't. The installer shouldn't explain the benefits because it will confuse people and - more to the point - if you have to explain to the user why it's a good idea then it isn't one.

---

### Post by MoebusNet on 2007-04-25
If Feisty had this as default, I might have been able to save my /home when the Feisty upgrade killed Edgy on my notebook.

+1

---

### Post by tom56 on 2007-04-25
[QUOTE=MoebusNet]If Feisty had this as default, I might have been able to save my /home when the Feisty upgrade killed Edgy on my notebook.[/QUOTE]

You can almost always still save it seperate partition or not. Boot up the Live CD and mount the drive - your install might be screwed but nothing should have touched your /home.

---

### Post by aysiu on 2007-04-25
> **tom56 said:**
> You can almost always still save it seperate partition or not. Boot up the Live CD and mount the drive - your install might be screwed but nothing should have touched your /home.
You might have missed the word *default* in the idea.

The idea is to have a separate /home partition **by default**

An idea that works in conjunction is [Gutsy should default to setting up a separate home partition](http://ubuntuforums.org/showthread.php?t=411871)

---

### Post by drf_av on 2007-04-25
+1 +1 +1 +1 +1
I've learned that the hard way, I just hope this had been implemented before.

---

### Post by Naralas on 2007-04-25
The objections to this are kinda silly, and mostly come from people who have decided that it's best to do it anyway.

DO IT
+10

It's one of the few ideas that adds without taking anything away.

---

### Post by tom56 on 2007-04-25
> **aysiu said:**
> You might have missed the word *default* in the idea.

The idea is to have a separate /home partition **by default**

An idea that works in conjunction is [Gutsy should default to setting up a separate home partition](http://ubuntuforums.org/showthread.php?t=411871)

No you've misunderstood me.

I was saying that when your install messes up, /home is usually ok even though it's on the same partition and is therefore recoverable using the Live CD. I was responding to MoebusNet's post - I thought I'd clicked quote but obviously not.

---

### Post by Rinzwind on 2007-04-26
[http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html](http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html)

Here's a take into creating te following partitions:

/ - Root partition
/home - Users home directory
/usr - Linux/BSD binary programs are installed here
/tmp - Temporary files partition
/var - Stores files which keep changing size, e.g. log, or squid caching files

The link also provides why this is better than the current version.

---

### Post by ronacc on 2007-04-26
a seperate /home makes good sense in most situations. if not default , perhaps a choice during install (do you want a seperate /home partition?).

---

### Post by hotani on 2007-04-26
Agreed, separate /home by default would save a lot of headaches. Now if only the live CD would recognize RAID arrays (my /home is on a RAID 1. I *really* hate installing with the alt. CD), but that's [another thread](http://ubuntuforums.org/showthread.php?t=410326).

---

### Post by altonbr on 2007-05-01
I just tried Mandriva 2007 - Spring One (or however the name goes) and although I hated the OS, I can confirm that during "simple partitioning" and "auto complete" in "normal" or "expert", Mandriva/diskdrake creates a separate home partition.

What was shocking was that I gave it 6GB of HDD space and 1GB of memory through VMWare, and it created a 3.2GB root, 666MB swap and 2.1GB home. Isn't that TINY!? But then again, if you're using a 6GB hard drive, I'm going to assume you're not using it for video editing or anything of the such.

---

### Post by jharbert on 2007-05-01
Definitely, I was very glad I initially set up my system with a separate home partition (found out about it while searching for how to divide up my hard drive for dual booting).  It's saved me multiple times (especially with upgrading).  One of my favorite features of Linux.

---

### Post by Naralas on 2007-05-01
Someone was saying it's easy to recover your home folder? Well it would be kinda nice if you didn't NEED to recover your home folder? It's just alive.

Pushing a Linux idea along is usually done best when it is compared to Windows.
Under XP I move Docs and Settings to a separate partition every time. It's an annoying task I always have to remember, and to remind my install of.
Don't give Gusty this flaw.

---

### Post by altonbr on 2007-05-02
> **Naralas said:**
> Someone was saying it's easy to recover your home folder? Well it would be kinda nice if you didn't NEED to recover your home folder? It's just alive.

Pushing a Linux idea along is usually done best when it is compared to Windows.
Under XP I move Docs and Settings to a separate partition every time. It's an annoying task I always have to remember, and to remind my install of.
Don't give Gusty this flaw.

How is this a flaw?

---

### Post by HeyItsMatt on 2007-05-03
I think this is a good idea too - maybe instead of having it be the "default" you can simply give the user an option to create a seperate /home partition.  I think even a brief explanation of what purpose this serves in the installer is enough for most newbies who are knowledgeable enough to hear about / try out Linux in the first place.

I'm still a Linux newbie, and right now I would like to upgrade to Feisty Fawn (perhaps it's not necessary, I don't know) but I'm very nervous after seeing numerous "upgraded to Feisty, computer died" threads on this forum.  I have my /home folder files and documents backed up, so if I do upgrade and kill Ubuntu somehow I haven't lost anything - but it would be great if the /home directory was on a separate partition that just showed up automatically after reinstalling Ubuntu.  Basically it would make things easy, automatic, and time-saving.

I am planning to move the /home directory to a new partition, but the directions I have seen so far are a bit scary and intimidating, and involve doing arcane things in the command line and to fstab that may or may not screw everything up.  It really makes me wish I had been given a simple no-brainer option to do this on installing Ubuntu.

I don't really understand the objections to this idea since I don't see how it can hurt to just offer an option for a common, useful partition configuration in the installer.

---

### Post by viciouslime on 2007-05-04
> **Naralas said:**
> Someone was saying it's easy to recover your home folder? Well it would be kinda nice if you didn't NEED to recover your home folder? It's just alive.

Pushing a Linux idea along is usually done best when it is compared to Windows.
Under XP I move Docs and Settings to a separate partition every time. It's an annoying task I always have to remember, and to remind my install of.
Don't give Gusty this flaw.

Yeh you're right, and we should get rid of seatbelts in cars and just build cars that don't crash :p ... it's not going to happen, all software is liable to break, and if someone tinkers with it and doesn't know what they're doing, then it's nice to know that his/her data will be safe.

---

### Post by Herman on 2007-05-04
Well I can't understand why people would want to keep all their old junk and mistakes and carry them all forward into their next install. I prefer to just carry my good stuff forwards, leave the trash behind and 'start again with a clean slate'. :)

I multi-boot and I use the current version of Ubuntu with my files in its home directory. When I'm ready I install the next unreleased test version and try it out for a while with no files in it. Then when it is released and stable enough I just move my files into the new version's home dir. Most of the time I have three versions of Ubuntu, past, present and future. Maybe I will have another OS or a different flavour of Ubuntu as well for a while to look at for curiosity's sake. I would hate to clutter my hard drives up with lots and lots of extra /home partitions I don't need or want. I just want each OS in its own single partition thanks. 
I have never had any problem 'walking' my files forwards into the nice shiny clean new home directory of a newer Ubuntu version the time comes. All it takes is five minutes of copying and pasting. :)

People should be backing up their data to separate media regularly too, it might not be wise to promote the idea they can just leave it in a /home folder and upgrade to the next new release and imply that everything will always be fine. Most people are lazy already.
                                
Sorry to be a stick in the mud, but I wouldn't agree with changing things from the way they are now. 

Regards, Herman :)

---

### Post by aysiu on 2007-05-04
Well, in the ideal world, you're right. But even then--yes, with regular backups--a separate /home partition can come in handy.

And I personally agree that carrying over old junk isn't fun. That's why I have a separate /documents partition instead of a separate /home partition. Nevertheless, a lot of people like their old junk settings and such.

It is only a default, not a mandate. And "studies show" (I'm making this up, of course, but it's still true) that users who don't back up their installations are not more likely to back if they don't have a separate /home partition.

---

### Post by ibbuntu on 2007-05-11
I got bitten by not having a separate /home partition. I knew nothing about it when I first installed ubuntu, and it would have saved me a lot of hassle had it been set as a default in the installation. I am currently trying to set up a separate /home, and was going to post this idea here because of the trouble I had, but clearly I was beaten to it by a long way.

+1

---

### Post by vigi1 on 2007-05-11
> **viciouslime said:**
> Why not do both? Lots of people simply don't have space for a backup. if I wanted to back-up now and then wipe completely and reinstall I would need to find someone willing to lend me a 500GB HDD... or burn over a 100 DVDs, aside from the massive amount of time involved, both of these options are clearly unpractical. With many people getting larger and larger HDDs (and filling them) there simply isn't the space to back EVERYTHING up.

The concept of a modular system is exactly what made me revisit linux over 12 months ago after trying mandrake some years ago without success(I am a generic user, not a programmer). 
When a Windows OS goes down even when you have data back up- it can take over 4 hours to reinstall and customize it. Often this was my only choice. With home on a separate partition you can do this on linux in 1 hour and not lose anything. 

I have a dual boot system, ubuntu feisty on a 20GB drive (split into 5 partitions) and XP on a backup drive that I use only for MYOB accounting and acronis directors suite. It works very well indeed.

What I see as the ideal would be if it were also possible to reload the operating system without having to reload  the /user program partition?

---

### Post by llamakc on 2007-10-20
Similar to this: [http://ubuntuforums.org/showthread.php?t=410093](http://ubuntuforums.org/showthread.php?t=410093) from the Gutsy idea pool.

Hardy should offer & recommend a separate partition for /home during the guided partitioner during install. This topic is frequently brought up on the forums. Additionally, it helps the new users to GNU/Linux & Ubuntu make the release-to-release transitions much easier.

(I checked for duplicate threads and didn't see any).

EDITED to add [https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome) Spec by Bou.

---

### Post by Auria on 2007-10-20
+1!

that would be a great addition, especially as dist-upgrade isn't always stable, then we can recommend clean install without losing data

---

### Post by DizzyTech on 2007-10-20
+1

Some packages, like Virtualbox, should have their default configs overridden to use another place than home for the storing of large files.

---

### Post by bobbocanfly on 2007-10-20
Brilliant idea, saves time and essentially data if there is an error in a dist-upgrade. The devs would be really stupid not to put this in.

---

### Post by smartboyathome on 2007-10-20
The only problem I see with this is how to apply it. New users aren't going to know what to give each one when the installer asks "What do you want your / partition to be? ... What do you want your /home folder to be?". If you set a size for the / partition by default, it might give a user little space for the system/home folder.

---

### Post by aysiu on 2007-10-20
> **smartboyathome said:**
> The only problem I see with this is how to apply it. New users aren't going to know what to give each one when the installer asks "What do you want your / partition to be? ... What do you want your /home folder to be?". If you set a size for the / partition by default, it might give a user little space for the system/home folder.
Read [post #9 in the thread linked to in the first post of the thread](http://ubuntuforums.org/showpost.php?p=2458086&postcount=9).

---

### Post by Awalton on 2007-10-20
I've been using a 5GB root partition since Dapper, and by keeping two floating 5GB partitions, one so I can have a backup partition in case an update destroys the root install in some way I can't repair on my own, and one so that I can install the next version of Ubuntu without destroying a working install (as I tend to be an early adopter and like to try things out before they get stressed into working right).

That being said, I think for most cases, 5GB is a tad bit limiting. I've had the root partition run out of space, and it's a very nasty thing to try to clean up, especially during the middle of a long update session. 7GB is probably closer to what you'd want, even though it's an odd number; rounding it to 10GB would be ideal (putting it in perspective, both Windows Vista and Mac OS X "Leopard" require about 10GB of free drive space to install; Ubuntu wouldn't require it for users who know better, but gives a nice, round figure for default, guided installs). Most people will be running Ubuntu on a machine that's less than 5 years old and again, putting things in perspective, a 20GB drive was considered "normal" in 2002, with a price tag hovering around $100 for a 40GB.

This gives a nice, simple partition table; root at 10GBish (or even more clever, 10GB minus swap size), swap to parity with RAM (or otherwise heuristically derived), and the rest of the disk given to /home.

---

### Post by gn2 on 2007-10-22
> **smartboyathome said:**
> The only problem I see with this is how to apply it. 

Ask Texstar?

PCLinuxOS has been doing it for ages.

---

### Post by drf_av on 2007-10-22
+1, and I think aysiu implementation is the best way to go. I'm using the same home partition from 1 year and a half and all my settings survived many fresh installs.

---

### Post by glotz on 2007-10-22
I think this should be a priority. Having a separate home is a very good idea.

---

### Post by gweaver on 2007-10-22
+1

This is a no brainer.

---

### Post by Twintop on 2007-10-22
> **aysiu said:**
> Read [post #9 in the thread linked to in the first post of the thread]("http://ubuntuforums.org/showpost.php?p=2458086&postcount=9").

That sounds reasonable to me, aysiu. It shouldn't be too terribly difficult to implement. Also, it should be included that if the installer detects an existing hard drive that looks like it is an Ubuntu /home folder, maybe try to auto-select it and not format it? I'm not sure how this would work for computers with multiple Linux distros installed on it, though.

---

### Post by glotz on 2007-10-22
Not everything has to be auto-detected. Most users will be happy to answer some extra questions in the advanced install mode.

---

### Post by smartboyathome on 2007-10-22
> **glotz said:**
> Not everything has to be auto-detected. Most users will be happy to answer some extra questions in the advanced install mode.

It is better to hold hands with a user while they learn and not send them off with middle school level work when they are in first grade, isn't it?

---

### Post by glotz on 2007-10-22
The toddlers shouldn't use advanced mode when installing.

---

### Post by smartboyathome on 2007-10-22
> **glotz said:**
> The toddlers shouldn't use advanced mode when installing.

Ok, but how would the advanced mode be implimented? I know there is a box at the end of the install that says advanced, but that shouldn't be enough. Are you thinking of making it kind of like Windows installers?

---

### Post by Twintop on 2007-10-22
You say:
> **glotz said:**
> Not everything has to be auto-detected. Most users will be happy to answer some extra questions in the advanced install mode.

then:

> **glotz said:**
> The toddlers shouldn't use advanced mode when installing.

So which is it? If more newbie-ish users are upgrading and have /home on a separate partition should it be auto detected or have them use the advanced mode? It really has to be one or the other in this case.

---

### Post by aysiu on 2007-10-22
> **Twintop said:**
> That sounds reasonable to me, aysiu. It shouldn't be too terribly difficult to implement. Also, it should be included that if the installer detects an existing hard drive that looks like it is an Ubuntu /home folder, maybe try to auto-select it and not format it? I'm not sure how this would work for computers with multiple Linux distros installed on it, though.
You mean like this idea?
[Re: [IDEA] Gutsy should default to setting up a separate home partition](http://ubuntuforums.org/showthread.php?t=411871)

---

### Post by glotz on 2007-10-22
@smartboyathome In advanced mode extra questions would be asked by the install.

@Twintop Most newbie users won't be having a /home partition.

---

### Post by Toadmund on 2007-10-22
I so want this!
It would beat transferring my important data (and sacrificing some) between two ubuntu's, in order to do a fresh install.

Creating a seperate home partition is on my mind lately, just how to do it?

---

### Post by Twintop on 2007-10-22
> **aysiu said:**
> You mean like this idea?
[Re: [IDEA] Gutsy should default to setting up a separate home partition]("http://ubuntuforums.org/showthread.php?t=411871")

Yes, exactly like that aysiu! :)

> **glotz said:**
> @Twintop Most newbie users won't be having a /home partition.

Thank comes back to the original idea though, making /home it's own partition by default automatically. If a 'toddler' installs 8.04 and it *does* make their own /home folder, and then needs to reinstall or whatnot, would they know they have their own /home on another partition and tell the installer to point to it? Probably not. This is why having it automatically detect is important IF this idea goes through.

---

### Post by tubasoldier on 2007-10-22
Ubuntu is one of the very few distributions that does not do this. Easy to fix yourself but definitely unneccessary

---

### Post by exile on 2007-10-22
Creating of a separate /home is one of those things that eventually (the longer you use linux) you wish you had done from the start. Even if its not created by default it would be nice to at least suggest it or give an example explaining the advantages in the partition installer?

---

### Post by Bou on 2007-10-23
> **aysiu said:**
> Read [post #9 in the thread linked to in the first post of the thread](http://ubuntuforums.org/showpost.php?p=2458086&postcount=9).

Agreed, but the user should always be able to decide. There should be a dialogue like this:

[IMG]http://img88.imageshack.us/img88/8524/pantallazokv7.png[/IMG]

But the recommended options should vary depending on the variables you proposed. What do you think about that?

---

### Post by Bou on 2007-10-23
I just filed a bug proposing this be included in the installation process:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/156177](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/156177)

---

### Post by gn2 on 2007-10-23
> **Toadmund said:**
> I so want this!

Creating a seperate home partition is on my mind lately, just how to do it?

Here's a how-to kindly created by one of the posters in this thread.....

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Bou on 2007-10-24
> **llamakc said:**
> Similar to this: [http://ubuntuforums.org/showthread.php?t=410093](http://ubuntuforums.org/showthread.php?t=410093) from the Gutsy idea pool.

Hardy should offer & recommend a separate partition for /home during the guided partitioner during install. This topic is frequently brought up on the forums. Additionally, it helps the new users to GNU/Linux & Ubuntu make the release-to-release transitions much easier.

(I checked for duplicate threads and didn't see any).

Hey llamakc, I just created a [spec]("https://wiki.ubuntu.com/RecommendSeparateHome") about the issue. Mind including it in the first post so the Ambassadors can easily see it?

Also, please feel free to edit and improve it, any of you guys.

---

### Post by veratyr on 2007-10-24
+1

I wish when I started out using ubuntu it had done this for me. It's a good practice and should be presented to a new user as such.

---

### Post by llamakc on 2007-10-24
> **Bou said:**
> Hey llamakc, I just created a [spec]("https://wiki.ubuntu.com/RecommendSeparateHome") about the issue. Mind including it in the first post so the Ambassadors can easily see it?

Also, please feel free to edit and improve it, any of you guys.

Thanks for doing that. I added it to the first post.

---

### Post by dr.silly on 2008-03-02
The Ubuntu Installer should at least have an option to install the /home directory to a separate partition. And conversely, use an already present /home directory on a partition.

---

### Post by lexen on 2008-03-02
It already does have that option, I have been using that option since dapper drake.  All you do is make a new partition and have the mount point /home.  Then, when you want to install another version of Ubuntu, you just have to mount that partition as /home again without formating it and you will have all your old files and settings.

     Describe what you are trying to do and what made you think that you couldn't do it.

---

### Post by dr.silly on 2008-03-02
whoops sorry :)

---

### Post by Bou on 2008-03-03
You might like this proposal: [http://brainstorm.ubuntu.com/idea/314/](http://brainstorm.ubuntu.com/idea/314/)

---

### Post by aysiu on 2008-03-03
I've merged three similar threads together.

---

### Post by altonbr on 2008-03-03
> **Bou said:**
> Agreed, but the user should always be able to decide. There should be a dialogue like this:

[IMG]http://img88.imageshack.us/img88/8524/pantallazokv7.png[/IMG]

But the recommended options should vary depending on the variables you proposed. What do you think about that?

This is perfect. I would have no problem with this dialogue.

---

### Post by viciouslime on 2008-03-05
Yup, sounds like an absolutely excellent solution :D

---

### Post by Herman on 2008-03-07
Yeah but don't forget you're talking about adding extra steps to the installer when most newbies are scared to death of it already as it is. 
Most new users hardly know what a partition is yet let alone understand what / (root) and /home are for.
It might be okay for people who have installed a few times already, but those people should by then find it easy enough to use the manual partitioning option in the installer as it is and create their own separate /home.

There are no viruses or malware for Linux and most new users bork their own installation themselves while they are trying to install software they shouldn't be installing or learning the command line and typing commands they're not familiar with.

An integral installation is much more flexible because folders are always the size of the data that's in then whereas partitions are rigid and require the use of a hard disk partitioner for resizing when they get too full.
Either that or you need to allow way more space than you really need to allow for an unknown amount of expansion of the files inside.

If you're going to dedicate a whopping 10.0 GB for / (root), then you already have more than enough for a whole second installation. Then they can multi boot and have one installation that's disposable that they can use as a sandbox for learning in.
For experienced users the other installation would be for testing the next release of Ubuntu
For cautious users they could upgrade one operating system at a time in case their operating system gets borked during an upgrade.

It's also important to keep reminding people that having a separate /home doesn't exempt them from the need to make regular backups to some other media, because that's what some people will think. They'll get lazier than ever. A few people really seem to think that they don't need to make a backup since they have a separate /home.

I think it would be better to included the option for splitting the free space in two and having two integral installations instead of a separate /home and / (root) set-up.
Or simply leave things the way they are now, intergral installations are great.

There is even some advantage to be gained by changing from having a separate /swap area to using a swap file instead. Read this: [Reasons to choose swap files over swap partitions]("http://ubuntumagnet.com/2007/10/reasons-choose-swap-files-over-swap-partitions")

Regards, Herman :)

---

### Post by viciouslime on 2008-03-08
> **Herman said:**
> Yeah but don't forget you're talking about adding extra steps to the installer when most newbies are scared to death of it already as it is. 
Most new users hardly know what a partition is yet let alone understand what / (root) and /home are for.
It might be okay for people who have installed a few times already, but those people should by then find it easy enough to use the manual partitioning option in the installer as it is and create their own separate /home.

There are no viruses or malware for Linux and most new users bork their own installation themselves while they are trying to install software they shouldn't be installing or learning the command line and typing commands they're not familiar with.

An integral installation is much more flexible because folders are always the size of the data that's in then whereas partitions are rigid and require the use of a hard disk partitioner for resizing when they get too full.
Either that or you need to allow way more space than you really need to allow for an unknown amount of expansion of the files inside.

If you're going to dedicate a whopping 10.0 GB for / (root), then you already have more than enough for a whole second installation. Then they can multi boot and have one installation that's disposable that they can use as a sandbox for learning in.
For experienced users the other installation would be for testing the next release of Ubuntu
For cautious users they could upgrade one operating system at a time in case their operating system gets borked during an upgrade.

It's also important to keep reminding people that having a separate /home doesn't exempt them from the need to make regular backups to some other media, because that's what some people will think. They'll get lazier than ever. A few people really seem to think that they don't need to make a backup since they have a separate /home.

I think it would be better to included the option for splitting the free space in two and having two integral installations instead of a separate /home and / (root) set-up.
Or simply leave things the way they are now, intergral installations are great.

There is even some advantage to be gained by changing from having a separate /swap area to using a swap file instead. Read this: [Reasons to choose swap files over swap partitions]("http://ubuntumagnet.com/2007/10/reasons-choose-swap-files-over-swap-partitions")

Regards, Herman :)

I think you might actually have convinced me that the current setup is indeed a better way...

---

### Post by Bou on 2008-03-08
> **Herman said:**
> Yeah but don't forget you're talking about adding extra steps to the installer when most newbies are scared to death of it already as it is. 
Most new users hardly know what a partition is yet let alone understand what / (root) and /home are for.

I tried to avoid using the terms / and /home. Instead I use "personal data" and "system files", which any user should be able to understand. The menu even explains what effect the decission will have, in barely two lines.

I really doubt that dialogue would scare anyone off.

---

### Post by Herman on 2008-03-08
> I tried to avoid using the terms / and /home. Instead I use "personal data" and "system files", which any user should be able to understand. The menu even explains what effect the decision will have, in barely two lines.
I really doubt that dialogue would scare anyone off.     Hello Bou,
You're right about that, your wording does make it seem a lot simpler, now that I have taken a second look at your proposed installer Window.
Sorry, I didn't mean anything personal here, but I do see this as a good subject for a healthy debate. :)

I just don't think having a separate /home is as great an idea as seems to be made out to be.

You people are talking about imposing on new users to make two decisions they may not have ever needed to make before and may not be very well prepared for. 

Firstly, you seem to be trying to imply that they should agree with your particular idea of what is the best partitioning strategy.
The fact is, keeping personal data in a separate /home partition doesn't really prevent people from losing their data during a re-install.
They should not be risking their data in the first place by leaving the only copy of it in the hard disk.
If they have a backup of it then how can they lose data during a re-install?
Therefore, you are implying that it's not necessary for people to make regular backups to some other media before a re-install or before using a hard disk partitioning program? I must disagree.
People should be reminded they still need to make a backup of their data anyway, /home partition or not, and if they do that them I don't see the real advantage in having one. It will save them a few minutes of transferring data from a backup, back  to the hard disk following a re-install., but for the rest of the time it's just a waste of hard disk space, which brings me to my second point.

Secondly, the basic / (root) or 'system' files right after a new installation only take up about 1.8 GB of hard disk space.
How much room do people really need have spare to accommodate an unknown amount of added software they might want to install?
You're fencing people in and creating a rigid boundary here, so a decision needs to be made.
5.0 GB? Will that be enough? 10.0 GB sounds like more then enough. Somewhere in between maybe?
Another thing to keep in mind is that Linux file systems can begin to become subject to fragmentation when they're filled to more than 80% of their capacity.
I would imagine that the extra space most people would leave spare, over and above what will ever actually be used, would have been more then the original 1.8 GB needed for the installation in the first place.
Would that amount of space not be better used for either data or a second installation they can use for a sandbox, as I mentioned in my previous post?

Regards, Herman :)

---

### Post by aysiu on 2008-03-09
I disagree, Herman.

In my experience, users who don't back up don't back up, and users who back up back up. Having a separate /home partition has nothing to do with whether people back up or not.

And that's how it should be and how it should be marketed--/home partition has *nothing* to do with backups. It means you don't have to copy your settings and files back from your backup after reinstalling. That's all.

As for space, please check out my space proposal in [post #9 of this thread](http://ubuntuforums.org/showpost.php?p=2458086&postcount=9).

---

### Post by Herman on 2008-03-09
:) Hello aysiu,
Your proportioning scheme in your space proposal looks okay.
Will that be programmed into the partitioner or will the new users need to know that?

People are easily influenced,if you remind people they need to make backups they might, if you imply their data will be safe they won't bother. We're working with human nature here. 
If you just change the wording a little I suppose you could fix that problem.

"Doing this will prevent you from losing your personal files if you ever have to re-install Ubuntu"

to,
"Doing this will make re-installing Ubuntu easier if you ever need to, but you'll still need to keep making regular backups to some other separate media".
Or something like that would be better.

Regards, Herman :)

---

### Post by aysiu on 2008-03-09
> **Herman said:**
> :) Hello aysiu,
Your proportioning scheme in your space proposal looks okay.
Will that be programmed into the partitioner or will the new users need to know that? Well, this is just a proposal, so I don't know. If I had it my way, I'd have it programmed into the partitioner as the default option (always able to be overridden by those who don't want it).

> People are easily influenced,if you remind people they need to make backups they might, if you imply their data will be safe they won't bother. We're working with human nature here. 
If you just change the wording a little I suppose you could fix that problem.

"Doing this will prevent you from losing your personal files if you ever have to re-install Ubuntu"

to,
"Doing this will make re-installing Ubuntu easier if you ever need to, but you'll still need to keep making regular backups to some other separate media".
Or something like that would be better. I agree completely.

---

### Post by Bou on 2008-03-10
> **Herman said:**
> "Doing this will prevent you from losing your personal files if you ever have to re-install Ubuntu"

to,
"Doing this will make re-installing Ubuntu easier if you ever need to, but you'll still need to keep making regular backups to some other separate media".

Yeah, I think that would be fine. I'd still like to state the advantages -that is, you can reinstall without losing your stuff- as clearly as possible. "Make it easier" would sound a bit too nebulous to me.

"Doing this will keep your personal files and configuration if you ever have to re-install Ubuntu. Bear in mind that regular backups to other separate media are still necessary, though".

How would that be? Seems a bit long to me, could a native think of a way to say the same more concisely?

---

### Post by dark_harmonics on 2008-03-10
I completely disagree with this idea. Confusing users with having to worry about partitioning is a waste of time and could scare off more users. The people who are advanced enough to care, already know how to make a separate home partition. Then there is a question to how much space the installer will decide you need for your system and home partitions. Isn't this a bit invasive? Somebody else deciding how much space you need? I think the defaults should stay the same or offer "schemes" that have different recommendations. 

Talking about it now though, I can see that anything other than the way they have it might confuse users. Not worth it in my opinion.

---

### Post by aysiu on 2008-03-10
> **dark_harmonics said:**
> I completely disagree with this idea. Confusing users with having to worry about partitioning is a waste of time and could scare off more users. The people who are advanced enough to care, already know how to make a separate home partition. Then there is a question to how much space the installer will decide you need for your system and home partitions. Isn't this a bit invasive? Somebody else deciding how much space you need? I think the defaults should stay the same or offer "schemes" that have different recommendations. 

Talking about it now though, I can see that anything other than the way they have it might confuse users. Not worth it in my opinion.
The whole point is that you *don't* confuse them with partitioning. Have you even read this thread?

---

### Post by daniel6 on 2008-03-11
Sure would be informative if all the participants in this thread would have posted a copy of their partition table. I have four installs under my belt. Two with 6.06LTS and two with 7.10. The first install was to dual boot with XP and was an absolute disaster. Took about a week and some blind dumb luck to recover the original hard drive. The second attempt was successful but I took total control of the process. Had I not had many years of experience with Windows I would have given up after the first disaster. Once you get past the CD/DVD trial, there is a need to understand partitioning - period! There is not a great deal of clear information available to the newbie.

Partitioning decisions go far beyond the /home question. Frequency of backups and size of backups are important. No point in backing up data on a daily basis that does not change for months. No point in backing up data that exists for only a few hours or minutes.

If you have only one hard drive and it dies, maybe a new install on a new drive with minimal restore from backup would save some time. These are things newbies just will not be able to handle.

The real answer lies in knowing how much space is needed across the lifetime of any given distribution and which directories are involved. This will give an idea of what the system requires. 

Anything beyond system requirements depends on the end user and how they use the system. There is no easy answer. Only experience and time will tell what an individual needs. A good tutorial on partitioning is sorely needed at this point. Something that covers a system with 4 40 gig hard drives and something with one 320 gig hard drive. Examples of partition tables and how that data relates to the partition editor. Good practical examples are hard to come by and are an essential part of learning how to make good decisions.

Putting /home in its own partition is a no brainer after some experience!

---

### Post by Herman on 2008-03-11
:) Hello daniel6,
You are absolutely right. New users do need somewhere they can access information about partitioning that is easy to understand and explains clearly what they need to know.
Myself and aysiu both have information like that in our web sites, but apparently new users aren't finding it.
aysiu's : [Plan Partitions]("http://www.psychocats.net/ubuntu/partitioning")
Mine: [Help on Partitioning]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning")
Let me know if mine needs more work, I think maybe it does. I will be interested in any feedback.
Here's the Wiki page on [installation]("https://help.ubuntu.com/community/Installation"), and here's the page on [partitioning]("https://help.ubuntu.com/community/forum/installation/Partitioning"). 
Maybe more effort needs to be directed towards explaining things better for new users, or pointing them to the information. 

Regards, Herman :)

---

### Post by mimada on 2008-03-11
How about throwing in a "Help" button in the dialog? Label the button "What is a partition?". The help page should explain in simple terms, what a partition is and the merits/drawbacks to partitioning a separate home.

It should perhaps have definitions to "home" and such too.

The dialog in the wizard should also survey the drive to show how much available space there is.

---

### Post by dark_harmonics on 2008-03-14
> **aysiu said:**
> The whole point is that you *don't* confuse them with partitioning. Have you even read this thread?

Oh yes i read quite a bit of it. I am thinking that it might be best to not create arbitrary partitions of a percentage. You never know how big (or small) a users hard drive will be, or whether they will need more space to install programs and libraries or not. If you do it percentage based, what if the user has a tiny hard drive? You've just cut out a swath of low-end computers that dont work by default.  If they have a large hard drive, you have wasted space on the system partition that could be used for data storage. 

If you set the system drive to a static size, you could underestimate how many programs a user will have, and they might run out of space, or overestimate and waste lots of space. 

I think the model should be left as it is, because guessing this way for users who dont know how to customize the size of their partitions is just not something the installer should do. Maybe a prompt that asks the user if they wish to customize their partitions that reccomends making a seperate home partition? Then we come back to the ease of use issue. Thats why i think the current way it works is the best.

**EDIT** I dont want anybody to get the wrong idea here. I do beleive having a seperate home partition is a very good idea on any computer. Of course, the best way to do anything in linux is to research and ask the community questions. Aysiu makes alot of good documentation and comments (more so than myself) and I have respect for any contributing member of this community.

---

### Post by dark_harmonics on 2008-03-14
> **mimada said:**
> How about throwing in a "Help" button in the dialog? Label the button "What is a partition?". The help page should explain in simple terms, what a partition is and the merits/drawbacks to partitioning a separate home.

It should perhaps have definitions to "home" and such too.

The dialog in the wizard should also survey the drive to show how much available space there is.

I really like this idea. Anything to make the process smarter AND more user friendly.

---

### Post by aysiu on 2008-03-14
> **dark_harmonics said:**
> Oh yes i read quite a bit of it. I am thinking that it might be best to not create arbitrary partitions of a percentage. You never know how big (or small) a users hard drive will be, or whether they will need more space to install programs and libraries or not. If you do it percentage based, what if the user has a tiny hard drive? You've just cut out a swath of low-end computers that dont work by default.  If they have a large hard drive, you have wasted space on the system partition that could be used for data storage. 

If you set the system drive to a static size, you could underestimate how many programs a user will have, and they might run out of space, or overestimate and waste lots of space. 

I think the model should be left as it is, because guessing this way for users who dont know how to customize the size of their partitions is just not something the installer should do. Maybe a prompt that asks the user if they wish to customize their partitions that reccomends making a seperate home partition? Then we come back to the ease of use issue. Thats why i think the current way it works is the best. Again, I think you misunderstand what's being proposed here.

No one is saying new users should be *forced* to create a separate /home partition.

What's being proposed is that Ubuntu default to creating a separate /home partition. There's a big difference between forcing someone to install a certain way and defaulting to installing a certain way.

Even now with the current setup, Ubuntu tries to guess who much you want to resize your current Windows partition and automatically proposes a size for your swap partition. You can drag the sizes around to suit your needs, but there is a default.

Same with the separate /home partition. There would be several options--one of which (the top option) would be to separate the user settings and files from the system files to make a reinstallation easier (so you don't have to copy back all your settings and files from your backup medium).

If a user does not want to select this option, she doesn't have to. And the partitioner would make sane guesses as to how much space to allocate or if there is even enough space *to* allocate (please see [post #9 of this thread](http://ubuntuforums.org/showpost.php?p=2458086&postcount=9) for those sane guesses). The user always has the option to change the allocations or not separate user settings and files from system files.

**All that is being proposed is a default.**

---

### Post by Herman on 2008-03-14
Users who choose not to create a separate /home partition at installation time, regardless of whether or not it's the default arrangement for the installer, should not to be made to feel that their installation is inferior.

A while ago, I helped at least one user who had preformed a perfectly good integral / (root) and swap installation to  to re-partition the hard disk, copy /home files to the new partition and mount it as /home in /etc/fstab.

Some people who like to espouse the virtues of having /home in a separate partition had convinced this user that such work was needed.

Actually, if someone has a perfectly good integral install, it is better, and can safely be left that way and used until some day when a re-install or upgrade is wanted.

Even if the operating system ever does become unusable for some reason, all the user would need to do is delete all the operating system files from the partition and leave the  /home files there.
Eg, from a Live CD, delete bin  boot  cdrom  dev  device.map  etc  initrd  initrd.img  lib  lib32  lib64  lost+found  media  mnt  opt  proc  root  sbin  srv  sys  tmp  usr  var  vmlinuz, but leave the /home directory alone, let it remain in the partition.
Then resize the partition and install a new / (root) beside it, mounting the original partition as /home.

So if someone doesn't make a separate /home during their initial installation it isn't an emergency. They can always convert their hard disk to that type of set-up later on sometime. (If they later become convinced that having a separate /home is better).

Regards, Herman :)

---

### Post by Bou on 2008-03-22
I have just realised that the whole process doesn't even need to add an extra step to the installing process. The whole thing can be added to step 5. See if you like this:

-The first time an user installs Ubuntu, he is given the option to set a separate /home. This option is selected by default, with a size for each partition based on a sane guess:

[IMG]http://img155.imageshack.us/img155/7958/firstinstallaro2.png[/IMG]

-Of course, he can just choose not to set a separate /home. This option will be selected by default if the results of the system test suggest that's the best thing to do.

[IMG]http://img186.imageshack.us/img186/6498/firstinstallbfs6.png[/IMG]

-Manual install is also possible. Selecting it greys out everything related to separate /home, since it's implied that the user doesn't want to be guided.

[IMG]http://img177.imageshack.us/img177/7976/firstinstallcvc2.png[/IMG]

-If the user set a separate /home, the next time he installs Ubuntu a new option appears and is selected by default, prompting to use the existing /home partition. All other options are still available, though.

[IMG]http://img155.imageshack.us/img155/9034/secondinstalliq1.png[/IMG]

This is just a mockup and the wording is open to change if you got a problem with it (I know we should add something about backups still being necessary), but I think the whole system is quite useful and straight-forward.

---

### Post by smartboyathome on 2008-03-22
I would say that 15+GBs is better for System files. At least for me, I get a lot of system files.

---

### Post by Old_Grey_Wolf on 2008-06-08
Why does Ubuntu not set up a /home partition by default? Why do I have to set it up manually?

---

### Post by CameO73 on 2008-06-08
Good question! I find it good practice to separate the user data from the system/applications (something Vista is trying to enforce nowadays). Why is this not the default? Maybe because 3 partitions seems like a lot?

I don't know. I hope someone from the inside can shed more light.

---

### Post by bruce89 on 2008-06-08
Because Ubuntu goes for the easiest thing possible.

A seperate /home ought to be the default.

---

### Post by kevin11951 on 2008-06-08
i dont really like having a /home partition, because i dont have alot of personal files, and only ubuntu on this computer, so a /home is pointless.

---

### Post by bruce89 on 2008-06-08
> **kevin11951 said:**
> i dont really like having a /home partition, because i dont have alot of personal files, and only ubuntu on this computer, so a /home is pointless.

Unless you do a reinstall of course.

---

### Post by Old_Grey_Wolf on 2008-06-08
The reason I ask is because I've used Ubuntu for a few years. The first time they rolled out a new version, I lost my personal data and settings. I learned that a separate /home partition would fix that problem. Fortunately I had my data backed up.

Updates don't ususlly work for me and I do fresh installs.

With a 6 month release cycle for the product, I was just curious.

---

### Post by gameryoshi600 on 2008-06-08
They should. but I don't need one i got my data backed up

---

### Post by bruce89 on 2008-06-08
[https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome)

---

### Post by Bou on 2008-06-08
Some time ago I sent this [proposal]("http://brainstorm.ubuntu.com/idea/5390/") to Ubuntu Brainstorm, which got to be one of the most popular ten.

Then I sent a proposal to the mailing list, which you can read [here]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-May/thread.html") (look for "Ubiquity - setting a separate /home by default") but it got rejected. Basically:

-They think it's not necessary, since you can install on an existing partition and it will erase system files but keep /home.
-They think setting a separate /home will waste lots of space on people's drives.

Personally, I would love you guys to take a look at the proposal and have your say in the mailing list.

---

### Post by unicorn_2003_1 on 2008-06-08
I don't see the point of having a seperate partition if it's still gonna be on the same harddisk.

---

### Post by bruce89 on 2008-06-08
> **Bou said:**
> 
-They think it's not necessary, since you can install on an existing partition and it will erase system files but keep /home.
-They think setting a separate /home will waste lots of space on people's drives.


I didn't realise Ubiquity did this, I'd not trust it though.

How can another partition waste space?

---

### Post by Old_Grey_Wolf on 2008-06-08
> **bruce89 said:**
> [https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome)

Does the link provided mean they are considering it, implementing it, or have rejected the idea?

---

### Post by Alasdair on 2008-06-08
I like having the entire system on the same partition, precisely because it nukes all the rubbish that builds up in my /home over time when I upgrade to the next release. Then I just restore what I want from a backup, keeping my home directory nice and tidy (for a few weeks at least :)).

---

### Post by Bou on 2008-06-08
> **bruce89 said:**
> How can another partition waste space?

It's better if you read it yourself, I don't remember the details all that well. But basically, you have the risk of running out of space on / having free space on /home, or running out of space on /home having free space on /.

Who knows, if you give them really good arguments they could reconsider. I'm quite a casual user, so I like it better as a personal option but I can't give the devs any hard facts to make them change their mind.

---

### Post by Old_Grey_Wolf on 2008-06-08
> **bruce89 said:**
> [https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome)

I like the proposal in the link above. It gives the user the freedom of choice whether to have a separate partition or not.

---

### Post by aysiu on 2008-06-08
For those who like having it all on one partition, that's great *for you*. No one is proposing anyone be *forced* to have a separate /home partition.

We're talking about defaults. And if you have a small hard drive, the default would be different.

---

### Post by animaniac on 2008-06-12
+1, if only for the fact that when beginners mess up it makes recovery more simple.

---

### Post by altonbr on 2008-06-13
"Install on an existing filesystem without overwriting /home" has now been implemented in Intrepid: [https://blueprints.edge.launchpad.net/ubuntu/+spec/ubiquity-preserve-home](https://blueprints.edge.launchpad.net/ubuntu/+spec/ubiquity-preserve-home)

This isn't "Install /home by default" but it's a step.

---

### Post by Old_Grey_Wolf on 2008-06-15
altonbr,

I'm looking forward to Intrepid.

Thanks for the info. :)

---

### Post by viciouslime on 2008-07-03
A great step! Thanks for pointing that out :)

---

### Post by jpds on 2008-07-04
I, personally, like this idea very much and often surprised when I find a system which does not have a separate /home.

I have to say I like the way that it has been implemented.

---

### Post by starcannon on 2008-08-11
+1 for [https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome)

I use the manual partition editor when I install, but then I've been doing this for 5+ years.

A new user doesn't know how to work it, or in the event of a recovery reinstall, how to use it if someone else set it up for them.

I'd add that part of the reuse of the existing /home directory or /home partition should include a username and password verification as well, this keeps people from locking themselves out of their data.

---

### Post by mc4100 on 2008-08-11
Personally, I love my /home partition ... that said, if I can quote the official Ubuntu Installation Guide:
> First, just a note about re-installations. With Ubuntu, a circumstance that will require a complete re-installation of your system is very rare; perhaps mechanical failure of the hard disk would be the most common case.
I don't really think much needs to be added: the benefits of having a /home partition **by default** are not going to be seen by new users, simply because -usually- they don't need to reinstall. Anyone who would be likely to benefit is probably smart enough to set up an extra partition manually.

---

