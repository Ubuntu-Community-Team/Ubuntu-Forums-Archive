---
title: "firefox history restore"
date: 2010-10-07
forum: Security
---

### Post by redlinethecar on 2010-10-07
Hey guys this might be a very weird post but here goes. I deleted my history from my laptop and my wife feels that I am hiding things and is taking it really bad right now. I need to come up with a way to recover my deleted history. I deleted it about an hour ago and I haven't shut the system down yet. I need to recover this so that I may live in piece please. I have not done a backup so that is not an option but I do know that these files can somehow be recovered because we all know it's not truly gone unless overwritten. also i have stop the storing of any new history because i dont want data to over write. I'm using ubuntu. Thank in advance.

---

### Post by redlinethecar on 2010-10-07
sorry ubuntu 10.04, Ok quick update:
I have tried scalpel and foremost and now realize that using these two is not going to help because they can only recover certain files. I believe the only file that I can recover is places.mysqlite. I have never worked so hard on something in my life! I haven't been able to recover anything yet as far as the item needed for my history but I thought I would update the situation. Thanks a lot for whoever is reading.

---

### Post by lovinglinux on 2010-10-07
[From SQLIte  FAQ:]("http://www.sqlite.org/faq.html#q20")

> **(20) I accidentally deleted some important information from my SQLite database. How can I recover it?**

    If you have a backup copy of your database file, recover the information from your backup.

    If you do not have a backup, recovery is very difficult. You might be able to find partial string data in a binary dump of the raw database file. Recovering numeric data might also be possible given special tools, though to our knowledge no such tools exist. SQLite is sometimes compiled with the SQLITE_SECURE_DELETE option which overwrites all deleted content with zeros. If that is the case then recovery is clearly impossible. Recovery is also impossible if you have run VACUUM since the data was deleted. If SQLITE_SECURE_DELETE is not used and VACUUM has not been run, then some of the deleted content might still be in the database file, in areas marked for reuse. But, again, there exist no procedures or tools that we know of to help you recover that data.

Nevertheless, if you can recover an old places.sqlite, then you might have a chance, since is that database that stores bookmarks and history.

Make a backup of your current places.sqlite file first.

---

### Post by waznot on 2010-10-07
Hi redlinethecar

I just tried something that may or may not work/help.

Right now I am on a windows computer running Firefox version 3.6.10.

I just did a 'Delete Complete History' (except for cookies). If I now type 'a' into the address bar the pull down list appears displaying all these pages I have been to that contain an 'a' in the url or the page title.

If this works on your set up, maybe your wife could try typing 'suspect' words into the address bar.

---

### Post by lovinglinux on 2010-10-07
> **waznot said:**
> Hi redlinethecar

I just tried something that may or may not work/help.

Right now I am on a windows computer running Firefox version 3.6.10.

I just did a 'Delete Complete History' (except for cookies). If I now type 'a' into the address bar the pull down list appears displaying all these pages I have been to that contain an 'a' in the url or the page title.

If this works on your set up, maybe your wife could try typing 'suspect' words into the address bar.

If you deleted the history, then the results you see in the location bar are from your bookmarks (if bookmarks are selected the Location Bar options). Once you delete the history, they are gone. They won't show anywhere.

---

### Post by waznot on 2010-10-07
Thanks for putting me right lovinglinux.  Does that mean that all the stored objects from the visted pages will no longer be in the tmp, cache, or wherever folder it is they go to? I mean all the information that is kept so it does not have to be downloaded again next time you visit the same page??

---

### Post by waznot on 2010-10-08
Would redlinethecar be able to get his web history from his internet provider? Or his internet security provider if he has one?

---

### Post by unspawn on 2010-10-08
> **redlinethecar said:**
> we all know it's not truly gone unless overwritten.
That's not entirely true. Journalling filesystems do not allow for recovery the way say ext2 did. Some things that will the lower the chance of (partial) recovery are the period between deletion and recovery, having no separate /home partition in combination with how full the partition is and the amount of disk writes the partition has seen since deletion including daemons running in the background, any software installation, if you tried to recover to the same disk, basically anything you do within the diskspace of your account. Immediately powering down after deletion (hold power button, leaving disk flagged "dirty"), booting a Live CD and creating a 'dd' copy of the disk to a physically different medium would have been my preferred approach. From that Live CD (say HELIX) I would run 'photorec' as it has a header / footer signature for sqlite.


> **redlinethecar said:**
> my wife feels that I am hiding things
Some things can't or shouldn't be solved by technology (alone). In this case we're talking about trust. Find out where the distrust comes from and work on that in the most open and honest way. After all you *did* delete the file for some reason...

---

### Post by lovinglinux on 2010-10-08
> **waznot said:**
> Thanks for putting me right lovinglinux.  Does that mean that all the stored objects from the visted pages will no longer be in the tmp, cache, or wherever folder it is they go to? I mean all the information that is kept so it does not have to be downloaded again next time you visit the same page??

If you choose to delete the cache when deleting history, then they are gone too.

---

### Post by The Cog on 2010-10-08
You might be able to recover something from places.sqlite. As it's a database file there is a possibility that many entries have simply been marked as deleted but not overwritten. Try the command 
> strings places.sqlite
You can type "strings " and then drag/drop the file onto the command prompt if that's easier. If there are a lot of strings in the file, perhaps pipe the output through **less** which allows you to scroll through the list:
> strings places.sqlite | less

P.S.
Perhaps better to only show that lines containing "http":
> strings places.sqlite | grep http | less

---

### Post by abraxyz on 2010-10-09
i have a similar problem. lost my sessionstore.js, as well as sessionstore.bak. now i'm desperately trying to recover them. looked around for data recovery tools, but neither of those include .js filetype recovery. i don't know what to do...

---

### Post by unspawn on 2010-10-10
> **abraxyz said:**
> i have a similar problem. lost my sessionstore.js, as well as sessionstore.bak. (..) looked around for data recovery tools, but neither of those include .js filetype recovery.
Run 'file' on one of them will show .js files "magic" is ASCII (English,C,C++) (program) text, meaning you can grep your disk for strings or use tools like photorec etc. Note my previous post: *any disk activity* since deletion will make it harder to (partially) recover items.

---

### Post by abraxyz on 2010-10-10
errm.. excuse me for being a complete noob here.. but.. how exactly do i do that? i also looked up photorec, and it doesn't have .js type amongst supported ones neither : (
much thanks

---

### Post by unspawn on 2010-10-10
> **abraxyz said:**
> it doesn't have .js type amongst supported ones
[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec) says the entries resembling "ASCII text" and "C or C++ program text" are ".txt Text file" and ".c C source file".

---

### Post by abraxyz on 2010-10-10
actually, i didn't get ascii but unicode when running 'file' on sessionstore.js. now i'm completely lost

---

### Post by unspawn on 2010-10-10
Just select ".txt" and ".c" FCOL!

---

