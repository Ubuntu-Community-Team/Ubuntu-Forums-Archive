---
title: "Copy queue - wishlist for Ubuntu 8.04"
date: 2007-11-29
forum: Ubuntu Brainstorm
---

### Post by makeyre on 2007-11-29
There's an excellent suggestion I read about on reddit this morning ([http://programming.reddit.com/info/61q9n/comments/](http://programming.reddit.com/info/61q9n/comments/)) called a copy queue: [http://breakthesystem.org/2007/a-proposal-to-os-makers/](http://breakthesystem.org/2007/a-proposal-to-os-makers/)

What would it take to get this into Ubuntu 8.04, and where should I put this suggestion to get it considered as part of the default install?  Does this seem like a job for a separate application or as part of GNOME/KDE?

---

### Post by Nano Geek on 2007-11-29
Ideas for future Ubuntu releases should be posted in the [Ubuntu Idea Pool]("http://ubuntuforums.org/forumdisplay.php?f=306").

---

### Post by rebegin on 2008-02-28
has anyone got info about this if it had been implemented or not?

---

### Post by smartboyathome on 2008-02-28
I don't think it has, but doesn't glipper do something similar?

---

### Post by rebegin on 2008-02-28
i'm actually using glipper, but this one is a clipboard-handling program :D is there an other prog. with the same name?

---

### Post by 23meg on 2008-02-28
It's been implemented as part of the gvfs-enabled Nautilus. The UI has some room for improvement though.

[http://ubuntuforums.org/showthread.php?t=676747](http://ubuntuforums.org/showthread.php?t=676747)

---

### Post by rebegin on 2008-02-28
for me it seems to be only queuing visually the threads displaying them in one window, but not to queue the threads really...i hope you understand what i mean :D

edit: it might do the thing i mean. i'm going to try it now. thanks

> **23meg said:**
> It's been implemented as part of the gvfs-enabled Nautilus. The UI has some room for improvement though.

[http://ubuntuforums.org/showthread.php?t=676747](http://ubuntuforums.org/showthread.php?t=676747)

---

### Post by 23meg on 2008-02-28
Do you mean not starting the next operation before the current one is finished?

---

### Post by rebegin on 2008-02-28
> **23meg said:**
> Do you mean not starting the next operation before the current one is finished?

yes, exactly!
edit: so could you please inform me if it is doing this as well?

---

### Post by 23meg on 2008-02-28
It doesn't. But is there a real use case where you wouldn't want it to be asynchronous? If so, please file a bug.

---

### Post by rebegin on 2008-02-28
an example (it describes the same as my problem, sorry to quote but it's faster, and grammatically more correct than mine would be):

"Sometimes when a friend visits me, I want to copy some files from ~/Music/PublicDomain and some from ~/Music/CreativeCommons and some from ~/Movies/OnlyLegalVideosHere over to their USB drive.

Or sometimes I want to get 13 different Linux ISOs from my file server.

I usually end up having 10 or more copy-jobs open at once,"

....

"So I’d like to suggest an advanced form of the copy dialogue: Add a copy queue. What I want is something like this:

I copy a file somewhere, and while I see the little progress bar window, I can simply drag another file or folder onto the bar, adding it to its queue. **The files will then be copied one after the other**."

from:
[http://breakthesystem.org/2007/a-proposal-to-os-makers/](http://breakthesystem.org/2007/a-proposal-to-os-makers/)

sometimes i have to collect stuff to a USB drive from 15-20 directory and that slows down really the speed....

> **23meg said:**
> It doesn't. But is there a real use case where you wouldn't want it to be asynchronous? If so, please file a bug.

---

### Post by pableu on 2008-05-16
I would also really like this feature. [Teracopy](http://www.codesector.com/teracopy.php) for Windows implements exactly this.

It's just in the nature of harddisks that parallel access isn't too fast.

---

### Post by CrazyGuy123 on 2008-05-16
If anyone wants to help out, could you do some tests to show how much it could improve speed if the copies where sequential (one after the other).

I suspect that if the kernel is doing a good job of scheduling IO, copying two in parallel should be FASTER, particularly for directories of many files.

---

### Post by watricky on 2008-06-01
I have a simple example from past experience. I can do some tests as well with some real-world values. And no, the kernel is NOT going to miraculously overcome my hardware's limitations. :P

I have 3 partitions (a+b+c) on 1 physical hard disk and 2 additional hard disks with a single partition on each (d+e). I have 2 additional computers on the network (Y+Z).

If I start a copy operation from d to disk a it does sequential seeks on d and sequential writes to a. If while this is happening I start a copy from e to Y, the same will occur. Both will run at maximum hard disk speed since there is no conflict of resource requirements. Let's assume for the time being that the network is gigabit, the networked computers have no speed issues and that the disks can read or write at 40MB/s.

If I start a third copy operation from Z to c, the first hard disk will have 2 asynchronous operations on it.
Writes to a and writes to c. The problem is the seek times on the hard disk. The disk is no longer going to be doing sequential writes. Every 256Kb, for example, the hard disk is going to quickly have to do a seek between the 2 partitions. The *total* operational speed of the first disk will be well below 40MB/s. Seek times are measured in milliseconds. From the CPU's point of view, a millisecond is an ETERNITY of wasted time.

This last operation is one that could be queued to occur *after* the copy from e to a is complete. Then the speed will stay at 40MB/s throughout both copy operations.

Real-world examples such, as given by rebegin above, have similar issues. Partitioned disks are where it is most prominent. 13 separate threads is a *lot* of seeking regardless of partition setup.

For my Windoze machine I've just found an app called teracopy. I was using Total Copy and I was pausing operations manually and then resuming them appropriately for optimum results. The main time I found this necessary was when copying media to or from a portable hard disk or over the network.

(edit) Teracopy (for Windows) does what is needed however its interface is *very* lacking. Plus you can't specify when you want an operation to be asynchronous anyway.

---

### Post by watricky on 2008-06-01
Real-world results:

files: 5 ISOs, all approximately 700MB each, copying from portable HDD to my PC.

Sequential/Synchronous: Select all 5 files, copy/paste: 2m, 19 seconds, +- 25MB/s

Parallel/Asynchronous: Select 1 file, copy/paste, select next, copy/paste, end up with 5 separate copy windows; 9m, 1 seconds, +- 6MB/s

---

### Post by billenbois on 2008-06-04
The issue with this feature is in my mind the UI.
You're copying a 4GB file and oh, suddenly you want to copy a 5mb file.
Of course, you don't want it to be queued and wait for the 4GB to be copied.

So you need a little button to unqueue it. Which is not very simple looking for users. They might also just never bother to click the button, and wait 4H for the 4GB file, and complain about how nautilus sucks :)

Another issue:
you copy a file from hard drive A to B.
now you start another copy from hard drive C to D.
this copy shouldn't be queued.

Likewise, what about copying from A to B and A to C where A and C are super fast drives and B is slow ? You would need the system to detect that and either make a "best decision" (calculate copy time and unqueue adequately) either the user to decide what to queue by clicking buttons

All in all this is more complicated than it seems, I wish someone would either do a very good "best decision" algorithm either find a more simple solution :P

The above problems are the answer to the question "why its only available are third party products and not integrated into the system directly" imo

---

### Post by yelo3 on 2008-06-04
the best thing is the button to en-queue! and parallel by default

---

### Post by CrazyGuy123 on 2008-06-05
Well from the results posted it's clear the core of the problem is the kernels IO scheduling,  When two copy operations are trying to read/write data from the same source the kernel should schedule it as if it were a low priority bulk transfer.  As such, block sizes should be huge (eg. 64MB for hard disk copies) such that seek times are pretty much eliminated.  When a process is IO bound for write operations the write cache should also be allowed to expand almost limitlessly on non-removable media.

In the case of copying thousands of small files, tens or hundreds of files should be copied simultaniously since then the disks command queueing and reordering comes into play and can reduce the number of seeks required.  In an ideal case copying a folder tree containing 1,000 files averaging 64kb could take ~10 secs (1001 seeks + ~70Mb read), but due to limitations in the design of linux this isn't the case.

The solution is to optimise the backend (kernel, copy process) rather than provide a nice UI to hide the inefficiencies.

---

### Post by Timon&amp;Pumba on 2008-06-11
The test of Watricky below assumes that each source can deliver files at a high enough bandwidth to occupy the target device. When copying multiple files from possibly different, slow sources, the asynchronous approach could be faster than sequential copying.

So, no approach is the overall winner. But I like the idea, because I experience the problems with multiple file copying as well.

> **watricky said:**
> Real-world results:

files: 5 ISOs, all approximately 700MB each, copying from portable HDD to my PC.

Sequential/Synchronous: Select all 5 files, copy/paste: 2m, 19 seconds, +- 25MB/s

Parallel/Asynchronous: Select 1 file, copy/paste, select next, copy/paste, end up with 5 separate copy windows; 9m, 1 seconds, +- 6MB/s

---

### Post by JohnLM_the_Ghost on 2009-01-15
This is exactly what I had in mind!
Although it is not about 8.04 or even 8.10... maybe for Jaunty!

I thought it could scan for involved devices and en-queue by (configurable) default, if that device is in use (i.e. having copy or move operation already). And have a "Do now!" kind of button on file operation window.

Naturally it should never en-queue same partition's move operations, cause they are super fast by nature!

I think the main reason would be because of increased HDD's wear and tear when it has to process two different copy instructions at once! (more specifically, jumping magnetic head to read both files in turns)

---

### Post by rebegin on 2009-01-15
copy queue management is now available in krusader svn.
i have created a howto here:
[http://ubuntuforums.org/showthread.php?t=998552]("http://ubuntuforums.org/showthread.php?t=998552")

---

### Post by JohnLM_the_Ghost on 2009-01-15
Thanks mate! But I would much want this for Nautilus... besides I am writing this in Brainstorm Page already!

EDIT: Posted!
[[IMG]http://brainstorm.ubuntu.com/idea/16615/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/16615/)

also added solution here
[[IMG]http://brainstorm.ubuntu.com/idea/6635/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/6635/)

---

### Post by Gootsch on 2009-03-08
i also want to use a queue to copy large amounts of data faster...

you copy or move one folder.. then you search through others and want to copy another one... but you have to wait and wait till the first copy is finished or you slow down everything.. that sucks...

i think, the ideal solution would be something like:


one or two additional small buttons in the copy-windows for every single task.
- a simple "pause" button (just like firefox has in the downloads window), so that i can add more and more tasks and decide when to finish them..
- a "pause until ... has finished"-button... you click the button and chose another copytask to wait for...

and default should be to copy everything parallel, because people are used to this behavior

---

### Post by rebegin on 2009-03-08
Gootsch, you can do something similar to this with krusader ;)
if you don't like using qt4 programs because of the way they look like, then you can still use gtkstyle and than there would be no difference between qt4 and gtk programs...

---

