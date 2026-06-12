---
title: "Willing to comment on multi-disk partitioning ?"
date: 2010-10-13
forum: Server Platforms
---

### Post by bdemers on 2010-10-13
I'd like to set up a dedicated fileserver, running iSCSI only.  This is an older box, has 4 scsi drives available for holding the OS.  (The iSCSI will be on a couple of external arrays, not used for booting).  The 4 scsi drives can be either 4GB UW or 18GB UW3 each, as I have both, the backplane being UW3.  The computer is maxed out on ram at 2GB.  I realize that I can configure those 4 drives in several different ways.  I wonder, though, do I really care for this application?  I'm guessing that the OS all goes into ram and since I'm doing mostly file manipulations my biggest concern will be tmp files, and therefore swapping.  The booting doesn't really impact much, at least it better not.   I assume the limited ram could max out and want to swap, depending on a load that right now I can't predict.  
Other than the swap, tmp files, and logs, what else is waiting to get me on a dedicated fileserver? This would affect my partition sizes. Am I better off(performance, reliability, nod going to performance) using a raid 0, spanning all 4 disks, or keeping separate volumes, splitting up the install partitions and interleaving the swap partitions? Or, again, do I care for this application?

---

### Post by annoyingrob on 2010-10-15
LVM would probably be your best bet as far as managing the drives. 

I run a file server (about 2TB) on 1gb of ram, you should be fine with 2.

---

### Post by bdemers on 2010-10-15
Thanks. Feel a bit better on the installed ram.  For sure I will consider lvm for the storage arrays.  What size swap partition do you use?

---

### Post by SeijiSensei on 2010-10-15
With 2GB of memory you could probably get by without any swap at all.  It's customary to dedicate the same amount of disk space to swap as the size of the physical memory, but I don't think you'll need that much for a file server.  Start with 1GB and watch your memory usage with the "top" command.

---

### Post by bdemers on 2010-10-15
I am using a recent version of the kernel, and I understand that if I take and not partition for swap, I can add a swap "file" if I need to later on. This would be rather benificial as I want to use 4GB drives to hold the OS, if at all possible.  Considering that a file server comes in at less than a gig, if I take Ubuntu's approach and use a single partition, incorporating the entire drive, I could raid 1 a pair of drives and still have a pair sitting idle. Very economical indeed.

Now, not asking how,yet, but is it possible for me to log  memory usage, including swap files, so I'd be able to see a history of useage, not just a snapshot?  I need to research this.  I have seen the graph that Gnome has built in, so maybe I can do this inside a server.

---

### Post by annoyingrob on 2010-10-15
> **bdemers said:**
> Thanks. Feel a bit better on the installed ram.  For sure I will consider lvm for the storage arrays.  What size swap partition do you use?

I run 2GB swap, but it almost never gets touched. My server does routing (IPv4 and IPv6) for my network, as well as NFS and samba file sharing. It also handles bandwidth monitoring on my cable modem, and even has an x11 server running so I can VNC into it. With all that running, I'm usually sitting at 600MB of ram used. The remaining is eaten up by caching when I transfer files.

The only time I ever pushed into swap usage was when I had bandwidthd monitoring my internal gigabit network, and tried transferring some large files really fast.

---

### Post by bdemers on 2010-10-15
[QUOTE=
The only time I ever pushed into swap usage was when I had bandwidthd monitoring my internal gigabit network, and tried transferring some large files really fast.[/QUOTE]

So here's where my rookiness shows up.  If understand correctly, it isn't until the cache fills available ram that the os will page out to the swap area.  Perhaps there are other factors that cause "premature paging" to occur?  If you had had more ram, then the limited paging that you did have would have been less, right?  

What I'm getting at here is if I have enough ram that it can be used for caching, why set up a swap file in ram?  I have a finite amount of ram, why take some of that and dedicate it as a swap file, when it could have been used for caching instead? I am told that a swap file in ram is slower than if that space had been used more normally.

Shore up the ram with a minimal amount of swap disk space, regardless of which approach, but in my case, where disk space is like gold, I might want to start with a 1GB swap.  Am I thinking correctly here?

Going further, if I were to set up the os on 2 of the 4 disks using raid1, I still have 2 available disks that can be set up as raid 0 and make that set a swap partition.  This would improve my latency time for those rare occasions that swapping does occur.  Does that make sense?

---

### Post by ratcheer on 2010-10-15
I have never been a sysadmin (except at home), but as an Oracle DBA, I paid pretty close attention to how the sysadmins set up the systems.

At my last job, we ran Solaris on fairly big servers that had 32 GB RAM. The sysadmin always put a swap file on every system drive, I think he usually had 16 GB swap files on each of four system drives. I don't know how right or wrong that was, but his systems always ran great.

I know you don't need anywhere that much, but I would consider putting a 512 MB swap on each system drive. Maybe even 1 GB.

Tim

PS - They may have been 8 GB swap files (16 million 1/2 KB blocks)

---

### Post by bdemers on 2010-10-15
The approach that your sysadmin took is the basis for a great how-to that started this whole dialog.  HOWTO: Multi Disk System Tuning
                      Stein Gjoen, [email]sgjoen@nyx.net[/email]

Good reading.  The main point that kept reappearing was that you need to consider the application.  Being very wet behind the ears, tough thing for me to pull off without emense trepidation.

---

### Post by annoyingrob on 2010-10-15
> **bdemers said:**
> So here's where my rookiness shows up.  If understand correctly, it isn't until the cache fills available ram that the os will page out to the swap area.  Perhaps there are other factors that cause "premature paging" to occur?  If you had had more ram, then the limited paging that you did have would have been less, right?  

What I'm getting at here is if I have enough ram that it can be used for caching, why set up a swap file in ram?  I have a finite amount of ram, why take some of that and dedicate it as a swap file, when it could have been used for caching instead? I am told that a swap file in ram is slower than if that space had been used more normally.

Shore up the ram with a minimal amount of swap disk space, regardless of which approach, but in my case, where disk space is like gold, I might want to start with a 1GB swap.  Am I thinking correctly here?

Going further, if I were to set up the os on 2 of the 4 disks using raid1, I still have 2 available disks that can be set up as raid 0 and make that set a swap partition.  This would improve my latency time for those rare occasions that swapping does occur.  Does that make sense?

Yes, swap is only used if your ram fills up, which will likely never happen on a small home linux fileserver. It's really nice to have it as a safety net just in case you DO run out of ram, but if you're limited on hard drive space, allocating even 512MB would probably be just fine. Nothing's going to touch the swap file unless it absolutely has to, because it's terribly slow. 

Personally, I wouldn't worry about the swap file speed or size. Make it as big or as small as you would like. If it turns out to be too small, worry about it then. Mine's 2GB because that's what the installation defaulted to. If you're running into a situation where you NEED a bigger swap partition, you have bigger problems, like a WAY overloaded system.

Hard drive caching will use any available ram you have but it will never push into swap, and it will always relinquish its usage to other programs that need it.

---

### Post by bdemers on 2010-10-15
Thanks for the sage advice. And for putting up with a bunch of newfy questions.  Without realizing it, I'm sure, you gave me another topic to look at intensely :caching and what the options are available to me.  I know what caching is, but are there add-ons or special routines that supplement the kernel, thereby improving performance?  Like read/write buffers for hard drives, that sort of thing. Maybe I should focus on this area for performance improvements first, not last.

With so many talented people developing this (Linux) os, how does a hardware jock, such as myself keep up with it all? -- just rhetorical

---

### Post by annoyingrob on 2010-10-15
The linux kernel natively supports hard drive caching to ram with pretty much any filesystem. There's not really much you need to research, it just does it. I just mentioned it because it takes up ram, but it's a pretty passive sort of thing. There may be some additional tuning you can do to it, but it's pretty much one of those "It's there, it works well, there's nothing you need to do with it" sort of features.

It scares a lot of new users that look at their system, and go "OMG, my ram is FULL!!!", but it's just Linux using your available space to increase performance.

---

