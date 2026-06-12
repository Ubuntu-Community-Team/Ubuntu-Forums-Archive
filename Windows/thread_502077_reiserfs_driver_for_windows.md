---
title: "reiserfs driver for windows"
date: 2007-07-16
forum: Windows
---

### Post by rmanni on 2007-07-16
Hi.

I'm looking for reiserfs driver for windows (2k). If there's no such thing, it would even be good to have a program from which I can access my reiser partition. I don't need write support, only read support.

I've tried the followings, but none of them is working: 
  - rfsd
  - crossmeta's driver
  - rfstool (not a driver, but also not working...)
  - ltools (not a driver, could list ext2/3 directories, but also not working for reiser...)

Rfstool was the best: found the partition (autodetect), but could not list the directories on it. Read violation or such occurs with every of them. It must be because of some windows updates, i think, because some years ago I used a tool to access my drive.

I think there's a solution because I've read on wikipedia ([http://en.wikipedia.org/wiki/Comparison_of_operating_systems](http://en.wikipedia.org/wiki/Comparison_of_operating_systems)) the folowwing next to the windows section:

"3rd-party drivers support ext2, ext3, reiserfs9, and HFS"

OK, does anyone uses such a thing?? Any experience?

The Manni

---

### Post by Imsati on 2007-08-10
Late to respond, but...

[http://www.teslacore.it/sssup1/reiserfs.html](http://www.teslacore.it/sssup1/reiserfs.html)

[http://yareg.akucom.de/](http://yareg.akucom.de/)

One of those two maybe?

--Jay

---

### Post by rmanni on 2007-08-11
> 
[http://www.teslacore.it/sssup1/reiserfs.html](http://www.teslacore.it/sssup1/reiserfs.html)

[http://yareg.akucom.de/](http://yareg.akucom.de/)

One of those two maybe?


Thanks for your reply, but...

The first one I never heard of, and I will test it, but I do not think will be much use, because it is an initial release and the project has been dead since that for 5 years. But I will try, anyway. But I think it is a "relativly" new problem (in 2-3 years) caused by one of the windows update packs.

The second one, yareg is just a gui for rfstool, which is not working, as I have written it before.

Anyway. Does it (does anything) work for XP/Vista? Can anyone read reiser under _a currently supported_ windows? Why is that nobody is interested in that? Everybody is running windows in virtual machine or what?

---

### Post by toupeiro on 2007-08-11
hmm, I don't know about riser specifically.  Can't say the scenario has ever come up.  But, I would say your best bet (if possible) is to get the data off of your reiserfs drive/partition, and repartition to something with a little more compatibility.  You could temporarily slave that drive to another machine with native reiserfs support and transfer via SMB or NFS  (or FTP for that matter), or use an ISO flavor of linux like knoppix or damn small linux, boot up and transfer the data that way.  I don't know what your circumstance is.  Reiser is kinda known for crashing and burning harder than the other filesystems, but has much better performance than ext/2 and ext/3 which is why people go for it from a performance perspective.  Personally, if you are not doing 7,200K - 10K+ drives, or doing some database hosting,  there is little point in maximizing your filesystem with riserfs anyway.  You'd be saving yourself some future headaches in working towards moving off of it.  Especially interoperating with Windows.  Maybe something out of this Novell Microsoft cludge will reveal better tools like this (isn't riserfs still what suse pushes pretty hardcore?)  but until then you are pretty limited in your options I think.  

##edit## 
I IM'ed a buddy of mine and he said he had sucess with rfsd and ltools in the past, but if the riserfs journal is messed up that it will not be readable with anything.  You might have to run fsck or something equivalent  against it first in an OS that can natively support it.

Best of luck to you!

---

### Post by Kevin Patel on 2008-05-29
I dont know about a driver for reiserfs, but i have been using Yareg (along with rfstools) in windows vista and it works just fine.No write support , but i can easily copy files from my reiserfs partition.

---

### Post by rmanni on 2008-05-30
> **Kevin Patel said:**
> I dont know about a driver for reiserfs, but i have been using Yareg (along with rfstools) in windows vista and it works just fine.No write support , but i can easily copy files from my reiserfs partition.

Sorry, I can not try it out anymore, I solved the problem with teaching my girlfriend how to use linux :)
Anyway, I have not found solution, maybe rfstools is still working for some configurations, for mine it did not. But maybe by that time they solved the problem anyway. I do not know.

Robert

---

### Post by grrregistration on 2008-07-26
Can someone post the Yareg files? The official website seems to be down...

---

