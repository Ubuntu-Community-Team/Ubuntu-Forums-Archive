---
title: "EXT4 - I just don't get it."
date: 2010-11-19
forum: The Cafe
---

### Post by slooksterpsv on 2010-11-19
All,

Maybe someone can explain this to me, but here's a little back-story first. I used Ubuntu with EXT4 for a while, probably 2-3 months, and then I noticed my data was becoming corrupt, ISO files I had that I had just used, wouldn't work, some music files I had wouldn't play in any player, not even VLC, etc. Well, come to find out a lot of people have had corruption with EXT4 and their files. Personally, I like my data and not having to reformat.

So I did some research and wanted to try Reiser4 - yes yes I know who Reiser is and what he did, it's not the File System's fault, it's his - no where is it in pretty much any kernel except Gentoo has a Reiser4 Live CD, I may try that later on. So I searched for File Systems and Benchmarks and finally found the best one for me where I do VMs, XFS.

Ok now for the interesting stuff - I was talking to my friend and he's going to redo his slack server and he uses ext3 and reiserfs - he was considering going to EXT4, but after hearing all the problems I've had he decided against - so we start looking at various other distros and find they've mainly switched to EXT4 as the default.
Why? - Even RHEL6 Server is default EXT4. I don't understand why though, if data can easily become corrupt, why use EXT4?

The other thing I've found with EXT4 and BTRFS (I tried BTRFS, way not ready for prime time) and others, is that large data operations make it to where your computer isn't usable until those operations are done somtimes - I did tests with XFS last night and that was not true, XFS I was able to send email, chat on pidgin, use chromium, with brief and minor pauses, but not like before where it was like 2-3 min. wait for pauses.

Overall how can they justify using a file system that does have file corruption happen easily? - Maybe it's just semantics or just me. Can someone give some insight?
Also if you have any information on when Reiser4 will be merged into the kernel or even available on Ubuntu WITHOUT having to compile the kernel, that would be great.

Thanks!

---

### Post by NightwishFan on 2010-11-19
I know nothing of Reiser4, you probably just have to patch your kernel sources to use it. Is it officially out yet? I would avoid using something until the developers say it is ready, even if it is functional.

My experience with ext4 is that it is very quick, even on my slow laptop disk. Though it has some known performance issues in databases and installing/removing debian packages. I do both of those a lot so I use ext3 as my root partition. I still use ext4 on my data partition. (I would go back to ext3 if I could).

I looked at other filesystems, XFS seemed promising however it had too many question marks. JFS seemed more likely to be something I would use however I have used and trusted ext3 for a long time. It seems to work well. :)

I recommend ext3.

---

### Post by MasterNetra on 2010-11-19
> **slooksterpsv said:**
> All,

Maybe someone can explain this to me, but here's a little back-story first. I used Ubuntu with EXT4 for a while, probably 2-3 months, and then I noticed my data was becoming corrupt, ISO files I had that I had just used, wouldn't work, some music files I had wouldn't play in any player, not even VLC, etc. Well, come to find out a lot of people have had corruption with EXT4 and their files. Personally, I like my data and not having to reformat.

So I did some research and wanted to try Reiser4 - yes yes I know who Reiser is and what he did, it's not the File System's fault, it's his - no where is it in pretty much any kernel except Gentoo has a Reiser4 Live CD, I may try that later on. So I searched for File Systems and Benchmarks and finally found the best one for me where I do VMs, XFS.

Ok now for the interesting stuff - I was talking to my friend and he's going to redo his slack server and he uses ext3 and reiserfs - he was considering going to EXT4, but after hearing all the problems I've had he decided against - so we start looking at various other distros and find they've mainly switched to EXT4 as the default.
Why? - Even RHEL6 Server is default EXT4. I don't understand why though, if data can easily become corrupt, why use EXT4?

The other thing I've found with EXT4 and BTRFS (I tried BTRFS, way not ready for prime time) and others, is that large data operations make it to where your computer isn't usable until those operations are done somtimes - I did tests with XFS last night and that was not true, XFS I was able to send email, chat on pidgin, use chromium, with brief and minor pauses, but not like before where it was like 2-3 min. wait for pauses.

Overall how can they justify using a file system that does have file corruption happen easily? - Maybe it's just semantics or just me. Can someone give some insight?
Also if you have any information on when Reiser4 will be merged into the kernel or even available on Ubuntu WITHOUT having to compile the kernel, that would be great.

Thanks!

While I don't know about servers, I do however do use ext4 for Ubuntu desktop, I haven't had any corruption issues from it. But thats just me and my machine I suppose. I would suggest to your friend to do a test run with it. There doesn't seem to be very many people with such issues with ext4. If he test runs it and experiences issues then by all means stick with ext3.

---

### Post by NightwishFan on 2010-11-19
I actually have had these issues. My friend had some faulty power grid in his area, and it went down once or twice a day, his Ubuntu started acting a bit odd and I found out some of the config files in his home folder were corrupted. Just backed up and reset them and it worked. (He did not do it himself as all he does literally is play music with rhythmbox, and hes linux savvy).

So I think if your power goes down it has a higher risk of happening. Though lately ext4 has been tuned for more safety. I just think I will use ext3 for now. I trust Theodore Tso, he seems like a great guy, though I see no reason to be hasty and move on yet. Performance with ext3 is not critically less for my workloads.

---

### Post by Starks on 2010-11-19
Data corruption with ext4 has long been resolved.

Stop living in 2008.

---

### Post by slooksterpsv on 2010-11-19
> **Starks said:**
> Data corruption with ext4 has long been resolved.

Stop living in 2008.

Say what you want, ext4 coming from kernel 2.6.35-22-generic, for Ubuntu 10.10, that's where my data is corrupting. 2008? More like a 2010 OS. You Fail!

---

### Post by gradinaruvasile on 2010-11-19
> **Starks said:**
> Data corruption with ext4 has long been resolved.

Stop living in 2008.

Happened to me in 2010 (Ubuntu 9.10). Lost a whole partition because of it. And i had no power failure, just a normal reboot.

BTW i had many annoyances with JFS too - it became corrupted easily (on Ubuntu and CentOS) and had to be force-checked at reboot from single-user mode.
Ext3 on the other hand gave me no problems so far.

---

### Post by qamelian on 2010-11-19
> **Starks said:**
> Data corruption with ext4 has long been resolved.

Stop living in 2008.
No, it hasn't. I still encounter from time to time using Maverick. The issue is not as bad as it used to be by a long shot, but to say it no longer exists at all is simply not true.

---

### Post by NightwishFan on 2010-11-19
Well I would be skeptical (I am even skeptical of my own account of the data corruption) unless you have hard proof of it. We only can solve something if we review our own insights.

---

### Post by Spice Weasel on 2010-11-19
XFS/JFS > all

Plus, with XFS you can actually defrag your HD...

---

### Post by Artemis3 on 2010-11-19
How about trying btrfs?? Can be used in 10.10 as long as you keep /boot separate with an older fs such as ext2.

---

### Post by slooksterpsv on 2010-11-19
> **Artemis3 said:**
> How about trying btrfs?? Can be used in 10.10 as long as you keep /boot separate with an older fs such as ext2.

Yeah, btrfs, what a nightmare, sorry to say. It seems like it's good, but whenever I'd have large data operations going my computer would freeze until it was finished. And the data throughputs weren't all that great either, it was about the same as ext3. BTRFS does have some work before it'll be good. So I'm sticking with XFS - I just reformatted last night to get away from BTRFS cause I do a lot with VMs and the disk activity of just loading a VM was enough to bring my system to its knees.

---

### Post by czr114 on 2010-11-19
> **Artemis3 said:**
> How about trying btrfs?? Can be used in 10.10 as long as you keep /boot separate with an older fs such as ext2.
btrfs is not ready for mainstream use. The specifications are still being laid out and the code base is still in development.

It also can't be fscked as there is no stable utility to do so.

---

### Post by cariboo on 2010-11-19
BTRFS is abysmally slow at this point, I made the mistake of using it on a system with a Celeron and 512Mb ram. Boot-up seems to be ok, but any file operations seem to take forever. Updating from Maverick to Natty took well over 4 hours, where it usually takes less than an hour on the same system.

---

### Post by LowSky on 2010-11-19
The only problamatic file system I have had with Ubuntu was NTFS. 

EXT4 since I was an option has never gone worng for me.

My other favo is XFS but its too slow dealing with small files. and you can't shrink partitions.

If you experience data corruption on such large scale it could really be a disk problem or information transfer issue.

Most of the documented cases where EXT4 has failed is because of the user incorrectly shut down.

---

### Post by slooksterpsv on 2010-11-19
> **cariboo907 said:**
> BTRFS is abysmally slow at this point, I made the mistake of using it on a system with a Celeron and 512Mb ram. Boot-up seems to be ok, but any file operations seem to take forever. Updating from Maverick to Natty took well over 4 hours, where it usually takes less than an hour on the same system.

To install 143 updates on Mint, it took 3 hours! It was horrible. I just did it like an hour ago and it only took like 15-20 min for the 143 updates, maybe less.

---

### Post by nlsthzn on 2010-11-19
Seeing that EXT4 is now being made the default file system in so many distro's (Red Hat as well) I can't believe there is a major corruption problem with it... it wouldn't make sense...

---

### Post by Duncan J Murray on 2010-11-19
I thought google had moved all their servers to ext4.  I'd be surprised if there were major problems with it.

---

### Post by czr114 on 2010-11-19
Google's engineers are known for extending open projects to meet Google's massive enterprise scale. Usage by Google, or any other huge company with near-limitless engineering capacity, shouldn't act as an endorsement, as their setup very well may not be the stock code available to us.

---

### Post by CharlesA on 2010-11-19
Haven't run into any data corruption issues since I migrated to ext4 a while ago. I use it on my RAID array, OS drives and backup drives.

---

### Post by santosh83 on 2010-11-19
> **NightwishFan said:**
> I actually have had these issues. My friend had some faulty power grid in his area, and it went down once or twice a day, his Ubuntu started acting a bit odd and I found out some of the config files in his home folder were corrupted. Just backed up and reset them and it worked. (He did not do it himself as all he does literally is play music with rhythmbox, and hes linux savvy).

So I think if your power goes down it has a higher risk of happening. Though lately ext4 has been tuned for more safety. I just think I will use ext3 for now. I trust Theodore Tso, he seems like a great guy, though I see no reason to be hasty and move on yet. Performance with ext3 is not critically less for my workloads.

My experience is just the opposite. The power here trips quite occasionally and while I used Jaunty (with ext4) since it's release and have suffered many many hard resets, I found no data corruption whatsoever, at least nothing visible to me.

---

### Post by NightwishFan on 2010-11-19
I agree. It is not related to data loss why I am on ext3, but I did have issues on another machine and that might be an explanation.

---

### Post by KingYaba on 2010-11-19
My storage drives are all in EXT3. :P

---

### Post by uRock on 2010-11-19
I was having trouble while using EXT4, which I have used since Jaunty, with Thunderbird 3.1.4 corrupting the inode count. Once I dropped back to TB 3.1.3 the problem went away.

I'd be even happier if we could use NTFS.

---

### Post by Shining Arcanine on 2010-11-19
> **slooksterpsv said:**
> All,

Maybe someone can explain this to me, but here's a little back-story first. I used Ubuntu with EXT4 for a while, probably 2-3 months, and then I noticed my data was becoming corrupt, ISO files I had that I had just used, wouldn't work, some music files I had wouldn't play in any player, not even VLC, etc. Well, come to find out a lot of people have had corruption with EXT4 and their files. Personally, I like my data and not having to reformat.

So I did some research and wanted to try Reiser4 - yes yes I know who Reiser is and what he did, it's not the File System's fault, it's his - no where is it in pretty much any kernel except Gentoo has a Reiser4 Live CD, I may try that later on. So I searched for File Systems and Benchmarks and finally found the best one for me where I do VMs, XFS.

Ok now for the interesting stuff - I was talking to my friend and he's going to redo his slack server and he uses ext3 and reiserfs - he was considering going to EXT4, but after hearing all the problems I've had he decided against - so we start looking at various other distros and find they've mainly switched to EXT4 as the default.
Why? - Even RHEL6 Server is default EXT4. I don't understand why though, if data can easily become corrupt, why use EXT4?

The other thing I've found with EXT4 and BTRFS (I tried BTRFS, way not ready for prime time) and others, is that large data operations make it to where your computer isn't usable until those operations are done somtimes - I did tests with XFS last night and that was not true, XFS I was able to send email, chat on pidgin, use chromium, with brief and minor pauses, but not like before where it was like 2-3 min. wait for pauses.

Overall how can they justify using a file system that does have file corruption happen easily? - Maybe it's just semantics or just me. Can someone give some insight?
Also if you have any information on when Reiser4 will be merged into the kernel or even available on Ubuntu WITHOUT having to compile the kernel, that would be great.

Thanks!

It sounds like you have bad hardware. You should probably check your hard drive's smart data to see if it is dying. You should also check how your system receives power. If it is not on a UPS, you should buy a UPS. If you are using a generic PSU, you should get a quality PSU. Computers are highly delicate instruments and bad power will interfere with their ability to function. Your issues with data corruption could be caused by that.

---

### Post by slooksterpsv on 2010-11-20
> **Shining Arcanine said:**
> It sounds like you have bad hardware. You should probably check your hard drive's smart data to see if it is dying. You should also check how your system receives power. If it is not on a UPS, you should buy a UPS. If you are using a generic PSU, you should get a quality PSU. Computers are highly delicate instruments and bad power will interfere with their ability to function. Your issues with data corruption could be caused by that.

It's a laptop, Gateway NV53 - I did the utilities for the disk and it checked out - I did the advanced test not the basic - so the drive is good.

---

### Post by psusi on 2010-11-20
A few points:

1)  ext4 is probably the most well tested and debugged linux filesystem there is, so if you are experiencing "corruption", you likely have a serious hardware flaw that needs addressed, and it won't make a difference what fs you use

2)  As long as you stick with general hand waving "corruption" rather than describing what actually goes wrong, nobody will be able to help you figure out what is actually wrong.

3)  reiser4 is dead, and will never see the light of day.  Now that Hans is in jail, one of his lead developers has created the brtrfs which incorporates many of the ideas that were meant for reiserfs4, but it is still in early beta stage.

---

### Post by Khakilang on 2010-11-20
Never had an issue with ext4 from Jaubty to Maverick. Maybe try to defrag your hard disk. Scan for virus. Wait a minute. Did I just say that? There is some bad habits in me still refuse to die.

---

### Post by weasel fierce on 2010-11-20
I must say I havent had any issues at all with ext4

---

### Post by iponeverything on 2010-11-20
> **psusi said:**
> A few points:

1)  ext4 is probably the most well tested and debugged linux filesystem there is, so if you are experiencing "corruption", you likely have a serious hardware flaw that needs addressed, and it won't make a difference what fs you use

2)  As long as you stick with general hand waving "corruption" rather than describing what actually goes wrong, nobody will be able to help you figure out what is actually wrong.

3)  reiser4 is dead, and will never see the light of day.  Now that Hans is in jail, one of his lead developers has created the brtrfs which incorporates many of the ideas that were meant for reiserfs4, but it is still in early beta stage.

It's easy write off subtle intermittent file system issues as hardware problems, user error or even imagination. I have had ext4 file system corruption with 10.10 on a new thinkpad. The problem was not reproducible. Because it does not affect you or it is not a common problem does not mean that it does not exist. I am sticking with tried and true ext3, because I don't need the hassle of a reinstall. 

There have quite a few folks with the "I don't see it, so it does not exist" attitude or the "its the default now, so the bugs are worked out" -- Tech history is rife with stories of serious bugs making it into production code.

---

### Post by slooksterpsv on 2010-11-20
Well I'm going to Reiser4, BTRFS is needing some major work, and I was able to compile the kernel to support Reiser4 and I got speeds that I thought were only possible on an SSD. So yeah EXT4, not my cup of tea, if I see issues with Reiser4, I'll go back to XFS.

---

### Post by Sean Moran on 2010-11-20
> **slooksterpsv said:**
> Well I'm going to Reiser4, BTRFS is needing some major work, and I was able to compile the kernel to support Reiser4 and I got speeds that I thought were only possible on an SSD. So yeah EXT4, not my cup of tea, if I see issues with Reiser4, I'll go back to XFS.
I dunno mate.  I'm running nine parttions last time I counted.  This is a minimal sport of little laptop config for me.  /dev/sda* in order:  FAT32, EXT4, EXTENDED, SWAP.
Logical: EXT4, EXT4, EXT4, EXT4, EXT4, EXT4.

I've been running EXT4 for a year now I guess, and usually copy everything from one partition to another every three months or less, and it's been perfect for all my .jpegs and all my .mp3s and all my .debs and all my data, without fail.  I'm running Karmic.

---

### Post by psusi on 2010-11-20
> **iponeverything said:**
> It's easy write off subtle intermittent file system issues as hardware problems, user error or even imagination. I have had ext4 file system corruption with 10.10 on a new thinkpad. The problem was not reproducible. Because it does not affect you or it is not a common problem does not mean that it does not exist. I am sticking with tried and true ext3, because I don't need the hassle of a reinstall. 


Not only is it easy, it is the only response possible when you insist on providing zero specifics.  Just saying you have "corruption" does not describe a problem.

---

### Post by slooksterpsv on 2010-11-20
Files that have become corrupt:

1. ISO image, I download a lot and then use them in VirtualBox. After I install I unmount cause I usually install the addins or have another ISO with items I need for it. These were becoming corrupt left and right, I'd try to load them it would give errors in VirtualBox; I'd try to use UNETBOOTIN to copy the ISO Files to a USB Flash drive and SD card - it would say it couldn't read the file. I've installed Mint 10 with these flash mediums.

2. Music files, I've had music in my Music folder; play just fine, even play fine on the drive I copied them from, after a while each song just wouldn't play - not in exaile, rhythmbox, banshee, vlc, or on Windows on Winamp.

Random files I've downloaded or had have went missing too:
Images, Music files, Downloads

---

### Post by ezsit on 2010-11-20
> 1) ext4 is probably the most well tested and debugged linux filesystem there is, so if you are experiencing "corruption", you likely have a serious hardware flaw that needs addressed, and it won't make a difference what fs you use

What? Are you kidding me? ext2 and ext3 are far more stable and well tested than ext4. Ext4 was released too early, proclaimed stable too early, and chosen by Ubuntu and Red Hat too early. 

Red Hat also switched to ext3 when it was relatively young but they got lucky in that ext3 was pretty stable then. ext4 is a lot more complicated than ext3 and needs more time to mature.

I would trust your own experience and stick with ext3 for as long as you need, the support is not going anywhere. And to those who were under the impression you are forced to use the ext4 filesystem, just do an advanced install and you can choose your own filesystem.

---

### Post by whoop on 2010-11-20
> **slooksterpsv said:**
> Files that have become corrupt:

1. ISO image, I download a lot and then use them in VirtualBox. After I install I unmount cause I usually install the addins or have another ISO with items I need for it. These were becoming corrupt left and right, I'd try to load them it would give errors in VirtualBox; I'd try to use UNETBOOTIN to copy the ISO Files to a USB Flash drive and SD card - it would say it couldn't read the file. I've installed Mint 10 with these flash mediums.

2. Music files, I've had music in my Music folder; play just fine, even play fine on the drive I copied them from, after a while each song just wouldn't play - not in exaile, rhythmbox, banshee, vlc, or on Windows on Winamp.

Random files I've downloaded or had have went missing too:
Images, Music files, Downloads

Why is this file system related? There could be various causes for this problem. Sounds way to extreme to be fully ext4 related...
If you don't trust ext4 anyway, I would suggest ext3, I still have allot of ext3 machines running here.

---

### Post by stefangr1 on 2010-11-20
> **ezsit said:**
> What? Are you kidding me? ext2 and ext3 are far more stable and well tested than ext4. Ext4 was released too early, proclaimed stable too early, and chosen by Ubuntu and Red Hat too early.

I don't think it's a good idea to use a relatively new filesystem for critical data. I personally ruined an external NTFS harddisk once, at a time it was suppozed to be safe enough. Better safe than sorry... I think I'll start using ext4 for my root filesystem the next time I do a fresh install, but keep using ext3 for the data partitions a little bit longer.

---

### Post by tgalati4 on 2010-11-20
I would research the exact brand and model of the hard drive in your laptop.  Many users have had no problems with ext4.  And if google is using it now, they would be the first to notice it.  

Sounds like the crow claiming the sunrise.

---

### Post by Shining Arcanine on 2010-11-20
> **whoop said:**
> Why is this file system related? There could be various causes for this problem. Sounds way to extreme to be fully ext4 related...
If you don't trust ext4 anyway, I would suggest ext3, I still have allot of ext3 machines running here.

ext4 is ext3 with a few minor changes and it was considered to be experimental for years. How was it released early?

---

### Post by whoop on 2010-11-20
> **Shining Arcanine said:**
> ext4 is ext3 with a few minor changes and it was considered to be experimental for years. How was it released early?

Come again?

---

### Post by Shining Arcanine on 2010-11-20
> **whoop said:**
> Come again?

What do you not understand?

---

### Post by whoop on 2010-11-20
> **Shining Arcanine said:**
> ext3 and ext4 are two different revisions of the same filesystem and the changes are not terribly fundamental. How can I make that any more clear?

Still, I don't know why you are telling me that...

---

### Post by Shining Arcanine on 2010-11-20
> **whoop said:**
> Still, I don't know why you are telling me that...

You posted saying that ext4 was released early. It is just a collection of patches for ext3 that are mostly backward compatible and were extensively tested for years. ext4 was not particularly ambitious, yet you say that it was early despite years of testing. How do you consider that to be the case?

---

### Post by whoop on 2010-11-20
> **Shining Arcanine said:**
> You posted saying that ext4 was released early.
Nope, never said that. You have me confused with someone else, sir...

---

### Post by Shining Arcanine on 2010-11-20
You are right. I replied to the wrong person. I meant to reply to the ezsit:

> **ezsit said:**
> What? Are you kidding me? ext2 and ext3 are far more stable and well tested than ext4. Ext4 was released too early, proclaimed stable too early, and chosen by Ubuntu and Red Hat too early. 

Red Hat also switched to ext3 when it was relatively young but they got lucky in that ext3 was pretty stable then. ext4 is a lot more complicated than ext3 and needs more time to mature.

I would trust your own experience and stick with ext3 for as long as you need, the support is not going anywhere. And to those who were under the impression you are forced to use the ext4 filesystem, just do an advanced install and you can choose your own filesystem.

---

### Post by jdong on 2010-11-20
IMO the problems with ext4 are not anything to do with filesystem corruption. Ext4 might lose a bit more of your data when you randomly pull the power plug compared to ext3, but filesystem corruption is not more likely. If you're experiencing filesystem corruption with ext4, that indicates an issue with your hardware. By this time, ext4 has been fairly extensively used in production environments and seems to does comparably to ext3.

---

### Post by ezsit on 2010-11-20
> It is just a collection of patches for ext3 that are mostly backward compatible and were extensively tested for years. ext4 was not particularly ambitious, yet you say that it was early despite years of testing. How do you consider that to be the case?

I said ext4 was released too early because the first time it was made the default file system, people were having problems with large files and file corruption. That problem was major and should have been fixed before ext4 was made a default. Also, ext4 is not just minor patches, adding b+trees to an extents based file system is a major change and one that alters the on-disk data structures.

ext3 was merely ext2 with the journaling system from JFS tacked on, the on-disk data structures never really changed and an ext3 disk could be mounted safely as ext2. The same cannot be said for ext4 volumes.

ext4 may have been tested for years, but it was obviously not enough time for everyone. ext3 has been bullet-proof for me for years and I have no intention of switching anytime soon. It's a file system, how sexy does it have to be?

---

### Post by Shining Arcanine on 2010-11-20
> **ezsit said:**
> I said ext4 was released too early because the first time it was made the default file system, people were having problems with large files and file corruption. That problem was major and should have been fixed before ext4 was made a default. Also, ext4 is not just minor patches, adding b+trees to an extents based file system is a major change and one that alters the on-disk data structures.

ext3 was merely ext2 with the journaling system from JFS tacked on, the on-disk data structures never really changed and an ext3 disk could be mounted safely as ext2. The same cannot be said for ext4 volumes.

ext4 may have been tested for years, but it was obviously not enough time for everyone. ext3 has been bullet-proof for me for years and I have no intention of switching anytime soon. It's a file system, how sexy does it have to be?

Issues with corruption usually occurred then when people were using kernels that had bugs that had long been fixed. By the time that they had declared things as being stable, many of the bugs that ailed users were already fixed.

---

### Post by johntaylor1887 on 2010-11-20
> **nlsthzn said:**
> Seeing that EXT4 is now being made the default file system in so many distro's (Red Hat as well) I can't believe there is a major corruption problem with it... it wouldn't make sense...

I agree. Been using it here for almost 2 years with no problems.

---

### Post by psusi on 2010-11-20
> **slooksterpsv said:**
> Files that have become corrupt:

1. ISO image, I download a lot and then use them in VirtualBox. After I install I unmount cause I usually install the addins or have another ISO with items I need for it. These were becoming corrupt left and right, I'd try to load them it would give errors in VirtualBox; I'd try to use UNETBOOTIN to copy the ISO Files to a USB Flash drive and SD card - it would say it couldn't read the file. I've installed Mint 10 with these flash mediums.

2. Music files, I've had music in my Music folder; play just fine, even play fine on the drive I copied them from, after a while each song just wouldn't play - not in exaile, rhythmbox, banshee, vlc, or on Windows on Winamp.

Random files I've downloaded or had have went missing too:
Images, Music files, Downloads

Did you get any specific error messages, or check dmesg for more details?  With that limited description it could simply be medium errors on a failing disk.  Do you have any other unusual configuration, like raid?  And which Ubuntu release was this?

> **ezsit said:**
> What? Are you kidding me? ext2 and ext3 are far more stable and well tested than ext4. Ext4 was released too early, proclaimed stable too early, and chosen by Ubuntu and Red Hat too early. 

Ext4 IS ext3, with a handful of new features.  Much of the code goes back to ext2 in the 1990s.  As far as I know, no serious bugs have been found in ext4 for a few years now, and since it IS the default in Ubuntu and other distributions, it is a good bet that if there were any, they would have been found.

> **ezsit said:**
> Red Hat also switched to ext3 when it was relatively young but they got lucky in that ext3 was pretty stable then. ext4 is a lot more complicated than ext3 and needs more time to mature.

Not really.  Again, 90% of ext4 is ext3.  The only two major changes were overhauling the journaling code, and adding extents.

> **ezsit said:**
> I said ext4 was released too early because the first time it was made the default file system, people were having problems with large files and file corruption. That problem was major and should have been fixed before ext4 was made a default.

There were one or two bugs found and fixed *years* ago.

> **ezsit said:**
> Also, ext4 is not just minor patches, adding b+trees to an extents based file system is a major change and one that alters the on-disk data structures.

b-trees are only used to index very large directories, and that feature was there in ext3 and ext2 as well.  Extents required almost no modification to the on disk structures.  The code to implement them, while not entirely trivial, is also not very complex.  I managed to implement and debug support for them in e2defrag in a weekend hacking session.  Ext4 has had years of testing them on probably millions of machines at this point.

> **ezsit said:**
> ext3 was merely ext2 with the journaling system from JFS tacked on, the on-disk data structures never really changed and an ext3 disk could be mounted safely as ext2. The same cannot be said for ext4 volumes.

And ext4 is merely ext3 with a handful of new features tacked on, most of which are backwards compatible in read only mode.  The one big one that isn't is extents, which you could remove just as easily as the ext3 journal if e2fsck were patched to convert back to a block list, which would be pretty easy and could be done in a weekend.

---

### Post by del_diablo on 2010-11-20
On Ext4 you WILL have a roughy 99% chance of losing data when the power goes.
Say what you want, but I doubt the bug is still fixed :(
When the power plug goes, so does lots of data.
The problem is that you lose such a ridicules amount of data in contrast to other filesystems.
Which in essence makes it a really really poor file system.
I guess we could add it to the pile of "its broken, but since it only affect the desktop, we will not fix it".
Xorg is a part of that pile, ATI is starting to get of that pile(doing a quite good job), GIMP and GTK is a part of that pile, and more, schedule in Linux is still a part of that pile.

---

### Post by CharlesA on 2010-11-20
> **del_diablo said:**
> On Ext4 you WILL have a roughy 99% chance of losing data when the power goes.
Say what you want, but I doubt the bug is still fixed :(
When the power plug goes, so does lots of data.
The problem is that you lose such a ridicules amount of data in contrast to other filesystems.
Which in essence makes it a really really poor file system.
I guess we could add it to the pile of "its broken, but since it only affect the desktop, we will not fix it".
Xorg is a part of that pile, ATI is starting to get of that pile(doing a quite good job), GIMP and GTK is a part of that pile, and more, schedule in Linux is still a part of that pile.

[This]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781") bug?

See [here]("http://www.linuxpromagazine.com/Online/News/Ext4-Users-Report-Data-Loss?category=13388") as well.

I wonder if having a UPS on yer machine would be a good idea.. Hmm..

---

### Post by toupeiro on 2010-11-21
> **del_diablo said:**
> On Ext4 you WILL have a roughy 99% chance of losing data when the power goes.
Say what you want, but I doubt the bug is still fixed :(
When the power plug goes, so does lots of data.
The problem is that you lose such a ridicules amount of data in contrast to other filesystems.
Which in essence makes it a really really poor file system.
I guess we could add it to the pile of "its broken, but since it only affect the desktop, we will not fix it".
Xorg is a part of that pile, ATI is starting to get of that pile(doing a quite good job), GIMP and GTK is a part of that pile, and more, schedule in Linux is still a part of that pile.

I live in California, ergo, I lose power all the time and never once have I lost data on my ext4 partitions over the years on systems both with and without power conditioning.  Not even on brown outs which are far more dangerous to electronics than losing power.  Take a statistics class. :)

EXT4 is fine for the average home user.


As for the best filesystem to use on linux:

[http://zfsonlinux.org/](http://zfsonlinux.org/)

/Thread

---

### Post by psusi on 2010-11-21
> **del_diablo said:**
> On Ext4 you WILL have a roughy 99% chance of losing data when the power goes.
Say what you want, but I doubt the bug is still fixed :(

This is true of ANY filesystem.  It is not a bug, it is called the disk cache.  Writes remain in ram for a while before being written to the disk, and if you lose power before they reach the disk, then you obviously lose that data.

> **del_diablo said:**
> When the power plug goes, so does lots of data.
The problem is that you lose such a ridicules amount of data in contrast to other filesystems.

No, you don't; you lose only what you wrote in the seconds before the power went out.

> **toupeiro said:**
> 
As for the best filesystem to use on linux:

[http://zfsonlinux.org/](http://zfsonlinux.org/)

/Thread

You mean a slow fs implemented in userspace that is fundamentally broken ( it fails horribly under load testing )?

---

### Post by NightwishFan on 2010-11-21
I am sure ZFS it is not THAT utterly broken. :) Why all that aggression?

Regardless this thread convinced me to switch back to ext4, my main issue is slower dpkg and databases though I think I deal with it.

---

### Post by CharlesA on 2010-11-21
I thought that ZFS on linux was not possible due to licensing reasons?

EDIT: I mean having ZFS ported directly the Linux.

---

### Post by santosh83 on 2010-11-21
> **CharlesA said:**
> I thought that ZFS on linux was not possible due to licensing reasons?

EDIT: I mean having ZFS ported directly the Linux.

Their answer: [http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue](http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue)

---

### Post by CharlesA on 2010-11-21
> **santosh83 said:**
> Their answer: [http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue](http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue)

Thanks. :)

---

### Post by jdong on 2010-11-21
> **santosh83 said:**
> Their answer: [http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue](http://zfsonlinux.org/faq.html#WhatAboutTheLicensingIssue)

The patent issue is much more annoying. It seems like Sun filed some patents around the key designs in ZFS. Now that Oracle owns them, I don't like the idea of what they might do when a "competing" ZFS implementation starts becoming popular.

---

### Post by slooksterpsv on 2010-11-21
This thread has gotten a bit out of control in regards to the topic. I have my answers, I know where I'm headed, so I'm marking the thread as solved.

I'm going to give EXT4 a try again and see what happens, maybe I messed something up, but I doubt it.

Anyways, thanks for all your input everyone. I still really like XFS and Reiser4 - although Reiser4 I couldn't make it my / root filesystem, it was still awesome to get transfer rates faster than a Lamborghini driving at 100 mph (160.93 kph)

---

### Post by psusi on 2010-11-21
> **NightwishFan said:**
> I am sure ZFS it is not THAT utterly broken. :) Why all that aggression?


Last I heard, running any of the usual fs benchmark/stress tests on it results in lots of errors, lost files, and fs corruption.  That sounds pretty broken to me.

---

### Post by jdong on 2010-11-21
> **psusi said:**
> Last I heard, running any of the usual fs benchmark/stress tests on it results in lots of errors, lost files, and fs corruption.  That sounds pretty broken to me.

I think it's better than that in both FreeBSD and OpenSolaris worlds. Can't comment on the FUSE implementation though.

---

### Post by toupeiro on 2010-11-21
> **psusi said:**
> 


You mean a slow fs implemented in userspace that is fundamentally broken ( it fails horribly under load testing )?

1) [a ZFS kernel module]("http://zfsonlinux.org/zfs-building-rpm.html") != user space filesystem..

I have a few pretty high IO VM's running on ZFS that would directly contradict your statements, but it must be my imagination, Your source is clearly infallible (see reference point one).

---

### Post by psusi on 2010-11-21
> **toupeiro said:**
> 1) [a ZFS kernel module]("http://zfsonlinux.org/zfs-building-rpm.html") != user space filesystem..

I have a few pretty high IO VM's running on ZFS that would directly contradict your statements, but it must be my imagination, Your source is clearly infallible (see reference point one).

From what I can see on that site and on the wikipedia page on zfs, that is a native reimplementation of zfs in the kernel, but it is not yet actually usable as a filesystem because it has not yet implemented the zfs posix layer, which means that the fuse implementation is still the only usable one.

---

### Post by carolinason on 2010-11-23
i don't really get ext4 either. it's slow. corruption should be the last thing that happened though since i am under the impression that the speed issues are related to data integrity, better slow than sorry i suppose. i would investigate other possible issues that cause corruption like hardware failure.


my parts->

disc 1
/boot    - ext2
/        - ext3

disk 2
/storage - ext3

---

### Post by johntaylor1887 on 2010-11-23
> **carolinason said:**
> i don't really get ext4 either. it's slow. 

I've done many installs of linux with ext4, and have yet to see any speed issues.

---

### Post by NightwishFan on 2010-11-23
Ext4 can be slow with some databases. Though for most stuff it is improved over ext3, and I have never seen faster copies. :)

---

### Post by Barrucadu on 2010-11-23
I think a lot of the perceived problems with ext4 is due to people using it once, having some issues, and then not going back to it - but still complaining about those issues later. I've had no problems with ext4 on three different computers, even with the occasional random powercut. Of course, my anecdotal evidence is as good as anyone's - pretty worthless.

---

### Post by m4tic on 2010-11-23
My computer would often shutdown for some reason and it still does, some issue with my power supply. Well i noticed a shift in reliability coming from ext3 to ext4. But i found a solution to protect data loss, that is i now have been using an NTFS partition managed on XP and sharing it with other operating systems. I advise this.

---

### Post by cariboo on 2010-11-23
I had seeming corruption issues with ext4, back when it was first released. I had it on a fakeraid 2 disk array. that was always getting corrupted, but whether it was because of ext4 or fakeraid I'm not sure. The raid array has since been broken up and the disks formatted as xfs. I haven't had any problems since.

---

