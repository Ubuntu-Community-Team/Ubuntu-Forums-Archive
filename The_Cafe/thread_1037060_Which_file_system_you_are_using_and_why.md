---
title: "Which file system you are using and why?"
date: 2009-01-11
forum: The Cafe
---

### Post by legolas_w on 2009-01-11
I am wondering between all of these file systems which ones you are using in your desktop computer and which one for your servers. which one has better list of features when we compare it with NTFS or WinFS?

Thank you for sharing your thought.

---

### Post by Polygon on 2009-01-11
i use ext3 cause it the default and it works

---

### Post by gnomeuser on 2009-01-11
ext4, it's stable and reasonable speedy. Waiting for online defragmentation support though. Eventually it will be replaced with btrfs but I want the data format to stabilize first.

---

### Post by cardinals_fan on 2009-01-11
EXT3 on my Fedora partition, ReiserFS on my Slackware partition and /home.

EXT3 because that's all the Fedora live CD offered, ReiserFS because it performs almost as well as JFS but is safer in an area with lots of power outages.

---

### Post by legolas_w on 2009-01-11
I heard that EXT3 is not recoverable like NTFS, is it the same for other file systems and the newly developed EXT4?

Thanks

---

### Post by binbash on 2009-01-11
ext3 because it is stable, however i am planning to move ext4 soon

---

### Post by Polygon on 2009-01-11
> **legolas_w said:**
> I heard that EXT3 is not recoverable like NTFS, is it the same for other file systems and the newly developed EXT4?

Thanks

define recoverable? it has a journal so if you have a power outage the filesystem wont be corrupted or anything......

---

### Post by urukrama on 2009-01-11
ext3, because it does what I need and because I haven't yet found the interest to explore the benefits of the other file sytems.

---

### Post by insane_alien on 2009-01-11
ext3, will switch to ext4 when ubuntu supports it in a stable version and can boot from it. basically i'll stick with defaults.

reasons for sticking with defaults
1/ don't need to think about it, 
2/ i don't really care if it makes my system a few microseconds quicker at reading a file.
3/ its what i already have, changing it would take too much time.

---

### Post by richg on 2009-01-11
I install Ubuntu on a drive right out of the box. I use whatever Ubuntu installs. Done this for five years with NO issues.

Rich

---

### Post by Barrucadu on 2009-01-11
JFS, because it fscks incredibly quickly. I used ReiserFS for a while because it is fast when working with lots of small files, but it takes an age to fsck (also, calling it "MurderFS" is just immature, using a filesystem written by a murderer doesn't make *you* a murderer).

---

### Post by y6FgBn)~v on 2009-01-11
> **polygon said:**
> i use ext3 cause it the default and it works

+1

---

### Post by |eafhound on 2009-01-11
Reiser, because i like to go fast

---

### Post by keith.newell on 2009-01-11
Ext3 for now, ext4 when ubuntu officially supports it.

---

### Post by markp1989 on 2009-01-11
im just using ext3, on most machines


i use ext2 on my eee because i heard that it doesnt write to the SSD as much because of the lack of journal

---

### Post by $USER on 2009-01-11
ext3

the performance differences arent enough for me to care, especially when I got 700MB iso's sitting right next to tiny config files on the same partition.

---

### Post by Slug71 on 2009-01-11
Ext4, because its in Jaunty which im using and it should be tested. Boots fine and rock solid so far.
Also boots quicker than Ext3.

---

### Post by jimi_hendrix on 2009-01-11
ext3 because its the only one i know...ext4 on my jaunty install

---

### Post by legolas_w on 2009-01-11
Wow, guys can someone let me know why they call it murderFS?
I saw in the wikipedia that it says: Reiser4 and ReiserFS "Murders your wife" :lolflag:

What is the story behind it?

See for yourself: [http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=209063556#Features](http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=209063556#Features)

---

### Post by PurposeOfReason on 2009-01-11
> **legolas_w said:**
> Wow, guys can someone let me know why they call it murderFS?
I saw in the wikipedia that it says: Reiser4 and ReiserFS "Murders your wife" :lolflag:

What is the story behind it?

See for yourself: [http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=209063556#Features](http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=209063556#Features)
Read 8 posts up.

I use ext3 though in my server I'm working on I'll be doing something else I'm thinking.

---

### Post by -grubby on 2009-01-11
Ext3 because it's stable, and I don't care enough about speed to have an unstable file system

---

### Post by kavon89 on 2009-01-11
> **Polygon said:**
> define recoverable? it has a journal so if you have a power outage the filesystem wont be corrupted or anything......

Not always true, depends on how it journals:

> JFS is a Journaling Filesystem. Rather than adding Journaling as an add-on like ext3, Journaling was implemented from the start. The journal is fixed at 32MB. JFS journals metadata only, which means metadata will remain consistent but **user files may be corrupted after a crash or power loss**. JFS' Journaling is similar to XFS where it only journals parts of the Inode.

ext3 for me, and I'll be quick to adopt ext4. I was going to try ReiserFS only because it got publicity when the developer was locked up.

---

### Post by RATM_Owns on 2009-01-11
ext4 for /home
reiserfs for /

---

### Post by legolas_w on 2009-01-11
Unbelievable, I read the Hans Reiser story and I should say that it was the most shocking things that I have read in 2009.
How can possible a successful guy like him kill someone else :O Unbelievable and sad.

---

### Post by samjh on 2009-01-11
I made a similar thread a while back: [http://ubuntuforums.org/showthread.php?t=854129](http://ubuntuforums.org/showthread.php?t=854129)

For me, the choice is JFS and Ext3.  JFS because it is fast and very crash-resistant.  Ext3 because of its popular support as the default file system of most Linux distributions.

---

### Post by SunnyRabbiera on 2009-01-11
I use ext3 as it seems stable

---

### Post by phrostbyte on 2009-01-11
ext3 because it's the default :p

---

### Post by ghindo on 2009-01-11
I use ext3 because it's the default Ubuntu filesystem and I haven't found any compelling reasons to switch to any other filesystem.

---

### Post by jrusso2 on 2009-01-11
I use JFS, ext2,3 have both managed to destroy my installs a number of times when the system lost power and even Linux has been looking for a replacement.

Reiser I used to use but with Hans in prison, he was its genius.

XFS has some major issues but I still use it for some things just not root.

---

### Post by jimi_hendrix on 2009-01-11
whats the advantage to using XFS JFS or ResierFS over ext3?

---

### Post by cardinals_fan on 2009-01-11
> **jimi_hendrix said:**
> whats the advantage to using XFS JFS or ResierFS over ext3?
JFS and ReiserFS usually perform better.

---

### Post by SomeGuyDude on 2009-01-11
XFS here, it's pretty snappy and responsive. I'd like to try another on my next install.

---

### Post by Frak on 2009-01-11
I use XFS.

---

### Post by mips on 2009-01-12
> **SomeGuyDude said:**
> XFS here, it's pretty snappy and responsive. I'd like to try another on my next install.

XFS feels slow on my laptop as it experienes a lot of disk i/o. I need to start implementing some tweaks to see if I can impreove performance.

---

### Post by Liviu-Theodor on 2009-01-12
For now, ext3 for Ubuntu, ext2 for Fedora servers, and NTFS for Windows. The Fedora serveres are preinstalled, it was not me who installed them, and ext3 or NTFS were the best available when I installed the OS on the computers.

---

### Post by uberdonkey5 on 2009-01-12
I use ext3, but really I'd prefer to use something faster like Resier when I reinstall. However I am PETRIFIED of reinstalling (I have dual boot still).Everything is just peachy on my computer now and if I reinstall I hate to go through all the codecs, prefered packages, firefox plugins etc, such a waste of time.

My dream is to get rid of my dual boot, and use Pinnacle Studio through virtual box on ubuntu, but running faster than I can in windows.

(how do different file systems affect virtualisation???)

---

### Post by Archmage on 2009-01-12
> **legolas_w said:**
> which one has better list of features when we compare it with NTFS or WinFS?

Kindly note that Microsoft decided to drop WinFS. Therefore they have no features at all. Therefore all other filesystem are better than WinFS. Even in Windows they are using NTFS instead of a non-existing filesystem.

---

### Post by mips on 2009-01-12
> **uberdonkey5 said:**
> 
(how do different file systems affect virtualisation???)

I had a WinXP install in Virtualbox a while back and the performance of WinXP for me 'felt' faster than a normal clean hd install. Only way to find out for yourself is to test it.

---

### Post by jrusso2 on 2009-01-12
Ext 2 was the worst.  If you ever lost power you lost data that was it.  If you were lucky you didn't lose the whole file system.  I was so glad when we started having alternatives.

---

### Post by SomeGuyDude on 2009-01-12
> **mips said:**
> XFS feels slow on my laptop as it experienes a lot of disk i/o. I need to start implementing some tweaks to see if I can impreove performance.

Hm. I hadn't noticed any of that. But, like I said, I'm really jazzed on testing out Reiser next.

---

### Post by Trail on 2009-01-14
EXT3 on / and ~ (lots of small files where XFS is slow), XFS on /media/* (lots of big files, better performance).

---

### Post by Archmage on 2009-01-14
> **uberdonkey5 said:**
> I use ext3, but really I'd prefer to use something faster like Resier when I reinstall. However I am PETRIFIED of reinstalling (I have dual boot still).Everything is just peachy on my computer now and if I reinstall I hate to go through all the codecs, prefered packages, firefox plugins etc, such a waste of time.

The next Ubuntu release should support ext4. Maybe you can than convert all your ext3 to ext4 if you dare.

---

### Post by adamlau on 2009-01-14
XFS. Because I have a large media collection and because the filesystem is tuneable, easy to manage (through xfprogs) and offers online defragmentation.

---

### Post by RudolfMDLT on 2009-01-30
> **insane_alien said:**
> ext3, will switch to ext4 when ubuntu supports it in a stable version and can boot from it. Basically i'll stick with defaults.

Reasons for sticking with defaults
1/ don't need to think about it, 
2/ i don't really care if it makes my system a few microseconds quicker at reading a file.
3/ its what i already have, changing it would take too much time.

+1 :)

---

