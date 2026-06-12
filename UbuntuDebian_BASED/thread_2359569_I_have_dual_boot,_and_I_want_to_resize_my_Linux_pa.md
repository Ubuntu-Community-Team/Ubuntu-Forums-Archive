---
title: "I have dual boot, and I want to resize my Linux partition"
date: 2017-04-25
forum: Ubuntu/Debian BASED
---

### Post by justpeaceful2504 on 2017-04-25
Hi, I have like 30gb on my Linux partition and I dont have memory left so I looked up in my partitions and I have like 160 gb unused, how can I put them into my Linux partition.
[IMG]http://i.imgur.com/OA9Km5b.png[/IMG]

---

### Post by howefield on 2017-04-25
What version of Ubuntu are you using and do you have anything slightly unusual on the current Linux partition like LVM or encryption ?

---

### Post by justpeaceful2504 on 2017-04-25
Oh, Im so sorry Im not even using ubuntu Im on Kali-Linux but can you help me tho?

---

### Post by howefield on 2017-04-25
> **justpeaceful2504 said:**
> Oh, Im so sorry Im not even using ubuntu Im on Kali-Linux but can you help me tho?

Cool, half a question answered is better than none at all. 

In the meantime thread move to the "*Ubuntu/Debian BASED*" forum.

---

### Post by yancek on 2017-04-25
If you have a standard MBR install which seems to be indicated in the image you posted and if you are not using something non-standard like LVM and if the tool you are using is portraying information accurately, you should be able to delete the 'swap' partition, unmount the 161GB partition then delete it and extend the 27.94 partition (whatever that shows as) into what is now unallocated space to the size you want.  You can only extend a partition to 'contiguous' space which is why you would need to delete the swap, other wise you cannot get to the 161GB partition.  This will work if the information you posted is accurate, the partitions in question are all logical and the other windows are primary.  I've never used the tool you are using so I don't know how accurate it is.

Due to the risk off changing partitions, I would suggest you do a backup of any important data prior to changing the partitions.

---

### Post by Bucky Ball on 2017-04-25
Just a word and in case this was your plan: you don't resize any Linux partitions using Windows tools. :) ALWAYS use Linux tools to resize the Linux OS partition. Just a heads up as you have posted a Win disk manager screen shot which suggests you may be planning to resize the partition with Win tools. You will need to boot to a live session ('Try Ubuntu' from the install disk) and use Gparted from there to resize the Linux partition.

Apart from other considerations, to do the job you will need to delete your /swap partition, delete the partition you want to expand the OS partition into (you need unallocated space to expand the partition to, you can't merge the two partitions that I know of), then resize you OS partition into the free space, leaving 4Gb of free space at the end of that partition to recreate the /swap. Done. :)

So, you are not joining the two partitions exactly. You are deleting the big one and expanding the OS partition to use the unallocated space created.

Good luck.

---

### Post by ajgreeny on 2017-04-25
It will be a great deal easier to help you if you can possibly boot to the live Ubuntu system (or perhaps live kali, if gparted can be used in that) and show us a screenshot of the disk from gparted.

Messing about with partitions that are described as "other" in your screenshot is risking big problems as we have no idea what they are nor how much of each is already used.  I see both of them say 0 space remaining unused, but I wonder if that is because the **Mini-tool partition wizard** you used can not read them.  I am surprised, however, that it does appear to recognise a Linux-swap partition.

Gparted from a live system will be much more informative and a lot safer, but backup all personal files first just in case all goes to worms.

---

### Post by howefield on 2017-04-25
In addition to the above I'd offer an alternative and that would to create a Data partition out of the unallocated space and symlink your data folders to it, eg Documents, Downloads, Music, Pictures and Video folders. Would that free enough space from your existing root partition ?

Either way if you delete the swap partition and then recreate it or create a "Data" partition you are going to have to edit your /etc/fstab file with updated information.

---

### Post by justpeaceful2504 on 2017-04-26
Here is a photo from GParted, so I should delete the swap one, delete the ext4 and create a new one ? Can you be more detailed please?

[IMG]http://i.imgur.com/0FO3FzD.png[/IMG]

---

### Post by justpeaceful2504 on 2017-04-26
And I cannot access my windows files, I could do it like 1-2 months ago.
[IMG]http://i.imgur.com/wjT6lRz.png?1[/IMG]

---

### Post by SuperFreak on 2017-04-26
Your Root Partition (/) should not be that full. It might be best to find out what the problem is there. Sometimes the sys.log or kern.log files fill up due to an error in the system

EDIT: By the way what you are proposing is taking over the Home partition to expand your Root Partition. Not a good plan

---

### Post by LastDino on 2017-04-26
+1 To superfreak

I've never used more than 25 GB on any of installations for  "/", I would start this by finding out what is actually filling it up. 

There is actually no real need to resize if you can free that space up, isn't it?


Also, Free MiniTool Disk partitioning for windows (from your opening post) does work well with Linux partitions and resizing operations, I use it when I'm in windows and have to perform such a operations, yet to have any issues. 

Please find out what is filling out your "/"

---

