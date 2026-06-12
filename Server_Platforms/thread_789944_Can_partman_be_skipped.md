---
title: "Can partman be skipped?"
date: 2008-05-11
forum: Server Platforms
---

### Post by whit on 2008-05-11
Is there a way to install Ubuntu Server without using partman? I know how to pre-partition the drive as I want, and format the partitions, outside of Ubuntu and before running its installer. I want to have Ubuntu accept that, rather than run me though a bolluxed process that on some systems ends up with partitions that don't properly end on cylinder boundaries (and that's not the only problem). If we take as given that I've partitioned, and formatted the partitions, and just want to instruct Ubuntu's installer which to mount as what and go ahead and install, is this possible? Can I tell Ubuntu "Here are the partitions I want to use. Don't touch the partition table. Don't format any partitions. Just install to them according to my selections."?

For those for whom partman works, it's fine I'm sure. It just doesn't work for me. It's so bad for my present purpose that I'll have to switch to a different distro if there's not a good way to work around it. So ... is there?

---

### Post by Sef on 2008-05-11
Moved to Server Platforms.

---

### Post by songshu on 2008-05-11
choose the option "do not format this drive" for each drive within partman and you are good to go.

do make sure the / target is empty otherwise it could get messy

---

### Post by koenn on 2008-05-11
> **songshu said:**
> choose the option "do not format this drive" for each drive within partman and you are good to go.

do make sure the / target is empty otherwise it could get messy
you're right about avoiding "dirty" targets, but actually, formatting the partitions IS a convenient way to accomplish that. 


The right way to install on pre-partitioned disks is, imo :

0. partition the disks any way you see fit
1. run the installer
2. when you reach the partitioning stage of the installer,
select "manually edit partition table". You might need to run the installer in expert mode for this option to be available, I don't remember. 

3. select an existing partition, (hit enter and) edit its properties :
* mount point
* select a filesystem (eg ext3, swap, ...)
* format Y/N   => "Yes" is a good idea
* ...

4. select "done setting up this partition"

5. repeat 3-4 for each partition you want to set up

6. select "write changes to disk" -- this is where your changes become effective

7. done

---

### Post by whit on 2008-05-11
Thanks both. Trying it now. Have a couple of HP ProLiant 360s with the HP (formerly Compaq) Smart Array 400i RAID controllers. Canonical claims that Ubuntu runs well on these. HP makes no claims for Ubuntu, but claims Debian Etch runs well on these. But with partman setting the partitions under Ubuntu 7.10, 8.04, or Debian Etch, partitions get set up which are not on cylinder boundaries.

Older HP firmware had some known trouble with some partitioning utilities, but even the latest version is somehow incompatible with partman. Evidently the people doing the compatibility testing at both Canonical and HP don't go to the trouble of looking closely at the partitions. Ubuntu and Debian install, but Linux partitions not set up to match the cylinder boundaries have a way of suddenly disappearing some time later.

I'm not seeing an option to run in the installer in expert mode. The question now is whether the "write changes to disk step" will result in partman's shifting the partitions off the cylinder boundaries, or whether it has the sense to leave them where they've already been set by fdisk. It would be nice, when the partitions are already marked for what's bootable, what's swap, and formatted if partman could just accept directions on what to install to, and do nothing more than pass those to the next stage. I'll be back with the results.

---

### Post by koenn on 2008-05-11
I think you can select "expert" through one of the function keys (F6, F10 ?) or by appending something to the boot statement. Well, with 6.06 at least. 

I'd be interested to know whether partman will actually changes values in your partition table if you tell it to do nothing (just give it mount points)

In case you want to try something else :
To completely skip the partman step, you'd have to run the installer in expert mode. This lets you randomly select/execute elements from the installation procedure. You could try to skip the 'partition disks" step and go straight to "install GRUB bootloader" but probably that won't work because  the installer wouldn't know where your / and /boot are going to be. Unless you can figure out a way to work around that (you can start a shell session during the install to tweak stuff - but I don't think it's going to be easy)

---

### Post by opus on 2008-05-11
You could also check into preseeding.  Preseeding allows you to automatically set those options and the installer won't even ask you.

I'm guessing though that if you don't make any changes to the partitions and only set the option to format the drives partman will do just that - only format, and not change the partitions themselves.

---

### Post by whit on 2008-05-11
Partman insists on saving changes, and insists on reformatting within the partitions selected. But thankfully it does not rewrite the partition table when it has not been asked to create any new partitions, but merely to select which ones to format and use. That's good enough! Thanks all.

If the "expert mode" is where there's the list of all the steps, and you can select which one to jump in at, I've been there before. When going to it from within the partman process, no matter where else I select - before or after that - it drops me right back into exactly where I was in the partman process that I was trying to either get around or back up and start again. Partman, IMHO, is a weak link even when it's not putting partition boundaries at unfortunate addresses.

---

### Post by songshu on 2008-05-11
if you start the computer with the install cd, you can type "expert" and hit enter to boot....

thats what it always been anyway unless something changed

---

### Post by songshu on 2008-05-11
you could offcourse load the live cd and debootstrap a new installation i think.

---

### Post by koenn on 2008-05-11
> **whit said:**
> 
If the "expert mode" is where there's the list of all the steps, and you can select which one to jump in at, I've been there before. When going to it from within the partman process, no matter where else I select - before or after that - it drops me right back into exactly where I was in the partman process that I was trying to either get around or back up and start again. Partman, IMHO, is a weak link even when it's not putting partition boundaries at unfortunate addresses.
Yes, that's because the debian installer remembers which questions were asked and answered, and comes back with the unanswered ones. You can avoid some of that with preseeding, there's an option to "don't ask twice". Still, you'd need to get through the partman phase to define the mount points,or work around that.

But at least you can get the partitions the way you wantd them  :)

---

### Post by whit on 2008-05-12
> **songshu said:**
> you could of course load the live cd and debootstrap a new installation i think.

In this case I'm remote from the systems, and installing over RILO (HP's version of a remote java-in-browser console). So the live CD would have been problematic. What I used to partition is the [System Rescue CD]("http://www.sysresccd.org/Main_Page"). Small image, solid set of tools, Gentoo based, and the best of several similar distros I tried in this context. 

Then it did turn out that partman, if used just to assign partition uses rather than to actually write the partitions, doesn't do anything harmful. Why something as flakey as partman has remained part of Debian and Ubuntu, when good old fdisk works better, is hard to guess.

---

### Post by whit on 2008-05-12
> **koenn said:**
> Yes, that's because the debian installer remembers which questions were asked and answered, and comes back with the unanswered ones.

It seems to peculiarly do this in the partitioning process. So you can't, for instance, start to look at what the "Guided" partitioning would offer you, decide you need something different, back up, and go down the custom fork. It just won't let you. It gives you choices which *should* do that. It pretends to offer you freedom and control. But whatever you choose it drops you right back where you'd decided you didn't want to be. That's the worst of all possible worlds. You have to begin the installation from the beginning, since trying to go a step or two back from anywhere in the partman process just runs you around in circles. Instead of a clear message, "You don't have a choice. I won't let you." partman forces you to discover on your own that it's trapped you in a circular hell.

Or maybe I missed the way out. This isn't supposed to be a text Adventure game though. Is it?

---

### Post by koenn on 2008-05-12
> **whit said:**
> 
Or maybe I missed the way out. This isn't supposed to be a text Adventure game though. Is it?
I think there actually is a way out. After every user choice, the installer recalculates the current state of what will becaome the partition table. Before "write changes to disk", you can still manually select and edit partitions, up to delete whatever the "guided partitioning" cooked up and start all over. I think. don't remember exactly, I usually go straight to "edit manually".

---

