---
title: "Does Linux handle NTFS differently than Win?"
date: 2008-12-04
forum: The Cafe
---

### Post by Patrick Snyder on 2008-12-04
I've recently read a few articles on file systems with a slant on fragmentation.

They usually say, Linux does it this way, Windows does it that way.

My question is, do they really mean: Ext2/3 does it this way and FAT or NTFS does it that way?

I use FAT and NTFS external hard drives for videos/music/games/downloads/etc because I switch between ubuntu and WinXP.  I'm constantly deleting, replacing, etc.  I wanted to know if I have to defrag the externals.  Many of the articles say you don't have to defrag Linux, but I started to wonder if they just meant you don't have to defrag Ext2/3.

Please let me know (^_^)/

---

### Post by inobe on 2008-12-04
windows defrags to access programs faster, it reduces seek time in a windows environment.

simply said, if its an external with vids,music, files, their is no need unless it has programs installed on it.

it would be useless defraging a drive with files considering they are manually searched for !

edit: linux file system is does not need defraging, every time you reboot or install and remove' the filing system managed

---

### Post by WaeV on 2008-12-04
I was wondering the same thing, and you may have answered the question but if you did I still don't fully understand.

This site explains the situation pretty well, but do the examples provided deal with FAT vs ext2 or Windows vs Linux? [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by inobe on 2008-12-04
i must add that windows users let the smallest of fragments under their skin, meaning the windows defrag tool is not good enough to them ! they must hunt down third party tools with fierce vengeance to defrag a .avi ....... when in fact their would be no noticeable difference in performance .

delete a app from windows, this space would never get allocated unless you use the defrag.exe

on a linux file system ext3 will allocate these blocks close enough.

ext3 will have fragments, with the example above and how ext3 works' the amount of fragmentation is not noticeable, thus no need to defrag, comprende ;)

---

### Post by WaeV on 2008-12-04
So linux doesn't need to defrag because linux file systems such as ext3 do not fragment?

---

### Post by solitaire on 2008-12-04
ext3 handles files better than NTFS and FAT, so the impact of Fragmented files is less noticeable under ext3 than the other 2 file systems. 

As long as you have 5% free space on a ext3 drive, fragmentation should not be an issue.

---

### Post by inobe on 2008-12-04
all file systems fragment

> Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.

it fragments but it doesn't need to be defraged.

---

### Post by magmon on 2008-12-04
Wow. Thats so much easier than windows!

---

### Post by WaeV on 2008-12-04
But even if you used NTFS with a linux OS, it would still fragment as bad as under Windows?

---

### Post by jdong on 2008-12-04
> **WaeV said:**
> But even if you used NTFS with a linux OS, it would still fragment as bad as under Windows?

Probably. The ntfs-3g allocator from my looking doesn't seem to do anything special to avoid fragmentation.

Then again, with modern TCQ/NCQ capable hard drives with large caches, the benefits of defragmentation for IO performance, in my opinion, are arguably less and less significant.

Let your computer take care of itself and stop wasting more time obsessing over cleaning up after your computer -- when it becomes a problem, deal with it, otherwise, leave it alone!

---

### Post by WaeV on 2008-12-04
Oh, I was just curious.  I can't remember the last time I defragged my Windows install.  Thanks for the answer.

---

### Post by jdong on 2008-12-04
Sure, no problem. My general philosophy on maintenance is to do it when it's necessary. there really isn't a need on any operating system to try too hard to "keep it running in tip top shape" :)

---

### Post by WaeV on 2008-12-04
heh, I thought about runing XP maximized in virtualbox under a minimalist linux system, then restoring to a snapshot every month or so to keep it running snappy.  I would have carried through with it but I found out 3D acceleration isn't too hot in a virtual system.

---

### Post by poebae on 2008-12-04
EDIT: oops, wrong thread

---

### Post by WaeV on 2008-12-04
Umm...  did you mean the "music that was stuck in my head" thread?

---

### Post by poebae on 2008-12-04
> **WaeV said:**
> Umm...  did you mean the "music that was stuck in my head" thread?
Yep, I had that thread open and thought I was replying in there :S

---

### Post by psusi on 2008-12-05
> **inobe said:**
> windows defrags to access programs faster, it reduces seek time in a windows environment.

simply said, if its an external with vids,music, files, their is no need unless it has programs installed on it.

it would be useless defraging a drive with files considering they are manually searched for !

edit: linux file system is does not need defraging, every time you reboot or install and remove' the filing system managed

None of that is at all true.  It does not matter what the file contains, be it a program, a video, or last year's payroll; if it is horribly fragmented, then reading it will be slow.

And rebooting, installing, or removing ( I assume you mean programs ) does nothing to relieve fragmentation.

---

### Post by jdong on 2008-12-05
> **psusi said:**
> None of that is at all true.  It does not matter what the file contains, be it a program, a video, or last year's payroll; if it is horribly fragmented, then reading it will be slow.

And rebooting, installing, or removing ( I assume you mean programs ) does nothing to relieve fragmentation.

Windows does have some magical self-defragging properties though (Prefetch.ini/ProcessIdleTasks, Prefetch essentially can store a nonfragmented block-ordered cache image for commonly started applications, etc) that are triggered by rebooting, installing, and/or removing. Or by, say, leaving the system alone :)

---

### Post by inobe on 2008-12-05
> **psusi said:**
> None of that is at all true.  It does not matter what the file contains, be it a program, a video, or last year's payroll; if it is horribly fragmented, then reading it will be slow.

And rebooting, installing, or removing ( I assume you mean programs ) does nothing to relieve fragmentation.

tell us what you mean when you say slow ?

describe to us how much time it will take for that avi to play on a disk containing 500 avi's ?

edit: i have a few hundred gigs on an ntfs drive' never defraged, i do not experience lag, once the drive is mounted' i can access and view hundreds of gigs instantly :shrug:

---

### Post by jdong on 2008-12-05
> **inobe said:**
> tell us what you mean when you say slow ?

describe to us how much time it will take for that avi to play on a disk containing 500 avi's ?

edit: i have a few hundred gigs on an ntfs drive' never defraged, i do not experience lag, once the drive is mounted' i can access and view hundreds of gigs instantly :shrug:

In my worst-case scenario test on ext3, I downloaded a 4GB Fedora torrent rate-limited at 100KB/s to simulate the filesystem's worst-case fragmentation.


Then, I dropped the disk cache and read it back. It read back at around 8MB/s when the ideal disk speed is 40MB/s sustained sequential. So yeah, fragmentation did have an impact there. Defragging it causes it to read back at around 30MB/s. Interestingly enough, XFS read back at 30MB/s the first time, and after a defrag it read back at 40MB/s exactly.

Now back to my original point of not obsessing over maintenance: If these are AVI files, **who cares?** for the average HD AVI you only need to read it back at 3MB/s. If you're burning this torrent to a DVD, you only need to read it back at 2MB/s then 6MB/s then 12MB/s peak (by which time growisofs's buffer would've prefetched enough anyway).


Now if this were a raw DV video capture that you were editing in realtime, sure, you probably need all 30-40MB/s -- in which case go crazy defragging. Otherwise, I don't see the sense in wasting time reading back the data slowly just so that you can gamble on writing it back out a bit more neatly.

---

### Post by Delever on 2008-12-05
Yes, linux handle NTFS differently.

This is typical windows disk, used alot. Red is swap file (unmovable), yellow - fragmented files, green - not fragmented files:

[IMG]http://img514.imageshack.us/img514/8797/windowsfragmentedxn1.jpg[/IMG]

Windows allocates space for files sequentially, while linux calculates best place for each file and puts it anywhere on disk.

This is clean NTFS disk (4GB), created under linux, with 1GB of average size files (1 - 4 MB).

[IMG]http://img80.imageshack.us/img80/1530/linuxntfsof9.jpg[/IMG]

Trying to defragment that under windows would take a lot of time, yet is is not actually fragmented. If you defragment it under windows, and continue to use filesystem under Linux, it will continue to place files all over the place, and it won't be so bad. 

However, if you create large number of files under windows on such filesystem, it will get very fragmented, because windows will place it's files sequentially, around files placed by Linux. it will get bad, because a) defragmenting such results in windows will take alot of time and b) linux don't defragment files!

So, it is best to choose from which OS you create new files on NTFS disk: either it is windows, and you defragment files frequently, or it is linux, and you don't worry about fragmentation. Using both and then performing defragmentation would wear down your disk faster, and it will take more time.

---

### Post by forrestcupp on 2008-12-05
But to be clear about it, when people say Linux drives don't need to be defragmented like Windows' drives do, they are talking about the file systems, not the OS's.

The simple and basic explanation is this.  NTFS/FAT file systems cram all of your files into as small of a space as they can toward the front of the drive.  So moving or deleting files leaves spaces that end up getting filled with other files that aren't exactly the same size.  If the new file is larger, it is split up on the drive, hence the fragmentation.  

Ext file systems don't try to cram the files into a small space; they spread the files out over the drive, which leaves plenty of space to work with.  This prevents fragmentation because the files aren't crammed together.  But this only prevents fragmentation until the drive starts to get full, which means there isn't as much space to work with.  A full drive will get fragmented with any kind of file system.

Because in an NTFS system the files are all readily available at the beginning of the drive, a freshly defragged NTFS drive is probably slightly quicker than an Ext drive.  But an Ext drive is probably slightly quicker than a fragmented NTFS drive, and it's definitely more consistent.

---

### Post by Delever on 2008-12-05
> **forrestcupp said:**
> But to be clear about it, when people say Linux drives don't need to be defragmented like Windows' drives do, they are talking about the file systems, not the OS's.

The simple and basic explanation is this.  NTFS/FAT file systems cram all of your files into as small of a space as they can toward the front of the drive.  So moving or deleting files leaves spaces that end up getting filled with other files that aren't exactly the same size.  If the new file is larger, it is split up on the drive, hence the fragmentation.  

Ext file systems don't try to cram the files into a small space; they spread the files out over the drive, which leaves plenty of space to work with.  This prevents fragmentation because the files aren't crammed together.  But this only prevents fragmentation until the drive starts to get full, which means there isn't as much space to work with.  A full drive will get fragmented with any kind of file system.

Because in an NTFS system the files are all readily available at the beginning of the drive, a freshly defragged NTFS drive is probably slightly quicker than an Ext drive.  But an Ext drive is probably slightly quicker than a fragmented NTFS drive, and it's definitely more consistent.

Yes, and Linux (well, Ubuntu) applies those rules to NTFS drives too. That's what i wanted to say.

---

### Post by forrestcupp on 2008-12-05
> **Delever said:**
> Yes, and Linux (well, Ubuntu) applies those rules to NTFS drives too. That's what i wanted to say.

That's pretty cool.  I didn't know it does that in NTFS.

---

### Post by Delever on 2008-12-05
> **forrestcupp said:**
> That's pretty cool.  I didn't know it does that in NTFS.

It is cool until you start using same disk under windows. Worst case scenario happened when I installed windows in empty NTFS disk without reformat (it was used alot by ubuntu before). Then I got complaints that it was not possible to defragment disk completely. It turned out, some small pieces (probably folder descriptors or something, i don't know) was left scattered all over the disk, and they were unmovable when Windows was turned on.

---

### Post by forrestcupp on 2008-12-05
> **Delever said:**
> It is cool until you start using same disk under windows. Worst case scenario happened when I installed windows in empty NTFS disk without reformat (it was used alot by ubuntu before). Then I got complaints that it was not possible to defragment disk completely. It turned out, some small pieces (probably folder descriptors or something, i don't know) was left scattered all over the disk, and they were unmovable when Windows was turned on.
Wow.  I've used an already created NTFS disk between Windows and Linux with no problems, but I've never tried installing Windows on one.

---

### Post by psusi on 2008-12-05
> **inobe said:**
> tell us what you mean when you say slow ?

Slow:  Adjective.

1. moving or proceeding with little or less than usual speed or velocity: a slow train.
2. characterized by lack of speed: a slow pace.
3. taking or requiring a comparatively long time for completion: a slow meal; a slow trip. 

> **inobe said:**
> 
describe to us how much time it will take for that avi to play on a disk containing 500 avi's ?

If you are just playing it then you either can read it fast enough to keep up with the playback or you can't.  If you can't ( because it is so badly fragmented ), you get skipping our pausing in the output.  If you are copying it to an external medium, the time it takes to do so is highly dependent on whether it is highly fragmented or not.

> **inobe said:**
> 
edit: i have a few hundred gigs on an ntfs drive' never defraged, i do not experience lag, once the drive is mounted' i can access and view hundreds of gigs instantly :shrug:

Define "view hundreds of gigs instantly".  You certainly aren't reading the contents of all of those files "instantly", so I assume you are confusing reading all of the files with browsing the directory of them.

> **jdong said:**
> 
Now back to my original point of not obsessing over maintenance: If these are AVI files, **who cares?** for the average HD AVI you only need to read it back at 3MB/s. If you're burning this torrent to a DVD, you only need to read it back at 2MB/s then 6MB/s then 12MB/s peak (by which time growisofs's buffer would've prefetched enough anyway).

Not obsessing about it is one thing; denying that it is there is another.  If you like to multitask then you may care about those fragmented avi files since alone you may be able to read them fast enough to keep up with the player or burner, but when it takes more time to do so, that leaves less time for other IO on the disk.

I agree that generally speaking, the effect is not enough for most people to take notice of and do something about, but that does not mean it isn't there.

> **forrestcupp said:**
> But to be clear about it, when people say Linux drives don't need to be defragmented like Windows' drives do, they are talking about the file systems, not the OS's.

No, they are talking about the OS.  It is the OS that decides where to place the files, not the FS.  Windows chooses poorly.  See the post above yours for a very good explanation.

---

### Post by inobe on 2008-12-05
when i mount the drive with linux, all files become instantly avail !

i do not experience what you have described ...

---

### Post by jdong on 2008-12-05
> **psusi said:**
> 
Not obsessing about it is one thing; denying that it is there is another.  If you like to multitask then you may care about those fragmented avi files since alone you may be able to read them fast enough to keep up with the player or burner, but when it takes more time to do so, that leaves less time for other IO on the disk.

I agree that generally speaking, the effect is not enough for most people to take notice of and do something about, but that does not mean it isn't there.


Right; that's my point -- I'm not saying "No fragmentation doesn't matter period", I'm trying to encourage everyone to ask "Wait... does it really make a difference for me?"

I bet for 80% or more of people who rigorously follow a defrag regimen, it probably is not going to make a significant difference for their workload, in which case in my opinion it's a bit silly to spend so much time and effort worrying over such a thing.

Absolutely there are workloads and usecases where maintaining peak filesystem performance is extremely vital to whether or not you can get anything useful done.

---

### Post by psusi on 2008-12-05
> **inobe said:**
> when i mount the drive with linux, all files become instantly avail !

i do not experience what you have described ...

Mounting the drive does not read all files on it.  Browsing the directory in nautilus also does not read the files; it just reads the directory to see that files are there.  Try COPYING the files.  That reads them ( and writes them to the new location ), and how long it takes to do so is affected by how fragmented they are.

---

### Post by Polygon on 2008-12-06
the only time i have ever experienced improvement with defragging my ntfs drive in windows is video game loading times. Since the game files are at least a couple GB, loading the game (the map, models, textures, etc) goes a lot faster if i have defragged anytime recently (but this was when i had not defragged for like years however...)

---

### Post by jdong on 2008-12-06
> **Polygon said:**
> the only time i have ever experienced improvement with defragging my ntfs drive in windows is video game loading times. Since the game files are at least a couple GB, loading the game (the map, models, textures, etc) goes a lot faster if i have defragged anytime recently (but this was when i had not defragged for like years however...)

Interesting to note, video game load times usually involves loading like 100 different files, some big some small. There's not only a question of whether or not the files are fragmented or not, but also if they are hot-clustered or not.

That is, defragmentation is worthless if all 100 files are not fragmented but rather are dispersed randomly throughout the disk.


There's few defraggers that try to be smart enough to address this situation; unfortunately game loading in its current implementation doesn't really take advantage of Windows' Prefetch and SuperPrefetch mechanisms , which do exactly this -- profile an application's load sequence then write a prefetching cache that contains the critical components used during loading, written out in sequential order.

---

### Post by inobe on 2008-12-06
> **psusi said:**
> Mounting the drive does not read all files on it.  Browsing the directory in nautilus also does not read the files; it just reads the directory to see that files are there.  Try COPYING the files.  That reads them ( and writes them to the new location ), and how long it takes to do so is affected by how fragmented they are.

since i am so bored' i pulled the windows ide drive out of the closet, connected, booted into windows, defraged media drive, unplugged windows and tossed it back in the closet, booted up to ubuntu, accessed the media drive.

same results, blazing fast, greased lightning to say the least...

hmm, being so bored' i started wondering about fragments on **SSD** drives .

---

### Post by jdong on 2008-12-06
> **inobe said:**
> since i am so bored' i pulled the windows ide drive out of the closet, connected, booted into windows, defraged media drive, unplugged windows and tossed it back in the closet, booted up to ubuntu, accessed the media drive.

same results, blazing fast, greased lightning to say the least...

hmm, being so bored' i started wondering about fragments on **SSD** drives .

Accessing is very different from trying to pull all the data off the drive. You will see a noticeable performance difference between reading from fragmented and defragmented files for sustained throughput. Probably a factor of 2 or 3.

---

### Post by Kellemora on 2008-12-06
You can take this with a grain of salt, but this is how the difference between ext and ntfs was explained to me.

NTFS is like a string of beads.  You write a file and it sequential along the string.  AAAAAAAA
When you add another file it looks like AAAAAAABBBBBBBB, so on and so forth.
NOW, when you OPEN file A and make changes to it, making it larger, when that file is saved back to the disk, you now have it looking like this AAAAAAABBBBBBBAAA.
Then you add another new file and the drive now looks like AAAAAAABBBBBBBBAAACCCCCCCC.
Open B and edit that file and you end up with AAAAAAABBBBBBBBAAACCCCCCCCBBB.  It just continually keeps getting more and more fragmented each time you change it.

EXT is more like a mail sorters wall of pigeonholes.
When you save a file A, it gets stuck into a pigeonhole somewhere on your hard drive.  You save another file B and it gets stuck into a different pigeonhole.  You open A and edit it, it gets stuck back into the same pigeonhole.

If you edit the file so that it becomes larger than the available pigeonhole it's divided into two pigeonholes, usually side by side if available.  If not, then the file may be located in two different areas of the disk.  But if you RENAME the file, it will save it in two pigeonholes that are sequential to each other.

Forensics loves to have to search Linux drives because it's a SNAP, everything is logical and follows a set file pattern.  But NTFS drives are their worst nightmare to have to piece together files, because they are here, they are there, they are everywhere.

I also understand that WRITING TO an ntfs file from Linux still uses the pigeonhole method of writing.  In other words it tries to keep the files together as they should be.  This seems logical to me because a file edited many times on a windows machine takes longer to reload than a file of the same size edited on a Linux box and saved to an ntfs drive.
Even more obvious if you look at the display of the drive through a defragging tool that gives a visual display.  It looks more fragmented because files are everywhere.  But when you run defrag, they line up like little indians very fast on the linux written drive, without moving and rewriting several times.

TTUL
Gary

---

### Post by jdong on 2008-12-06
Again, we should point out none of these properties are due to the filesystem but rather the implementation of the filesystem driver. Even EXT3/EXT4 has had multiple allocation algorithms swapped in and out over time.

---

### Post by HermanAB on 2008-12-06
Actually, defragmenting NTFS doesn't make much difference and is almost never needed.  NTFS uses a balanced tree structure (B-tree) to store data, much the same as Ext2/3/4 on Linux.

Here is some more data from the horse's mouth:
[http://technet.microsoft.com/en-us/library/cc781134.aspx](http://technet.microsoft.com/en-us/library/cc781134.aspx)

Cheers,

Herman

---

### Post by jdong on 2008-12-06
Actually B-tree or not is not the problem, a B-tree doesn't do anything to address the issue of nonsequential read access to the drive which is the primary problem that people associate with "Fragmentation" on mechanical disks.

However, as I pointed out earlier in the case of loading games or an applications, file fragmentation alone isn't the problem, you need to look at the big picture with "hot-clusteredness" too. Are all the 200 files you need to start OpenOffice located together on the disk? In the order that you need them to start up OpenOffice? That's an issue that blindly defragmenting the disk doesn't resolve at all. In fact in trying to find contiguous free space a defragmenter might actually **de-cluster** files that were located together when they were installed close to the same time.

---

### Post by JNelson on 2008-12-06
How can clustering files next to each help if it has to go back to the MFT/Inode to read the next file?

---

### Post by jdong on 2008-12-06
> **JNelson said:**
> How can clustering files next to each help if it has to go back to the MFT/Inode to read the next file?

Those are small compact structures and usually the firmware and software readahead mechanisms nab enough of the MFT or inode table that it is a non-issue. Some filesystems even store a complete bitmap cache in RAM at mount-time (reiserfs)

---

### Post by JNelson on 2008-12-06
Dont any linux filesystems store data inline the Inode if it ls small enough like ntfs?


NTFS Inode size 1KB so a file like 400bytes can get stored in it.

---

### Post by jdong on 2008-12-06
> **JNelson said:**
> Dont any linux filesystems store data inline the Inode if it ls small enough like ntfs?


NTFS Inode size 1KB so a file like 400bytes can get stored in it.

reiserfs and reiser4 employed this strategy (they called it tail packing). It offered compact space storage but made metadata write access significantly slower to the point that Namesys recommended turning off the feature on performance-critical applications (remember **-o notails**?).

---

### Post by psusi on 2008-12-06
> **inobe said:**
> since i am so bored' i pulled the windows ide drive out of the closet, connected, booted into windows, defraged media drive, unplugged windows and tossed it back in the closet, booted up to ubuntu, accessed the media drive.

same results, blazing fast, greased lightning to say the least...

hmm, being so bored' i started wondering about fragments on **SSD** drives .

So you repeated a test that I already told you was invalid and said it shows I am wrong?  Are you not reading what I am saying?  I'll try it one more time:

Mounting the drive and looking what files are on it does not cause all of them to be read, ergo it does not matter how fragmented they are or are not.

> **HermanAB said:**
> Actually, defragmenting NTFS doesn't make much difference and is almost never needed.  NTFS uses a balanced tree structure (B-tree) to store data, much the same as Ext2/3/4 on Linux.

Here is some more data from the horse's mouth:
[http://technet.microsoft.com/en-us/library/cc781134.aspx](http://technet.microsoft.com/en-us/library/cc781134.aspx)

Cheers,

Herman

Clearly you have never used Windows very much over the years ( or DOS before it ) or you should know that defragmenting makes a rather large difference, and that is why there are a number of tools on the market that people willingly pay for to do so.

NTFS stores only the file names in a directory listing in a B-tree, not file data.  Ext[234] can optionally store a second directory index that is sorted in hash order for faster name lookup, in addition to the normal directory listing that is just a big array of names and inode numbers.  Neither has anything to do with fragmentation of files' data blocks.

---

### Post by jdong on 2008-12-06
> **JNelson said:**
> Dont any linux filesystems store data inline the Inode if it ls small enough like ntfs?


NTFS Inode size 1KB so a file like 400bytes can get stored in it.

**wait a minute**... can you give me a citation that shows NTFS supports tail-packing? I don't recall anywhere that I've read which claimed NTFS is capable of doing tail-packing or any other form of block suballocation.

---

### Post by JNelson on 2008-12-06
Nm

---

### Post by JNelson on 2008-12-06
Nm

---

### Post by JNelson on 2008-12-06
It says it in the inside windows 2k book and wiki has it too.

[http://en.wikipedia.org/wiki/NTFS#Internals](http://en.wikipedia.org/wiki/NTFS#Internals)

> To optimize storage for the common case of small data files, NTFS prefers to place file data within the master file table if it fits instead of using MFT space to list clusters containing the data. The former is called "resident data" by computer forensics workers. The amount of data which fits is highly dependent on the file's characteristics, but 700 to 800 bytes is common in single-stream files with non-lengthy filenames and no ACLs. Encrypted-by-NTFS, sparse, or compressed files cannot be resident.

Since resident files do not directly occupy clusters ("allocation units"), it is possible for an NTFS volume to contain more files on a volume than there are clusters. For example, an 80 GB (74.5 GiB) partition NTFS formats with 19,543,064 clusters of 4 KiB. Subtracting system files (64 MiB log file, a 2,442,888-byte $Bitmap file, and about 25 clusters of fixed overhead) leaves 19,526,158 clusters free for files and indices. Since there are four MFT records per cluster, this volume theoretically could hold almost 4 × 19,526,158 = 78,104,632 resident files.

---

### Post by jdong on 2008-12-06
Yes, you are correct. I also found some references that talk about this too; Any free space at the end of a 1KB MFT record can be used to store the rest of the file.

---

### Post by JNelson on 2008-12-06
JFS could implement what NTFS does, I found it in an email from the jfs developer 9-12 months ago.

> No.  It could, but it doesn't.  The file format allows it, and symlinks
are stored that way, but it was never implemented for regular files.
Implementing it now would cause backwards-compatibility problems with
older kernels.

---

### Post by jdong on 2008-12-06
BSD FFS was first to support this; btrfs will support this. In general I've noticed that performance is significantly worse when tailpacking compared to not tailpacking in most filesystem implementations of this feature, and the primary reasons for doing it is if you are storing enough small files to exceed your filesystem's max # of files limitation.

---

### Post by psusi on 2008-12-06
I don't see how it could slow things down to have the data in the inode that you already have read instead of in another data block on disk.

AFAIK, the notails option was added to reiserfs for compatibility with things like LILO, which couldn't handle it.

I'm still trying to figure out if ext4 can pack extended attributes and/or file data in the inode if there is room, especially since they increased the default inode size from 128 to 256 bytes, even for newly formatted ext2/3 filesystems, which won't make use of the extra space.

---

### Post by jdong on 2008-12-06
> **psusi said:**
> I
AFAIK, the notails option was added to reiserfs for compatibility with things like LILO, which couldn't handle it

Absolutely not. Tailpacking had a significant performance impact on reiserfs:

[http://www.informatik.uni-frankfurt.de/~loizides/reiserfs/gaugeperf.html](http://www.informatik.uni-frankfurt.de/~loizides/reiserfs/gaugeperf.html)

I wish Namesys's site were still up; they had a specific FAQ entry that recommended disabling notails where performance was more important than space savings.

On the 10,000 files per directory test, the difference was nearly a factor of 2 in fragmentation tests:


[img]http://www.informatik.uni-frankfurt.de/~loizides/reiserfs/gif/gaugeperf/reiser-10000-dircmp.png[/img]   [img]http://www.informatik.uni-frankfurt.de/~loizides/reiserfs/gif/gaugeperf/reiser-notail-10000-dircmp.png[/img]

---

### Post by JNelson on 2008-12-06
Jdong,
Block suballocation is different than placing the file in the Inode. Block suballocation is using parts of unused blocks. Like a 4KB block has 1KB in yet it has 3KB space in the rest of the block. Reiserfs will use that 3KB space in the 4KB block. 

NTFS dosent support block allocation in the free space zone that i know of. NTFS stores small data inline in the MFT record called a resident file. When the file is bigger than 1KB it is called a non-resident file.

---

### Post by psusi on 2008-12-06
I'm not sure what that benchmark is doing exactly, but it is certainly more than just reading the files.  By packing the file data into the tree, it spreads out the stat data in the tree, which would make it slower to try to read all of that, for instance, by doing a du.

In the case of ext though, the inode space is there whether you use it or not, so it can only help to use it.

---

### Post by jdong on 2008-12-06
> **JNelson said:**
> Jdong,
Block suballocation is different than placing the file in the Inode. Block suballocation is using parts of unused blocks. Like a 4KB block has 1KB in yet it has 3KB space in the rest of the block. Reiserfs will use that 3KB space in the 4KB block. 

I was using the term block allocation to refer to the general practice of reduction of internal fragmentation by using slack space in whatever quantization unit of the storage medium a particular filesystem uses. Tail packing is simply a special case of the general concept of block suballocation in data structure design -- you are using the rest of the 800 bytes of the 1KB MFT entry.

---

### Post by inobe on 2008-12-06
> **psusi said:**
> So you repeated a test that I already told you was invalid and said it shows I am wrong?  Are you not reading what I am saying?  I'll try it one more time:

Mounting the drive and looking what files are on it does not cause all of them to be read, ergo it does not matter how fragmented they are or are not.


what test ?

i was accessing the files !

i can open all of them, i can amarok to rescan the disk, i can play these files or transfer them, after rearranging file with defrag.exe i can still move these files with the same bandwidth.

i guess it wasn't that fragmented to begin with.

i see you fella's are getting pretty technical here :lolflag:

---

### Post by jdong on 2008-12-06
> **inobe said:**
> what test ?

i was accessing the files !

i can open all of them, i can amarok to rescan the disk, i can play these files or transfer them, after rearranging file with defrag.exe i can still move these files with the same bandwidth.

i guess it wasn't that fragmented to begin with.

i see you fella's are getting pretty technical here :lolflag:

(1) Rescanning the disk with Amarok reads a 2KB MP3 or MPEG4 header that contains your IDv3 tags.

(2) You did not report whether or not there's a difference in transfer speed (**numbers, please**) before and after defragging.

(3) Playing a music file uses about 30KB/s bandwidth at most; even the most fragmented file will probably read at 500KB/s or so. Try with some DV editing or raw HD DV streaming that **must** read back at 30MB/s otherwise you will drop frames or skip, and you'll find a very different situation.

(4) Don't try to mock people who have experience writing filesystem defragmenters and are having an in-depth technical discussion about filesystem design and then refuse to listen to them trying to correct you on your misconceptions. It's a waste of time for everyone involved.

---

### Post by Kellemora on 2008-12-06
Well Gang

I know diddly squat about how a hard drive works or how it's files are stored.

But I do know this!

I work with large graphical files every single day, and the more we open and close those files the longer it takes for them to open on an NTFS drive.

We can gain greater speed opening these large image files by renaming them so they write to the disk new, so I image they are pulling all the pieces back together again and saving them all together as a contiguous file once again.

Since defrag takes so darn long and also sometimes corrupted some of our files.  We now just copy one drive to another drive and back again the next go around.  Works like a charm, is fast and keeps the drives running file loading times fast.

Since moving to Ubuntu and the EXT3 file system, we no longer have to do this!  It's like the files never become fragmented!  And there must be some hidden program within the file system that moves files around on the hard drive so that rarely used files are located where the longest seek times occur and the most used files are located where the fastest seek times occur.
It could be too that Ubuntu is just a whole lot faster than the Doze also.

If I open the same file on the Doze at the same time I open the same file on Ubuntu, I'm ready to go on Ubuntu and can actually have some work DONE before the DOZE machine is even ready to go.

Now, if I perform the exact same operation to these files, then save them and open them again the next day.  Ubuntu EXT3 opens sometimes in less time than the first time that file was opened.  But the Doze is lagging way behind it's original opening of that file.

So I think the way it was explained to me like a string of pearls vs pigeonholes is a very good analogy of WHY things are just faster in Linux or EXT3 file systems.

TTUL
Gary

---

### Post by tdrusk on 2008-12-06
I didn't feel like reading the whole thread, but I remember reading something a "convert to Linux" site that said something like, 
> Let's pretend you own a office with one person who just files your papers. Person A gets the job done as fast as possible, but wastes a lot of space with his mess. Every once in a while person A's boss has to shut the business down for a day so he can organize all the files. Person B keeps the papers organized from the start and never needs to worry about cleanup. Person A is Windows, Person B is Linux!

---

### Post by inobe on 2008-12-06
> **jdong said:**
> (1)
Don't try to mock people who have experience writing filesystem defragmenters and are having an in-depth technical discussion about filesystem design and then refuse to listen to them trying to correct you on your misconceptions. It's a waste of time for everyone involved.

my intentions were not to mock anyone, most importantly' i don't want to waste anyone's time.

i find this topic interesting and psusi came up with some questions i found confusing, i questioned it' nothing more.

as far as this discussion goes' i hope i'm still welcomed to join in, i also apologize for acting like a bone head :)

---

### Post by jdong on 2008-12-06
> **inobe said:**
> my intentions were not to mock anyone, most importantly' i don't want to waste anyone's time.

i find this topic interesting and psusi came up with some questions i found confusing, i questioned it' nothing more.

as far as this discussion goes' i hope i'm still welcomed to join in, i also apologize for acting like a bone head :)

You're absolutely welcome to join in. 

As psusi explained several times, there's a difference between files "appearing instantly" and exactly how fast you can read them back. As I pointed out earlier, music playback is an extremely lightweight task. On the other hand, a task like DV processing can require 1000x or 5000x faster access to files than music playback -- would a fragmented filesystem be able to keep up with **that**? Probably not! My cheap hard drive barely can satisfy that need in theory -- the last thing I need is scattered file fragments slowing things down more.

It's the same thing as me entering my bicycle into a NASCAR race because "I get on my bike and instantly get to classes; I've never felt it to be slow" :)

Depending on what you do, fragmentation may or may not be a problem for you. Different allocation policies make different tradeoffs between quickly being able to find a spot to write a file, near-full-condition performance, and lower fragmentation in the long run.

---

### Post by inobe on 2008-12-07
that cleared things up on that, please answer this..

wouldn't a backup drive separate from a system drive reduce fragmentation, partitioning the drives as well ?

back in my windows day's i use to assist at a wind-os forum, it kinda drove me nuts when everyone formatted and never setup partitions, i tried to explain why it took so long running defrag.exe on a 120 gigabyte disk 80% full with no partitions !

i also tried my best to explain that its not good practice keeping thousands of files on a system partition, avi's pics, docs, etc..


am i correct ?

please include what an MFT is

---

### Post by jdong on 2008-12-07
> **inobe said:**
> that cleared things up on that, please answer this..

wouldn't a backup drive separate from a system drive reduce fragmentation, partitioning the drives as well ?

back in my windows day's i use to assist at a wind-os forum, it kinda drove me nuts when everyone formatted and never setup partitions, i tried to explain why it took so long running defrag.exe on a 120 gigabyte disk 80% full with no partitions !


Well, separating data from the OS (in Linux, putting /var and /home apart from /usr) does help **isolate** fragmentation to mostly your data. This can prevent clutter in your own data from slowing down the rest of the OS, but it doesn't really help de-clutter the data. If you need access to your data fast too, this doesn't help.

>  please include what an MFT is

This is the Master File Table. It is a reserved area on an NTFS disk that stores the critical filesystem structures that say where everything else is on the disk.

---

### Post by psusi on 2008-12-07
More specifically the MFT is an array of fixed length records ( usually 1 KB ) that describe every file in the volume.  The entry contains things like the file name or names ( multiple names can refer to the same file, which are called hard links ), the owner and other access permissions, creation and access timestamps, size, and if the file data is small, the data may be there as well, or if it is large, the MFT entry just contains a list of data blocks that contain the file's data.

In your example of a single partition that is 80% full, if that disk were divided into two equal partitions with the files evenly distributed between them, then you would have two volumes that were 90% full so they would be more likely to be fragmented, and more difficult to defragment since there is less free space to work with.  The advantage to having separate partitions is that you can have one for the system files which change infrequently and so aren't likely to become fragmented so programs load fast, and your bulk data that changes frequently can sit on the other partition where fragmentation will only affect those files.

---

### Post by inobe on 2008-12-07
i noticed SSD drives are a starting trend, what would be the difference in fragmentation considering their are no platters among moving parts ?

it's a question that goes off topic, i just feel its the right time to ask :)

edit: on topic, with win-os chkdsk, i noticed it claims to fix bad sectors, it says that on the UI ?

---

### Post by psusi on 2008-12-07
> **inobe said:**
> i noticed SSD drives are a starting trend, what would be the difference in fragmentation considering their are no platters among moving parts ?

Out of order access on solid state drives makes little to no difference since there is no head that has to seek to a different part of the physical media.

> **inobe said:**
> 
it's a question that goes off topic, i just feel its the right time to ask :)

edit: on topic, with win-os chkdsk, i noticed it claims to fix bad sectors, it says that on the UI ?

That looks like a statement rather than a question.

---

### Post by inobe on 2008-12-07
oh' its a question, i am asking if that is true :)

---

### Post by psusi on 2008-12-07
chkdsk will find sectors that can not be read ( when given the /r switch ) and mark them as bad( by adding the block to the $Badclus file ) so they will not be used.

---

### Post by inobe on 2008-12-07
last question and i will leave you alone.


how does linux handle bad sectors, i am asking because i ran into some fsck errors in the past when opensuse was operating my pc.


thank you

---

### Post by psusi on 2008-12-07
If you have bad sectors I suggest using the smartmontools package to control the drive's SMART features.  You can tell the disk itself to scan for bad sectors, and when found, you can use dd to write zeros to that sector which will force the disk to attempt to rewrite that sector, which may work if it just got scrambled and the media isn't physically damaged.  If the media is physically damaged, then the disk will automatically remap the address to a good sector in its spare pool to correct the problem.

Otherwise you can use e2fsck -c to check for bad blocks and flag them to not be used, similar to chkdsk.

---

### Post by eternalnewbee on 2008-12-07
Hi there. It so happens that I have a hard disk with errors, so I installed smartmontools to give it a try, but I can't find it. What should I do?

---

### Post by jdong on 2008-12-07
To clarify on bad sectors:

On Windows (2000 and greater), NTFS hot-fixes bad clusters on seeing them. There should be no need to run chkdsk explicitly to find bad clusters.


On Linux, it is considered an IO error and the disk will be remounted read-only. You can then use e2fsck -c to flag bad sectors.

I've rarely found smartmontools to predict or react to the presence of bad clusters, and I've had at least 10 hard drives go out on me. Only one of them SMART successfully predicted 15 minutes before it'd die, that it'd die.

When you see  bad sectors, it's a very bad sign. Usually hard drives reserve 5% of more of blocks internally for bad-sector remapping. It's only when they've used up all their remapping that they report to the OS that there's bad sectors. A drive with bad sectors showing up is very likely to develop more and more.

---

### Post by inobe on 2008-12-07
my experience, the disks were useless after several days !

had warnings about bad blocks, running e2fsck seemed to have fixed the errors long enough to where i can grab my data.

eventually the disks started clicking rapidly.

i still have both, i plan on taking them apart to study them, they are trashed considering my data has been extracted, i am curious what i will find:)

---

### Post by psusi on 2008-12-07
> **eternalnewbee said:**
> Hi there. It so happens that I have a hard disk with errors, so I installed smartmontools to give it a try, but I can't find it. What should I do?

man smartctl

Also if you aren't sure what program a package installed, run dpkg -L foo and it will show you every file package foo installed.  Look for ones in /bin and see if they have a man page or run them with --help.

> **jdong said:**
> When you see  bad sectors, it's a very bad sign. Usually hard drives reserve 5% of more of blocks internally for bad-sector remapping. It's only when they've used up all their remapping that they report to the OS that there's bad sectors. A drive with bad sectors showing up is very likely to develop more and more.

The drive can only remap the sector when you try to write to it.  Reads will continue to fail until you try to write new data.  Unfortunately I don't think fsck or chkdsk bother trying to rewrite the sector; they just mark it as bad and won't try to use it again.  That's why I like to use smartmontools and then dd.  I've seen a bad sector crop up on a disk a few times now that apparently was just a random corruption which was fixed when writing the sector again, without the drive even remapping it ( or at least not reporting it had done so ).  I guess sometimes a bit gets flipped or maybe the system powers off before the entire sector was written or something, and it leaves the sector bad in that the CRC says it's got wrong data, but physically the media is fine.

---

### Post by inobe on 2008-12-07
i used Gsmartcontrol, i haven't been able to find out its worthiness.

[http://gsmartcontrol.berlios.de/home/index.php/en/Downloads](http://gsmartcontrol.berlios.de/home/index.php/en/Downloads)

here is a test log using one of my wd raptors

```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Raptor family
Device Model:     WDC WD740GD-00FLC0
Serial Number:    WD-WMAKE2398597
Firmware Version: 33.08F33
User Capacity:    74,355,769,344 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Nov  6 19:45:09 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)    Offline data collection activity
                    was aborted by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever
                    been run.
Total time to complete Offline
data collection:          (1719) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  30) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x001f)    SCT Status supported.
                    SCT Feature Control supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time             0x0007   113   110   021    Pre-fail  Always       -       4891
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       769
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       6623
10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       769
194 Temperature_Celsius     0x0022   113   097   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0009   200   179   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        70         -

SMART Selective self-test log data structure revision number 1
SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by Stephen90 on 2010-05-20
I know this is an older thread bit I just thought I would put my 2 cents in.  As a computer user that primarily uses linux but still relies on Windows for certain tasks (gaming and NTFS management mostly) here is my experience.  I have multiple drives (excess of 2.5 TB) that I use to keep movies, music, documents, and OS's.  Most of my allocated space is in NTFS due to the interoperability between Windows and Linux and the capability of 4GB+ filesizes.  After mainly using Ubuntu Linux for about 4-5 months, and running chkdsk (in Windows Vista) to keep the file system error free, I ran the defrag analysis (in Windows Vista) on 2 NTFS file systems one 450GB and one 1TB.  One partition was 54% fragmented and one partition was 65% fragmented.  

These percentages seem quite elevated to me, and defrag is currently running on them.  One major difference between Windows NTFS handling and Linux NTFS handling, is that linux gives the user more options dealing with mounting/unmounting, and if not properly unmounted before shutdown power loss etc... data loss can occur and errors dealing with the file system index occur.  Linux does not always immediately write data to the drive, but rather allocate space when the copy command is given, and physically transfer the data when the OS deems it "optimal." 

The 1TB drive (65% fragmentation) was so excessively fragmented that the past 2 times I had mounted it in Linux that it would NOT unmount, forcing me to use REISUB (similar to CTRL+ALT+DEL for linux) to safely restart linux

BOTTOM LINE: If using NTFS in linux, be sure to unmount the NTFS partition properly every time it is used!  Periodically boot in Windows to run chkdsk and defrag to keep the file system usable and avoid data loss.

---

### Post by K.Mandla on 2010-05-20
Let's put this one to rest, shall we?

---

