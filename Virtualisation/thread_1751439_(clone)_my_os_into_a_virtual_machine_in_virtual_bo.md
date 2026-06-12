---
title: "(clone?) my os into a virtual machine in virtual box?"
date: 2011-05-06
forum: Virtualisation
---

### Post by ClientAlive on 2011-05-06
Well I figured a question like this would have come up a few times by now; but, after a little searching I didn't really see anything that looks the same.

I have Ubuntu 10.04 running and recently installed Oracle VM Virtual Box. One of the main reasons was to have my same o/s in it to do trial runs, use it for learning code without hurting anything, etc.

So here's my question:

Is there any easy way (by that I mean a way I can grasp) to clone my current o/s into virtual box. I don't know if "clone" is the right word to use. I just mean making an exact replica of it as a virtual machine in there.

What if I were to make a recovery disc out of my current o/s and install from that in vb? Or something like that?

Can anyone explain?

Thanks

---

### Post by b0b138 on 2011-05-06
You could try using remastersys to make an iso of your current install then use that to install into the vm.  Not sure if this would be enough of a clone for you though.

Or you could use the dd command to make a copy of your current install to a file.  Then again to write it to the vm hd.  Both would need to be done from a live cd, on your system and in the vm.

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

---

### Post by ClientAlive on 2011-05-07
> **b0b138 said:**
> You could try using remastersys to make an iso of your current install then use that to install into the vm.  Not sure if this would be enough of a clone for you though.

Or you could use the dd command to make a copy of your current install to a file.  Then again to write it to the vm hd.  Both would need to be done from a live cd, on your system and in the vm.

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)


Thanks bob138. Under the circumstances I'm not sure this would work though. Unless I missed something in that article the destination for the data has to be larger than the source.

Here's my situation:

I have about a 40 gig hard drive with a default install of 10.04 and a bunch of additions (apps) to it by this point (which also change configurations files and such in the system I hear). So two partitions I think. I have a standard install of 10.04 in virtual machine set to eat up a max of 8 gig. Truthfully, that 8 gig is probably about all I can spare for this. I certainly don't have double the amount of space as the amount of space.

One of the main reasons for wanting my o/s in a virtual machine is to make trial runs of things before I do it on my real, host o/s. I'm just not sure how effective those trial runs would be if there is a big enough difference between my host o/s and the guest o/s. If the results of the trial run were off somehow I could still end up breaking my host o/s when applied those things to it - right?

---

### Post by ClientAlive on 2011-05-08
bump

---

### Post by lmarmisa on 2011-05-08
Try to use [Clonezilla Live]("http://www.clonezilla.org/clonezilla-live.php"). You should select the option hard drive backup and use a second hard drive (for example, an external USB hard drive) for storing the backuped files.

Then, create a virtual machine with a virtual disk (dynamically expanding storage) with the same size of your physical hard drive, boot this virtual machine into Cloezilla Live and restore your backuped files in the virtual hard drive.

---

### Post by ClientAlive on 2011-05-09
> **lmarmisa said:**
> Try to use [Clonezilla Live]("http://www.clonezilla.org/clonezilla-live.php"). You should select the option hard drive backup and use a second hard drive (for example, an external USB hard drive) for storing the backuped files.

Then, create a virtual machine with a virtual disk (dynamically expanding storage) with the same size of your physical hard drive, boot this virtual machine into Cloezilla Live and restore your backuped files in the virtual hard drive.


I just grabbed the clonezilla iso tonight, actually. I was kinda hoping to install more than one o/s in that vm. Wonder if clonezilla will let me put it in the vm under less space? Just have to try it out I guess.

Thanks

---

