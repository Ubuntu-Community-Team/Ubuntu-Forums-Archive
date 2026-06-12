---
title: "BTRFS Might Be The Default File System In Ubuntu 10.10"
date: 2010-05-14
forum: The Cafe
---

### Post by Sporkman on 2010-05-14
> The EXT Family of file systems (ext2, ext3, ext4) have been ruling almost all Linux distributions for a long time and Ubuntu has been no exception. But things may no longer be the same Ubuntu 10.10 Maverick Meerkat.  Scott James Remnant of the Ubuntu Foundations team said in a blog post that plans are ON for doing work to have btrfs file system  (btrfs is pronounced “Butter F S” or “B-tree F S“) as an installation option and options of making it the default file system in Ubuntu 10.10 have not been ruled out yet. ...

[http://digitizor.com/2010/05/15/breaking-news-btrfs-might-be-the-default-file-system-in-ubuntu-10-10/](http://digitizor.com/2010/05/15/breaking-news-btrfs-might-be-the-default-file-system-in-ubuntu-10-10/)

---

### Post by chessnerd on 2010-05-14
Uh, from my understanding BTRFS is far from complete (latest build is only 0.19) and it hasn't had much development recently (last release was in June 2009) not to mention the fact that, because support only recently incorporated into the kernel, it hasn't had much testing. 

Having it as an option is fine, but making it the default would be a bad idea.

---

### Post by Sporkman on 2010-05-14
> I do stress the emphasis of that statement, a number of things would have to be true for us to take that decision:

   1. btrfs would need to not be marked “experimental” in the kernel config; we understand that this is planned for 2.6.35, which is the kernel version we are expecting to ship in Maverick.
   2. btrfs is not currently supported by GRUB2 (our boot loader) or the installer; these pieces would need to be finished before Feature Freeze.
   3. If that happens, we may make it the default for Alpha releases to gain testing; that testing must go smoothly.
   4. The btrfs upstream must be happy with the idea.
   5. We must be happy with the idea.

It’s a tough gauntlet, and it would only made with the knowledge that production servers and desktops can be run on Lucid as a fully supported version of Ubuntu at the same time.  I’d give it a 1-in-5 chance.

[http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

---

### Post by chessnerd on 2010-05-14
> **Sporkman said:**
> 
> I do stress the emphasis of that statement, a number of things would have to be true for us to take that decision:

1. btrfs would need to not be marked &#8220;experimental&#8221; in the kernel config; we understand that this is planned for 2.6.35, which is the kernel version we are expecting to ship in Maverick.
2. btrfs is not currently supported by GRUB2 (our boot loader) or the installer; these pieces would need to be finished before Feature Freeze.
3. If that happens, we may make it the default for Alpha releases to gain testing; that testing must go smoothly.
4. The btrfs upstream must be happy with the idea.
5. We must be happy with the idea.

It&#8217;s a tough gauntlet, and it would only made with the knowledge that production servers and desktops can be run on Lucid as a fully supported version of Ubuntu at the same time. I&#8217;d give it a 1-in-5 chance.
[http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

I see. 

Well, I suppose anything is possible, but still, can BTRFS be ready for testing by June 3 for the first alpha release? We're talking only 18 days from now.

---

### Post by Sporkman on 2010-05-14
> **chessnerd said:**
> We're talking only 18 days from now.

(aside) Wow - time flies - I can't believe it's almost June already...

---

### Post by McRat on 2010-05-14
What advantages would we see running BTRFS over EXT4?

---

### Post by Phrea on 2010-05-14
> **Sporkman said:**
> (aside) Wow - time flies - I can't believe it's almost June already...

Indeed !
I had to read that one twice, to let it sink in. :O

---

### Post by chessnerd on 2010-05-14
> **McRat said:**
> What advantages would we see running BTRFS over EXT4?

For details about BTRFS features, you can look to Wikipeda: [http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

From my understanding, BTRFS has many advancements in file storage that will make storing files safer, faster, better, etc. and will offer advancements in "copy-on-write," "checksums," and "mirroring." Whatever those things are...

As end users, we probably won't notice much difference unless something goes wrong and the filesystem does/doesn't cause data loss. Maybe reading/writing files will become faster by .09 seconds per MB or something, but either way, Linux with ext3, ext4, BTRFS, Reiser, etc. will be faster than Windows.

---

### Post by jwo7777777 on 2010-05-18
> **McRat said:**
> What advantages would we see running BTRFS over EXT4?

I plowed through the documentation and some forums regarding Btrfs.  It seems to be designed to solve a lot of "under the hood" issues that other file systems fixed previously with band-aids.

It is mostly authored by a database company software engineer with lots of previous file-system design and programming experience and personal and professional interest in the outcome. (i.e. not a basement coder just dinking around)

---

### Post by uOpt on 2010-05-18
It is basically what ZFS did for Solaris and FreeBSD.

It gets rid of the separation between RAID and filesystem, integrating them, avoiding the RAID hole that can leave blocks in an inconsistent state, and avoiding to having to re-sync the whole partition when changing drives (the stress from that often kills a second drive and then you are in trouble).

Snapshots are also "the" feature to have.

It also has filesystem level checksumming which given current disk capacities and documented disk error rates is pretty much a must in this day and age and will be more important soon.

Whether BTRFS is ready for a major Linux distribution I don't know but I have been using ZFS with great success on FreeBSD.

---

### Post by gnomeuser on 2010-05-18
Another important feature is compression support. For people like embedded vendors this means they can create a smaller image to transfer to devices which saves them money and time. 

With snapshots restoring to factory defaults now also just becomes restoring the initial snapshot, also a highly desirable feature.

The btrfs dataformat is stable now (has been for months) and the code is looking very solid. Performance is good as is general stability.

I would be happy to see it as the default FS in Maverick, I think it would lift the release and set a strong course for future releases. It would also give us 2 years to hammer on it till the next LTS goes out.

---

### Post by JDShu on 2010-05-18
Indeed, 10.10 is the best opportunity for Ubuntu to get the experimental stuff out so that lots of users can test it out for the next LTS.

---

### Post by Don1500 on 2010-05-18
All I want is for the OS to work and not have to think about the file system. If btrfs is better than extX then I'll use it, but it has to be bullet proof first.

---

### Post by FrozenFOXX on 2010-05-18
> **Don1500 said:**
> All I want is for the OS to work and **not have to think about the file system.** If btrfs is better than extX then I'll use it, but it has to be bullet proof first.

This is what uOpt was getting at.  Anyone who's used ZFS in a professional or amateur capacity can tell you that it's a *beautiful* thing to just spin up a pool, throw your disks into it, and call "end of story." If you wanna get nuts you can just have it snapshot the file system every night or so in case you think you'll delete something accidentally, but BTRFS is part of a whole new breed of file system, a new philosophy of bringing storage architecture back into the rest of the system.


As an end user you won't have to worry, it'll be more reliable and you won't have to think about it.  Then if you, say, wanted to make a raid and never wanted to have to deal with the ***** that is mdadm (seriously, Solaris Volume Manager's easier to deal with and I'm PAID to work with that and hate it) you just A)Buy disk drives B)Put disk drives into computer C)Tell btrfs through friendly tool of choice to add them into the storage pool.  Done.

Assuming that Oracle continues its support (which it will, considering they've put a lot of time and money into making their DB run awesome on Linux so as not to lose out on user base at the enterprise level) we should expect all the wonderful things from ZFS in time.


If it all sounds like gobbledy-gook just trust us when we say it's better, safer, simpler, and you'll like it.

---

### Post by Sporkman on 2010-08-31
Nope:

[http://www.omgubuntu.co.uk/2010/08/btrfs-wont-be-supported-in-maverick.html](http://www.omgubuntu.co.uk/2010/08/btrfs-wont-be-supported-in-maverick.html)

---

### Post by Dustin2128 on 2010-08-31
can't say I'm surprised; or that I really care that much honestly. Maybe it will be in neurotic newt :D?

---

### Post by JDShu on 2010-08-31
Natty Narwhal actually. And I wouldn't be surprised if it was included in 11.04. Btrfs has come a really long way in the past six months.

---

### Post by jrusso2 on 2010-08-31
Finally they are getting smart and getting rid of one of Linux big weaknesses the ex file system

Now just get rid of X

---

### Post by cprofitt on 2010-08-31
I was very impressed when Chris Mason came and spoke to my LUG about Btrfs. I have been looking forward to it ever since.

---

