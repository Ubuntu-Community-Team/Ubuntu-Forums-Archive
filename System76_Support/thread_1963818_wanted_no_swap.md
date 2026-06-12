---
title: "wanted no swap"
date: 2012-04-23
forum: System76 Support
---

### Post by Newbunto on 2012-04-23
I recently took delivery of a new system76 laptop. It has a SSD and a HDD, with the operating system installed on the SSD. I thought that in my 'delivery' instructions I asked for no swap partition (because I didn't want a swap partition on the SSD) but I seem to have got one anyway.

Why did this happen?

Is there some reason why I should have or have to have a swap partition?

Is there any easy way of fixing this? I don't count reinstalling from scratch as easy but are there detailed instructions for how to do this if that's the only way? (Maybe it would be a good idea to include an installation DVD with a new laptop.)

---

### Post by gardnan on 2012-04-23
First of all, I really think that you should have swap on your system, especially if your system has relatively low memory (512MB in my system and it can hit swap pretty hard). However, if you are absolutely CERTAIN that you don't need any more memory than what is in RAM, then you can disable the swap partition by removing in from the /etc/fstab file. However, if you want to completely get rid of the swap partition, then you would have to partition the disk, which would involve a reinstall.

However, I iterate again that it is HIGHLY RECOMMENDED that you have some swap on your computer. Don't go without it unless you really know what you are doing.

---

### Post by Newbunto on 2012-04-23
Yep, I know that I can disable the swap partition. That doesn't make its disk space available on the root file system though.

I am reasonably confident that I don't need a swap partition (16 GB of RAM) but the real point is that I can put a swap partition on the HDD if I find that I need a swap partition. Having an unnecessary swap partition on the relatively small and expensive SSD is not ideal.

PS Ubuntu 11.10 (64bit obviously)

---

### Post by prshah on 2012-04-23
> **Newbunto said:**
> 
Is there some reason why I should have or have to have a swap partition?


> **Newbunto said:**
> Yep, I know that I can disable the swap partition. That doesn't make its disk space available on the root file system though.

With 16GB RAM, you are right in thinking that you do not need a swap partition.

However, swap is required if you want the ability to hibernate.

If you do not want hibernate capability, you can use the terminal (Applications-Accessories-Terminal) command ```
sudo swapoff -a
``` to disable all swap, and then use gparted / palimpsest <?> to delete the swap partition. To expand your other partitions into the unallocated ex-swap space, you will have to boot off a live CD and use utilities such as gparted.

If you plan to move your swap partition to the HDD, the procedure is much the same. However, you have to ensure that your new swap space UUID is the same as the old one, or you have to make changes in hibernate setup. See this post for more details on this: [http://ubuntuforums.org/showpost.php?p=5176229&postcount=11](http://ubuntuforums.org/showpost.php?p=5176229&postcount=11) (Please also peruse the whole thread for background)

Unless you have a compelling need for the space, I would not bother to move the swap. With 16GB RAM it will hardly ever be used. If you want to make absolutely sure, reduce swappiness to 10 (or 0, but not recommended). Please see [http://ubuntuforums.org/showpost.php?p=10835952&postcount=2](http://ubuntuforums.org/showpost.php?p=10835952&postcount=2) for more details on this.

Please ignore any mentions of /etc/fstab. Ubuntu no longer REQUIRES a flat file for configuration; however, it will honour entries it finds there. If you don't have any relevant entries, do not add anything.

---

### Post by Newbunto on 2012-04-23
> To expand your other partitions into the unallocated ex-swap space, you  will have to boot off a live CD and use utilities such as gparted.This is the part that I am really hazy on. I don't have a live CD (DVD) for Ubuntu either.

> Unless you have a compelling need for the spaceRight now it's a 120 GB SSD with 16 GB that is "never" going to be used. With the price that SSDs are, that is far from ideal !

I don't have a compelling need for the space *right now* but I figure that it isn't going to get any easier to fix this - as I put more software and files on the disk.

As a first time Linux user it may be too hard but I will be sure to back up the SSD if I decide to try anything.

Edit: PS The swap is mentioned in fstab

---

### Post by Skaperen on 2012-04-23
> **Newbunto said:**
> This is the part that I am really hazy on. I don't have a live CD (DVD) for Ubuntu either.
Any chance you can buy a blank DVD and download the Ubuntu DVD for the version you have?  The live mode is integrated in the ISO.

Alternative is to wait for 12.04 LTS to release (3 days), download and burn a DVD for that, and do a full re-install yourself (use the manual partition section to leave your /home partition unchanged but to be mounted).  The install process will complain about lack of swap, anyway, but you can bypass that as I did.

---

### Post by isantop on 2012-04-23
> **Newbunto said:**
> I recently took delivery of a new system76 laptop. It has a SSD and a HDD, with the operating system installed on the SSD. I thought that in my 'delivery' instructions I asked for no swap partition (because I didn't want a swap partition on the SSD) but I seem to have got one anyway.

Why did this happen?

Is there some reason why I should have or have to have a swap partition?

Is there any easy way of fixing this? I don't count reinstalling from scratch as easy but are there detailed instructions for how to do this if that's the only way? (Maybe it would be a good idea to include an installation DVD with a new laptop.)

I should clarify (and this definitely *should* have been specified by the order; not sure why it wasn't) that we can't provide custom partitioning. It's just a simple limitation of the way we get Ubuntu onto our systems, but easy enough to work around with a reinstallation once you receive the system.

That said, it it *highly* recommended to run with an active swap partition. Otherwise, if the system RAM ever does fill, or can't empty fast enough, then the system *will* crash, and there's a potential for data loss there. Furthermore, I'd recommend keeping the swap in the SSD, because otherwise whenever the system swaps memory, it will have to wake up the hard drive, which takes time, and will be slower than the SSD anyway. In short, you'll negate most of the speed benefit you had going with the SSD in the first place.

---

### Post by Newbunto on 2012-04-23
> **Skaperen said:**
> Any chance you can buy a blank DVD and download the Ubuntu DVD for the version you have?  The live mode is integrated in the ISO.

I have now downloaded Ubuntu and made a bootable CD (and USB flash drive, just in case). I haven't tested either as yet.

I think this is good to have but I am starting to think that a full re-install is not viable as I have no idea what was pre-installed and what settings were made.

Maybe the next best option is to put a normal file system on the swap partition. So my 120 GB SSD would be 100% usable but as two separate file systems. For my purposes that is almost as good as having a 120 GB disk to use in a single file system.

---

### Post by Newbunto on 2012-04-24
> **isantop said:**
> I should clarify that we can't provide custom partitioning.

You should find somewhere on the Order window to say that.

You could provide a CD (DVD, flash drive?) with the laptop if the customer is going to have to do the install him/herself - but really you should provide that anyway.

---

### Post by isantop on 2012-04-24
> **Newbunto said:**
> you should provide that anyway.

Actually, it isn't really feasible for us to do this. It would increase the amount of waste we generate, and the CDs we would ship would be out of date in six months or less, rendering it useless. Therefore, it's easier on the environment for customers to use a custom-made CD. 

It's very easy to get the system back up to factory spec. The detailed instructions are here: [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System). This process will restore any drivers and modifications we made to the system for any given version of Ubuntu. Plus, it will work regardless of how your system is partitioned.

---

### Post by Newbunto on 2012-04-26
It's not "useless". I would rather have something out of date to boot from than nothing at all.

I understand your point about waste. If you were to provide it on a flash drive then it would not have to go to waste. Those who really didn't want it could reformat it and use it as normal. Those who did want it can still use it as a normal flash drive. The bootable Linux doesn't use much of the disk. The rest is usable. 4GB or 8GB would probably be about right as a compromise between space and cost. A Live flash drive can be kept up to date too if the user chooses to do so.

Experience suggests that it's better to create a Live-whatever *before *you need it. Much better for the blood pressure.

The Live-whatever could still be an alternative to the pre-install if the customer wants a partition other than your default partition.

I will consider the reinstall option.

---

### Post by Newbunto on 2012-04-29
> **isantop said:**
> It's very easy to get the system back up to factory spec.

That would not appear to be the case. :-( I will start another thread on that.

Another option for System 76 would be to give the user the choice of ordering a Live-whatever. So by default there is no waste but if the customer actually wants it, the customer gets it. I've already wasted several hours trying to get a Live-anything and would happily have paid a little bit more for my shipment to have included it and saved me the bother.

---

### Post by pqwoerituytrueiwoq on 2012-04-29
you can easily get rid of swap by booting a live usb/cd (try using unetbootin to make it)
open gparted and delete the swap partation and re-size the other partition on the left then edit your /etc/fstab file to not have swap and you are done

---

