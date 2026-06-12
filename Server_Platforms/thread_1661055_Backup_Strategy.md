---
title: "Backup Strategy"
date: 2011-01-06
forum: Server Platforms
---

### Post by johmut on 2011-01-06
Hi All, 

All my data is stored on a separate device/partition: a 2TB USB disk with one ext4 partition. 
I have 3 more USB disks: 1x 1TB + 2x 500GB = 2TB right ? 

I want to backup my data from the 2TB volume to the (older/slower/cheaper) other volumes combined. 

I am thinking to use LVM to group the 3 smaller USB disks into one 2TB logical volume and use that to back up the 2TB primary volume. Do you think that is a good idea ? 

In case of disaster I can replace the 2TB primary disk and restore from my 2TB logical volume right ? 
What happens if :

[LIST]
[*]I have to replace my internal hard disk and reinstall ubuntu ? 
Can I re-attach the logical volume ?
[*]One of the physical volumes of my volume group dies ? 
Can I remove it and replace it with a new physical volume (bound to have other dimensions) ?
Understandably I will loose my backup data.... or ?
[/LIST]
PS: running Ubuntu 10.10 

TIA for any help you can provide,
Best Regards,
johmut

---

### Post by elico on 2011-01-06
you can bakcup the 2tb FS in other methods instead of LVM
LVM is nice but if you can avoid it in this case i would say i like it without LVM

---

### Post by johmut on 2011-01-07
> **elico said:**
> you can bakcup the 2tb FS in other methods instead of LVM
LVM is nice but if you can avoid it in this case i would say i like it without LVM

OK, how would you do it then ? Can you explain a bit why LVM is not a good idea and how your approach would be better ? 

TIA &
Best Regards,
Johmut

---

### Post by vortmax on 2011-01-09
I agree, LVM is not the way to go.  I've tried it several times, and it is more of a pain than its worth.

Do you actually have 2TB worth of data to backup or does the disk have a lot of empty space?  I would personally just tar and gzip (or bzip) the data, then copy it over.  Depending on what kind of data it is, you might be able to fit the entire compressed archive on the 1Tb drive.

---

### Post by johmut on 2011-01-09
> **vortmax said:**
> I agree, LVM is not the way to go.  I've tried it several times, and it is more of a pain than its worth.

Do you actually have 2TB worth of data to backup or does the disk have a lot of empty space?  I would personally just tar and gzip (or bzip) the data, then copy it over.  Depending on what kind of data it is, you might be able to fit the entire compressed archive on the 1Tb drive.

Thanks, but my data is music and video so I don't expect to much of a compression ratio.

What seems to be the problem with LVM ? I know for example IBM uses it exclusively on their AIX systems.
I was thinking if it's good enough for professional hosting services it should definitely be good enough for me. Sorry to be a bit pushy but it seemed like the right tool for the job, I need to understand why it's not. 

TIA and
Best Regards,
johmut

---

### Post by koenn on 2011-01-09
the downsides of LVM are the ones you point out in your own OP :

1/ if one disk of the group dies, the whole group goes, and all data is gone

2/ LVM is software. If you need to reinstall your system, you'd have to rebuild the exact same LVM config and get the disks to take their place in it. The disks themselves will have some LVM info written on them, which might help, but it's still additional complexity and room for failure. 
You do not want complexity and room for failure in a restore. 

You should actually just try this. Attach the disks to a computer, configure them into 1 LV, put data on it (enough to fill more than 1 disk). Then reinstall the system and see what it takes to get access to that data again. 
Then judge if that's an acceptable restore procedure with acceptable risk for you

---

