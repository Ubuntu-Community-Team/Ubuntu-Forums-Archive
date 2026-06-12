---
title: "Win7 borks partition, a what not to do when installing win7."
date: 2010-05-10
forum: The Cafe
---

### Post by MasterNetra on 2010-05-10
After starting my own web design business (nothing special just a sole proprietorship), i find myself needing to go back to windows to use my old CS3 suite because I only have 1GB of ram and its not enough to split between Ubuntu and Win7...well not enough to run CS3 on a VMed Win7 anyway nor would running it on a VMed xp be a good idea as it would take forever to do anything with CS products. 

Anywho, So I had reluctantly inserted the Win7 media into the computer and started installation. Well apparently after I had wiped partitions I forgot to manually set them up I clicked next with the unpartitioned space selected, after click i realize this but shrugged assuming Windows was going to take care of it properly and it seemed to. It unpacked, installed, and loaded fine. I got everything on windows setup, including CS3 which takes a couple of hours to install. Its nearly time for me to start my work week but I still had time to install ubuntu real quick. 

So I poped in the Ubuntu CD and restarted the computer, after loading I bring up GParted and to my surprised only one NTFS partition and it had a caution icon. But I continued forward and attempted to downsize the partition, which failed rather quickly spewing errors in the log that I haven't the slightest clue as to what they even could even possibly mean. I try this with multiple Distros and utilities with the same response. Checked Win7's fragmentation, it was fine. So I guess the moral of the story, assumptions are bad mkay and always use linux to handle partition formatting and such create the space windows needs, manually go and create ntfs space and when prompted let windows create its little 100mb partition (aka System reserve).

Guess what I'm going to be doing all day this Saturday?

---

### Post by betrunkenaffe on 2010-05-11
Title is misleading. More appropriate "I borked partition, what not to do when installing win7"

I've experienced issues with partitions before and most of the time they are with the windows side however not always.

---

### Post by MasterNetra on 2010-05-11
> **betrunkenaffe said:**
> Title is misleading. More appropriate "I borked partition, what not to do when installing win7"

I've experienced issues with partitions before and most of the time they are with the windows side however not always.

While yes it is my fault for letting Windows 7 handle the Unpartitioned space on its own. Should it really be too much to ask for it to set it up probably, it seems to have no problem of telling you how it wants it done, but when it is set to do it on it's own, it fraks it up.

---

### Post by wilee-nilee on 2010-05-11
I had the same thing happen to me twice when I let W7 format/partition the open space. If you pre-format the ntfs partitions with gparted first this doesn't happen.

---

### Post by MasterNetra on 2010-05-11
> **wilee-nilee said:**
> I had the same thing happen to me twice when I let W7 format/partition the open space. If you pre-format the ntfs partitions with gparted first this doesn't happen.

It also seems fine when you set it up manually through Win7, if you try using all the unpartitioned space in a single ntfs partition win7 prompts requesting to take some of it for small system reserve parition (which I think just houses parts if not all of booting files). I let it create the mini partition and move forward.

---

### Post by betrunkenaffe on 2010-05-11
Don't know if this is correct way of saying it but seems the Windows partitioner is a "best effort" one. If it doesn't get it right but it can use it, it just keeps on trucking.

I was just pointing out that not all Linux partitioners are flawless either :)

---

### Post by wilee-nilee on 2010-05-11
> **MasterNetra said:**
> It also seems fine when you set it up manually through Win7, if you try using all the unpartitioned space in a single ntfs partition win7 prompts requesting to take some of it for small system reserve parition (which I think just houses parts if not all of booting files). I let it create the mini partition and move forward.

I always manually build the partitions, except for the 2 times I mentioned. It makes sense that this would work as your limiting the size with a manual method. It is to bad both Ubuntu and MS can't find better ways to auto install, I think the Ubuntu way is okay but you have to know where to put grub, if your dual booting, and using multiple HD's. 

I have never lost any thing though I keep everything needed off the computers on a HD, and only copies of them on the actual computers.

---

### Post by MasterNetra on 2010-05-11
> **wilee-nilee said:**
> I always manually build the partitions, except for the 2 times I mentioned. It makes sense that this would work as your limiting the size with a manual method. It is to bad both Ubuntu and MS can't find better ways to auto install, I think the Ubuntu way is okay but you have to know where to put grub, if your dual booting, and using multiple HD's. 

I have never lost any thing though I keep everything needed off the computers on a HD, and only copies of them on the actual computers.

I should invest in a backup drive one of these days when the money is available...

---

### Post by CharlesA on 2010-05-11
I haven't had any problems with installing Windows 7 to the entire drive, then shrinking the NTFS volume from Disk Managemant. Installed both Ubuntu and BackTrack along side it.

The 100MB partition that Win7 setup creates is for the boot files.

---

### Post by MasterNetra on 2010-05-11
> **CharlesA said:**
> I haven't had any problems with installing Windows 7 to the entire drive, then shrinking the NTFS volume from Disk Managemant. Installed both Ubuntu and BackTrack along side it.

The 100MB partition that Win7 setup creates is for the boot files.

The problem is that Win7 took all the space converted into only one ntfs partition and put everything there and created a number of errors on the partition that prevent the partition's resizing, for me there currently is not a separate 100mb partition. In the past when it did install correctly I had no issues in resizing either.

---

### Post by Swagman on 2010-05-11
I thought everyone knew that Microsoft expects you ...

To play it their way

or 

No way.

And YES they **DO** want their ball back.. nyah nyah dee nyah nyah !!

---

### Post by deanhopkins on 2010-05-11
After my last Win7 install, my Extended partition containing a 120gb crunchbang install was completely missing after rebooting when the install was complete.

Great.

---

### Post by tad1073 on 2010-05-11
Sounds like you need to run chkdisk in widows...

---

### Post by Diluted on 2010-05-11
I'm surprised you went ahead and resized despite the warnings, especially when you're messing with partitions.

It would be interesting to see the error log, since it may point to the problem. Windows uses different cylinder boundaries, so maybe the partitioning tool is freaking out because of this.

---

### Post by MasterNetra on 2010-05-11
> **Diluted said:**
> I'm surprised you went ahead and resized despite the warnings, especially when you're messing with partitions.

It would be interesting to see the error log, since it may point to the problem. Windows uses different cylinder boundaries, so maybe the partitioning tool is freaking out because of this.


It didn't really matter though as it refused to do anything to the partition.

> **tad1073 said:**
> Sounds like you need to run chkdisk in widows...

It found 5 corrupt attribute records (128,""), nothing else it seems. It removed them so I guess I'll try firing up ubuntu once more and see if the problem is solved.

---

