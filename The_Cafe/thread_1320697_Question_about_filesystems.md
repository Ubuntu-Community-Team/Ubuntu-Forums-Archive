---
title: "Question about filesystems"
date: 2009-11-09
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-11-09
I was looking up some comparisons of various file systems but honestly most of the articles weren't filled with techno jargon and really didn't explain what the advantages of the varios FS's were in plain English.

I'm thinking of splitting my HD up into 3 partitions:
- One for Ubuntu and my home directory
- One for my video/audio/ebook files (which are backed up on an external HD)
- One for the saved data for my Windows XP, Server 2003, and 7 virtual machines.

I was planning on using ext4 for the main partition because from what I've heard it's a good all FS. There are some supposid stability issues, but I'm not hosting a corporate server where a lost file could cost me thousands of dollars worth of downtime. 

Would there be any benefit to using other FS's for my backed up files or virtual machine or misc saved data? Or should I just stick with ext4?

---

### Post by Somme on 2009-11-09
The latest news were about the fact that ext4 might corrupt files bigger than 500Mb - that was enough for me to not to choose it for now ( even on Karmic, I still use ext3 ).

---

### Post by Joe Ker1086 on 2009-11-09
> **Somme said:**
> The latest news were about the fact that ext4 might corrupt files bigger than 500Mb - that was enough for me to not to choose it for now ( even on Karmic, I still use ext3 ).

Never heard this one......Ill have to test it out, running fedora 12 beta with ext4 and have no problems

---

### Post by FuturePilot on 2009-11-09
> **Joe Ker1086 said:**
> Never heard this one......Ill have to test it out, running fedora 12 beta with ext4 and have no problems

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579")

---

### Post by konqueror7 on 2009-11-09
ext4 is pretty much stable on my box...i would just advice to use in your */boot* ext3/ext2 instead...

---

### Post by Marlonsm on 2009-11-09
> **Somme said:**
> The latest news were about the fact that ext4 might corrupt files bigger than 500Mb - that was enough for me to not to choose it for now ( even on Karmic, I still use ext3 ).

I've also never heard of that.
I'm currently using ext4 and all my files are normal, including the big ones.

---

### Post by cariboo on 2009-11-09
When ext4 first was released it did have a problem with large files, most of the problems were fixed in Jaunty, I regularly move 4Gb+ files around with no problems.

---

### Post by FuturePilot on 2009-11-09
> **cariboo907 said:**
> When ext4 first was released it did have a problem with large files, most of the problems were fixed in Jaunty, I regularly move 4Gb+ files around with no problems.

No, when it was first released it had a problem with leaving you with 0 byte files after a crash or hard shutdown. It still has issues with large files. See my previous post. Personally, I still don't trust Ext4 yet.

---

### Post by RiceMonster on 2009-11-09
I use ext4 with Fedora 11 and Arch Linux. I haven't had any problems at all yet. I believe there's still a bug going around that may cause data corruption, but I haven't encountered this. However, I haven't really done any notably large data transfers. I'd probably still use ext3 on a server just to be safe.

---

### Post by blueshiftoverwatch on 2009-11-09
> **cariboo907 said:**
> When ext4 first was released it did have a problem with large files, most of the problems were fixed in Jaunty, I regularly move 4Gb+ files around with no problems.
Based on what I've heard from reading different threads around the forums it seems like a ton of people have heard about ext4 having issues with large files. But not that many people have actually had those issues themselves. Sounds sort of like unwarranted hysteria. Just like how every Ubuntu release is touted as "the worst ever" when the majority of people don't have that many problems and are happy with the new release. But just out of curiosity, how much better is ext4 than ext3? I've heard that it's both faster and is more resistant to fragmenting than the previous implementation of ext. And since the hard drive is the biggest bottleneck of the modern computer system (most of us aren't ready to spend the money on solid state drives yet) having a file system that was able to squeeze more speed/efficiency out of the hard dive seems like a good idea.

But anyway, this wasn't so much a thread about the advantages or disadvantages of ext4 as much as it was just me asking whether or not I should stick with the default file system (ext4) for partitions where I'm not installing an OS.

My backup partition is going to be used primarily for storing large video files as well as small audio files. Once they're on the drive they're pretty much just going to be left alone except for when I want to access them, so theirs not going to be a whole lot of writing to that drive going on. Is ext3/4 the best file system for that kind of kind of purpose? Or would XFS, JFS, ResierFS, Reiser4, or any of the other plethora of file systems for Linux be more efficient? If Ext4 has some possible bugs with large files than what FS should I use on a partition where large files are going to be stored? Ext3 seems like the obvious answer but there are lots of other FS's out there that must have some purpose if people use them over Ext3.

What kind of file system would be best for storing the virtual file systems of the Windows OS's that I want to work with in Virtualbox? So that if my main OS crashes I'll only have to re-install/configure Ubuntu all over again instead of Ubuntu plus 3 different Windows OS's.

---

### Post by FuturePilot on 2009-11-09
> **blueshiftoverwatch said:**
> Based on what I've heard from reading different threads around the forums it seems like a ton of people have heard about ext4 having issues with large files. But not that many people have actually had those issues themselves. Sounds sort of like unwarranted hysteria. 


So we should just ignore known problems like they don't exist because it may not affect us? I think it's better to be aware of problems instead of just brushing them off like they don't exist. It's not unwarranted hysteria. It's getting the information out there so people know about it so they can make their own decision instead of running in to the problem unaware of its existence and then complaining that Ubuntu sucks because it ate my data. Unwarranted hysteria would be "OMG EXT4 WILL DESTROY ALL YOUR FILES AND DATA!!!!!!111" I have yet to see anyone say anything along those lines.

---

### Post by blueshiftoverwatch on 2009-11-09
> **FuturePilot said:**
> So we should just ignore known problems like they don't exist because it may not affect us? I think it's better to be aware of problems instead of just brushing them off like they don't exist. It's not unwarranted hysteria, it's getting the information out there so people know about it so they can make their own decision. Unwarranted hysteria would be "OMG EXT4 WILL DESTROY ALL YOUR FILES AND DATA!!!!!!111" I have yet to see anyone say anything along those lines.
Maybe people haven't said it in all caps with multiple exclamation points at the end like in your post. But that's basically the impression I've gotten from reading a lot of the posts recently. I never said that possible problems should be ignored. I was just saying that 90% of the posts that talk about Ext4 in a negative light seem to be people who have **heard** that Ext4 might have some bugs to be worked out instead of people who have actually **experienced** those bugs for themselves and can confirm that they actually exist. Just like how in high school a rumor about someone would go around and 90% of the people who heard and repeated the rumor have only heard about it from other people and haven't actually confirmed whether or not the rumor is true or false for themselves. Or if there was some truth to the rumor, how much of it was factual and how much was misinformation.

But like I said, this thread isn't so much about the Ext3 vs Ext4 debate. It's about me wanting to learn what the strengths and weaknesses of the various alternative FS's are so that I can make an informed decision about what FS's I want to use for my planned "backup" partition and the partition I want to keep my VM files on. Because most of the articles I've found that compare FS's are written using a lot of jargon or are several years old and might not reflect updates that have been made to the FS's or workarounds to certain problems that have been implemented since then.

---

### Post by blueshiftoverwatch on 2009-11-09
Since I'm going to be storing all of my large files on a separate partition and Linux is mainly a whole bunch of very small files (which Reiser works well with) what do you think about making ReiserFS or Reiser4 the FS for my Ubuntu partition, ext3 for my video/audio storage partition due to it's stability, and XFS for my Windows VM partition since it handles large files very well and the virtual file systems that VM's use are each represented as one file.

1. Is this a good idea?

2. Do Reiser and XFS work "out of the box" like ext3/4 does or will it require a bit of tinkering?

---

### Post by falconindy on 2009-11-09
ReiserFS 3 (not 4) is just as reliable and solid as Ext3. It's a high performer for for partitions with lots of small files (e.g. /etc or /var). XFS is also solid and works well on partitions with lots of larger files (e.g. audio/video dumps). They both work 'out of the box' provided you have the proper support packages which are available in the repos. If I were to reformat right now, I'd probably do the following:

/boot on ReiserFS
/var and /etc on ReiserFS
/ on Ext3
/home on Ext3
Everything else on XFS

Note: Be aware that unlikely Ext3/4, an XFS partition can be enlarged, but not shrunk.

---

### Post by blueshiftoverwatch on 2009-11-09
How will my performance be affected if I'm using ReiserFS as my main partition while at the same time playing audio/video files stored on an Ext3 partition?
> **falconindy said:**
> ReiserFS 3 (not 4) is just as reliable and solid as Ext3. It's a high performer for for partitions with lots of small files (e.g. /etc or /var).
I was planning on just making the entire Ubuntu partition ReiserFS. As long as I download large files (like ISO files) to the Ext3 partition I should be good, right?
> **falconindy said:**
> XFS is also solid and works well on partitions with lots of larger files (e.g. audio/video dumps).
I don't know if I'd consider mp3 files ranging in size from 1-5MB to be large files. I was going to use Ext3 for my audio/video dump and XFS for my virtual Windows machines since each virtual file system is represented by one file. So I'm going to be dealing with individual files that are at least 10GB in size.

---

### Post by blueshiftoverwatch on 2009-11-10
I know that it's possible to set permissions on files/folders that only certain users or groups are allowed to write to them. Is it possible to do that but allow only certain applications to write to certain folders?

---

### Post by karlmp on 2009-11-12
if you think you have good karma then use ext4

[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Set_Filesystem_Mountpoints](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Set_Filesystem_Mountpoints)

---

### Post by Techsnap on 2009-11-12
I use JFS because it's a nice mix of really stable and pretty fast.

---

