---
title: "WARNING! possible data loss with Ext4"
date: 2009-05-25
forum: The Cafe
---

### Post by dave_blob on 2009-05-25
I don't know if this is the right place to post this, but I have to put it somewhere to warn people.

I JUST SUFFERED MASSIVE DATA LOSS using the new ext4 filesystem in ubuntu!! 

I'm not one for exaggeration or hysteria, i'm only stating this to warn others.

**Backstory: **
I just purchased & installed a brand new 1TB WD hdd. Set it up, formatted it as ext4(using gparted) after reading that its fast and shiny and relatively trouble free, and good for large media files(due to extents).

Spent all of yesterday copying/moving media, isos and photos from my other disks onto this one. 

**Event:**
Ubuntu hard-locked during an intensive period of file copying. Im not sure why, it could because i was copying lots from USB drives and NTFS fuse simultaneously, it could be my graphics drivers... who knows, who cares, lockups happen.

I force-restarted the computer. I then browsed through the new disk in Nautilus. All the directories were empty! #$*&%^*&^!
I tried to access them through the terminal, and i kept getting "i/o error" whenever I tried to 'ls' the folders.
So i assumed the disk was left inconsistent by the hard-reset, which ext4 is apparently quite vulnerable to due to Delayed Allocation. 
Sure, np, thats happened to me before with other filesystems(although not so bad).

So i run e2fsck.ext4 on my disk.

There were so many errors, it took about 5min to fix, and I had to have the -y flag on because there were literally 10s of 1000s of errors found. During this im getting a rage-filled sinking feeling, and im pretty sure my data is ******. 

Sure enough, after fsck, about half(~200gb) of my data was simply missing!!! It was missing random files from random folders, and some cases whole folder trees.


**UNFORGIVABLE.**
That is a horrendously large amount of data loss for a lockup, which can happen quite often (esp. people with ATI cards :p). I understand the tradeoffs in Delayed Allocation, but if that was what caused the disappearance of half my disk, well then im sorry but its a bloody silly tradeoff. 

Lucky for me I still had other copies of my important stuff(photos!), but people could easily lose a lot of important data here. 

I would file a proper bug request, but I have no idea what to put in it as evidence/explanation. But I will do if someone can tell me where to look.

BE CAREFUL WITH EXT4 IN JAUNTY! Dont put anything in it you're not prepared to lose.

I hate to sensationalize, but unless someone can explain to me how else this could have happened to me that isnt ext4s direct or indirect fault, then this post stands.

---

### Post by HermanAB on 2009-05-25
Yup, you use Ext4 at your own risk.  Ext3 is more stable, but I prefer JFS.

---

### Post by 73ckn797 on 2009-05-25
The interrupted actions are probably what has cause the problems. Try not to do so much at one time and let the system operations work and settle in.

---

### Post by dave_blob on 2009-05-26
> **73ckn797 said:**
> The interrupted actions are probably what has cause the problems. Try not to do so much at one time and let the system operations work and settle in.

I realise the crash is what caused the problem. I am just warning people as to the magnitude of data loss a simple lock-up can cause.


I just reproduced the situation.....

In the background I am copying 50gb of stuff from an ide ext3 drive to my new ext4 drive. 
At the same time I attempt to delete a bunch (~1000) of files and folders from the ext4.

Total system lockup after a few min.

Log files show:
```
May 26 13:39:50 dave-desktop kernel: [ 3297.077797] b_state=0x00188029, b_size=4096
May 26 13:39:50 dave-desktop kernel: [ 3297.077799] device blocksize: 4096
May 26 13:39:50 dave-desktop kernel: [ 3297.077801] grow_buffers: requested out-of-range block 18309445582848 for device sdb1
May 26 13:39:50 dave-desktop kernel: [ 3297.077803] EXT4-fs error (device sdb1): ext4_xattr_delete_inode: inode 7168: block 18309445582848 read error
May 26 13:39:50 dave-desktop kernel: [ 3297.078363] __find_get_block_slow() failed. block=168444322381824, b_blocknr=0
May 26 13:39:50 dave-desktop kernel: [ 3297.078365] b_state=0x00188029, b_size=4096
May 26 13:39:50 dave-desktop kernel: [ 3297.078367] device blocksize: 4096
May 26 13:39:50 dave-desktop kernel: [ 3297.078369] __find_get_block_slow() failed. block=168444322381824, b_blocknr=0
May 26 13:39:50 dave-desktop kernel: [ 3297.078371] b_state=0x00188029, b_size=4096
May 26 13:39:50 dave-desktop kernel: [ 3297.078372] device blocksize: 4096
May 26 13:39:50 dave-desktop kernel: [ 3297.078374] grow_buffers: requested out-of-range block 168444322381824 for device sdb1
May 26 13:39:50 dave-desktop kernel: [ 3297.078376] EXT4-fs error (device sdb1): ext4_xattr_delete_inode: inode 7174: block 168444322381824 read error
May 26 13:39:50 dave-desktop kernel: [ 3297.131349] __find_get_block_slow() failed. block=28329604284416, b_blocknr=0
May 26 13:39:50 dave-desktop kernel: [ 3297.131352] b_state=0x00188029, b_size=4096
May 26 13:39:50 dave-desktop kernel: [ 3297.131354] device blocksize: 4096
May 26 13:39:50 dave-desktop kernel: [ 3297.131356] __find_get_block_slow() failed. block=28329604284416, b_blocknr=0
May 26 13:39:50 dave-desktop kernel: [ 3297.131358] b_state=0x00188029, b_size=4096
May 26 13:39:50 dave-desktop kernel: [ 3297.131359] device blocksize: 4096
May 26 13:39:50 dave-desktop kernel: [ 3297.131362] grow_buffers: requested out-of-range block 28329604284416 for device sdb1
May 26 13:39:50 dave-desktop kernel: [ 3297.131365] EXT4-fs error (device sdb1): ext4_xattr_delete_inode: inode 7192: block 28329604284416 read error
```

Well, that does it.
Sorry ext4, but you are hideously unreliable, and I wont be using you again in a hurry.

---

### Post by Dngrsone on 2009-05-26
Well, I'm glad I don't use ext4...

Oh, but then, I **don't try to do everything all at once**.  I guess I'm just one of those old-school guys who have trashed their systems too many times trying to multi-task that I know better now than to rely on the computer to work flawlessly no matter how much I abuse it.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

For those who don't understand sarcasm:  The magnitude of the data loss had more to do with the sheer amount of work you were trying to accomplish at the same time, precipitating in the crash, not in the nature of ext4 itself.

---

### Post by 73ckn797 on 2009-05-26
> **Dngrsone said:**
> Well, I'm glad I don't use ext4...

Oh, but then, I **don't try to do everything all at once**.  I guess I'm just one of those old-school guys who have trashed their systems too many times trying to multi-task that I know better now than to rely on the computer to work flawlessly no matter how much I abuse it.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

For those who don't understand sarcasm:  The magnitude of the data loss had more to do with the sheer amount of work you were trying to accomplish at the same time, precipitating in the crash, not in the nature of ext4 itself.


That is exactly what I was saying. Such a massive movement of data needs to be left alone. Go have coffee or a beer. Eat dinner and let things finish doing what they are doing.

Patience IS a virtue!

---

### Post by Regenweald on 2009-05-26
Ext4 here. + data=writeback even. No crashes, but I don't try as many IO operations. Hope you reported the details in launchpad.

---

### Post by dave_blob on 2009-05-26
Im sorry guys, "dont do too much" is not really an accepable answer. 

Its 2009. I should be able do more than one simultaneous transfer operation without lockups and large data corruption.

---

### Post by Kingsley on 2009-05-26
File a bug report.

---

### Post by aysiu on 2009-05-26
I don't buy this "don't do too much" line either.

The real line should be "don't use Ext4 yet if you're at all worried about data loss."

The data loss in Ext4 issue has been known for quite some time, and that it why Ubuntu is still Ext3 by default in Jaunty Jackalope.

**Further Reading**
[Bug #317781 in Linux (Ubuntu): Ext4 data loss"](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)
[Ext4 data loss; explanations and workarounds](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

---

### Post by 73ckn797 on 2009-05-26
> **dave_blob said:**
> Im sorry guys, "dont do too much" is not really an accepable answer. 

Its 2009. I should be able do more than one simultaneous transfer operation without lockups and large data corruption.


When it reaches the point of things being able to occur in "the twinkling of an eye" then people will still complain. It is human nature to want what I want when I want it. That only leads to people posting complaints of the results of wanting so much so soon.

I hope you find your desired capacity to spin so many plates at one time, in a sense. I, personally, do not find that really accomplishes my desired results in the long run.

Keep in mind that just because it is 2009, it doesn't mean we have figured out how to re-invent the wheel or make a better mouse trap. Do not think that we have yet mastered all that we want to do. I really do not think you feel that way. You will ultimately find that to be a frustrating situation. Not that someday it won't get here but we have not arrived there as of yet.

This is my opinion.

---

### Post by kpkeerthi on 2009-05-26
@dave_blob
If you want the community benefited, file a bug report or supplement the existing bug report with your findings.

---

### Post by 73ckn797 on 2009-05-26
> **aysiu said:**
> I don't buy this "don't do too much" line either.

The real line should be "don't use Ext4 yet if you're at all worried about data loss."

The data loss in Ext4 issue has been known for quite some time, and that it why Ubuntu is still Ext3 by default in Jaunty Jackalope.

**Further Reading**
[Bug #317781 in Linux (Ubuntu): Ext4 data loss"]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781")
[Ext4 data loss; explanations and workarounds]("http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892")


I will not try to sell you on it then (GRIN). I completely agree with you, however.

---

### Post by FuturePilot on 2009-05-26
> **dave_blob said:**
> 
Ubuntu hard-locked during an intensive period of file copying. Im not sure why, it could because i was copying lots from USB drives and NTFS fuse simultaneously, it could be my graphics drivers... who knows, who cares, lockups happen.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824")

And this is why I've gone back to Ext3. The new features of Ext4 are not worth my data.

---

### Post by Tipped OuT on 2009-05-26
> **dave_blob said:**
> 
Its 2009. I should be able do more than one simultaneous transfer operation without lockups and large data corruption.

It's 2009 and we still don't have flying cars! :lolflag:

---

### Post by bigbrovar on 2009-05-26
> **Tipped OuT said:**
> It's 2009 and we still don't have flying cars! :lolflag:

pretty disappointing if i might had

---

### Post by Dngrsone on 2009-05-26
> **Tipped OuT said:**
> It's 2009 and we still don't have flying cars! :lolflag:

I was thinking along the same lines-- where's my holographic storage and brain jack?.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

### Post by SupaSonic on 2009-05-26
> **Tipped OuT said:**
> It's 2009 and we still don't have flying cars! :lolflag:

That does put things into perspective.

---

### Post by collinp on 2009-05-26
EXT4 caches files before actually writing them to the hard disk. This is its fabled speed increase. So when your system hardlocked, everything in the cache disappeared.

Also, expect things like this to happen with something as new as ext4.

---

### Post by xzero1 on 2009-05-26
> I force-restarted the computer.I take it you at least tried ALT-SYSRQ (REISUB) keys before force-restart   correct? 

I appreciate your post. Since I use ext4 this is something to consider. I would recommend posting in the installation and upgrades or general help area.

---

### Post by Pasdar on 2009-05-26
> **dave_blob said:**
> I don't know if this is the right place to post this, but I have to put it somewhere to warn people.

I JUST SUFFERED MASSIVE DATA LOSS using the new ext4 filesystem in ubuntu!! 

I'm not one for exaggeration or hysteria, i'm only stating this to warn others.

**Backstory: **
I just purchased & installed a brand new 1TB WD hdd. Set it up, formatted it as ext4(using gparted) after reading that its fast and shiny and relatively trouble free, and good for large media files(due to extents).

Spent all of yesterday copying/moving media, isos and photos from my other disks onto this one. 

**Event:**
Ubuntu hard-locked during an intensive period of file copying. Im not sure why, it could because i was copying lots from USB drives and NTFS fuse simultaneously, it could be my graphics drivers... who knows, who cares, lockups happen.

I force-restarted the computer. I then browsed through the new disk in Nautilus. All the directories were empty! #$*&%^*&^!
I tried to access them through the terminal, and i kept getting "i/o error" whenever I tried to 'ls' the folders.
So i assumed the disk was left inconsistent by the hard-reset, which ext4 is apparently quite vulnerable to due to Delayed Allocation. 
Sure, np, thats happened to me before with other filesystems(although not so bad).

So i run e2fsck.ext4 on my disk.

There were so many errors, it took about 5min to fix, and I had to have the -y flag on because there were literally 10s of 1000s of errors found. During this im getting a rage-filled sinking feeling, and im pretty sure my data is ******. 

Sure enough, after fsck, about half(~200gb) of my data was simply missing!!! It was missing random files from random folders, and some cases whole folder trees.


**UNFORGIVABLE.**
That is a horrendously large amount of data loss for a lockup, which can happen quite often (esp. people with ATI cards :p). I understand the tradeoffs in Delayed Allocation, but if that was what caused the disappearance of half my disk, well then im sorry but its a bloody silly tradeoff. 

Lucky for me I still had other copies of my important stuff(photos!), but people could easily lose a lot of important data here. 

I would file a proper bug request, but I have no idea what to put in it as evidence/explanation. But I will do if someone can tell me where to look.

BE CAREFUL WITH EXT4 IN JAUNTY! Dont put anything in it you're not prepared to lose.

I hate to sensationalize, but unless someone can explain to me how else this could have happened to me that isnt ext4s direct or indirect fault, then this post stands.

That's why I always tell my wife, "When you want to move something important from one media to another, always copy it, and only when the process is done, delete the initial". I do this on any file system.

Some weeks ago in Win7 I was moving family photos from my desktop to my second partition (I don't even listen to my own advice sometimes). Basically, the files disappeared in between the moving. They never arrived at their new destination. However, I didn't know this. I formatted Win7 because of other bugs, once that was done. A few days later my wife asked, 'where are the pictures'... that's when we figured everything was lost, lol.

---

### Post by Delever on 2009-05-26
"Don't do too much" - NO

Ext4 has to mature and it will be fine though.

---

### Post by gnomeuser on 2009-05-26
Take two things from this:

a) Your proprietary video driver definitely didn't improve the situation, this is why using them is dangerous and unrecommendable. I hope this is what people take from this, anyone who tells you those things are safe are outright lying. If you care the least bit about stability or security, do not use them

b) Your understanding of how filesystems work is lacking, expecting data to be on the drive if you crash during a write operation is expecting the impossible.

There is no way to protect against what happened, a crash changes everything, we can't even do high priority flushing of the cache as the carpet was literally pulled from under us.

If you are worried about your data there are options to do more frequent writes, this will hurt performance considerably though and it still will not fix the problem.

For the record I have been on 100% ext4 for over a year now, it's a very reliable filesystem provided you don't intentionally destabilize it.

---

### Post by Paqman on 2009-05-26
> **gnomeuser said:**
> 
a) Your proprietary video driver definitely didn't improve the situation, this is why using them is dangerous and unrecommendable. I hope this is what people take from this, anyone who tells you those things are safe are outright lying. If you care the least bit about stability or security, do not use them


That's an unrealistic expectation. The vast majority of people are running machines that will need a proprietary driver to get their hardware to function properly.

---

### Post by Duskao on 2009-05-26
I gotta say, the idea of multi-tasking is a funny one really. Sure you can multi-task with so many applications... once again, thats applications. But even when there were single processors multi-tasking was pretty much unheard of. At least the idea of watching a video, zipping a file and using a messenger service while surfing the net unless you wanted to go to a screeching hault. But the problem with this, is that it isn't specified. Sure, you can do all that and more now with multi-core processors, but thats because most applications run off the processor. 

Well, you wouldn't try running two intensive games with one video card would you? Probably not, your asking for brutal performance and a chance to overheat the video card. The same is true with your hard drive. You only have one, and it doesn't matter how fast it is or what file system you use, you likely still only have one, or are using only 1. Plus the idea of deleting something while creating something at the same time on a hard drive is a bad one. Here's another analogy: try filling up a cup while pouring out whats in there at the same time. Basically you are just asking for errors, or worse, like what happened. Plus transferring files is extremely HD, processor and RAM intensive. Don't forget, your computer is only as fast as the slowest part of it, which is generally the hard drive. 

I have had the same thing happen with my computer while using Fat32 and NTFS back when I used windows, but when it happened with windows, more likely then not it would disable the system and I would have to reinstall the OS. 

In my opinion, your lucky that you didn't completely mess up the OS and potentially fry the HD.

Hope things go better for ya in the future.

---

### Post by Delever on 2009-05-26
> **Duskao said:**
> I gotta say, the idea of multi-tasking is a funny one really. Sure you can multi-task with so many applications... once again, thats applications. But even when there were single processors multi-tasking was pretty much unheard of. At least the idea of watching a video, zipping a file and using a messenger service while surfing the net unless you wanted to go to a screeching hault. But the problem with this, is that it isn't specified. Sure, you can do all that and more now with multi-core processors, but thats because most applications run off the processor. 

Well, you wouldn't try running two intensive games with one video card would you? Probably not, your asking for brutal performance and a chance to overheat the video card. The same is true with your hard drive. You only have one, and it doesn't matter how fast it is or what file system you use, you likely still only have one, or are using only 1. Plus the idea of deleting something while creating something at the same time on a hard drive is a bad one. Here's another analogy: try filling up a cup while pouring out whats in there at the same time. Basically you are just asking for errors, or worse, like what happened. Plus transferring files is extremely HD, processor and RAM intensive. Don't forget, your computer is only as fast as the slowest part of it, which is generally the hard drive. 

I have had the same thing happen with my computer while using Fat32 and NTFS back when I used windows, but when it happened with windows, more likely then not it would disable the system and I would have to reinstall the OS. 

In my opinion, your lucky that you didn't completely mess up the OS and potentially fry the HD.

Hope things go better for ya in the future.

In my humble opinion, I should be able to do anything I have a button for. If I can't - please disable a button or tell me. Like apt tells you that you can't run several instances of it at the same time.

There are many services which can both read and write to disk at the same time, so having robust file system is essential. However, if you know that your drivers are not stable, it makes sense to be extra careful, because different file system might not help much.

---

### Post by mihai.ile on 2009-05-26
> **Delever said:**
> In my humble opinion, I should be able to do anything I have a button for. If I can't - please disable a button or tell me. Like apt tells you that you can't run several instances of it at the same time.

There are many services which can both read and write to disk at the same time, so having robust file system is essential. However, if you know that your drivers are not stable, it makes sense to be extra careful, because different file system might not help much.

Well generally I agree with you but there is always the performance trade off. If you use ext4 configured for performance you are already saying that you don't care as much for data loss.

People say to do less, well ok, ext4 crashes if you put too much into it but now I ask:

Don't you think ext4 should be a little smarter and slow down some of the operations so the system would not crash? I personally think this would be the ideal solution for such cases.

---

### Post by Paqman on 2009-05-26
> **Delever said:**
> In my humble opinion, I should be able to do anything I have a button for.

Indeed. Handling the hardware is the job of the OS, not the user. The OS should do it's best to satisfy everything the user tries to do, without creating errors. That's pretty much its whole job.

For the last few decades that has meant handling multitasking.

---

### Post by blueturtl on 2009-05-26
To all of those who say it's the guy's fault for trying to do too many things at the same time:

A multiuser multitasking operating system is supposed to be able to handle multiple things at the same time. Granted, each added process will slow the others down, but it should never ever cause lockups or data loss.

Granted, it's a little foolish to try so many file copy operations at the same time since the hard disk is the slowest component in any system. It will pretty much take exactly the same amount of time to do four big file transfer operations simultaneously as it takes to do them one after another.

The real issue IMO is that the OP's system crashed. File systems deal with these situations differently. There was nothing unexpected about what happened, since EXT4 is designed to work this way! The root cause for the data loss wasn't EXT4, it was the combination of unstable kernel/driver or possibly bad hardware.

In conclusion based on what I've read so far I would say that combining bleeding edge/unstable software such as Ubuntu with a file system like EXT4 may not be wise. If you have solid good hardware and feel that [distro-of-choice] is not crash prone, then rolling out with EXT4 shouldn't be a problem.

---

### Post by VastOne on 2009-05-26
Very interesting thread to say the least...

I use ext4 extensively on 15 production machines with 0 data loss running everything from payroll to water and sewer administration for the city that I work for. Are we lucky or just patient? 

For all the talk about what these clunkers of computers should be able to do or not do, we are NOT in a time of "it should do what I want when I want" or "if I push a button it should just do it".  To me this speaks more of a society not appreciating what it does have...(very different thread, sorry)

There is no intelligence here just 01010101, and only from the users fingertips back is there any thought capable of a common sense process or right from wrong.  Do we want a button that says "Are you sure" (NOT ME) or should we read all we can about a new product and take into considerations the risk/reward factor and OWN the responsibility of such decisions?

I will conclude this soap box sermon with an opine...We are just scratching the surface with what these "toys" can do and we are basically the bleeding edge for Debian testing...

On both accounts, I enjoy the process...Where we were (W95 vs OS/2) where we are (this discussion in all it's brilliance) and where we will be ... Hopefully (please) a simple command that tells us Do not hurt one another...

---

### Post by aysiu on 2009-05-26
[quote=VastOne]I use ext4 extensively on 15 production machines with 0 data loss running everything from payroll to water and sewer administration for the city that I work for. Are we lucky or just patient?[/quote] I don't think anyone has suggested that use of Ext4 necessitates data loss or that data loss will occur frequently.

But if you are the type to ever complain about data loss, then you should use Ext3 just to be safe.

You're taking a risk and willing to accept that risk, and you haven't experienced any adverse effects. Good for you.

---

### Post by calrogman on 2009-05-26
Here's an easy fix for you, use Ext4 for /, and Ext3 for /home.

---

### Post by SomeGuyDude on 2009-05-26
> **dave_blob said:**
> Im sorry guys, "dont do too much" is not really an accepable answer. 

Its 2009. I should be able do more than one simultaneous transfer operation without lockups and large data corruption.

Every time I try to move a buttload of files my CPU usage spikes. If I don't underclock my CPU it eventually overheats.

Here's an experiment, see what happens if you try to render a movie, compile a big piece of software, and backup your entire home folder to an external drive. See how well your proc likes that.

I've been on ext4 for a while now and it's been great.

---

### Post by SomeGuyDude on 2009-05-26
> **blueturtl said:**
> A multiuser multitasking operating system is supposed to be able to handle multiple things at the same time. Granted, each added process will slow the others down, but it should never ever cause lockups or data loss.

See my above post. Some things DEVOUR proc power. Sure you can have GIMP, Firefox, Pidgin, Sonata, and a handful of other apps running no problems, but see what happens when you try and layer CPU-intensive operations like video rendering, compiling, and let's say you want to play Crysis at full-res while you're at it. Good luck.

---

### Post by VastOne on 2009-05-26
> **aysiu said:**
> I don't think anyone has suggested that use of Ext4 necessitates data loss or that data loss will occur frequently.

But if you are the type to ever complain about data loss, then you should use Ext3 just to be safe.

You're taking a risk and willing to accept that risk, and you haven't experienced any adverse effects. Good for you.

Verbatim of what I said in rest of my post, thanks for the concurrence. :D

---

### Post by anaconda on 2009-05-26
> **HermanAB said:**
> Yup, you use Ext4 at your own risk.  Ext3 is more stable, but I prefer JFS.

My words EXACTLY..

---

### Post by mcduck on 2009-05-26
> **SomeGuyDude said:**
> Every time I try to move a buttload of files my CPU usage spikes. If I don't underclock my CPU it eventually overheats.

Here's an experiment, see what happens if you try to render a movie, compile a big piece of software, and backup your entire home folder to an external drive. See how well your proc likes that.

I've been on ext4 for a while now and it's been great.
If your CPU overheats because of running at 100% you definitely have a cooling problem. Really. 

Any CPU should be able to run at 100% use for weeks, if not months, without any problems. If this is not the case with your machine clean it, get a proper cooler, or return it to where you bought it because it's faulty.

Edit: That being said, trying to do multiple disk read/writes is a different thing. Of course it should work without problems, but you really don't get any benefit from it. Writing the stuff one file at a time takes exactly the same time, if not less, than trying to do it all at the same time.

---

### Post by Delever on 2009-05-26
> **SomeGuyDude said:**
> Every time I try to move a buttload of files my CPU usage spikes. If I don't underclock my CPU it eventually overheats.

Here's an experiment, see what happens if you try to render a movie, compile a big piece of software, and backup your entire home folder to an external drive. See how well your proc likes that.

I've been on ext4 for a while now and it's been great.

Good cooling helps - I tried :)

---

### Post by anaconda on 2009-05-26
> **dave_blob said:**
> Im sorry guys, "dont do too much" is not really an accepable answer. 

Its 2009. I should be able do more than one simultaneous transfer operation without lockups and large data corruption.

Yep, you should

Usually more than one simultaneous transfer work just fine, BUT it is slower. And doing the jobs one at the time is faster AND lighter for the read/write heads of your hd.

Which do you think is faster
Read a chunk of data -> write it to the destination, read next chunk (right next to the first one) and write it to the destination(to right where the write head already were. etc.

OR

Read a Small chunk of data from place1, move the read head, read another small chunk, move the read head and write a small chunk, move the write head, write some more, move the write head...

Easy to test too. by listening your hd noise. 
Just have 5 copies of ubuntu isos, and select them all in nautilus and copy them to another disk....

Or select each one separately and drag it to the destination disk one by one, while the previous ones are still copying.
You will hear the read/write heads jumping from place to place.  And the copying is slower this way.

The problem is partly due to ubuntus stupid default settings. Copy command copies files with too small chunks at a time (was it something like 2kb?). With the amount of RAM nowdays the chunks could easily be tens of MB:s and then the read/write heads wouldn't have to jump as much, and both copy commands would be about as fast.

---

### Post by Skripka on 2009-05-26
> **dave_blob said:**
> I don't know if this is the right place to post this, but I have to put it somewhere to warn people.

I JUST SUFFERED MASSIVE DATA LOSS using the new ext4 filesystem in ubuntu!! 



_***It is a KNOWN issue that has been reported with workarounds MANY times everywhere on the internet- FOR MONTHS.  Yes.. MONTHS***_

Sorry you didn't see the warnings LOTS of folks have posted.


**[B]_*It IS NOT a problem with Ext 4*_**[/B]


The problem is mainly with applications that are not written with delayed allocation in mind, and a hard reboot/shutdown is used or occurs.

---

### Post by HappyFeet on 2009-05-26
No problems here with ext4. Then again, I'm not worried about it, as I've never kept my personal files on the same drive as my OS. I don't trust any OS with my personal stuff.

---

### Post by Kareeser on 2009-05-26
If delayed allocation introduces problems like this, then I really think ext4 should re-think their underlying concept... it doesn't necessarily seem like a stable foundation to build a file system out of.

As for too many writes/reads at the same time - a hard drive should be able to intelligently handle all of those requests in a queue, and process them in a priority sequence. Running multiple reads and writes shouldn't overload the hard drive, in theory...

---

### Post by ghindo on 2009-05-26
> **Kareeser said:**
> If delayed allocation introduces problems like this, then I really think ext4 should re-think their underlying concept... it doesn't necessarily seem like a stable foundation to build a file system out of.From my understanding of the issue, ext4 acts as such because that's how POSIX specifies a filesystem should act.

---

### Post by imbjr on 2009-05-26
The electricity in this house has recently started suffering from being cut by something unknown overloading the fuse.

This did concern me when I decided to format the drive to ext4, but so far I have not had problems caused by sudden power-downs, which occur perhaps once a fortnight.

I take it you consider your destination drive healthy in all other respects?

---

### Post by Polygon on 2009-05-26
> **Kareeser said:**
> If delayed allocation introduces problems like this, then I really think ext4 should re-think their underlying concept... it doesn't necessarily seem like a stable foundation to build a file system out of.

As for too many writes/reads at the same time - a hard drive should be able to intelligently handle all of those requests in a queue, and process them in a priority sequence. Running multiple reads and writes shouldn't overload the hard drive, in theory...

its not ext4's fault. its up to the program to tell the filesystem to sync after it does any writes to a file, like when its closing, rather then just assuming that it will sync every 5 seconds.

---

### Post by Kareeser on 2009-05-26
Polygon:

Ah, I see... but what about the original problem, that of a OS freeze (for whatever reason). In that case, any data in limbo (either in limbo or queued to be written) would be lost...

I'm sure THAT is part of the ext4 concept, right?

(To be clear, I'm not trying to be rude, I just want to understand)

---

### Post by whoop on 2009-05-26
If a crash occurs during movement of a large bunch of files data loss will occur on many filesystems. If you are moving files (especially many or large ones) I don't know how extensive delayed allocation will be utilized. Not that extensive I think, even if the tools don't fsync() that often.

---

### Post by xpod on 2009-05-26
> WARNING! MASSIVE DATA LOSS with ext4

> Lucky for me I still had other copies of my important stuff(photos!), but people could easily lose a lot of important data here.


So no "MASSIVE DATA LOSS" at all in reality.
I think this thread title needs amending.
I`ve used ext4 myself for around 6 months and i do so in the complete knowlage there may be problems along the way.That much i do understand.

---

### Post by xzero1 on 2009-05-26
> its not ext4's fault. its up to the program to tell the filesystem to sync after it does any writes to a file, like when its closing, rather then just assuming that it will sync every 5 seconds.Does this make sense? Why not put a common behavior that should be enforced because of inevitable crashes, program bugs etc into the file system. Is this what the linux community wants in their operating system? I doubt that.

---

### Post by khelben1979 on 2009-05-26
> **dave_blob said:**
> Im sorry guys, "dont do too much" is not really an accepable answer. 

Its 2009. I should be able do more than one simultaneous transfer operation without lockups and large data corruption.

Agreed.

Go back to EXT3.

---

### Post by lovinglinux on 2009-05-26
> **imbjr said:**
> The electricity in this house has recently started suffering from being cut by something unknown overloading the fuse.

This did concern me when I decided to format the drive to ext4, but so far I have not had problems caused by sudden power-downs, which occur perhaps once a fortnight.

I take it you consider your destination drive healthy in all other respects?

I'm also experiencing electricity issues here. I had several power shut downs since I installed Jaunty and none of them resulted in data loss, including when downloading torrents. I never had a power failure while moving files tho. Nevertheless, whenever the data being transfered is important, I never move them, but copy the files then delete them from the source after completion and verification, regardless of the file system in use.

> **xpod said:**
> So no "MASSIVE DATA LOSS" at all in reality.
I think this thread title needs amending.
I`ve used ext4 myself for around 6 months and i do so in the complete knowlage there may be problems along the way.That much i do understand.

I agree. The title sounds like TV news headlines. When I read it, I thought the OP lost everything on the machine, including the OS files. Users should be advised of possible issues of ext4, but the data loss here could happen o any file system and could be avoided with common sense and safe practices (as it was).

---

### Post by dave_blob on 2009-05-26
> **gnomeuser said:**
> Take two things from this:

a) Your proprietary video driver definitely didn't improve the situation, this is why using them is dangerous and unrecommendable. I hope this is what people take from this, anyone who tells you those things are safe are outright lying. If you care the least bit about stability or security, do not use them

b) Your understanding of how filesystems work is lacking, expecting data to be on the drive if you crash during a write operation is expecting the impossible.

There is no way to protect against what happened, a crash changes everything, we can't even do high priority flushing of the cache as the carpet was literally pulled from under us.

If you are worried about your data there are options to do more frequent writes, this will hurt performance considerably though and it still will not fix the problem.

For the record I have been on 100% ext4 for over a year now, it's a very reliable filesystem provided you don't intentionally destabilize it.

a) Too bad, lots of people have to use propriety drivers because the OS drivers cant do things that they need (eg TV out, have decent 3D performance). Many people are willing to take the tradeoff for a loss of stability to be able to use their computer the way that they want to, to get it to do the things they bought it for. 
FTR, im using the ose radeon drivers at the moment, because of issues with the ATI ones, so it wasnt even that - i was just pointing out that to proprietry radeon users, crashes can be non-rare :p.

b) I understand the filesystem plenty well enough. As I said in my OP, I understand the tradeoffs involved in delayed allocation, speed vs windows of dataloss. I understand that I am vulnerable to lose whatever was written in that window, which at 1 min could be about around a gig max in a copy situation. I accept that tradeoff. 

What I dont accept is that, in a crash, the filesystem can hose huge chucks of itself that were already written long ago - that it can corrupt the filetable of stuff that should have been flushed hours ago.

c) It now looks like the filesytem itself caused the lockup:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824)

As I was able to reproduce it by deleting a large tree of files. 

What am I supposed to do if the filesystem itself is the destabilizer?

---

### Post by dave_blob on 2009-05-26
> **Skripka said:**
> _***It is a KNOWN issue that has been reported with workarounds MANY times everywhere on the internet- FOR MONTHS.  Yes.. MONTHS***_

Sorry you didn't see the warnings LOTS of folks have posted.


**[B]_*It IS NOT a problem with Ext 4*_**[/B]


The problem is mainly with applications that are not written with delayed allocation in mind, and a hard reboot/shutdown is used or occurs.
I saw the warnings about some apps not losing little files due to frequent writes, about files being truncated.

I did not see any warnings that a lockup could cause it to mess up the filetable so much that you lose *hundreds of GB* of long-ago commited files.

---

### Post by dave_blob on 2009-05-26
To address other points that have been made:

I did not try the ALT+SYSREQ+K combo to restart X, because i couldnt @#@#en remember it! :p I had to look it up now for this post - which i obviously couldnt do when locked up.

@the multitasking haters:
Yes, I realise that doing multiple simultaneous actions on the same HDD is actually slower than running them in series. However, I had a lot of file organising to do - I was basically queing up many operations so that I could go off and do other things while waiting for them to complete, so that I didnt have to keep coming back to the PC. Not unreasonable IMHO.

@the title haters:
yeah its probably a bit over the top. However, 200gb is a massive amount of data, and it was lost! :p Title stands. 
Also I lost a bunch of movies that I didn't have space for elsewhere, but yeah I don't mind that so much.


@bug report filers:
I want to file a report, but is the info I posted in the first page enough for diagnostics? I dont want to post a bug that just gets closed for lack of evidence etc.

---

### Post by xpod on 2009-05-26
> Title stands. 

You forgot the word "corrected";)

---

### Post by VastOne on 2009-05-26
> **xpod said:**
> You forgot the word "corrected";)

:mrgreen:

Good one

---

### Post by jwbrase on 2009-05-26
> **dave_blob said:**
> I saw the warnings about some apps not losing little files due to frequent writes, about files being truncated.

I did not see any warnings that a lockup could cause it to mess up the filetable so much that you lose *hundreds of GB* of long-ago commited files.

Well, there's always some chance of data corruption to existing files on any FS if you get a power loss during a write. Ext4 is on the cutting edge, and the cutting edge is not a safe place to keep critical data.

---

### Post by aysiu on 2009-05-26
Yeah, I changed the title. It was a bit sensationalist. I kept the word *WARNING!* in. But, really, Ubuntu 9.04 still defaults to Ext3 and with good reason.

If you choose to use Ext4, you should do your homework.

---

### Post by Regenweald on 2009-05-26
Hope everyone does their homework for BTRFS :) See you guys there next year hopefully ?

---

### Post by bshosey on 2009-05-26
I have had system lock ups in different OSes and loss data due to that.
That said I would be more interested in what made the system lockup. It is a true shame that happened and I hope the devs can help prevent this from happening again.

---

### Post by Noah_Kapiolani on 2009-05-26
After reading from beginning to end of this thread, I thank you all. From the dramatic to the blamers to the givers of calm logic.  For my system, I will have the boot drive use ext4 because it is supposed to be faster and. hey,  at least I have a free install disk and AptonCD and try some partition cloning app (suggestions?). For all personal data, i'll use a 1TB sata for data on ext3 because data loss really sucks. Oh, and all hard drives fail so I have to have another copy put away right? Yep.  Learned that the hard way from two shiny black WD external USB hard drives that failed, one in less than a year and the other in less than two.  Anywho, what I don't understand is why processors, ram, and motherboards have progressed by leaps and bounds since my first year putting one together to today yet hard drives mostly just get bigger and only slowly get significantly faster.  My fresh PC build flies in comparison to anything else I've owned or had to work with, but just try and copy over more than one huge dataset at a time and watch the dog gone thing slow down to a crawl for any other requests that require hard disk access.  That part of the PC experience has not changed much in a decade.  We stand on the shoulders of giants yet we are not nearly as advanced as we think we are! In fact, what is really scary, is that the more we know, the more we know what we don't know!  Take the study of medicine or flu virii, for example.  On the other hand, perhaps that having an OS that is tied to only one disk is the problem or the key to a workaround.  Perhaps if Ubuntu seperated the user space physically by having one disk exclusively for the system and one for the user that could potentially minimize a access conflict and increase performance?  Why can't Joe sixpack que up a long to do list? Perhaps the default could be changed from having Ubuntu trying to do them all at once and slowing things down to a crawl and making it more likely to crash under duress.

---

### Post by ranjhith on 2009-06-14
I'm a Victim too.

A system freeze happened when I did a deletion of a torrent+data in Deluge (Bittorrent client). A restart didn't take me to the desktop after entering the login credentials. /var/log/syslog reported read errors in FileSytem which I repaired with fsck manually.

Another reboot took to a desktop which looked alien to me. All my GNOME settings (including wallpaper) just vapourized. So as my Firefox settings (including all addons). That didn't stop there. A complete folder where all my downloads go, cudn't be traced! Some videos in another folder are missing.

EXT4 seems to do some delayed allocation. So, I understand that files under *updation* can go missing on a hard reset. But, I cudn't understand why my _complete_ *downloads* folder wud go missing! 

To HELL with it.

Can someone enlighten on this *missing folders* phenomena? Can this be explained with EXT4 behaviour?

---

### Post by T.J. on 2009-06-20
Hi everyone,

Just a little common sense here.  Ubuntu is very good but no software is ever perfect, and I must remind you that the non LTS Ubuntu releases are based on a snapshot of Debian unstable that is discarded in favour of a new one every six months.

I honestly have to ask: "What do you expect?"

Setting that aside, Ext4 follows the POSIX specs, as it as meant to.  The problem is that a number of open source developers working on Linux have become used to Ext3's behaviour of data commits, and taken them as a standard.  *This is very bad.* Linux behaviour is *not* the default for all POSIX systems. They really need to read and follow the POSIX specification! It is the only specification that ensures compatibility between all of the UNIX/open source projects around the world that Ubuntu is assembled from.  Doing anything else causes problems like this, and makes software harder to port.

If it makes anyone feel any better, do the sensible thing - BACKUP YOUR DATA! 

Just so, Theodore Tso (the Ext3/4 maintainer) has already committed a patch for the Linux crowd who want the old Ext3 behaviour, and it was released in 2.6.30.  Ubuntu hasn't updated kernels yet.

Going a bit off topic here - but based on the comments made in this thread, the problem was noted with video lockups. Ubuntu 9 has two things that combine to give a lot of problems with X and video drivers.  

1) Xorg disbled the keyboard shutdown for X upstream - a very bad idea IMHO
2) Usplash gives some people trouble when trying to switch consoles to shutdown X without a reset.

I'd suggest that if you are going to use Ext4 on Ubuntu Linux that you self update to the new kernel, or at the very least  - enable the X keyboard shutdown, and uninstall usplash.  That way, at least you have a chance to shutdown your Ubuntu system cleanly if the video goes wonky.

---

### Post by evermooingcow on 2009-06-20
Couple of months back I had some data corruption too. I was using EXT3 on Debian stable (how much more stable can you get?) and as far as I know the systems involved did not crash and there was no excessive I/O involved either.

I had a Debian stable file server hosting an NFS root to a client also running Debian stable and all I did was shut down the client. It shutdown without error but when I tried to boot up it threw up an error basically indicating unreadable root and NFS failure. After inspection I found that the exported directory on the server was inaccessible due to data corruption. I ran fsck and it ended up wiping out my entire NFS root directory.

I'm not really sure what caused it. I'm pretty sure the cause is NFS related - perhaps wrong export options on the server or mount options on the client..but I had a similar setup with OpenSuse not too long ago and never ran into such problems. Maybe I was lucky (or unlucky)?

I don't trust EXT4 and I don't trust EXT3 either. Stuff just happens sometimes regardless of system.

I do run EXT4 now but I keep external backups in EXT3. I've always ran a dedicated file server but since I had issues I cut down on applications and just run NFS in read-only, SSHD and rtorrent. The less I have the less there is that could potentially fail right?

---

### Post by T.J. on 2009-06-20
> **evermooingcow said:**
> 
I had a Debian stable file server hosting an NFS root to a client also running Debian stable and all I did was shut down the client. It shutdown without error but when I tried to boot up it threw up an error basically indicating unreadable root and NFS failure. After inspection I found that the exported directory on the server was inaccessible due to data corruption. I ran fsck and it ended up wiping out my entire NFS root directory.


It's off topic, and I apologize to everyone, but to answer this....NFS is a network file system, but depending on the version, options, and the underlying filesystems, you can have serious potential for data corruption if it is mounted in root or write mode.  You should always verify NFS is unmounted before you shutdown, and never, ever mount write to an NFS client where it can be modified by any utilities unless you know EXACTLY what is going on.

If you want reliable read and write for multiple clients at the same time, try GFS or another serialized filesystem instead.  If we need to discuss it, we should start a different thread.

---

### Post by T.J. on 2009-06-20
> **ranjhith said:**
> I'm a Victim too.

Another reboot took to a desktop which looked alien to me. All my GNOME settings (including wallpaper) just vapourized. So as my Firefox settings (including all addons). That didn't stop there. A complete folder where all my downloads go, cudn't be traced! Some videos in another folder are missing.

Can someone enlighten on this *missing folders* phenomena? Can this be explained with EXT4 behaviour?

I can't explain everything, but the loss of some settings might be attributed to a hard reset with an Ext4 filesystem.  Gnome keeps dozens of little files and if they are changed before a commit and you press the reset button - poof.

Some lazy programmers may not be in the habit of using a system call such as fsync() to be positive the important data is saved immediately. This is a known issue.  Hopefully, we will update to 2.6.30 soon, where this is problem can be addressed.

---

### Post by Sepanderi on 2009-07-10
> **xzero1 said:**
> I take it you at least tried ALT-SYSRQ (REISUB) keys before force-restart   correct? 

Whoa, I had no idea about this key combination, so I had to google a bit more about it and then obviously try it out on my virtual machine. Gotta remember this in case I run it to trouble. :D

A list of other useful commands as well: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

