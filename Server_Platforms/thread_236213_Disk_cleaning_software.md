---
title: "Disk cleaning software"
date: 2006-08-14
forum: Server Platforms
---

### Post by Steve S. on 2006-08-14
Sorry if this is posted somewhere...just couldn't find it (may have been user error/search parameters).  And sorry if this is in the wrong category, but it seemed qualified.

I know that in Windows you can thoroughly clean a disk's "unused" space with various software that would make a few passes on it, thus blanking it.

Anything like that in Ubuntu?  In Synaptic?

---

### Post by jamesford on 2006-08-14
not totally sure but i think if u delete something in ubuntu (if ur using the ext3 filesystem) it does get blanked, not just tagged as deleted and as such all your unused space should already be blanked

not 100% sure on this

---

### Post by ciscosurfer on 2006-08-14
Is [this something]("http://enterprise.linux.com/article.pl?sid=06/02/16/2149248&tid=47&tid=89") you're looking for?

If not, [here is good place to start]("http://www.google.com/search?hl=en&lr=&q=securely+delete+linux+files&btnG=Search").  It's also a good idea to look in the [security section]("http://www.ubuntuforums.org/forumdisplay.php?f=7") of Ubuntu Forums too.

---

### Post by ciscosurfer on 2006-08-14
> **jamesford said:**
> not totally sure but i think if u delete something in ubuntu (if ur using the ext3 filesystem) it does get blanked, not just tagged as deleted and as such all your unused space should already be blanked

not 100% sure on this

Unfortunately, this is untrue :(  Bits are bits and they simply get scattered.

---

### Post by jamesford on 2006-08-14
allright , but it looks like it does something:
Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.

---

### Post by Steve S. on 2006-08-14
> **ciscosurfer said:**
> Is [this something]("http://enterprise.linux.com/article.pl?sid=06/02/16/2149248&tid=47&tid=89") you're looking for?

If not, [here is good place to start]("http://www.google.com/search?hl=en&lr=&q=securely+delete+linux+files&btnG=Search").  It's also a good idea to look in the [security section]("http://www.ubuntuforums.org/forumdisplay.php?f=7") of Ubuntu Forums too.

Yes, ciscosurfer, shred is just what I'm looking for.  Anything like that in synaptic?  I only know how to sudo aptitude and synaptic install...not very good with source.  Suggestions?

---

### Post by Steve S. on 2006-08-14
Oh, is shred a command?  Need to install it?

I see that you can only use it via Knoppix if you want to use it on the free space on the partition that has your OS.  Again, do I need to install shred, use just command line it?

Sorry, not on my linux box right now and want to get all this sorted before I get back to it.

---

### Post by ciscosurfer on 2006-08-14
@Steve S.
The program shred is actually part of the coreutils package that have on your system right now...however, b/c you can't be mounted to the filesystem you wish to change, you must use a liveCD to work on it (any liveCD that contains shred -- you can see if it's included by typing in a terminal```
which shred
```If /usr/bin/shred appears, it's available to use).  It's also ***very important*** to keep in mind the notes below when working on your system, i.e., you data mode must be data=ordered or data=writeback (you can find out more about this using the command **man mount**.  It's a ***very good idea*** to read up on these facts before attempting to completely wipe anything.

@jamesford
You are correct about ext3 (and other log-structured or journaled systems)...I read your post too fast and didn't see that you mentioned ext3 #-o.  You can, however, change your system to allow data=writeback or data=ordered and shred will work as described. So yes, you are right in saying that ext3 does zero-out its inodes and that it (and other journaled systems, etc.) then subsequently breaks the following assumption >> (from man shred)

> CAUTION: Note that shred relies on a very important assumption: that the file system overwrites data in place. This is the traditional way to do things, but many modern file system designs do not satisfy this assumption. The following are examples of file systems on which shred is not effective, or is not guaranteed to be effective in all file system modes:

* log-structured or journaled file systems, such as those supplied with
AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

* file systems that write redundant data and carry on even if some writes
fail, such as RAID-based file systems

* file systems that make snapshots, such as Network Appliance's NFS server

* file systems that cache in temporary locations, such as NFS
version 3 clients

* compressed file systems

In the case of ext3 file systems, the above disclaimer applies (and shred is thus of limited effectiveness) only in data=journal mode, which journals file data in addition to just metadata. In both the
data=ordered (default) and data=writeback modes, shred works as usual. Ext3 journaling modes can be changed by adding the data=something option to the mount options for a particular file system in the /etc/fstab file,
as documented in the mount man page (man mount).

In addition, file system backups and remote mirrors may contain copies of the file that cannot be removed, and that will allow a shredded file to be recovered later.

---

### Post by Steve S. on 2006-08-14
Well, highs and lows: I checked Gnoppix (does anyone know how to set ra0 as the active Network connection in Knoppix?) and it has shred ready to go.

I thank you for the lead, ciscosurfer.  But, the more I look at the above information, I realize that this may not be what I'm after.  It says it may not be effective with ext.3 filesystems?

Is there software that can shred/erase the unused portion of a drive?  Command line with something like this that appears to be somewhat iffy is a little nerve racking ```
Destroy entire system? y/n:
```:confused:

What about kdirstat (something I saw in Synaptic)?  Is that what I'm looking for?

---

### Post by ciscosurfer on 2006-08-14
You can issue this in a terminal to learn more about it```
apt-cache show kdirstat
```But no, I don't think this is what you want at all.

In terms of it not being effective on ext3 filesystems, I would like you to re-read completely my previous post and pay special attention to the quoted part.

---

### Post by Steve S. on 2006-08-14
> **ciscosurfer said:**
> You can issue this in a terminal to learn more about it```
apt-cache show kdirstat
```But no, I don't think this is what you want at all.

In terms of it not being effective on ext3 filesystems, I would like you to re-read completely my previous post and pay special attention to the quoted part.

Ahhh...thank you, ciscosurfer, for your patience.  I read it further, including the man page, and I have a few notes.

One, the main drive that I run my primary operating system from, is ext3.  As mentioned, it appears to be difficult to regain deleted data from this type of system.  This may be problem solved on this drive(as that is all I am really looking for)?

I have a backup drive that is running ext2, however.  Shred appears that it would work fine for a specific file that I would like securely deleted.  However, what I am looking for is more along the lines of [this]("http://www.snapfiles.com/get/evdestroy.html"), specifically something like the second line: > The program can also wipe your empty disk space, which allows you to remove traces of any previously deleted files as well.

Is there anything like THAT in Ubuntu?  And/or am I misreading the concept of shred?

---

### Post by ciscosurfer on 2006-08-15
I am not honestly aware of any program for Ubuntu Linux (or any Linux distro) that works like the one you mentioned from SnapFiles.  I'm sure they are out there, but I don't know of them.  And one thing to keep in mind is how different each program you may install is and this by itself could be one reason why there are many catch-all programs that do this dirty work for you.  

They are many security programs that afford varying levels of security protection and you can find a number of them by searching for them on the Web. 

I can usually find all files relating to specific programs I install and so if, for some reason, apt or dpkg can't remove them fully (all dependencies, extra files, etc.), I can always manually remove them myself.  As for "tracks" like the ones left behind on a Windows box: some programs maintain log files, meta files, and others, that describe changes in events within the program, added files, and things of that nature.  In terms of cookie removal, history removal, etc., I simply know where they are stored and so I remove them myself or let my browser take care of the dirty work for me.  

One of the nice things, in my opinion, about Linux over Windows, is its lack of "bloat."  Yes, Linux does have its fair share of files, but not nearly as many that can be strewn around a Windows box after an install or removal.  

And in terms of security, and because my filesystem is ext3 in normal journaled mode, in this case, I don't have any use for programs like shred because a form of "shredding" has already taken place due to how the filesystem functions: (technically) by zeroing-out the inode files to allow for proper journaling.  But again, this too can be modified if I so desire by changing my data mode to writeback (data=writeback), for example, and then I can use shred without hassle and possibly (I don't know) get better outcomes (I've simply never seen a need for it).  

But by all means, keep searching around the forums here and on the Net to see if there is something that better suits your fancy.

---

### Post by Steve S. on 2006-08-16
Thanks, ciscosurfer.  I'll check around.

If anyone discovers something like this for Ubuntu, please post.

I am pleased that ext3 seems to take care of itself for the most part, but would like something for ext2.

---

### Post by regneva on 2006-08-20
Try doing this while inside the partition whose free space you want to wipe:

# dd if=/dev/zero of=./bigfile
# sync
# shred -u -v -n 5 ./bigfile
# sync

Check out [http://www.linuxsecurity.com/content/view/117638/49/](http://www.linuxsecurity.com/content/view/117638/49/) for more information.

---

### Post by Steve S. on 2006-08-21
> **regneva said:**
> Try doing this while inside the partition whose free space you want to wipe:

# dd if=/dev/zero of=./bigfile
# sync
# shred -u -v -n 5 ./bigfile
# sync

Check out [http://www.linuxsecurity.com/content/view/117638/49/](http://www.linuxsecurity.com/content/view/117638/49/) for more information.

Rockin'!  Thanks, regneva, I'll check it out!

---

