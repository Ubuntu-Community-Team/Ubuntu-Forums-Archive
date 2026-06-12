---
title: "ext3 or reiserfs on my future Dapper?"
date: 2006-02-14
forum: The Cafe
---

### Post by SilvioTO on 2006-02-14
When Dapper will official naturally I'll install it. I need a suggestion; for general use I'll format my HD with classic ext3 or reiserfs? :-k 
What's better for you?

Thanks, Silvio.

---

### Post by super on 2006-02-14
from what i understand ext3 is pretty good. it's very stable and has good file-system recovery after unclean umounts. (like blackouts or pressing the reset button)

however you plan to work with big files (ie: dv editing, ripped dvds), you might check out reiser4, as ext3 is (comparatively) slow at working very large files.

also as far as i know beagle is not compatible with reiser4. for me this was a deciding factor.

[all the technical info]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

---

### Post by papangul on 2006-02-14
Reiserfs is much faster than ext3 in deleting files, otherwise both perform similarly for other tasks.
So choose reiserfs for the partion where you frequently delete your files(/home partition) and choose whatever for others.
I have ext2 for my boot partition, ext3 for /, and reiserfs for /usr and /home.

---

### Post by TrendyDark on 2006-02-14
ext3 is more stable, by far. You lose a little speed, but it's not noticable unless you're transfering or deleting LARGE files. I moved my 30gigs of music from a reiserfs drive to a FAT32 drive once and once from a ext3 to a FAT32, the reiserfs won.

---

### Post by Krigl on 2006-02-14
How about the greater danger of crash (irreversible data loss including) with reiser? Any links or personal experience? I remind how "alfa-female of Czech Linux geeks" wrote "ReiserFS is Evil" when counting out what last year has taught her.

---

### Post by mstlyevil on 2006-02-14
Most recent distros use reiserfs. I have used both and I just can not tell all that much of a difference myself. I find both to be stable so just use which one you want. Either way you can not go wrong.

---

### Post by SilvioTO on 2006-02-15
After readed all your posts, I decided for ext3; I prefer stability. Thanks! ;) 
Silvio.

---

### Post by briancurtin on 2006-02-15
ive used reiser and ext3, and have had zero problems with either one in the 8 months i have used only linux

---

### Post by kingsidy on 2006-02-15
i think that the default file system for suse is reiserfs. therefore when i moved to ubuntu, i used reiser as well. i have done hard reset, and i do not see any probems starting back up. 
it is like choosing between fat32 and ntfs (sort of) fat32 might be more stable and mature, but ntfs can handle hug single files better.

---

### Post by prizrak on 2006-02-15
reiser is faster for small file I/O than EXT3. It is also much faster for fsck checks. Ext however can be accessed from Windows with the use of third party apps, there is no such app for reiser as far as I know. All in all there is little difference between the two.

---

### Post by sapo on 2006-02-15
[QUOTE=prizrak]reiser is faster for small file I/O than EXT3. It is also much faster for fsck checks. Ext however can be accessed from Windows with the use of third party apps, there is no such app for reiser as far as I know. All in all there is little difference between the two.[/QUOTE]
Sure there is, i m using [this tool](http://p-nand-q.com/download/rfstool.html) with [this GUI](http://yareg.akucom.de/) and it works just fine to read reiserFS from windows :)

---

### Post by GoldBuggie on 2006-02-15
> it is like choosing between fat32 and ntfs (sort of) fat32 might be more stable and mature, but ntfs can handle hug single files better.  		  	  		  		    		
Not to sound to picky but comparing with fat is wrong since it is not a journaling filesystem(is about the worst fs i know actually).

I prefer ext3 instead of reiserfs. Recovers files better and when tweaked I find it to be slightly faster in the tass I do. But both are very nice fs. It all depends on what you want to do with your system.

I would recommend loo&#7729;ing into the differences and also have a look at other fs like XFS....it might suit your needs.

---

### Post by gord on 2006-02-15
for day to day use your neeeeeeeeeeever gonna be able to tell the diffirence. but i have have my share of problems with reiserfs and lost a few files... allthough i was doing some pritty unorthodox stuff at the time.

it also gets a bit dodgy with virtual machines (vmware and the like) that are also formatted to reiserfs. 

my advice is to use ext3 unless you have an actual reason not to.

---

### Post by arctic on 2006-02-15
[QUOTE=mstlyevil]Most recent distros use reiserfs. I have used both and I just can not tell all that much of a difference myself. I find both to be stable so just use which one you want. Either way you can not go wrong.[/QUOTE]Sorry, but this is not correct. Most major distros stick to ext3 as default filesystem - and for good reason. Ext3 is way more tested and stable and way better for system recovery than reiserfs, which is still relatively young and buggy. You will run into problems with reiserfs where other filesystems like ext3 or jfs won't leave you spitting in anger. :mrgreen: 

You should always go for stability over speed, thus ext3 is almost always the better choice. (after all, the speed difference is not really noticeable for the average user). ;)

---

### Post by mstlyevil on 2006-02-15
[QUOTE=arctic]Sorry, but this is not correct. Most major distros stick to ext3 as default filesystem - and for good reason. Ext3 is way more tested and stable and way better for system recovery than reiserfs, which is still relatively young and buggy. You will run into problems with reiserfs where other filesystems like ext3 or jfs won't leave you spitting in anger. :mrgreen: 

You should always go for stability over speed, thus ext3 is almost always the better choice. (after all, the speed difference is not really noticeable for the average user). ;)[/QUOTE]

I stand corrected. I should have just said most distros I have tried.

---

### Post by stimpack on 2006-02-15
For all the talk about stability you will NEVER notice any difference.

I normally couldnt careless what FS to use as long as its not crap like fat32, except when I demoed Linux to a windows friend that ext3 20boot filecheck popped up for all drives, damn embaressing, switched to reiserfs for all now.

---

### Post by Gandalf on 2006-02-15
[QUOTE=papangul]Reiserfs is much faster than ext3 in deleting files, otherwise both perform similarly for other tasks.
So choose reiserfs for the partion where you frequently delete your files(/home partition) and choose whatever for others.
I have ext2 for my boot partition, ext3 for /, and reiserfs for /usr and /home.[/QUOTE]
Sorry but Reiser is not at all faster when it comes to delete files, anyway i haven't find it anywhere faster than ext3
[IMG]http://linuxgazette.net/122/misc/piszcz/group002/image003.png[/IMG] 
I use ext3 with dir_index option and it just rocks..

Check [http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html) for a Benchmark and see the reults urself, I even tried JFS but ext3 with dir_index beats it (ext3 in that benchmark is used by default i.e dir_index not activated...

---

### Post by WildTangent on 2006-02-15
I've been using reiser for months, and I haven't once had file system problems.

-Wild

---

### Post by super on 2006-02-15
there's actually this same dicussion in the dapper devel forums.

[link to thread]("http://www.ubuntuforums.org/showthread.php?t=42463&highlight=reiser+beagle")

the gist of the thread:

[QUOTE=jdong]> ext3 was a hack, but this was only true a long long time ago, ext3 is a LOT faster than it was, and it is far more stable than reiserfs is.
Ok, I agree with the first part, but definitely not the stability thing. First off, ext3 is stable, and at least "above average" when compared to the filesystem choices for popular operating systems. However, I really can't say that reiserfs is unstable at all. I run Novell/SuSE systems here, that use SuSE's reiserfs, and they've all been through their fair share of resets, kernel dumps from my driver tweaks, and power outages. Yet, they've all made it through perfectly. I see no evidence that shows ext3 is any more stable than reiserfs -- in fact, I'd put them on the same level (highly stable, production level) as far as stability.

> stable is good, and you need to get "ext3 is slow" out of your head, because it's plain wrong.
Ok, here's where I run into some disagreements. Ext3 without DIR_INDEX is significantly slower than, say, reiserfs and XFS, in specific circumstances, especially when manipulating lots of tiny files. DIR_INDEX speeds this up to almost par with others, but that's at the cost of some "stability". An advantage of traditional EXTfs's layout is that the filesystem structures are highly recoverable after physical damage. DIR_INDEX implements binary structures which sacrifice much of this. However, "physical damage" is such a out-of-norm operating condition that should be solved via lower-level protection (RAID, CRC-verifying bus chipsets, etc) that a filesystem should never have to deal with.[/QUOTE]

---

### Post by papangul on 2006-02-15
[QUOTE=Gandalf]Sorry ...[/QUOTE]
Actually I'm sorry because I was carrying this wrong idea for a long time ( i must have made some mistake in reading the tables of  a benchmark :(  ). My idea was just opposite to this graph of yours. Thanks.
When I install drapper I would just invert my selections.
But is there any confusion about the dir_index option ? I remember people debating hotly on a thread about using ext3 with dir_index(or something like 'hashtree') option.

---

### Post by super on 2006-02-15
@papangul

dir_index is reasonably safe. not much need to worry.
> An advantage of traditional EXTfs's layout is that the filesystem structures are highly recoverable after physical damage. DIR_INDEX implements binary structures which sacrifice much of this. However, "physical damage" is such a out-of-norm operating condition that should be solved via lower-level protection (RAID, CRC-verifying bus chipsets, etc) that a filesystem should never have to deal with.

to enable dir_index:
```
sudo tune2fs -O dir_index /dev/hdxy
sudo umount /dev/hdxy
sudo e2fsck -D /dev/hdxy

```


check dir_index status with:
```
sudo tune2fs -l /dev/hdxy | grep dir_index
```

EDIT: should add that 'x' is the device and 'y' is the partition assignment

---

### Post by GreyFox503 on 2006-02-15
[quote=Gandalf]
Check [http://linuxgazette.net/122/piszcz.html]("http://linuxgazette.net/122/piszcz.html") for a Benchmark and see the reults urself, I even tried JFS but ext3 with dir_index beats it (ext3 in that benchmark is used by default i.e dir_index not activated...[/quote] 
This article was posted to slashdot a while ago, and most of the discussion centered around the validity of the results.  This benchmark was run on a 500mhz computer, which many posters said made a big difference, especially for Reiser4, which supposedly decreases I/O by using more CPU power.

I'm not an expert in filesystems, but you might get different results if you ran them on a new machine.  These results just show that ext2/3 is faster on their test machine.

And in case you're interested, I run reiserfs.  Why?  Well, after I noticed that Ubuntu checked my filesystem after every 30 (?) boots, I tried a different one on my next installation.  It doesn't auto-check reiserFS installations in the same way as using ext3. Whether it needs the checking or not I don't know, but I've been using reiserfs every since with zero problems.

Now if only reiser4 would make it into the kernel, I would be more apt to try it.

---

### Post by papangul on 2006-02-15
[QUOTE=super]@papangul

dir_index is reasonably safe. not much need to worry.


to enable dir_index:
```
sudo tune2fs -O dir_index /dev/hdxy
sudo umount /dev/hdxy
sudo e2fsck -D /dev/hdxy

```


check dir_index status with:
```
sudo tune2fs -l /dev/hdxy | grep dir_index
```

EDIT: should add that 'x' is the device and 'y' is the partition assignment[/QUOTE]
Thanks a lot for the info ! :-D

---

