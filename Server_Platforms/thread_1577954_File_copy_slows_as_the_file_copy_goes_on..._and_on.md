---
title: "File copy slows as the file copy goes on... and on.... and on..."
date: 2010-09-19
forum: Server Platforms
---

### Post by bvasiljev on 2010-09-19
This is the basic problem i have:

Copying 160GB file (single file) takes me about 3-ish days.

From one disk to another.

Same thing being done over windows 7 or windows XP takes about 2.5 hours more or less. EVERY TIME.

One is a 250 GB SATA drive, other is 320GB drive
One is attached to the onboard SIL3112 SATA controller (not raid)
Second is attached to an addin-card SIL3114 SATA controller via eSata port.
Ubuntu Server 10.04, console only.

Both NTFS formatted partitions - need the NTFS because of compatibility with evil OS-es i have to use at work.

This is what i've tried so far:

File copy methods: cp, rsync, midnight commander file copy - all with the same result. 
Starts at 13.5 MB/s then crawls down to 3.5MB/s within one hour. And then it keeps slowing down. At the very end of copying it's about 50 KB/s.

Tried mounting both partitions with either sync or nosync flag.

Other than that i have no further ideas. Other than keeping a dual boot with window$, but what's the purpouse of using open source then :-(.

One other thing that comes to mind now is that speed never went slower than 19 MB/s under window$ in this exactly same setup, while under ubuntu it never went OVER 15 MB/s. Why such a big difference and only the OS is different.

I've seen other posts all over the net with people having this problem and it was always blamed on cabling, but never any real answer because cabling obviously isn't a problem in this case.

Any ideas?

---

### Post by LightningCrash on 2010-09-19
Sounds like it's an issue with the NTFS driver itself.
The NTFS support under Linux is very CPU intensive, in my experience.

I wonder what your system stats are during this time period?

---

### Post by BkkBonanza on 2010-09-19
Something must be "wrong" because I've copied hundreds of GB between SATA drives, where one was NTFS and it's always been quite fast, limited only by my drive speed. I only mention this because it shouldn't be considered "normal" linux behaviour. You may want to look at NTFS mount options to see if there's something unsual.

If you use rsync and cancel (ctrl-c) when it starts slowing to 3.5 MB/s, then start again, when it's caught up with where it was, does it continue fast or slow for the next data?

---

### Post by bvasiljev on 2010-09-23
> **BkkBonanza said:**
> 
If you use rsync and cancel (ctrl-c) when it starts slowing to 3.5 MB/s, then start again, when it's caught up with where it was, does it continue fast or slow for the next data?

Never did try that - i'm paranoid about a possibility it won't continue at exact byte where it stopped :-)

Today i took out the backup drive out of the computer that does the copying and put it into my work PC which has a wee bit less antique components

Core2Duo 2x3,20 Ghz
Intel MoBo Intel DG33FB G33 Express chipset

Ubuntu 10.04 LTS

Mount options are at install default, didn't tamper with those on this one.

Same thing with different numbers - starts at 56 MB/s and now i'm looking at it after 10 or so minutes and it's down to 27 MB/s and falling (currently copied 25 GB)

Tomorrow i'll clear up a couple of drives and format them to ext4 and try this on ext4 to see how it's supposed to act under a native FS.

If it starts doing the same then i'd ask someone else to do the same thing and tell me what the heck is going on.

CPU's both cores are at 100% though, but they're at that from the very start.

p.s. it's at 23.4 MB/s now :-(

---

### Post by scrooge_74 on 2010-09-23
Disk issues?

I once had (disks in ext3) that would give me problems copying or moving files, mount errors and such. That would happen after a reboot, would spent half a day fixing mounts and moving data just in case I lost it. 

In the end I disconected the problematic disc. Latter on PC/server died so I replaced it with a bigger one so I could hold more disk and this time I was going out of my mind, having problems trying to install.  Well turns out I had one defective SATA cable. The "problematic disk" has being working with no problems after that.

So even the little things can have an effect

---

### Post by BkkBonanza on 2010-09-23
It's typical for the speed to drop after a bit when limited by disk. Initially the linux caching will make it seem very fast but at some point it has to start writing cache to disk as well. Not nearly as much as you experience.

It's odd that the CPU is at 100% though - I can usually copy large files with little CPU use. A quick test just now shows typically 10-12% above idle, for me.


Having used rsync a thousand times I can assure you it will continue where it left off. Sometimes I do a double rsync, that is, a second one, just to be sure to pick up any files changed during the first copy. Since the second one goes almost instantly there's much less time for more changes.

---

### Post by bvasiljev on 2010-09-24
Not a bad cable, tried it with 3-4 separate cables and now on two separate computers running ubuntu. Even one of the drives is different second time (but also formatted to NTFS)

So currently the only constants in this story are:


[LIST]
[*]NTFS file system (wich unfortunatelly i have to keep using because there are no reliable ext4 drivers for window$ as far as i know)
[*]File of 160GB wich is actually a truecrypt container
[*]Ubuntu 10.04 (LTS or Server)
[/LIST]

Rsync doesn't continue where it stopped, it's a single file and it won't "resume" it. Either i didn't pick up the exact command line option for that or it doesn't do resuming single files

This morning when i woke up the transfer from last night was at 3.48 MB/s
This really starts looking to me like a bug in the NTFS driver. I'll try and find out who is maintaining that particular package (NTFStools i think) and write them an e-mail or two... or four.

---

### Post by scrooge_74 on 2010-09-24
Dumb question here? Why you need the drives to be ntfs, can use samba instead ? and let the Windows computers think they are on a Win network?

---

### Post by bvasiljev on 2010-09-24
Work PC's are all windows. I don't have anywhere to plug in an external Ext4 formatted USB hard drive and share it over Samba at work.

---

### Post by BkkBonanza on 2010-09-24
I've used [Ext2 IFS]("http://www.fs-driver.org/") before on Windows to access my ext3 drives. It worked well but was a long time ago now. Before I gave up Windows... 

It doesn't support ext4 but I do recall it worked fine with my ext3 external usb drives.

---

### Post by scrooge_74 on 2010-09-24
> **bvasiljev said:**
> Work PC's are all windows. I don't have anywhere to plug in an external Ext4 formatted USB hard drive and share it over Samba at work.


I'm still lost here, but trying to help. Can't you mount a samba server in your linux machine?  Sorry I'm not sure what set up you have (probably didn't understand the opening post)

---

### Post by Cool Javelin on 2010-09-24
DMA or Direct Memory Access?

Just reaching here, but...

It is a controller to move data from one place to another (either mem to mem, mem to I/O, or I/O to I/O.) I know windows supports DMA access to hard drive controllers, (in 98 you had the option to turn it off and it defaulted to off, in XP or newer, it defaults to on,) but I don't know enough about Ubuntu (Linux) to know if that is using DMA.

You mentioned the processor is running at 100%. With DMA, the processor should only be servicing the DMA interrupts before and after blocks of data have been transfered by the DMA controller. (ie. Move this 16K block of data from here to there, and tell me when you are done.)

I would expect the CPU to be spending very little time on the task of copying data from one drive to another unless DMA wasn't functioning and the CPU was doing all the grunt work.

You say this is more then one machine, is there any other hardware that is common between the 2 machines, Audio board, external hard drive controllers, sound cards?

Maybe the DMA interrupts are shared with some other piece of hardware, or some other something (bad driver?) is preventing Ubuntu from properly using the DMA controller.

Good luck.

Mark.

---

### Post by bvasiljev on 2010-10-01
Tried this on a completely different configuration this time. Still the same results.

It was an asrock board this time running dual core Athlon64 with ATI 780 something chipset. Integrated graphics, only usb stick running live ubuntu off it and these two drives plugged in - tried the same thing, same problem occured... after we got back from a long watercooler meeting, it was down to 9 MB/s

This is really starting to annoy me.

Samba isn't an option at work. I'm pushing it already by taking my work home, don't have wiggle room to play around with networking home-brew pc's to the work network.

---

### Post by X1R1 on 2010-10-01
Its a matter of the NTFS drivers and someone said here, I have had the exact same problem but with a Flash drive, The problem occurs during filesystem conversion I think, for example, when you copy a file from a machine using ext3 filesystem to a ntfs drive, the copying speed will always drop down, (with samba this doesnt happen).

---

### Post by BkkBonanza on 2010-10-01
Doing a bit of googling indicates this issue is a well known ntfs-3g bug. Apparently it will consume all cpu resources and slow down on very large files.

One workaround suggested by a post I saw was to avoid the ntfs-3g drivers byt installing VitrualBox, then running a Windows VM and attaching the ntfs drives raw/direct as partitions there. It apparently will use copy fast using the normal Windows drivers.

Reading the posts on this issue it's not encouraging to see the Linux users attitude isn't that we need to fix this but rather we shouldn't complain it's broke because it's free. I did a small test on my system with an 8GB file and sure enough it will slow down right from the start. Initially 34MB/s and withing seconds down to 30, 27, 24 etc. I stopepd watching at 16 MB/s, and cancelled the test.

---

### Post by BkkBonanza on 2010-10-01
Doing a bit of googling indicates this issue is a [well known ntfs-3g bug]("http://forums.whirlpool.net.au/archive/1485315"). Apparently it will consume all cpu resources and slow down on very large files.

One workaround suggested by a post I saw was to avoid the ntfs-3g drivers by installing VirtualBox, then running a Windows VM and attaching the ntfs drives raw/direct as partitions there. It apparently will copy fast using the normal Windows drivers.

Reading the posts on this issue it's not encouraging to see the Linux users attitude isn't that we need to fix this but rather we shouldn't complain it's broke because it's free. I did a small test on my system with an 8GB file and sure enough it will slow down right from the start. Initially 34MB/s and within seconds down to 30, 27, 24 etc. I stopped watching at 16 MB/s, and canceled the test.

See here, 
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204)

Someone else reports a new PPA with a "fixed" version of ntfs-3g:
[https://launchpad.net/~x3lectric/+archive/team-iquik-releases/+packages](https://launchpad.net/~x3lectric/+archive/team-iquik-releases/+packages)
How to: [https://launchpad.net/~x3lectric/+archive/team-iquik-releases](https://launchpad.net/~x3lectric/+archive/team-iquik-releases)

Also, apparently building from source here, can fix it,
[http://www.tuxera.com/community/ntfs-3g-download/](http://www.tuxera.com/community/ntfs-3g-download/)

Edit: I added this PPA and updated to the new driver. It seems to be better in CPU usage and doesn't slow as much, but it still degrades over time. I'm mystified how such a simple thing as copying files can throw the driver into a tizzy. Kind of junky really.

Copying 8GB file - started at 34MB/s and pretty stable at 17MB/s after 5 minutes. Finished with,

8388608000 bytes (8.4 GB) copied, 495.465 s, 16.9 MB/s

---

### Post by BkkBonanza on 2010-10-01
Another test I did show the ntfs-3g drivers are pretty slow for writing.

I wrote zero bytes to my ext3 partition and then did the same to my ntfs one.
Same machine, same drive types and same SATA connections.

dd if=/dev/zero of=/media/NAS1/test bs=4k count=256k
1073741824 bytes (1.1 GB) copied, 10.912 s, 98.4 MB/s

dd if=/dev/zero of=/media/NAS2/test bs=4k count=256k
1073741824 bytes (1.1 GB) copied, 37.4862 s, 28.6 MB/s

Hmmm.

---

### Post by oldfred on 2010-10-01
Some more info here:

[http://www.tuxera.com/community/ntfs-3g-faq/#highcpu](http://www.tuxera.com/community/ntfs-3g-faq/#highcpu)

It looks like defrag helps and some settings in linux.

---

### Post by bvasiljev on 2010-10-02
Hm... time to try out the ext3 driver for windows.

---

### Post by scrooge_74 on 2010-10-02
So samba is not an option (you can't installed on your own PC you are not taking that to work just the drives right?)

What about using Virtualbox install XP then conect the drives and tell the XP to use them as it would if it was in full control of the PC? That I have done (no large files but i used it that way before)

---

### Post by bvasiljev on 2010-10-02
At this time i've patched the problem with a live windows xp cd. It's not the way i want it done but it enables me to copy the container in under 3 hours wich is fine i guess considering mechanical drive inferiority. But it sucks that i have to use windows to stay compatible with windows :-)

---

### Post by scrooge_74 on 2010-10-03
You could do better using a VM XP instead of having to relay on a Live CD

---

