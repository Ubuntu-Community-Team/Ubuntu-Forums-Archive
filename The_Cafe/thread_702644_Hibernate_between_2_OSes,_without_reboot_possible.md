---
title: "Hibernate between 2 OSes, without reboot possible?"
date: 2008-02-20
forum: The Cafe
---

### Post by oedipuss on 2008-02-20
Is it possible to hibernate both windows and ubuntu, and switch from one to the other without doing a full reboot ? 
It would be nice to have a quick way to dual boot a machine, and that's the closest thing I can think of that's kinda doable. 
Perhaps there's some way to return to GRUB without rebooting the pc, that would basically do the trick.

---

### Post by lespaul_rentals on 2008-02-20
I don't think so.  Sorry.

---

### Post by tszanon on 2008-02-20
Interesting, but probably not possible (yet?).

---

### Post by Crashmaxx on 2008-02-20
My laptop does this. When I hibernate Ubuntu is basically shuts down with the session saved. When I turn it back on I get grub and can select Windows if I want. And when I reboot into Ubuntu it just comes back from hibernate.

---

### Post by perce on 2008-02-20
It's possible, because Windows (at least XP, the one I tried with) and Linux store the information in two different places: Windows in some file in its partition, and Linux in the swap partition. You should need no extra configuration, just hibernation working on both OS's.

---

### Post by tszanon on 2008-02-20
If I got it, the OP does not want to reboot the pc. As far as I know, there's no solution for this case (up to now). There is no way to switch  the operating systems without rebooting.

---

### Post by akiratheoni on 2008-02-20
The closest thing you can get to 'switching' OSes without a reboot is virtualization, but you won't get the full capabilities of Windows if you run it under Linux.

---

### Post by phrostbyte on 2008-02-20
This is how it works on my laptop by default. If I Hibernate in Windows and bootup the GRUB menu loads. Then I can go into Ubuntu. After I am finished with Ubuntu, I can unhibernate Windows.

---

### Post by Bliepo32 on 2008-02-20
You could of course use sometinh like VMWare, so running it virtually.

---

### Post by tszanon on 2008-02-20
> **phrostbyte said:**
> This is how it works on my laptop by default. If I Hibernate in Windows and bootup the GRUB menu loads. Then I can go into Ubuntu. After I am finished with Ubuntu, I can unhibernate Windows.
You're right, this can be done, not only in laptops, but in desktops and servers and whatever else that supports dual booting :). But it seems that the OP does not want to reboot the computer, and that's the problem. I don't think you can switch operating systems without rebooting.

---

### Post by az on 2008-02-21
To hibernate *is* to reboot.  The difference is that to hibernate puts the contents of your ram on disk for retrieval the next time you boot.  As mentioned, since windows and linux both use different places to store the contents of ram at hibernation time, you can have both OSes hibernating at the same time.

To suspend your computer is to put it into low-power mode.  The computer is still on,  but the processor is slowed/stopped until it's needed again.  Since the ram is not accessed, its power is reduced.  Your computer is not off.  It's not possible to suspend in one OS and wake up in another.  Suspend is not hibernation.

---

### Post by IPCK on 2008-02-21
Mate, i am sure you could try VM ware. You could try this out and use windows as a  virtual server while booting your system.I don't think there is any other option other  than restarting your system.

---

### Post by oedipuss on 2008-02-21
Vmware, virtualbox etc are nice and all, but there are limits to what a VM can do. 
By not rebooting I meant some way to return to grub after the hibernation process is finished, without going through the initial stages of booting up your pc. 
It wouldn't save that much time, really, I'm just curious if returning to grub can be done, and was a little unsure if there could be problems with the double hibernation I didn't think of.

---

### Post by quanumphaze on 2008-02-21
I think what the OP means is that Ubuntu it to hibernate as usual but instead of turning off the computer, it runs GRUB again. This means that you don't have to wait through the POST and save ~10 seconds.

It *could* be possible if someone codes it. Not much chance to make Windows do it though. But I am not a programmer.

---

### Post by original_jamingrit on 2008-02-21
> **quanumphaze said:**
> I think what the OP means is that Ubuntu it to hibernate as usual but instead of turning off the computer, it runs GRUB again. This means that you don't have to wait through the POST and save ~10 seconds.

It *could* be possible if someone codes it. Not much chance to make Windows do it though. But I am not a programmer.

Right, all you really need to do is reload all of the modules/drivers that the BIOS would normally provide at startup as well, and then go into the GRUB boot loader.  But this is also accomplished by putting either OS into hibernate, allowing your machine to power down and then boot it again.  It possible, but seems like it would take a lot of work for something small.  Maybe some bored coder could take this up for a weekend?

---

### Post by fwojciec on 2008-02-21
> **Crashmaxx said:**
> My laptop does this. When I hibernate Ubuntu is basically shuts down with the session saved. When I turn it back on I get grub and can select Windows if I want. And when I reboot into Ubuntu it just comes back from hibernate.

Don't do this!!!  Unless you're willing to risk data corruption that is...

---

### Post by perce on 2008-02-21
> **fwojciec said:**
> Don't do this!!!  Unless you're willing to risk data corruption that is...

Why should you corrupt your data by doing this?

---

### Post by fwojciec on 2008-02-21
> **perce said:**
> Why should you corrupt your data by doing this?

I'll give you an example.  Imagine you were using windows, you hibernated and you restarted into Ubuntu -- Ubuntu mounts the windows partition (which was not unmounted) so you have a good chance of loosing data.  A similar thing can happen with any partition that is shared between the two operating systems you subject to such a practice.

EDIT: To make the point clearer: hibernating one OS and booting into the other -- if there are shared partitions -- is, pretty much, equivalent to force-resetting your system instead of shutting it down properly...  Or actually, it is worse -- you could boot into the other OS, make changes to the shared partition, and then resume into the first system that will still think that the state of the shared partition is the same as when the system went into hibernation.  In other words -- opportunities for data corruption are endless.

---

### Post by oedipuss on 2008-02-21
> **fwojciec said:**
> I'll give you an example.  Imagine you were using windows, you hibernated and you restarted into Ubuntu -- Ubuntu mounts the windows partition (which was not unmounted) so you have a good chance of loosing data.  A similar thing can happen with any partition that is shared between the two operating systems you subject to such a practice.

EDIT: To make the point clearer: hibernating one OS and booting into the other -- if there are shared partitions -- is, pretty much, equivalent to force-resetting your system instead of shutting it down properly...  Or actually, it is worse -- you could boot into the other OS, make changes to the shared partition, and then resume into the first system that will still think that the state of the shared partition is the same as when the system went into hibernation.  In other words -- opportunities for data corruption are endless.

So by using only the absolutely necessary shared partitions, and not keeping critical data in them, one should be ok.
What about mounting windows partitions as read-only in ubuntu, to avoid unnecessary changes , or unmounting them (at least from ubuntu's side) before hibernation ?

More importantly, can the data be practically damaged by the mount / unmount process itself ?

---

### Post by fwojciec on 2008-02-21
> **oedipuss said:**
> So by using only the absolutely necessary shared partitions, and not keeping critical data in them, one should be ok.
What about mounting windows partitions as read-only in ubuntu, to avoid unnecessary changes , or unmounting them (at least from ubuntu's side) before hibernation ?

More importantly, can the data be practically damaged by the mount / unmount process itself ?

As regards your last question -- yes, especially when we're talking about journaled filesystems (most modern filesystem types).  Basically mounting a partition that wasn't clearly unmounted can always result in data corruption.

With regard to your earlier questions -- I don't know enough to be able to answer this authoritatively but I certainly would not do it on my systems.

---

### Post by Crashmaxx on 2008-02-21
Hibernation should cleanly unmount and mount the partitions. It just dumps the ram to swap and load the swap to ram when loaded. Don't think their is any danger in mounting a hibernated partition.

---

### Post by fwojciec on 2008-02-21
> **Crashmaxx said:**
> Hibernation should cleanly unmount and mount the partitions. It just dumps the ram to swap and load the swap to ram when loaded. Don't think their is any danger in mounting a hibernated partition.

Hibernation does not unmount drives (try unmounting the root partition with a system up and running -- you can't, and neither can hibernate routine).  What hibernate does is to freeze the system state with the drives suspended but mounted.  That's a fact.  

There is a danger in mounting a hard drive that was not unmounted -- a danger of data loss or corruption.  That is also a fact.

Feel free to do what you want with your system but please don't recommend dangerous practices to other users by claiming that they are safe.

---

### Post by Crashmaxx on 2008-02-21
> **fwojciec said:**
> Hibernation does not unmount drives (try unmounting the root partition with a system up and running -- you can't, and neither can hibernate routine).  What hibernate does is to freeze the system state with the drives suspended but mounted.  That's a fact.  

There is a danger in mounting a hard drive that was not unmounted -- a danger of data loss or corruption.  That is also a fact.

Feel free to do what you want with your system but please don't recommend dangerous practices to other users by claiming that they are safe.

Ok, I see you are right, but there should be a pretty easy way to solve this. From here:
[http://www.tuxonice.net/HOWTO-4.html](http://www.tuxonice.net/HOWTO-4.html)
> 
Windows touches your FAT partitions whilst Linux is hibernated

Problem: Similar to the scenario above, if you have mounted FAT drives or partitions when hibernating and you then boot into Windows, as soon as you boot back into Linux you will probably end up corrupting your FAT drives.

Solution: Unmount your FAT drives before hibernating. If you are using the Hibernate Script, you can use the following line in your hibernate.conf:

    UnmountFSTypes vfat fat msdos



---

### Post by fwojciec on 2008-02-21
If you manually unmount all drives that might be accessed by another operating system while the first one is suspended then indeed you should be able to avoid data loss -- at least in principle.  This is also only true for the drives that can be unmounted while the system stays up and running (basically only "data" partitions, you can't do this with "system" partitions).

So if you suspend in Windows and then boot into Ubuntu which automatically mounts the Windows *system* partition you're risking data loss...  Again, this can be worked around -- but even if you do the opportunity for human error will remain.

This discussion, at this stage, is academic.  The best practice is to use hibernation if you're planning to boot back into the same OS.  If you planning to boot into another OS it's best to shut down.  Is the gain of few seconds of boot/power up time really worth putting your data at risk?

---

### Post by oedipuss on 2008-02-21
Thanks for that info, btw .
I wouldn't have guessed there's that kind of risk.

Now that I think about it, shouldn't there be some kind of warning about this ? 
I imagine lots of people who dual boot actively do just that, and might lose data without realizing why. 
(Or perhaps there is already, in which case ignore me :P )

---

### Post by az on 2008-02-22
> **fwojciec said:**
> 

There is a danger in mounting a hard drive that was not unmounted -- a danger of data loss or corruption.  That is also a fact.

Feel free to do what you want with your system but please don't recommend dangerous practices to other users by claiming that they are safe.

When linux hibernates, it syncs the drives, and won't hibernate until all drives are synced.   It then cleans up and packs the contents of ram to swap.  It then shuts down (power down the hard disks).  A resume from hibernation is no different than a normal boot in the sense that the bios powers on the hardware including the disks.  The initrd will perform hardware detection and all drives in fstab will be mounted as per a usual startup.  

The only difference between a power up from shutdown and a power up from hibernation is at this point, where the initrd will look at the swap space to see if there is a resume signature there.  If there is not, the init scripts continue to run as usual.  If there is one, the contents of ram are loaded and a few other things are cleaned up (network interface, screen, etc...)

The point is, there is no difference between a drive that is off after hibernation and a drive that is off after power off.  There is no data left in the buffer.  It's the same as if it were unmounted.

---

### Post by fwojciec on 2008-02-22
> **az said:**
> When linux hibernates, it syncs the drives, and won't hibernate until all drives are synced.   It then cleans up and packs the contents of ram to swap.  It then shuts down (power down the hard disks).  A resume from hibernation is no different than a normal boot in the sense that the bios powers on the hardware including the disks.  The initrd will perform hardware detection and all drives in fstab will be mounted as per a usual startup.  

The only difference between a power up from shutdown and a power up from hibernation is at this point, where the initrd will look at the swap space to see if there is a resume signature there.  If there is not, the init scripts continue to run as usual.  If there is one, the contents of ram are loaded and a few other things are cleaned up (network interface, screen, etc...)

The point is, there is no difference between a drive that is off after hibernation and a drive that is off after power off.  There is no data left in the buffer.  It's the same as if it were unmounted.

There were links in previous posts that suggest, and quite authoritatively, something rather different.  Is what you're saying your guess or are you basing this on some concrete knowledge?

And as far as your suggestion that during resume process drives are mounted the same way as during a regular boot on the basis of the info in /etc/fstab -- that is simply incorrect!  I know this by experience because once I let a reiserfs partition that was suspended earlier to be mounted during boot (the order of calls in initrd was wrong and the filesystems were initialized before checking for suspend signature) and I nearly lost all data on it -- I had to go through a long and complicated recovery procedure.

---

### Post by az on 2008-02-22
> **fwojciec said:**
> There were links in previous posts that suggest, and quite authoritatively, something rather different.  Is what you're saying your guess or are you basing this on some concrete knowledge?

Ubuntu uses HAL to put your computer to sleep, not suspend2.  I think the information from some of that page is from 2003.

> **fwojciec said:**
> 
And as far as your suggestion that during resume process drives are mounted the same way as during a regular boot on the basis of the info in /etc/fstab -- that is simply incorrect!  I know this by experience because once I let a reiserfs partition that was suspended earlier to be mounted during boot (the order of calls in initrd was wrong and the filesystems were initialized before checking for suspend signature) and I nearly lost all data on it -- I had to go through a long and complicated recovery procedure.

I dunno.  How long ago was that?  I know plenty of people who have had misfortunes with reiserfs. 

As far as the resuming, the last time I looked at the scripts in the default initrd, that's what they do.

---

### Post by fwojciec on 2008-02-22
> **az said:**
> Ubuntu uses HAL to put your computer to sleep, not suspend2.  I think the information from some of that page is from 2003.

HAL, in either case, would be only used to trigger the suspend command, not to actually manage it all the way.  As far as I know, in fact, Ubuntu kernel is patched with suspend2 (tuxonice now) patch by default, or at least was in Edgy -- that was the last time I checked what Ubuntu did as far as hibernation was concerned, perhaps it is not the case nowadays.  The fact that the page was written in 2003 has nothing to do with anything -- it is still the official info provided by the developers of one of the major hibernation frameworks for Linux that's under active development and as such it has to be regarded as current.  

Speculation that it might be outdated is irresponsible -- considering the serious consequences in case it is still valid.

> **az said:**
> I dunno.  How long ago was that?  I know plenty of people who have had misfortunes with reiserfs.

As far as the resuming, the last time I looked at the scripts in the default initrd, that's what they do.

It happened a few months ago -- it was caused by my mistake, and I was not using Ubuntu though so I'm not sure if the exact same problem could be reproduced on Ubuntu.  The fact that I was using reiserfs certainly aggravated the issue and made the recovery procedure particularly troublesome but I don't think it changes anything as far as the principle is concerned.  The problem is, as far as I understand it, not if the drives are synced or if there is anything left in the buffer -- the issue here is journaling and the possibility of a mismatch between what's recorded in the journal and what is physically written to the drive itself. 

Finally -- even if what you're saying is true for a well implemented Linux system it doesn't have to be true when Windows and Windows filesystems are involved (especially NTFS which is poorly supported in Linux by default).

All I'm saying is that it is best to exercise caution and to use the hibernation mechanism as it was designed to work instead of experimenting with it and using it "creatively" for the sake of dubious benefits.

---

