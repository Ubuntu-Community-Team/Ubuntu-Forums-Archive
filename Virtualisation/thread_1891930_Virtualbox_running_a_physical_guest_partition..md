---
title: "Virtualbox running a physical guest partition."
date: 2011-12-06
forum: Virtualisation
---

### Post by jrisreal on 2011-12-06
How would I go about doing this?  I've googled it and found answers, but none of them were clear enough for me.  I haven't used linux for a while and I'm just getting back into the flow of things, so something geared towards windows users/linux noobs would be great.

Now, I just find it really annoying to have to reboot out of linux in order to run my windows disc and work on music.  My Digital Audio Workstation is FL Studio and it's windows-only.  I can run it in wine, but it gives very high latency, plus all my VST's Samples and whatnot are on my partition, which would be difficult to copy over to wine.

Thanks in advance for any help,
 -Evangelist Music

---

### Post by leclerc65 on 2011-12-07
I have Windows run inside Virtualbox. Win and Ubuntu share a NTFS data partition (mounted at boot by 'ntfs-config'). I found that is my ideal compromise. I still need Win for my GPS, and I hate dual booting like you.

---

### Post by haqking on 2011-12-07
Though you can run a physical partition as a VM it is not recommended and may result in your trashing your partition.

However you can take an image of it using something like [www.clonezilla.org](www.clonezilla.org) and then re-cloning that image back into a VM for use whilst in Linux.

Any changes made to the VM wont reflect on the actual partition of course.

Cheers

---

### Post by jrisreal on 2011-12-07
> **haqking said:**
> Though you can run a physical partition as a VM it is not recommended and may result in your trashing your partition.

However you can take an image of it using something like [www.clonezilla.org]("http://www.clonezilla.org") and then re-cloning that image back into a VM for use whilst in Linux.

Any changes made to the VM wont reflect on the actual partition of course.

Cheers
wow thanks!  I think I'm going to go with this, back up my Windows drive to external HDD, and delete the windows partition, making more space for linux

---

### Post by haqking on 2011-12-07
> **jrisreal said:**
> wow thanks!  I think I'm going to go with this, back up my Windows drive to external HDD, and delete the windows partition, making more space for linux

make sure you check the integrity of your backups and clones and of course the ability to restore before removing any partitions or data of course.

Good luck

---

### Post by jrisreal on 2011-12-07
> **haqking said:**
> make sure you check the integrity of your backups and clones and of course the ability to restore before removing any partitions or data of course.

Good luck
I'm not worried about that, the integrity on the existing partition is pretty crapped, but it still boots, so I can run my audio programs atleast.

---

