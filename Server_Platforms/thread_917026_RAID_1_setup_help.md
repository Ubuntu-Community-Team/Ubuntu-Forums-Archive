---
title: "RAID 1 setup help"
date: 2008-09-11
forum: Server Platforms
---

### Post by brad8266 on 2008-09-11
I want to setup a RAID 1 array using 2 hard drives. I already have the OS loaded on the first drive and I installed and partitioned the second drive. I cant create the array with mdadm now because the first drive (sda) is busy. Do I need to boot to a live disk to accomplish this or what?? If so where do I download a live disk image from?

Thanks

---

### Post by brad8266 on 2008-09-11
.....

---

### Post by Krupski on 2008-09-11
> **brad8266 said:**
> 1. I have backup already in place.
2. I need to setup raid.
3. None of your posts have addressed the topic.
4. You arent thinking out of the box at all, redundant disks and backup are 2 standard items, nothing new.

I have multiple archived backups already in place in case of drive/file corrpution or a fire in the building. Now can we get to the topic please? 8 replies and none are on topic.

OK let's see if I can help you...

First let me ask... are both hard drives the same capacity (and hopefully exactly the same type)?

Next let me ask... is your CURRENT OS installation expendable? Things would be a lot easier if you could start from scratch.

What will ultimately have to happen is that you boot up with a live CD (so the hard drives are not locked because of being in use) then install 'mdadm', create the RAID array, possibly create a link to the array drive and finally install to the link name.

You could probably boot up with a live CD, then by running 'mdadm', create the array and let the driver re-sync the two drives together.

Problem is, I don't know WHICH drive would be sync'd to which!

That's why I said it would be easier if you could start from scratch.

Let me know the answers to these questions then we can proceed to the next steps.

(p.s. I assume you want RAID-1 (mirror))?

-- Roger

---

### Post by brad8266 on 2008-09-11
1.It is expendable right now so I dont care if it rebuilds but I would rather it successfully sync as is though with the OS alrerady on the one disk. Like you said that may not work though.
2. The hard drives are different but are partitioned to match each other.
3. yes RAID 1 is all I want.
4. Where can I download a live cd image from or do I need to create it?

---

### Post by Krupski on 2008-09-11
> **brad8266 said:**
> 1.It is expendable right now so I dont care if it rebuilds but I would rather it successfully sync as is though with the OS alrerady on the one disk. Like you said that may not work though.
2. The hard drives are different but are partitioned to match each other.
3. yes RAID 1 is all I want.
4. Where can I download a live cd image from or do I need to create it?

You can download the live CD from the main Ubuntu site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Be sure you DO NOT check the "alternate desktop CD" box... as this one does NOT have the live CD feature.

Since your data is expendable, you may wish to try this: (pseudo-instructions first):

* Boot live CD
* Use 'dd' to zero-fill the two partitions you wish to marry together as a RAID device
* Install mdadm
* Run mdadm - create the array
* Format the array with EXT3
* Install Ubuntu fresh on the array
* During install, choose manual partitioning so that the installer does not re-do your RAID array
* During GRUB install (occurs at the end of the Ubuntu install), make sure GRUB sets up the proper boot device.

If this makes sense, then let me know if there any steps that you need detailed instructions for and I'll post it for you.

-- Roger

---

### Post by brad8266 on 2008-09-11
I have the CD that I used to load Ubuntu in the first place, this is the right CD?? I cant get this to do anything.

---

