---
title: "shred or dd or any thing???"
date: 2009-02-28
forum: Security
---

### Post by lastfrontier on 2009-02-28
is there a linux program out there that will work like shred but with a recursive option i want to wipe a bunch of solide state drives some to sell and otheres for security reasons if not shred what about dd i heard this can write 1's and 0' but can it wipe entire disc drives and or solide state drives???????????

---

### Post by bodhi.zazen on 2009-02-28
I advise dban

[http://www.dban.org/](http://www.dban.org/)

---

### Post by HermanAB on 2009-02-28
Simply write zeros over the whole drive using dd.  Doing more than that isn't worth the effort:
$ sudo dd if=/dev/zero of=/dev/sdx

Where x is for the particular drive.  Be careful not to overwrite the system drive which would normally be sda.

Cheers,

Herman

---

### Post by lastfrontier on 2009-02-28
ok that sounds like something i can use but what would be the string for an sd disk [sudo dd if=/dev/zero of=/media/disk] also what i am looking for is a burn barrel for my comp in place of the trash i want to stop putting things in the trash i want to shred the whole folder/directory i saw a person use this command [sudo shred /dev/sdd -f -v -z --iterations=10] and it worked but when i try it i get error saying this is a directory and it wont work it seems that files i can do just not directorys

---

### Post by Biochem on 2009-02-28
There is no good wiping program that works on file. Modern journaled file-system write on unused sector then mark the previous one as unused.

Now if you want to wipe the whole hard drive you can do it with shred or dd on the device itself. Since you are mentioning a folder in /media/ I suspect that is what you want to do on a removable devise. to proceed follow the sollowing step

first, before you connect the drive run 
```
sudo fdisk -l
```
then connect the drive and run the same command again. there should be an additional line in the second run and that is your actual device name. What you see in /media/ is your mountpoint where you access the filesystem.

Next, unmount the filesystem
```
sudo umount /media/someLabel
```

You will now be able to wipe the whole device using either
```
sudo shred /dev/sdd -f -v -z --iterations=10
```
or
```
sudo dd if=/dev/urandom of=/dev/sdX
```

---

### Post by lastfrontier on 2009-03-03
thanks it worked very well for what i needed at that moment i will continue to dig for more info that was very helpful thanks again...

---

### Post by lastfrontier on 2009-03-06
what i want for example i have a folder /directory named trash instead of the trash program and i want to fill the trash with what ever and at some point i want to shred the folder in it's entirety kind of like a -r option to shred i want to shred all that i trash can any one help??????????

---

### Post by lykwydchykyn on 2009-03-06
Have you checked out secure-delete?  It's in the repositories, might be worth a look.

---

### Post by HermanAB on 2009-03-07
By the way, **all** disk drives have an erase utility built into the drive controller.  This is the only way to do a secure erase on a disk, but it is very slow.  See the hdparm man page for details.  It is a two step process:
```
sudo hdparm --security-set-pass PWD /dev/sdb
sudo hdparm --security-erase PWD /dev/sdb
```

After that, the disk will be squeaky clean.

Cheers,

Herman

---

### Post by Biochem on 2009-03-07
> **lastfrontier said:**
> what i want for example i have a folder /directory named trash instead of the trash program and i want to fill the trash with what ever and at some point i want to shred the folder in it's entirety kind of like a -r option to shred i want to shred all that i trash can any one help??????????

As I said before there is no secure way to wipe a folder or a file on a mounted filsystem. The only way I can think of is to empty the trash then wipe the free space. secure-delete as such an option but you can also use the following

```
dd if=/dev/urandom of $HOME/Delete_this_file_later
```

in both case you fill the hard drive with random data. The secure delete is a bit better since it also fill the inode table to remove all traces of deleted file. However, both options takes forever and is not something you want to do regularly.

IMHO, if you know you will want to wipe files save it on an encrypted partition (or folder with encfs).

---

### Post by lastfrontier on 2009-03-07
yea that is probley what i will do save it in an encrypted file and i can wipe it when it is full with shred i like truecrypt and it makes a file which can be wiped clean with shred i will also lookinto secure-delete thanks for the help if there is any one out there with any other info i would sure love to hear it shred seems to work good i would think that this would be a big topic with so many people out there doing there banking and taxes on there computer

---

### Post by graysky on 2009-04-04
```
$ sudo shred /dev/sdc1 -uv
```

This is working well but is it very slow as you can imagine (650 Gb partition).  Are the default 25 iterations really needed?  Wouldn't 2 or 3 be sufficient?

---

### Post by lykwydchykyn on 2009-04-04
> **graysky said:**
> ```
$ sudo shred /dev/sdc1 -uv
```

This is working well but is it very slow as you can imagine (650 Gb partition).  Are the default 25 iterations really needed?  Wouldn't 2 or 3 be sufficient?

1 is probably sufficient for most needs.  What are you wanting to do?

---

### Post by graysky on 2009-04-04
> **lykwydchykyn said:**
> 1 is probably sufficient for most needs.  What are you wanting to do?

Wipe a failing drive before I send it back to Seagate for a new one.

---

### Post by lykwydchykyn on 2009-04-04
> **graysky said:**
> Wipe a failing drive before I send it back to Seagate for a new one.

I doubt there's much chance anyone at seagate is going to try to recover anything off your drive.  Who knows, though; they may have disgruntled, nosy employees.

You have to look at it this way:  wiping it one time reduces the number of people who are able to recover data from it to a very tiny percentage of people with very special tools.  Each subsequent wipe makes it marginally harder for those people to recover things.  So if you're worried that one of "those people" is going to get their hands on the drive and try to recover data from it, you'd want to wipe it as many times as you can possibly stand to (assuming you can't just smash it with a hammer outright).  If you're not worried about that, it's a waste of time to do it more than once.

Of course, "those people" may not even exist.  See this:
[http://16systems.com/zero.php](http://16systems.com/zero.php)

---

### Post by graysky on 2009-04-06
Cool, thanks for the info.  Maybe once is enough after all.  It just makes me scratch my head why shred defaults to 25x if what you're saying is accurate.

---

### Post by bodhi.zazen on 2009-04-06
> **graysky said:**
> Cool, thanks for the info.  Maybe once is enough after all.  It just makes me scratch my head why shred defaults to 25x if what you're saying is accurate.

People are paranoid.

Lesson : ALWAYS confirm any information you read on Security from at least 2 reputable sources.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

[http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/](http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/)

---

### Post by lykwydchykyn on 2009-04-06
> **bodhi.zazen said:**
> People are paranoid.

Lesson : ALWAYS confirm any information you read on Security from at least 2 reputable sources.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

[http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/](http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/)

Amen to that.  I think it goes for anything on the Internet, though, not just security.

Thanks for those links, bodhi.zazen.  You may have saved a few hard drives from destruction at my workplace.

---

### Post by HermanAB on 2009-04-07
Hmm, I don't want to be unkind but there is much misinformation in this thread.  (BTW, I do military security work).

Some pointers:
[LIST]
[*]If you are really worried about security, then you have to use encryption and encrypt whole partitions with LUKS.
[*]Utilities like shred are not significantly better than a simple rm.
[*]There is an erase utility built into the drive controller of all disk drives.  This is the only way to do a secure erase (though the military still doesn't trust it).
[*]For commercial/home use, you can erase a disk by either overwriting it with zeros using dd, or by invoking the abovementioned secure erase function using hdparm - a two step slooooow process.
[*]If it is a military drive - melt it with an acetylene torch.
[/LIST]

So, for erasing a failing business or home drive, I would suggest you simply do:
dd if=/dev/zero of=/dev/sdb

---

### Post by Krupski on 2009-04-07
> **lastfrontier said:**
> is there a linux program out there that will work like shred but with a recursive option i want to wipe a bunch of solide state drives

I had a whole large cardboard box full of old hard drives that the company wanted "cleansed" before they were disposed of.

So, I took them out into the country and shot each one. Twice.

:)

---

### Post by lykwydchykyn on 2009-04-07
> **HermanAB said:**
> 
So, for erasing a failing business or home drive, I would suggest you simply do:
dd if=/dev/zero of=/dev/sdb

shred overwrites the entire drive from /dev/urandom, then finishes off with an option zero overwrite.  How is that less secure than dd (probably not any more necessary, though)?

If you shred a file, it overwrites the sectors with random data.  How is that not more secure than rm, which merely deletes the inode record?  There are utilities to recover files from ext3 that have been deleted with rm (though they don't always work well -- I suppose if the file were fragmented enough it would be about as good as shred!).

---

### Post by graysky on 2009-04-07
> **HermanAB said:**
> So, for erasing a failing business or home drive, I would suggest you simply do:
dd if=/dev/zero of=/dev/sdb

Hmmm... two questions:

1) Does that command work on the entire drive regardless of how it's partitioned?  In other words, if there are multiple partitions on the disk, will that command get them all?

2) Is there a verbose switch so that I can see the % progress or time remaining?  It's a 750 GB disc and I'd like to know how many hours/days this will take :)  I didn't see anything in the man page.

---

### Post by lykwydchykyn on 2009-04-07
> **graysky said:**
> Hmmm... does that command work on the entire drive regardless of how it's partitioned?  In other words, if there are multiple partitions on the disk, will that command get them all?

Yes.  In fact, within the first few milliseconds it wipes out the partition table.

---

### Post by bodhi.zazen on 2009-04-07
> **graysky said:**
> Hmmm... two questions:

1) Does that command work on the entire drive regardless of how it's partitioned?  In other words, if there are multiple partitions on the disk, will that command get them all?

2) Is there a verbose switch so that I can see the % progress or time remaining?  It's a 750 GB disc and I'd like to know how many hours/days this will take :)  I didn't see anything in the man page.

sdb = entire hard drive
sdb1 = first partition

see : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by graysky on 2009-04-07
I understand.... so what about the verbose option?  My /dev/sdc1 is 700 GB.

---

### Post by jdong on 2009-04-07
For SSD's, I don't believe there's strong evidence that says wiping it more than once actually does anything more in terms of scrambling the data.

For what you're doing, I'd say just scrub it once with either zeroes or randomness such that your drive's contents cannot be readily read, and that's good enough.

I doubt anyone's going to go through the level of effort to recover your data after that unless you or someone else is paying them BIG MONEY to.

---

### Post by Biochem on 2009-04-08
> **lykwydchykyn said:**
> If you shred a file, it overwrites the sectors with random data.  How is that not more secure than rm, which merely deletes the inode record?  There are utilities to recover files from ext3 that have been deleted with rm (though they don't always work well -- I suppose if the file were fragmented enough it would be about as good as shred!).

Actually, on journaled file-system like ext3, those same recovery program works very well after a file has been "shredded". That's because journaled file-system don't over-write the actual sector to allow recovery in case of a crash.

---

### Post by the_maplebar on 2009-04-08
> **Biochem said:**
> Actually, on journaled file-system like ext3, those same recovery program works very well after a file has been "shredded". That's because journaled file-system don't over-write the actual sector to allow recovery in case of a crash.

I see this mentioned a lot, but the shred man pages state that this is not the case with ext3 (in default mode).  Does anyone know if the man page is accurate here?
> 
In the case of ext3 file systems, the  above  disclaimer  applies only in data=journal mode, which journals file data in addition to just metadata.   In  both  the data=ordered  (default) and data=writeback modes, shred works as usual.

---

### Post by jdong on 2009-04-08
The manpage is accurate with regards to ext3, however, the behavior should never be assumed unless you're very familiar with the filesystem. Not all filesystems handle overwrites by literally overwriting the same blocks -- this doesn't necessarily have to do with journaling as much as it has to do with modern filesystem optimizations.

---

### Post by hovzio on 2009-04-08
hi, I wrote this zenity script last dec. You have to put it in $HOME/.gnome2/nautilus-scripts/. Then you can right click on a file in nautilus, go to "scripts" end press swype or whatever you choose to call the program. 

Caution, this script uses dd do overwrite a single file (no directories) with the output of /dev/random. This can be changed to /dev/urandom or /dev/zero. I am a begginer!! Please read over things and do a test run first!! I would love to hear some feedback, especially improvements. How do I get that progress bar working!I know nothing about liscesnsing etc, (I know I should..where do i start?) feel free to do as you please with this, I don't think its anything special. Please be carefull, read through the script and don't go executing just any code you recieve. At least have somone else ok it if you don't understand things. 

I must admit I'm kinda embarrased giving this out. Its just a little project that doese the trick for me, take it easy on me. I must say it works rather well but it doese take quite a while to erase large files like movies etc but its perfect for docs and so forth. talking to much... here goes, :)

---

### Post by jdong on 2009-04-08
> **hovzio said:**
> hi, I wrote this zenity script last dec. You have to put it in $HOME/.gnome2/nautilus-scripts/. Then you can right click on a file in nautilus, go to "scripts" end press swype or whatever you choose to call the program. 



Yes, copying from /dev/urandom does "work", but it's not the optimal method of wiping. You should really consider hooking it to call the "wipe" command properly -- it's been written by someone with expertise in securely deleting files and will work both faster and more securely (not only does it do an overwrite it also arbitrarily truncates the files and otherwise mutilates it beyond undeletion.

---

### Post by graysky on 2009-04-08
Ok!  I just started the following command on my 750 GB drive:
```
$ sudo dd if=/dev/zero of=/dev/sdd1
```

There is no output from dd.  Any thoughts on how long it should take?

---

### Post by hovzio on 2009-04-08
> **graysky said:**
> Ok!  I just started the following command on my 750 GB drive:
```
$ sudo dd if=/dev/zero of=/dev/sdd1
```

There is no output from dd.  Any thoughts on how long it should take?

This will take a long time, probably to long.. I think the approach jdong mentioned above using wipe may work better. The dd command has no output till its complete.

@jdong, thanks I'll take a look at wipe.

---

### Post by jdong on 2009-04-08
> **graysky said:**
> Ok!  I just started the following command on my 750 GB drive:
```
$ sudo dd if=/dev/zero of=/dev/sdd1
```

There is no output from dd.  Any thoughts on how long it should take?

/dev/zero is cheap to read from because it's all zeroes. It will take as long as it takes to write to the entire disk. 50MB/s is a good estimate for a modern 7200RPM SATA drive, so punch into Google "750GB / 50MB/s" and it should tell you how long, correct for the size of your disk.

That's right, Google is your friend for unit conversion phobias :)

---

### Post by dslink on 2009-04-08
Smash the platters, only secure way really man.

---

### Post by jdong on 2009-04-09
> **dslink said:**
> Smash the platters, only secure way really man.

You can probably piece together smashed platters as well as a ripped up sheet of paper...

The only "secure" way is probably heating up the platters to the curie point, but even then I have no clue if it's theoretically feasible for some forensic process to obtain your data back or at least some part of it.

But at any rate, once you're guarding against the casual onlooker with basic data recovery tools, this forum is probably not the best place to be getting your security advice ;-)

---

### Post by HermanAB on 2009-04-09
You can watch the progress of dd, by opening another console and sending it a signal using kill. First ps to get the numeric PID of dd:

ps | grep dd
kill -USR1 PID

Dd will then print a progress report on the first console and immediately carry on without interruption.

---

### Post by graysky on 2009-04-09
@Herman - yep, that works great.

```
$ sudo dd if=/dev/zero of=/dev/sdd1 bs=1M
22697+0 records in
22697+0 records out
23799529472 bytes (24 GB) copied, 249.917 s, 95.2 MB/s
44978+0 records in
44978+0 records out
47162851328 bytes (47 GB) copied, 484.785 s, 97.3 MB/s
160223+0 records in
160223+0 records out
168005992448 bytes (168 GB) copied, 2102.25 s, 79.9 MB/s
209635+0 records in
209635+0 records out
219818229760 bytes (220 GB) copied, 2868.86 s, 76.6 MB/s
dd: writing `/dev/sdd1': No space left on device
715403+0 records in
715402+0 records out
750153729024 bytes (750 GB) copied, 10718 s, 70.0 MB/s
```

Took about 3 h to finish the entire 750 GB by the way.

---

### Post by somnambulant on 2009-05-21
If you use dd_rescue it will show the progess.

# dd_rescue /dev/zero /dev/sda

---

### Post by Perkins on 2009-05-30
Last time I looked into the subject, on magnetic drives it was possible to easily recover the last four or five states of any particular sector through detailed analysis of the magnetic field.  This is why most disk wiping programs run a minimum of ten overwrites with random data.  If your data is sensitive enough that people would be willing to pay the few thousand dollars to have the drive analyzed and the data recovered, then you really need to overwrite it at least that many times.  Of course, if your data is that sensitive, you should probably be storing it encrypted to begin with.  Especially if it's in a laptop or other portable device.

For the original poster, so far as I know solid-state devices are not so easily recoverable.  Once you overwrite a sector, it's overwritten.  However, these devices switch sectors around for wear-leveling purposes to make the drive last longer.  So the only way to be sure you've actually overwritten the sector that had your data is to fill all the empty space with zeros.  One pass should do it though.

---

### Post by rookcifer on 2009-05-31
> **Perkins said:**
> Last time I looked into the subject, on magnetic drives it was possible to easily recover the last four or five states of any particular sector through detailed analysis of the magnetic field. 

This is not confirmed by any sort of evidence.  This idea of needing numerous overwrites was put forth by Peter Guttmann in one of his papers and it was for some reason considered the Bible on the subject, even though no experimental evidence confirmed it.  I have seen other papers that suggest even one overwrite makes recovering any data impossible.  There was even a guy who contacted numerous data recovery companies and offered them a hefty reward if they could recover files that were overwritten only one time.  None of them took him up on the offer.  Now, even Peter Gutmann has recanted and said that 35 overwrites are not really necessary (and he claims his paper was misunderstood).

Here is a snippet of an [article]("http://www.h-online.com/news/Secure-deletion-a-single-overwrite-will-do-it--/112432") discussing how one overwrite is all that is needed.  You can read the technical paper itself from within the article:
> 
The myth that to delete data really securely from a hard disk you have to overwrite it many times, using different patterns, has persisted for decades, despite the fact that even firms specialising in data recovery, openly admit that if a hard disk is overwritten with zeros just once, all of its data is irretrievably lost.

Craig Wright, a forensics expert, claims to have put this legend finally to rest. He and his colleagues ran a scientific study to take a close look at hard disks of various makes and different ages, overwriting their data under controlled conditions and then examining the magnetic surfaces with a magnetic-force microscope. They presented their paper at ICISS 2008 and it has been published by Springer AG in its Lecture Notes in Computer Science series (Craig Wright, Dave Kleiman, Shyaam Sundhar R. S.: Overwriting Hard Drive Data: The Great Wiping Controversy).

They concluded that, after a single overwrite of the data on a drive, whether it be an old 1-gigabyte disk or a current model (at the time of the study), **the likelihood of still being able to reconstruct anything is practically zero.**

---

### Post by rkillcrazy on 2010-04-28
From what I recall, the 1st poster was asking if there were a way to do "a bunch of drives."  I'm wanting to know that as well.  I want to you a LIVE CD to do a **DD** or **SHRED** command to do **ALL** HDDs connected.  Is there a way to do a **dd_rescue /dev/zero /dev/*** or something like that?

04-28-2010
1022 EDT

---

### Post by lykwydchykyn on 2010-04-28
> **rkillcrazy said:**
> From what I recall, the 1st poster was asking if there were a way to do "a bunch of drives."  I'm wanting to know that as well.  I want to you a LIVE CD to do a **DD** or **SHRED** command to do **ALL** HDDs connected.  Is there a way to do a **dd_rescue /dev/zero /dev/*** or something like that?

04-28-2010
1022 EDT

That's pretty much what Darik's boot-and-nuke does.
see [www.dban.org](www.dban.org)

---

### Post by dragos2 on 2010-04-28
SSD drives manage date differently, here are one of the best guides to them:
[www.**anand**tech.com/show/2738](www.**anand**tech.com/show/2738)
[www.**anand**tech.com/show/2829](www.**anand**tech.com/show/2829)

So overwritting data on a SSD is not that simple, nor formatting.

---

### Post by rkillcrazy on 2010-04-28
> **lykwydchykyn said:**
> That's pretty much what Darik's boot-and-nuke does.
see [www.dban.org](www.dban.org)

And I've used DBAN a lot...  I was just curious if the Ubuntu Live CD would do the same.  It sounded like the first guy was also curious...

04-28-2010
1539 EDT

---

### Post by lykwydchykyn on 2010-04-28
> **rkillcrazy said:**
> And I've used DBAN a lot...  I was just curious if the Ubuntu Live CD would do the same.  It sounded like the first guy was also curious...

04-28-2010
1539 EDT

I don't see why not, though the problem is that it would wipe the drives one after the other, whereas DBAN wipes them all in parallel.  

I suppose you could open up multiple terminal windows and do one drive in each, but what a chore!

---

### Post by rookcifer on 2010-04-29
> **lastfrontier said:**
> is there a linux program out there that will work like shred but with a recursive option i want to wipe a bunch of solide state drives some to sell and otheres for security reasons if not shred what about dd i heard this can write 1's and 0' but can it wipe entire disc drives and or solide state drives???????????

Shred can wipe whole drives with either 0's, 1's or both.  "DD" can as well.

---

### Post by arizonalarry2 on 2010-07-11
I tried DBAN and as far as I can tell it takes about an hour per gigabyte, far too long for household use. Use DD or Shred instead.

---

### Post by ov3rcl0ck on 2010-07-11
> **HermanAB said:**
> Simply write zeros over the whole drive using dd.  Doing more than that isn't worth the effort:
$ sudo dd if=/dev/zero of=/dev/sdx

Where x is for the particular drive.  Be careful not to overwrite the system drive which would normally be sda.

Cheers,

Herman

Yeah this is called Zeroing out the drive, not as secure as a Guttman, but zeroing the disk will make it hard enough to read the data.

Boot and Nuke, like other suggested will wipe the disk clean and basically impossible to read the data.

Zeroing should be enough, because it will make old data either 90% corrupt or completely unreadable.

---

### Post by bodhi.zazen on 2010-07-11
> **ov3rcl0ck said:**
> Yeah this is called Zeroing out the drive, not as secure as a Guttman, but zeroing the disk will make it hard enough to read the data.

Boot and Nuke, like other suggested will wipe the disk clean and basically impossible to read the data.

Zeroing should be enough, because it will make old data either 90% corrupt or completely unreadable.

The Guttman theory has been disproven

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

One overwrite (with zeros) is sufficient. The key is the data must be over written.

---

