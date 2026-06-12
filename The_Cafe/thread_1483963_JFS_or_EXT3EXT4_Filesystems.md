---
title: "JFS or EXT3/EXT4 Filesystems ?"
date: 2010-05-15
forum: The Cafe
---

### Post by frenchn00b on 2010-05-15
Hello,

Do you prefer and use rather JFS or ( EXT3 or EXT4 )? 

If you vote, please say why such choice.

Cheers Tux Community :KS:KS

---

### Post by jetsam on 2010-05-15
I said ext3.  It's been the standard for a long time; it's journaling; it's fast enough; I'm not beta testing anything right now; why change?

---

### Post by frenchn00b on 2010-05-15
I experienced that one take 2 PC:

One running Windows XP running NTFS filesystem
a second one running LINUX with a EXT3 filesystem
Two PC are running fsck and chkdsk at boot to correct / fix it.

Make this test.

Start the PC, work on it few hours, remove the cable (hard power-cut, hard for harddisks and hardware), and repeat the operation (unplug the cable for power-cut / and work on the disk).
One day of another, the harddisk filesystem will die. 

Result:
NTFS holds the severe test pretty well and life of the disk can remain pretty long of 100-200 times.
The EXT3 filesystem, the harddisk filesystem, will be corrupted after 20 times, although the fsck.

So conclusion:
- EXT3 is not reliable
- NTFS is better for the data reliability
- What does really FSCK ? 

Other point in favor of NTFS:
- have you ever tried photorec? If you can really get you data back, one has completely lost all filenames and folder. It is a big mess of no use at the end.
- Windows ofter great tools to recover a disk, and you very often recover the harddisk in its full integrality or 1-5% are lost. 

So why LINUX EXT3, when there is better?

---

### Post by K.Mandla on 2010-05-15
ext2.

---

### Post by jetsam on 2010-05-15
> **frenchn00b said:**
> 
So why LINUX EXT3, when there is better?

Well, in my actual day to day experience of computers which goes back decades, I've never seen an ext3 filsystem lose data except through accidental or enthusiastic deletion; ie user error.  NTFS I've peronally had one hard drive die, gone for good, nothing to be saved, and I've fixed a few other near drive-death experiences on friend's systems with linux.  

So why NTFS when there is so much better available for free?  

Moreover, the data analysis tools available on linux put what you get in the MS ecosystem to crying shame.  First thing I do if I have a troubled system to deal with is throw in a linux boot disk to analyze the situation in a guaranteed virus free environment with a system that can read _everything_.  

So yes, if I light my computer on fire five times, perhaps NTFS will survive 1% of the time, while ext3 will do the only sensible thing to do and just self-destruct like I must want it to.  

I pretty much disagree that what you've presented in your post is an advantage in any way.

---

### Post by frenchn00b on 2010-05-15
Benchmarking, rather OLD, showing that EXT to JFS are today of same level. [http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)  , in this one, JFS was superior for the data reliability. JFS has some good recovery tools, e.g. [http://jfsrec.sourceforge.net/](http://jfsrec.sourceforge.net/)

---

### Post by gradinaruvasile on 2010-05-15
In my experience NTFS dies way faster than EXT3 - maybe its only the Windows implementation/driver/whatever but i repaired quite a few Windows machines that entered a restart loop because of file system corruption.
NEVER EVER had this type of problem with EXT3.
I dont even mention the fact that its proprietary and the Linux implementation is lacking features being essentially a hack/reverse engineering. Also i had many problems with it in Linux especially when writing multiple small files on them, it used 100% CPU and didnt finish the copy. And its not only me, others experienced the same issue.

JFS - it is fast, uses low CPU but it corrupts at the very sign of forced reboot/power failure (i mean every time i had to force fsck it). I used it in the past but it wasnt reliable. We used it on a production server with CentOS, the same story - forced fsck was required to be able t mount it.
And once i lost an entire pertition with it - no amount of fscking or other workarounds made it mountable again.

Ext4 - its fast and doesnt corrupts like JFS, but i had problems with it when using it as boot partition - sometimes Gnome settings were just lost, some configuration files vanished etc. after reboot. But as a large storage only partition its very good given its speed.

Ext3 - its the most stable of them all in my experience - not as optimised as Ext4, but you can rest assured your data is safe on it (at least i am).

---

### Post by VCoolio on 2010-05-15
I bought a verbatim external hd last week, decided to try jfs on it (since it is said to be fast with bigger files). It formatted way faster than a much smaller ext4 partition on the same disk with gparted. My jfs partition has a good performance, but I haven't compared with others, so I can't say if it's better. I'm happy with it, but I have too few data to vote.

---

### Post by frenchn00b on 2010-05-15
I checked about the reference for linux: LINUX.COM
they report a very positive study of JFS:
[http://www.linux.com/archive/feed/119025](http://www.linux.com/archive/feed/119025)

Here it is the JFS webpage:
[http://jfs.sourceforge.net/](http://jfs.sourceforge.net/)
Do we have the last version in our kernels?

---

### Post by gradinaruvasile on 2010-05-15
I know about the positive theory, but in practice it just dont flies like that.
I had problems with JFS in ubuntu 7.10-9.10 (i now use Debian and no JFS) and the same on CentOS 5.4 on servers. Its just not reliable in these conditions.

---

### Post by frenchn00b on 2010-05-15
> **gradinaruvasile said:**
> I know about the positive theory, but in practice it just dont flies like that.
I had problems with JFS in ubuntu 7.10-9.10 (i now use Debian and no JFS) and the same on CentOS 5.4 on servers. Its just not reliable in these conditions.

thank you for your information, fruitfull

so if you type : 
```
fsck.jfs -a -f /dev/sdb   
```
(which is the jfs disk)  
you can kill it or damage it (so to be avoided )
Which command shall not be tested on JFS please?

---

### Post by gradinaruvasile on 2010-05-15
> **frenchn00b said:**
> thank you for your information, fruitfull

so if you type : 
```
fsck.jfs -a -f /dev/sdb   
```
(which is the jfs disk)  
you can kill it or damage it (so to be avoided )
Which command shall not be tested on JFS please?

I dont know what did you understand from what i said.
In my 2 posts i said that JFS tends to be corrupted on forced reboot/power loss (once or twice i even had issue like this even on normal reboot).

The fsck command you posted is the command that has to be used to force-check and repair it in these cases. I never said that the command damages the file system - i said that i had to force check them in the cases it was corrupted.

My point is that i dont like to have a file system that corrupts in certain scenarios.

Not to speak of inexperienced users having the textmode message of doom that informs them that X cannot start because some random named file cannot be created in /tmp/ folder because their file system is read only.

---

### Post by screaminj3sus on 2010-05-15
ext4, just as stable as ext3 in my experience and faster, seems like a no-brainer to me.

---

### Post by jrusso2 on 2010-05-15
The only file systems I ever had go bad on power loss was ext 2 or ext 3 never jfs or xfs so I use those.

---

### Post by kat_ams on 2010-05-15
JFS is far superior to EXT4

I have both EXT4 and JFS systems in my company, the JFS systems are extremely stable.

My EXT4 system has random data loss, screen hangs, long data loading times (running on a SSD!), long copy and save actions and other random errors.

My JFS systems have always been rock solid, high performance and quick startup.

Plus Linus Torvaldus sums it up:
[http://www.linux-magazine.com/Online/News/Linus-Torvalds-Upset-over-Ext3-and-Ext4]("http://www.linux-magazine.com/Online/News/Linus-Torvalds-Upset-over-Ext3-and-Ext4")

Kernel chief Torvalds is hardly convinced by these arguments. In his view, "if you write your metadata earlier (say, every 5 sec) and the real data later (say, every 30 sec), you're actually more likely to see corrupt files than if you try to write them together... This is why I absolutely detest the idiotic ext3 writeback behavior. It literally does everything the wrong way around -- writing data later than the metadata that points to it. Whoever came up with that solution was a moron. No ifs, buts, or maybes about it."

So if Linus himself says how bad EXT3 and 4 are....

---

### Post by handy on 2010-05-15
I've used both ext3 & JFS on the same 200GB partition, which had about 30GB of small to medium size files & the rest (it was near full) was full of movies. I couldn't really notice any difference in the speed of use, they were both fast enough for me.

The only reason I changed from JFS back to ext3 was that I could access the ext3 partition from OS X, & not JFS.

They were both reliable.

As far as NTFS being more reliable than ext3 or JFS, from personal experience I find that hard to believe. The NTFS is certainly better than the FATs though (again from experience).

---

### Post by dtfinch on 2010-05-15
When setting up a new server, I used to randomly choose either JFS or EXT3. My only EXT4 use so far has been on my desktop and netbook, though it was the default.

Directory traversal (like running "find" in /) seems slower on JFS than EXT*. I haven't heard anything else bad about it. Both JFS and EXT3 seem to be able to survive a crash pretty well.

I try avoid is XFS, though my reasons have diminished since 2007 or so when they (claim to have) fixed that one huge guaranteed data loss on every crash issue that they spent all those years denying was a bug. It's still the largest, most complicated filesystem in the linux kernel.
[http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F](http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F)

EXT4 had the same data loss "not a bug" that XFS had. I don't know whether it's been completely fixed yet. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all)

---

### Post by yester64 on 2010-05-15
Can that be the reason that some documents are corrupted on my harddrive.
Sometimes images are not viewable, the same to movies.
I am kinda shocked.
So what is better to use? I never paid so much attention to the filesystem really as i thought its tested.
I am starting to worry now.:(

---

### Post by McRat on 2010-05-15
Wow.

That's not good.  I think I've already seen this with EXT4.

I turned off a U32 machine with Google Chrome on it.  I might have turned it off with the power switch.  But I don't think so. When I turned it back on, Chrome gave an error message, and it lost all the history.  This had happened with Firefox as well, so it's not a Chrome thing.

So it writes the directory entry, THEN writes the data.  So if it shuts down before dumping the write cache, it might list a bogus directory listing with no data in it?

Or am I understanding this wrong?

---

### Post by mmix on 2010-05-16
EXT4, here.

---

### Post by &#32 Greg on 2010-05-16
JFS fsck's really fast...

---

### Post by The Real Dave on 2010-05-16
For my root dirs on all my systems I use ext4, it's simply quicker, and I havn't had problems since the few I had in the very beginning. 

However, my /home partition on my main desktop and on my server, /home being the storage location, all have ext3, because I know that it's rock solid.

At least, more rock solid :)

---

### Post by CharlesA on 2010-05-16
I recently switched from ext3 to ext4 on my file server. Haven't run into any problems yet.

That being said, I've used ext4 for / on both 9.10 and 10.04 without any problems. Switched from ext3 to ext4 for the data drives due to faster fsck among other things.

I've heard a bit about the data corruption problem if the machine loses power when it is writing to the drive, but haven't run into that, since my main power is usually pretty reliable and the machine is connected to a UPS in case the power goes out.

---

### Post by kelvin spratt on 2010-05-16
I use jfs its fast and solid.

---

### Post by sxmaxchine on 2010-05-16
ext3 because it has been good for me and ext4 because it is fast

---

### Post by madjr on 2010-05-16
[Next-gen Btrfs May Be The Default File-System In Ubuntu 10.10]("http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg")

[Fedora is testing the system rollback feature]("http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1") and [meego]("http://www.phoronix.com/scan.php?page=news_item&px=ODIzOA") plan to be using it as default

*The current default filesystem is EXT4, the lead developer of which has previously called a &#8216;stopgap&#8217; towards BTRFS.*

i will be using that, so other

---

### Post by handy on 2010-05-16
Good to hear that Btrfs is in sight. :)

I'm looking forward to Btrfs proving itself to be stable, I expect I'll be migrating to that file system. I also expect that I'll give ext4 a complete miss.

---

### Post by chucky chuckaluck on 2010-05-16
I use Reiser. (Does that make me a bad person?)

---

### Post by papangul on 2010-05-16
I have used them all (jfs, xfs reiserfs and ext3/4) extensively on my desktop and I very much prefer the current default ext4. I have a separate small boot partition which has always been ext2 formatted though.

JFS should not even be an option. Last time I used it, the jfs partitions would simply refuse to mount normally after each hard reboot. I had to run fsck and mount the partitions manually afterwards.:mad:

---

### Post by jetsam on 2010-05-16
> **chucky chuckaluck said:**
> I use Reiser. (Does that make me a bad person?)

Does it work and is it stable?

It doesn't make you a bad person of course, but you may be a risk taker.  Since I've read a bunch of your posts, I know for a fact you're a risk taker.  I like your posts a lot, by the way, and the backgrounds are outrageous. :)

---

### Post by &#32 Greg on 2010-05-16
> **jetsam said:**
> Does it work and is it stable?

I don't think that was his point.

---

### Post by Shining Arcanine on 2010-05-16
Why is this a multiple option poll? I voted all 4 options. :/

---

### Post by chucky chuckaluck on 2010-05-16
> **jetsam said:**
> Does it work and is it stable?

It doesn't make you a bad person of course, but you may be a risk taker.  Since I've read a bunch of your posts, I know for a fact you're a risk taker.  I like your posts a lot, by the way, and the backgrounds are outrageous. :)

Stable? It's fast and all my ladyboy videos are on dvd, so I've got nothing to lose. (Thanks for the compliments.)

---

### Post by khelben1979 on 2010-05-16
Since I use Debian Lenny I'm forced to stick with EXT3, but later on when I upgrade to the next stable release of Debian I get a newer kernel which don't motivate me to continue on using EXT3.

I definitely think that EXT4 is a very bad choice if the Linux kernel isn't modern enough to handle it. Better to use EXT3 in that case for stability reasons.

The article which was mentioned in this thread about Linus Torvalds is very old now and would not relate to the current situation. EXT4 should be pretty stable by now, right?

---

### Post by m4tic on 2010-05-16
I only go for what's fast and my computer has a tendency to lock up every once in a while since i have carpet floor. I've found JFS to be fast for me over the years and EXT4 does not do it for me

---

### Post by -humanaut- on 2010-05-16
JFS corrupted my entire filesystem once (know in bug) Ext3/4 or XFS is what I use (plus ext2 for /boot) JFS is damn fast though.

---

### Post by handy on 2010-05-16
> **papangul said:**
> ...
JFS should not even be an option. Last time I used it, the jfs partitions would simply refuse to mount normally after each hard reboot. I had to run fsck and mount the partitions manually afterwards.:mad:

Funny that? I've used JFS on multiple drives on two very different machines hardware wise & never had any problems. I also live in an area that for four or so months of the year is quite storm prone & suffers a LOT of blackouts, so spontaneous cold boots happen quite a number of times in that period.


@jetsam: I think that chucky was alluding to this:

[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

;)

---

### Post by warp4ever on 2012-05-26
I used JFS back in my OS/2 - eCS days where it workes flawlessly.
In Linux I only remember the fsck's on JFS when rebooting, which by the way always solved any problem without dataloss.

I wouldn't touch EXT4 with a bargepole after "losing" a lot of data on my, NFS filesystem server, a lot of times.
So I stick with "solid" EXT3 although it has it's quirks with my usb drives.
(still contemplating the JFS in the back of my head though)

I don't use windows (since win98) whereas ntfs is unknown to me.
(although it's a fork of IBM's HPFS)

---

### Post by Bandit on 2012-05-26
> **gradinaruvasile said:**
> In my experience NTFS dies way faster than EXT3 - maybe its only the Windows implementation/driver/whatever but i repaired quite a few Windows machines that entered a restart loop because of file system corruption.

JFS - it is fast, uses low CPU but it corrupts at the very sign of forced reboot/power failure

Ext4 - its fast and doesnt corrupts like JFS, but i had problems with it when using it as boot partition... But as a large storage only partition its very good given its speed.

Ext3 - its the most stable of them all in my experience - not as optimized as Ext4, but you can rest assured your data is safe on it (at least i am).


I was going to post in my 2 cents, but Grads post pretty much sums up the same experience as I have had. Even the windows reboot reboot reboot reboot :lolflag:

---

### Post by Elfy on 2012-05-27
Old thread closed.

---

