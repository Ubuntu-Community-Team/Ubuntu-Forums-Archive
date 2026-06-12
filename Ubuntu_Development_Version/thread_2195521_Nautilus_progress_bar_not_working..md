---
title: "Nautilus progress bar not working."
date: 2013-12-24
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-12-24
While transferring a couple of files to my server, I noticed the progress bar wasn't working, it got stuck at preparing to move file. Before I create a bug report, I was wondering if any one else has run into the same thing

---

### Post by ventrical on 2013-12-24
Not here. Works great from usb to hdd.

---

### Post by Cavsfan on 2013-12-24
Haven't had any problems with it. I copied a few hundred meg of songs to Trusty from another partition and it worked fine.

---

### Post by cariboo on 2013-12-24
I was transferring a couple of 1.4GiB .mkv files when I noticed it. I've got a 100Mps network so it takes a bit of time to transfer the files, that's why I noticed it, when transferring smaller files the progress bar isn't there long enough to notice a problem.

---

### Post by P-I H on 2013-12-25
I have problem on my system to transfer big files to my NFS mounted server. 
I have added information to this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585657)

---

### Post by Elfy on 2013-12-25
> **cariboo907 said:**
> I was transferring a couple of 1.4GiB .mkv files when I noticed it. I've got a 100Mps network so it takes a bit of time to transfer the files, that's why I noticed it, when transferring smaller files the progress bar isn't there long enough to notice a problem.

Installed nautilus to check here. Moved 3Gb of files about, didn't see anything here. 

I assume that while the progress bar was 'stuck' the files were actually being processed and moved. 

That said I've not tried moving them across the network. I'll have a look at that later.

---

### Post by cariboo on 2013-12-25
The files moved with no problem, and the progress bar disappeared when the move was done.

---

### Post by ventrical on 2013-12-25
I had the same with the Raring and Saucy dev but it self healed near release day.

---

