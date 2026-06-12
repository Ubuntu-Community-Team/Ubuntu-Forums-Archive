---
title: "Defragging Linux"
date: 2010-11-03
forum: The Cafe
---

### Post by zer010 on 2010-11-03
I've read and been told that there is no need to defrag when using Linux. While not having to defrag is one of the many reasons why I love using Linux, I sometimes wonder if there might be any benefit in defragging a Linux filesystem. Could it possibly eek out the tiniest bit more speed in load times?  All the while I'm wondering about this, I'm running the ext4 filesystem. 
I was wondering a.) Why doesn't Linux need defragging?  b.) Is there an app or a way to do it anyways?  c.) Is it ever a good idea?

---

### Post by P4man on 2010-11-03
Contrary to what many people say, Ext4 is not immune to fragmentation. It is however, **much** better at preventing it than windows/ntfs.

Is there a benefit to defragging? Yeah maybe, even if only marginal and if you have done a lot of deleting and overwriting on a nearly full drive. The problem is there are no good defraggers for ext4 that Im aware off. Copying everything to another drive, and copying it back is a primitive way of getting there. Is it a good idea or worth it? Probably not.

---

### Post by NightwishFan on 2010-11-03
This may make sense (or not) [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Ext4 is going to use defragging eventually, though I do not think the code has landed yet. There are ways to do it manually though. (Which I can not seem to find) :/.

All in all I will say.. No. You will not gain any noticeable performance, unless your disk is very very full where it does not have space to move big files around.

---

### Post by Sean Moran on 2010-11-03
> **NightwishFan said:**
> This may make sense (or not) [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)


Thank you for that good link to a good piece of information NightwishFan.  I just learned something new for the day, that EXT4 isn't what it looks like in the pictures.

I have long laboured under the misapprehension that my HDD partitions were organised just like FAT32 that I once knew roughly what data was where after a defrag, but now I know better.

I am glad about what the author mentioned about how the simplest way to defrag anything is just to copy the lot to a blank partition, for that's the way I've generally been managing every month or three over the past 18 months.

Great to get a mental picture on where everything actually physically ends up here on EXT4, and it's not the physical structure that I had been imagining until reading that article.  

Furthermore, I have a new reason to return to separating the home partition from the root partition like I used to do, but haven't been bothering with for the past year. 

Thank you very much.

---

### Post by Oxwivi on 2010-11-03
I got a 10 GB HDD running Ubuntu with aorund 3 GB free. Defragmenting is definitely worth looking into for me.

---

### Post by P4man on 2010-11-03
That link may be interesting, but its not for Ext4. The article predates Ext4, and Ext4 no longer uses block mapping, but extends. Some more info here:
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

---

### Post by TNT1 on 2010-11-03
> **Oxwivi said:**
> I got a 10 GB HDD running Ubuntu with aorund 3 GB free. Defragmenting is definitely worth looking into for me.

10Gb? Surely it'd be easier to do a backup to a flash drive and format and copy back?

---

### Post by Oxwivi on 2010-11-03
If I have a Flash drive that is. And formatting is not a great solution with all the time it takes, then updating then setting it up all the way it used to be, to your liking.

---

### Post by TNT1 on 2010-11-03
> **Oxwivi said:**
> If I have a Flash drive that is. And formatting is not a great solution with all the time it takes, then updating then setting it up all the way it used to be, to your liking.

True... Remastersys to a flash drive? Can you even do that?

---

### Post by Oxwivi on 2010-11-03
Refer to the first sentence: *Do I have a flash drive?*

---

### Post by TNT1 on 2010-11-03
> **Oxwivi said:**
> Refer to the first sentence: *Do I have a flash drive?*

Ah, right. Sorry.

---

### Post by kleskjr on 2010-11-03
> **Oxwivi said:**
> I got a 10 GB HDD running Ubuntu with aorund 3 GB free. Defragmenting is definitely worth looking into for me.

I guess you can put a huge file into your HDD, lets say 2.5 GB. In order to save the file, I think that the system should defragment. After deleting the file you will have a nice defragmented HDD.

---

### Post by Paqman on 2010-11-03
You can defragment a Linux filesystem by taking an image then copying it back. It'd be worth doing if your filesystem had been too full for any period of time.

---

### Post by P4man on 2010-11-03
> **kleskjr said:**
> I guess you can put a huge file into your HDD, lets say 2.5 GB. In order to save the file, I think that the system should defragment. After deleting the file you will have a nice defragmented HDD.

? No. If it does anything at all, then filling up the harddrive will only make fragmentation worse. The online defragger for Ext4 isnt here yet. But again I question its necessity. I think the speedup the OP is looking for will exist between the ears mostly.

---

### Post by Oxwivi on 2010-11-03
> **kleskjr said:**
> I guess you can put a huge file into your HDD, lets say 2.5 GB. In order to save the file, I think that the system should defragment. After deleting the file you will have a nice defragmented HDD.
Might work. I'll consider downloading the Debian DVD then. :D

---

### Post by Johnsie on 2010-11-03
If you compress everything in /usr you will save alot of space


The techniquie in this post wil work with normal Ubuntu on any machine:

[http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/)

Read the comments because some of them are helpful.

---

### Post by Oxwivi on 2010-11-03
I have hardly 50 MB of personal files - I'm a cloud person.  Actually, there's no file I need, as I mostly browse the web. Just have a document or two at hand and around half-a-dozen music files.

Other than that, I removed all the default games, and many softwares unused by me and istalled Glest and BZFlag. Nothing much to compress is what I'm saying.

And wouldn't compressing increase load times?

---

### Post by Oxwivi on 2010-11-03
Okay wait, just read the article. What does the /usr directory have anyway?

---

### Post by Sean Moran on 2010-11-03
> **Oxwivi said:**
> Okay wait, just read the article. What does the /usr directory have anyway?
I'm no expert but I believe that /usr/ contains most of the operating system, particularly the library files.  I tend to think of /usr/ as a little bit like the old WINDOWS\SYSTEM directory on Win98, but very surprised and keen to test out the procedure in the article.  Thanks again Johnsie for another very imformative link.

Also Oxwivi, I did read something on a HOWTO last year that I use to save a little space on the CD distros when I need to include all the upgrades and still make it under 700Mb, and along with removing the gnome-games, there is this command to remove extra language packs:

```

apt-get remove --purge `dpkg-query -W --showformat='${Package}\n' | grep language-pack | egrep -v '\-en'`

```It's beyond my level of understanding, but it works okay.  Apparently frees around 159Mb on Karmic, but not sure on the latest trends.

---

### Post by JOHNNYG713 on 2010-11-03
> **TNT1 said:**
> True... Remastersys to a flash drive? Can you even do that?
Not to get off subject but, Yes, build the ISO install to flash drive with Unetbootin.

---

### Post by ironic.demise on 2010-11-03
> **Oxwivi said:**
> I got a 10 GB HDD running Ubuntu with aorund 3 GB free. Defragmenting is definitely worth looking into for me.
 10gb, wow... didn't know you could still get those :/

---

### Post by P4man on 2010-11-03
> **ironic.demise said:**
> 10gb, wow... didn't know you could still get those :/

You cant, but the real miracle is that its still working!
Have to say though, a new harddrive will provide a speedboost orders of magnitude higher than any defragging.

To the owner of that drive, out of curiousity can you open disk utility from the system menu and benchmark that drive ? Do a read test only. Im sort of curious how a 10GB drive performs compared to modern drives.

---

### Post by ironic.demise on 2010-11-03
> **P4man said:**
> You cant, but the real miracle is that its still working!
Have to say though, a new harddrive will provide a speedboost orders of magnitude higher than any defragging.
 
To the owner of that drive, out of curiousity can you open disk utility from the system menu and benchmark that drive ? Do a read test only. Im sort of curious how a 10GB drive performs compared to modern drives.
My brother has started a Cisco course at his college, He brings back the trash they want to throw out.
He's brought back 20gb hdds, wireless cards (alas, no antenna), cd readers and general "techies box in the loft" things.
 
The 20gb hdd... if I so much as put them in my box the box freezes up.

---

### Post by HermanAB on 2010-11-03
Defragging is really a DOS FAT thing.  It is not really a problem with modern binary tree like file systems, including Ext2/3 and NTFS.

---

### Post by grahammechanical on 2010-11-03
Am I going off topic, but what is a journaling file system? Does this type of file system make any difference to the need to defragment?

Regards

---

### Post by mips on 2010-11-03
If you use XFS you can defrag it using xfs_fsr.
[http://www.thushanfernando.com/index.php/2009/01/25/maintaining-your-xfs-with-xfs-fsr/](http://www.thushanfernando.com/index.php/2009/01/25/maintaining-your-xfs-with-xfs-fsr/)

---

### Post by Oxwivi on 2010-11-03
> **JOHNNYG713 said:**
> Not to get off subject but, Yes, build the ISO install to flash drive with Unetbootin.
I ask you again to read my post: *Do I own a flash disk?*

---

### Post by Oxwivi on 2010-11-03
Ah, I removed the disk utility because I didn't find any use for it, but I shall post my benchmark test after I reinstall it. :)

And yes, you will not find even 80 GB HDD nowadays. My original HDD was 80 GB, but it doesn't work any more, which is why I'm using 10 GB that my bro-in-law had. By the way, I have another system with 3.something GB, though I've yet to be able to install any new Linux distro. I tried RedHat 9 and it worked, dunno about older Ubuntu though.

---

### Post by Oxwivi on 2010-11-03
Hmm... looks like I missed removing it actually, anyway, here are the results:

**Minimum read rate** 15.8 MB/s
**Maximum read rate** 27.0 MB/s
**Average read rate** 24.3 MB/s

**Average access time** 11.8 ms

---

### Post by P4man on 2010-11-03
Right. I have to say, that average seek time is surprisingly low. Shockingly in fact. But ooh, that throughput sucks. For reference, this is the result of the cheapest 1TB I could buy :

[[IMG]http://img5.imagebanana.com/img/t5numda9/1.0TBHardDiskATASAMSUNGHD103SJBenchm.png[/IMG]](http://www.imagebanana.com/)

Its 6x-8x as fast. And hardly a record breaker by itself. Costed me ca 45 euro. FYI.

---

### Post by Oxwivi on 2010-11-03
That hurts! TT_TT

---

### Post by pizza-is-good on 2010-11-03
> **HermanAB said:**
> Defragging is really a DOS FAT thing.  It is not really a problem with modern binary tree like file systems, including Ext2/3 and **NTFS**.

Fragmenting is a big problem in NTFS. It doesn't seem to be that way because we have huge HDDs today, and they never get close to full capacity, but try to fill it up, delete some files, fill it up again, delete other files. That drive will need a huge defrag that will probably take a long time to complete.

---

### Post by weasel fierce on 2010-11-03
> **Oxwivi said:**
> I ask you again to read my post: *Do I own a flash disk?*

I think the gentleman was answering the other guys question mate

---

### Post by Oxwivi on 2010-11-04
The post he quoted was an answer to my problem, and he was supporting that quote, dude.

Doesn't matter now, moving on...

---

### Post by zer010 on 2010-11-04
Thanks for all of the great responses!  Personally, I'm just running a 40GB HDD with /home as a separate partition. I'm not really seeing any significant slowdown since install, but was just wondering about this. I've seen a defragger somewhere(can't remember where), but was wary about checking it out from what I've heard. Also, I sometimes get asked as to why there is no need to defrag in Linux. Now I have a good grasp on the situation. Special thanks to NightWish for that awesome, informative link! :KS

---

### Post by linux18 on 2010-11-04
There is a quick ways to defrag an xfs filesystem.
1. use XFS as your filesystem and you could use the sudo xfs_fsr command to defrag

---

### Post by HermanAB on 2010-11-04
> Fragmenting is a big problem in NTFS. It doesn't seem to be that way because we have huge HDDs today, and they never get close to full capacity, but try to fill it up, delete some files, fill it up again, delete other files. That drive will need a huge defrag that will probably take a long time to complete.

...and after you so meticulously defragged it, it still won't be any faster than before.  NTFS is a binary tree file system just like Ext3.  So all the arguments in favour of Ext3 not requiring defragging also apply to NTFS.

---

