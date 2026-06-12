---
title: "Question about using shred to securely erase HDD"
date: 2016-06-14
forum: Security
---

### Post by SpaceManJack on 2016-06-14
So I am thinking about using shred or dd to wipe my internal HDD in my laptop, so I'm researching both of them heavily. And I was reading this article here about shred [http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-hard-drive](http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-hard-drive)
and I see the dude say "Unmount all currently mounted partitions on that device, if any." So then I went and googled how to unmount partition and I see people saying something about gparted and whatnot and I'm just getting confused, cause when I read into dd I see no one, not a single person mention anything about making sure your HDD is unmounted of any mounted partitions before you execute the wipe.

So I'm in limbo here should I use shred or dd to securely wipe my HDD. And if I choose to use shred then please explain to me in layman's terms what all the fuss is about unmounting partitions before you enter in the shred command? Is it necessary, if it is then how do I do it in the simplest way? How come no one mentions anything about unmounting partitions when it comes to dd? Thanks.

p.s. so say that my HDD is partitioned, so what if it is, why can't i just enter in "sudo shred -v /dev/sdX" and just start the wipe process and be done with it. Or maybe I should say shred and just go with dd thereby not worrying myself with partition this or partition that?

---

### Post by sudodus on 2016-06-14
For most purposes it is enough to simply create a new partition table and create new partitions with file systems. But if you have confidential information, that must be completely wiped, I would suggest that you use ***hdparm*** or ***DBAN***. See the following link,

[best way to wipe a drive](http://ubuntuforums.org/showthread.php?t=2124829)

(I have tried them, and both work for me.)

---

### Post by HermanAB on 2016-06-14
Bear in mind that shred doesn't really work, for various reasons and various levels of work, one reason being journaled file systems and another automatic SSD disk block mapping.

It depends on the threat and risk.  If your adversary is your little kid brother, then simply deleting a file is enough.  If your adversary is a nation state, then you need to apply a sledge hammer and a torch and drop the remains in a river...

In general, the best solution is to always encrypt your disks.  If you then need to erase them, simply hit yourself upside the head with a brick to forget the password.

---

### Post by SpaceManJack on 2016-06-15
can i get some more commenters here please! these guys didn't even answer my question!

do i need to unmount partitions for dd? does dd work huh? can i please get an expert to answer me! So it looks like I need to unmount partitions if my drive is partitioned for shred right? ok but what about dd!!!! CAN I PLEASE GET A FREAKIN LINUX EXPERT HERE PLEASE!!!!

has anyone here used dd or shred to wipe their HDD? Did it work? Thanks

---

### Post by sudodus on 2016-06-15
Our replies imply that shred and dd are not the best alternatives, and we suggested other alternatives.

But, yes, I can reply about ***dd***.

I recommend unmounting before using dd, and to use dd to overwrite the whole device. This is probably one of the best alternatives for USB pendrives. You can use it for hard disk drives too, but I think there are better alternatives. If you still want to use it, I suggest that you use mkusb to wrap a safety belt around dd. See these links:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Wipe the whole device](https://help.ubuntu.com/community/mkusb/wipe#Wipe_the_whole_device)

***Edit:*** The same holds for ***shred***: Unmount all partitions, wipe the whole device (but mkusb does not offer any safety belt for it).

---

### Post by xen3 on 2016-06-17
> **scott130 said:**
> can i get some more commenters here please! these guys didn't even answer my question!

If you have the partition mounted, then the "local filesystem driver" for that filesystem (that was on the partition) may get in trouble. It too, will be confused ;-).

You would be deleting the filesystem from under it.

Shred and DD are not going to care.

They will proceed anyway.

Of course what the other person said about shred not working due to file system journalling is not applicable, because you intend to wipe the entire filesystem as well.

Unless you "have no other way to do it", wiping a filesystem from under a running system is not useful, so you would also want to have the thing unmounted.

Typically then if you want to wipe an entire harddrive, you need to do it from a Live session.

Unless you are worried that some adversary is going to take your harddrive apart, a single pass with dd if=/dev/zero of=/dev/sdX would generally be enough.

If you are more concerned, use shred -n1 -z /dev/sdX, for example. If you just want to fill empty space, use sfill /directory/ -f -ll or sfill /directory/ -f -l, or something of the kind.

Sfill is typically the only thing you can do without unmounting, and is meant to be used on a mounted system, for wiping empty space.

What the person said about "shred" and "file system journalling" is meant for shredding individual files on a filesystem. However in most standard configurations, journals do not keep filedata, only metadata (such as the filename, modification dates, etc.) so it also does not apply to the shredding of files on most systems. There might be some history of file operations that you didn't shred though (I don't know). Anyway, that's aside the question here.

Regards.

---

### Post by coldraven on 2016-06-17
As suggested above I would create a bootable DBAN disc, boot up with it and start overwriting your data with random stuff.(your drive **will** be unmounted)
[http://www.dban.org/](http://www.dban.org/)

---

### Post by xen3 on 2016-06-17
I don't think that provides any benefit over using dd or shred, at the cost of needing to burn another ISO (or usb stick) and at the cost of not knowing regular tools, that do the same thing.

---

### Post by coldraven on 2016-06-18
> **xen3 said:**
> I don't think that provides any benefit over using dd or shred, at the cost of needing to burn another ISO (or usb stick) and at the cost of not knowing regular tools, that do the same thing.

The only benefit is that you have a permanent utility to use in the future. You could securely wipe drives for Windows using friends for example.

---

### Post by HermanAB on 2016-06-18
There is a secure erase utility built into the disk drive controller of all disks that were manufactured this century at least.  Only the disk drive controller can erase the whole disk, including the space between tracks, since it controls the step motor.  So you don't need any special software - you just need to activate this function.

---

### Post by xen3 on 2016-06-18
Activating this function is typically more special than using "special" software that is not special at all ;-).

Just saying that it is more out of the ordinary to use that, than the solutions you could otherwise use to achieve the same (and basically to the same effect, except that you know how to use those utilities in a better way, considering that some other device might not have that feature, such as a flash drive).

---

### Post by SpaceManJack on 2016-06-21
I just need to acitvate the functoin huh? Well I checked out a tutorial for activating hdparm and guess what, it blew my mind with how complicated it looked! Can I please get some experts to weigh in here, I have a western digital laptop internal HDD, how would I go about activating the built in secure erase feature? This said built in feature is hdparm right? 

p.s. Am I wrong about hdparm being hard to do? I mean I looked at a tutorial and there were several steps one needs to do and honestly it intimidated me.

p.s.s. I guess I should have been upfront about this but I have already used DBAN to wipe my HDD but being as I am extremely paranoid and just want to be sure, I would like to wipe it again but with a diff program, that way I can rest assured that it definitely got wiped, this may be redundant but I just wanna rest easy is all so please answer my questions.

---

### Post by sudodus on 2016-06-21
I think you can feel safe after wiping with DBAN.

And I agree that some of the documentation about hdparm is intimidating ;-) But I have used hdparm successfully according to the link in post #2 (here in your thread). It is described with some detail in [post #12 in that link](http://ubuntuforums.org/showthread.php?t=2124829&p=12555068#post12555068).

---

### Post by xen3 on 2016-06-21
Yup, those commands are pretty complex.

Dude, if you want to wipe, just run shred -n1 -z /dev/sdb (for instance), it will do two passes, one with random numbers and one with zeroes.

See, this is also the problem with automatic tools, you don't really know what they do.

Run shred like this:

shred -v -n1 -z /dev/sdX, which will make you see a progress indicator.

---

### Post by SpaceManJack on 2016-06-22
what about unmounting partitions on the drive before I use shred? I have been reading all these tutorials and it said that if your drive is partitioned then you must unmount said partitions before you use shred? Can you elaborate this for me? I mean I dont know if my HDD is partitioned or not, when I installed ubuntu on it I just did the automatic install (another thing to point out is I actually already have used DBAN on the HDD like 3 times with many wipes). \

Why cant I just pop in the live CD and enter in "shred -v -n1 -z /dev/sdX" and thats it, I mean is there really anything else I need to do before I can enter in that command?

---

### Post by SpaceManJack on 2016-06-22
I went and read post #12 and again I was overwhelmed by what I saw could you please cherry pick the commands from said post that I need to enter to use hdparm please? I mean what do I do, enter in every single command he entered in exactly as he entered them? Come on man I'm confused.

---

### Post by xen3 on 2016-06-22
> **scott130 said:**
> what about unmounting partitions on the drive before I use shred? I have been reading all these tutorials and it said that if your drive is partitioned then you must unmount said partitions before you use shred? Can you elaborate this for me? I mean I dont know if my HDD is partitioned or not, when I installed ubuntu on it I just did the automatic install (another thing to point out is I actually already have used DBAN on the HDD like 3 times with many wipes)

Please, don't be so scared of things.

> Why cant I just pop in the live CD and enter in "shred -v -n1 -z /dev/sdX" and thats it, I mean is there really anything else I need to do before I can enter in that command?

Well, duh, you can, that's exactly what you can do. The Live CD is not going to mount your harddisk by itself. It has no reason to, it is not reading anything from it.

What on earth do you think can happen to a system running a live CD, when (a) the Live CD is not writable and (b) everything else that is writable, you want to destroy?

That is like not knowing whether you can blow up a house, because you don't know whether the fridge is still on or not!!!!

Or because you don't know if the electricity is still on!!!!.

The only thing that can possible happen is that you succeed in your mission of destroying everything. There is nothing else that you can write to, there is nothing else that can be destroyed, or overwritten, except for and apart from the very stuff you want to overwrite.

Well not considering that these days you can destroy UEFI bioses, but that won't happen here ;-).

You could have been done days ago. If the disk is not mounted, you do not need to unmount (you can check with the "mount" command) AND IF YOU HAVE ALREADY used DBAN 3 times, then THERE IS NO FILESYSTEM LEFT TO MOUNT IN THE FIRST PLACE. There is no filesystem left to mount anyway.

So, granted, the Live CD HAS nothing to mount. There is no filesystem left. Your disk is already wiped clean several times.

It needs a filesystem to mount anything, but you have already destroyed that several times, and left it in debris that is not existent anymore.

There is no trace of anything left on that disk, and you still want to overwrite it. Fine. The disk doesn't have a partition table. It has no partitions. It has nothing. It is empty space, or possible random garbage now.

Therefore, there is nothing ever ever ever to unmount and even if something was mounted (but you're not using it) nothing could ever happen to your Live CD session because it does not depend on the harddisk.

Now I don't know about SSDs but I hardly doubt anything is left. You could wipe the entire system from underneath someone's nose and they won't notice it because they're not using it.

Even if the Live CD mounted something by accident and started reading files, the worst thing that could happen would be for it to hang.

But it can't, because there is no filesystem to mount, and not even any partition table (or partition) to mount it from.

Your disk is wiped clean already. It can't mount anything.

I'm not sure if you're worried about governments using magnetic resonant imaging techniques after taking your (platter) disk apart or not, but unless you have something they really really want, that won't happen either. The only caveat is SSDs. Is this an SSD? There could be traces of data on reserved space you cannot write to. But I don't know how possible it is for anyone else to read from it, in that case.

SSDs, apparently, are not erased by writing data to it, the various tools of the manufacturers apparently initiate that same command that hdparm could, and it just voltage spikes the entire data store, resetting all data at once: [http://www.makeuseof.com/tag/securely-erase-ssd-without-destroying/](http://www.makeuseof.com/tag/securely-erase-ssd-without-destroying/). All manufacturers may have tools for Linux as well, I know Transcend has.

---

### Post by HermanAB on 2016-06-23
Here you go:
$ ls /dev/sd*
$ sudo hdparm --security-set-pass user /dev/sdX
$ sudo hdparm --security-erase-enhanced /dev/sdX
Veeery looong waaait...

Change sdX to the applicable device name from the first command.

---

